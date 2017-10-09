# Docker OXID eShop 6
Docker Container with PHP 7, MySQL 5.7 and OXID eShop 6 (beta)

## Installation

- [Pull this repo](https://github.com/proudcommerce/docker-oxid6.git)
  Sugestion: use a directory under your User directory!
  f.e. 
  cd /c/Users/jvelletti/ 
  mkdir sites 
  cd sites 
  git clone git@github.com:velletti/docker-oxid6.git shop 
  this will create the folder /c/Users/jvelletti/sites/shop
  
- [Install docker compose](https://docs.docker.com/compose/install/) (should be done with docker Toolbox, if have an older Wondwos system or no HYPER V or want to use Virtual box and vagrant in parallel for other projects !)

- Change into container directory: `cd container`
- Change volume mappings:
    `vi docker-compose.yml`
    HINT: Using MAC OS or Windows, the source path path with your project should be unter your "users" path, as docker will sync files to those directorys. 
    f.e. if you have a windows mashine and your usersname is jvelleti, change the volume mapping to 
    /c/Users/jvelletti/sites/shop/data/:/var/www/html
    on MAC OS:
    /c/User/sites/shop/data/:/var/www/html
    see also : https://docs.docker.com/docker-for-mac/osxfs/
    
- Create docker images and container:
    `docker-compose build`
- Fire up docker container:
    `docker-compose up` (for background: `docker-compose up -d`)
- Connect to apache container:
    `docker exec -ti oxid6_apache bash`
- Change to www-root:
    `cd /var/www/html/`
- [Install composer](https://getcomposer.org/download/)
  or use this line :
  
  - curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer creates=/usr/local/bin/composer
  
- [Install OXID](http://oxid-eshop-developer-documentation.readthedocs.io/en/latest/getting_started/eshop_installation.html)
  - cd /var/www
  - composer create-project --no-dev oxid-esales/oxideshop-project shop6beta dev-b-6.0-ce
  
  will create /var/www/shop6beta/source and  /var/www/shop6beta/vendor
  
  - ln -s /var/www/shop6beta/source folder to /var/www/html  
  (if possible)  
  
  - Note:
    At the oxid shop installatin you will be asked for the database hostname, to find the correct hostname do the following:
    `docker ps`
    `docker inspect [CONTAINER ID of oxid6_mysql]`
    search for "IPAddress"

- Have fun ...


## Support

Feel free to create pull requests ;-)

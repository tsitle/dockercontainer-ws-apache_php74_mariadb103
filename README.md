# Apache2 + PHP 7.4 + MariaDB 10.3 Client Docker Container for AARCH64, ARMv7l, X86 and X64

For hosting PHP powered websites.

## Required Docker Image
The Docker Image **ws-apache-php74-mariadb103-\<ARCH\>** will automaticly be downloaded from the Docker Hub.  
The source for the image can be found here [https://github.com/tsitle/dockerimage-ws-apache\_php74_mariadb103](https://github.com/tsitle/dockerimage-ws-apache_php74_mariadb103).

## Docker Container usage
- copy the file `docker-compose-<ARCH>-SAMPLE.yaml` to `docker-compose.yaml`
- edit the file as needed
- run `$ ./dc-ws-apache.sh up`

To stop the container run `$ ./dc-ws-apache.sh down`

## Docker Container configuration

- CF\_PROJ\_PRIMARY\_FQDN [string]: FQDN for website (e.g. "mywebsite.localhost") (default: empty)
- CF\_SET\_OWNER\_AND\_PERMS\_WEBROOT [bool]: Recursively chown and chmod CF\_WEBROOT? (default: false)
- CF\_WWWDATA\_USER\_ID [int]: User-ID for www-data (default: 33)
- CF\_WWWDATA\_GROUP\_ID [int]: Group-ID for www-data (default: 33)
- CF\_ENABLE\_CRON [bool]: Enable cron service? (default: false)
- CF\_LANG [string]: Language to use (en\_EN.UTF-8 or de\_DE.UTF-8) (default: empty)
- CF\_TIMEZONE [string]: Timezone (e.g. 'Europe/Berlin') (default: empty)
- CF\_ENABLE\_HTTP [bool]: Enable HTTP for Apache? (default: true)
- CF\_CREATE\_DEFAULT\_HTTP\_SITE [bool]: Create default HTTP Virtual Host for Apache? (default: true)
- CF\_ENABLE\_HTTPS [bool]: Enable HTTPS/SSL for Apache? (default: false)
- CF\_CREATE\_DEFAULT\_HTTPS\_SITE [bool]: Create default HTTPS/SSL Virtual Host for Apache? (default: true)
- CF\_SSLCERT\_GROUP\_ID [int]: Group-ID for ssl-cert (default: 102)
- CF\_DEBUG\_SSLGEN\_SCRIPT [bool]: Enable debug out for sslgen.sh?
- CF\_CSR\_SUBJECT\_COUNTRY [string]: For auto-generated SSL Certificates (default: DE)
- CF\_CSR\_SUBJECT\_STATE [string]: For auto-generated SSL Certificates (default: SAX)
- CF\_CSR\_SUBJECT\_LOCATION [string]: For auto-generated SSL Certificates (default: LE)
- CF\_CSR\_SUBJECT\_ORGANIZ [string]: For auto-generated SSL Certificates (default: The IT Company)
- CF\_CSR\_SUBJECT\_ORGUNIT [string]: For auto-generated SSL Certificates (default: IT)
- CF\_WWWFPM\_USER\_ID [int]: User-ID for wwwphpfpm (default: 1000)
- CF\_WWWFPM\_GROUP\_ID [int]: Group-ID for wwwphpfpm (default: 1000)
- CF\_PHPFPM\_RUN\_AS\_WWWDATA [bool]: Run PHP-FPM process as user/group www-data ? (default: false)
- CF\_PHPFPM\_ENABLE\_OPEN\_BASEDIR [bool]: (default: false)
- CF\_PHPFPM\_UPLOAD\_TMP\_DIR [string]: (default: "/var/www/upload\_tmp\_dir")
- CF\_PHPFPM\_PM\_MAX\_CHILDREN [int]: (default: 5)
- CF\_PHPFPM\_PM\_START\_SERVERS [int]: (default: 2)
- CF\_PHPFPM\_PM\_MIN\_SPARE\_SERVERS [int]: (default: 1)
- CF\_PHPFPM\_PM\_MAX\_SPARE\_SERVERS [int]: (default: 3)
- CF\_PHPFPM\_UPLOAD\_MAX\_FILESIZE [sizestring]: (default: "100M")
- CF\_PHPFPM\_POST\_MAX\_SIZE [sizestring]: (default: "100M")
- CF\_PHPFPM\_MEMORY\_LIMIT [sizestring]: (default: "512M")
- CF\_PHPFPM\_MAX\_EXECUTION\_TIME [int]: (default: 600)
- CF\_PHPFPM\_MAX\_INPUT\_TIME [int]: (default: 600)
- CF\_PHPFPM\_HTML\_ERRORS [bool]: (default: false)

Only on X64:

- CF\_ENABLE\_XDEBUG [bool]: Enable XDebug PHP module? (default: false)
- CF\_XDEBUG\_REMOTE\_HOST [string]: Remote Host for XDebug (default 'dockerhost')

## Using cron
If you'd like to use cron you'll also need to copy the file `mpcron/crontab-template` to
`mpcron/<USERNAME>`.  
E.g. for installing a crontab for the user "www-data" copy the file to `mpcron/www-data`.  
Then uncomment the mountpoint for that file in the `docker-compose.yaml`.

---
title: "configuration issue with respect to .htaccess file on ubuntu"
date: 2013-06-28
forum: Server Platforms
---

### Post by jamesbon on 2013-06-28
I am building an application tshirtshop I have following configuration in 


/etc/apache2/sites-enabled/tshirtshop

> <VirtualHost *:80>
            ServerAdmin webmaster@localhost
            DocumentRoot /var/www/tshirtshop
            <Directory /var/www/tshirtshop>
                    Options Indexes FollowSymLinks
                    AllowOverride All
                    Order allow,deny
                    allow from all
            </Directory>
            ErrorLog ${APACHE_LOG_DIR}/error.log
            # Possible values include: debug, info, notice, warn, error, crit,
            # alert, emerg.
            LogLevel warn
            CustomLog ${APACHE_LOG_DIR}/access.log combined
    </VirtualHost>




and following in .htaccess file in location


/var/www/tshirtshop/.htaccess

> 
    <IfModule mod_rewrite.c>
    # Enable mod_rewrite
    RewriteEngine On
    # Specify the folder in which the application resides.
    # Use / if the application is in the root.
    RewriteBase /tshirtshop
    #RewriteBase /
    # Rewrite to correct domain to avoid canonicalization problems
    # RewriteCond %{HTTP_HOST} !^www\.example\.com
    # RewriteRule ^(.*)$ http://www.example.com/$1 [R=301,L]
    # Rewrite URLs ending in /index.php or /index.html to /
    RewriteCond %{THE_REQUEST} ^GET\ .*/index\.(php|html?)\ HTTP
    RewriteRule ^(.*)index\.(php|html?)$ $1 [R=301,L]
    # Rewrite category pages
    RewriteRule ^.*-d([0-9]+)/.*-c([0-9]+)/page-([0-9]+)/?$ index.php?DepartmentId=$1&CategoryId=$2&Page=$3 [L]
    RewriteRule ^.*-d([0-9]+)/.*-c([0-9]+)/?$ index.php?DepartmentId=$1&CategoryId=$2 [L]
    # Rewrite department pages
    RewriteRule ^.*-d([0-9]+)/page-([0-9]+)/?$ index.php?DepartmentId=$1&Page=$2 [L]
    RewriteRule ^.*-d([0-9]+)/?$ index.php?DepartmentId=$1 [L]
    # Rewrite subpages of the home page
    RewriteRule ^page-([0-9]+)/?$ index.php?Page=$1 [L]
    # Rewrite product details pages
    RewriteRule ^.*-p([0-9]+)/?$ index.php?ProductId=$1 [L]
    </IfModule>




the site is working on localhost and is working as if there is no .htaccess rule specified 
i.e. if I were to view a page as 


    [http://localhost/tshirtshop/nature-d2](http://localhost/tshirtshop/nature-d2)


then I get a 404 Error but if I view the same page as 


    [http://localhost/tshirtshop/index.php?DepartmentId=2](http://localhost/tshirtshop/index.php?DepartmentId=2)


then I can view it.

> sudo apache2ctl -M


Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_prefork_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgi_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 php5_module (shared)
 reqtimeout_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 status_module (shared)
Syntax OK



What is the mistake if any one can point out in above configuration, or else I need to check any thing else?
I am using Apache2 on Ubuntu 12.04

Here I would like to mention that Ubuntu comes with a default site enabled 
/etc/apache2/sites-enabled/000-default
I notice that when I disabled the default site 
a2dissite 000-default 
then my working application stopped working all together that means the configuration in
/etc/apache2/sites-enabled/tshirtshop is useless

---

### Post by jamesbon on 2013-06-30
I have been able to solve problem,
what happens is when you install Ubuntu and use apache2 in it there is a default website which is activated as soon as apache2 is installed in ubuntu 


so that default website which is active is 


    /etc/apache2/sites-enabled/000-default


what happens is I have 2 files in sites-enabled directory


    /etc/apache2/sites-enabled/tshirshop  
    /etc/apache2/sites-enabled/000-default


when Ubuntu's Apache loads the vhosts from sites-enabled directory 


it loads the vhost configurations in alphabetical order 
so 000-default was loaded before tshirtshop 
and in 000-default there is a line which is following




    DocumentRoot /var/www
<Directory /var/www/>
            Options Indexes FollowSymLinks MultiViews
            AllowOverride None
            Order allow,deny
            allow from all
    </Directory>




Reasons my configuration was not working 
1) Note the `AllowOverride None`  so this was the reason my .htaccess file was not loaded since the 000-default site configuration was loaded before reading tshirtshop vhost
2) In my /etc/apache2/sites-enabled/tshirshop file I wrote 


    DocumentRoot /var/www/tshirtshop
and was accessing the application as 


    [http://localhost/tshirtshop](http://localhost/tshirtshop)


so I changed the vhost tshirtshop's DocumentRoot


    DocumentRoot /var/www/tshirtshop


to 
 DocumentRoot /var/www


and disabled the default site of Ubuntu's apache


    sudo a2dissite default


Now my configuration of /etc/apache2/sites-enabled/tshirtshop is being read and applied to.So now my .htaccess file is being respected.

---

### Post by jamesbon on 2013-06-30
I have been able to solve problem,
what happens is when you install Ubuntu and use apache2 in it there is a default website which is activated as soon as apache2 is installed in ubuntu 


so that default website which is active is 


    /etc/apache2/sites-enabled/000-default


what happens is I have 2 files in sites-enabled directory


    /etc/apache2/sites-enabled/tshirshop  
    /etc/apache2/sites-enabled/000-default


when Ubuntu's Apache loads the vhosts from sites-enabled directory 


it loads the vhost configurations in alphabetical order 
so 000-default was loaded before tshirtshop 
and in 000-default there is a line which is following




    DocumentRoot /var/www
<Directory /var/www/>
            Options Indexes FollowSymLinks MultiViews
            AllowOverride None
            Order allow,deny
            allow from all
    </Directory>




Reasons my configuration was not working 
1) Note the `AllowOverride None`  so this was the reason my .htaccess file was not loaded since the 000-default site configuration was loaded before reading tshirtshop vhost
2) In my /etc/apache2/sites-enabled/tshirshop file I wrote 


    DocumentRoot /var/www/tshirtshop
and was accessing the application as 


    [http://localhost/tshirtshop](http://localhost/tshirtshop)


so I changed the vhost tshirtshop's DocumentRoot


    DocumentRoot /var/www/tshirtshop


to 
 DocumentRoot /var/www


and disabled the default site of Ubuntu's apache


    sudo a2dissite default


Now my configuration of /etc/apache2/sites-enabled/tshirtshop is being read and applied to.So now my .htaccess file is being respected.

---


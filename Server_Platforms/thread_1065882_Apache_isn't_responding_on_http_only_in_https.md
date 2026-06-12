---
title: "Apache isn't responding on http only in https"
date: 2009-02-10
forum: Server Platforms
---

### Post by f.sivas on 2009-02-10
I got a fresh install of Ubuntu + Lamp server but i can't make apache working for http. I've instaled ajaxterm and is working ok in port 443, listen for exterior conections.
My problem is that i can't get Apache in http. It work ok in my local networks but not in exterior.
Thanks for the help

---

### Post by cdenley on 2009-02-10
If it works OK on your local network, but not over the internet, then it must be a networking issue. Check the settings on your router, and verify your ISP allows servers on port 80.

---

### Post by f.sivas on 2009-02-10
Yes, my isp alows trafic from port 80 because i've got another server runing apache but in windows. And my router setings is ok too.

---

### Post by cdenley on 2009-02-10
> **f.sivas said:**
> Yes, my isp alows trafic from port 80 because i've got another server runing apache but in windows. And my router setings is ok too.

If apache is listening and responding on that port, and your router is configured correctly, then it should be working. Whether the request comes from the LAN or WAN, apache should respond the same. If you get a response from the LAN but not from the WAN, and you aren't blocking non-LAN IP's with iptables, then the problem isn't with the server.

---

### Post by f.sivas on 2009-02-10
I've tried to change the port number to 8080 but it's all the same. Can i do something more about?

---

### Post by jimv on 2009-02-10
Stick that machine in the DMZ temporarily and see if it works then.

---

### Post by Vegan on 2009-02-10
Post your config file so we can see if there is any errors...

:guitar:

---

### Post by f.sivas on 2009-02-10
Thanks for the replies.
Once again I've made a fresh install and it´s all the same.
I can't get connections outside my networks to http, but I've installed Ajaxterm and **i can access to https**.
> **jimv said:**
> Stick that machine in the DMZ temporarily and see if it works then.
I've already made the direct connection to the modem without the router and the result is the same

> **Vegan said:**
> Post your config file so we can see if there is any errors...

:guitar:

$ vi /etc/apache2/apache2.conf  
```

#                                                                               
# Based upon the NCSA server configuration files originally by Rob McCool.      
#                                                                               
# This is the main Apache server configuration file.  It contains the           
# configuration directives that give the server its instructions.               
# See http://httpd.apache.org/docs/2.2/ for detailed information about          
# the directives.                                                               
#                                                                               
# Do NOT simply read the instructions in here without understanding             
# what they do.  They're here only as hints or reminders.  If you are unsure    
# consult the online docs. You have been warned.                                
#                                                                               
# The configuration directives are grouped into three basic sections:           
#  1. Directives that control the operation of the Apache server process as a   
#     whole (the 'global environment').                                         
#  2. Directives that define the parameters of the 'main' or 'default' server,  
#     which responds to requests that aren't handled by a virtual host.         
#     These directives also provide default values for the settings             
#     of all virtual hosts.                                                     
#  3. Settings for virtual hosts, which allow Web requests to be sent to        
#     different IP addresses or hostnames and have them handled by the          
#     same Apache server process.                                               
#                                                                               
# Configuration and logfile names: If the filenames you specify for many                                    
# of the server's control files begin with "/" (or "drive:/" for Win32), the    
# server will use that explicit path.  If the filenames do *not* begin          
# with "/", the value of ServerRoot is prepended -- so "/var/log/apache2/foo.log
"                                                                               
# with ServerRoot set to "" will be interpreted by the                          
# server as "//var/log/apache2/foo.log".                                        
#                                                                               
                                                                                
### Section 1: Global Environment                                               
#                                                                               
# The directives in this section affect the overall operation of Apache,        
# such as the number of concurrent requests it can handle or where it           
# can find its configuration files.                                             
#                                                                               
                                                                                
#                                                                               
# ServerRoot: The top of the directory tree under which the server's            
# configuration, error, and log files are kept.                                 
#                                                                               
# NOTE!  If you intend to place this on an NFS (or otherwise network)           


# mounted filesystem then please read the LockFile documentation (available     
# at <URL:http://httpd.apache.org/docs-2.1/mod/mpm_common.html#lockfile>);      
# you will save yourself a lot of trouble.                                      
                                                
#                                                                               
# Do NOT add a slash at the end of the directory path.                          
#                                                                               
ServerRoot "/etc/apache2"                                                       
                                                                                
#                                                                               
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.            
#                                                                               
#<IfModule !mpm_winnt.c>                                                        
#<IfModule !mpm_netware.c>                                                      
LockFile /var/lock/apache2/accept.lock                                          
#</IfModule>                                                                    
#</IfModule>                                                                    
                                                                                
#                                                                               
# PidFile: The file in which the server should record its process               
# identification number when it starts.                                         
# This needs to be set in /etc/apache2/envvars                                  
#                                                                               
PidFile ${APACHE_PID_FILE}                                                      
                                                                                
#                                                                               
# Timeout: The number of seconds before receives and sends time out.            
#                                                                               
Timeout 300                                                                     
                                                                                
#                                                                               
# KeepAlive: Whether or not to allow persistent connections (more than          
# one request per connection). Set to "Off" to deactivate.                      
#                                                                               
KeepAlive On                                                                    
                                                                                
#                                                                               
# MaxKeepAliveRequests: The maximum number of requests to allow                 
# during a persistent connection. Set to 0 to allow an unlimited amount.        
# We recommend you leave this number high, for maximum performance.             
#                                                                               
MaxKeepAliveRequests 100                                                        
                                                                                
#                                                                               
# KeepAliveTimeout: Number of seconds to wait for the next request from the     
# same client on the same connection.                                           
#                                                                               
KeepAliveTimeout 15                                                             
                                                                                
##                                                                              
## Server-Pool Size Regulation (MPM specific)                                   
##                                                                              
                                                                                
# prefork MPM                                                                   
# StartServers: number of server processes to start                             
# MinSpareServers: minimum number of server processes which are kept spare      
# MaxSpareServers: maximum number of server processes which are kept spare      
# MaxClients: maximum number of server processes allowed to start               
# MaxRequestsPerChild: maximum number of requests a server process serves       
<IfModule mpm_prefork_module>                                                   
    StartServers          5                                                     
    MinSpareServers       5                                                     
    MaxSpareServers      10                                                     
    MaxClients          150                                                     
    MaxRequestsPerChild   0                                                     
</IfModule>                                                                     
                                                                                
# worker MPM                                                                    
                                                                               
# StartServers: initial number of server processes to start                     
# MaxClients: maximum number of simultaneous client connections                 
# MinSpareThreads: minimum number of worker threads which are kept spare        
# MaxSpareThreads: maximum number of worker threads which are kept spare        
# ThreadsPerChild: constant number of worker threads in each server process     
# MaxRequestsPerChild: maximum number of requests a server process serves       
<IfModule mpm_worker_module>                                                    
    StartServers          2                                                     
    MaxClients          150                                                     
    MinSpareThreads      25                                                     
    MaxSpareThreads      75                                                     
    ThreadsPerChild      25                                                     
    MaxRequestsPerChild   0                                                     
</IfModule>                                                                     
                                                                                
# These need to be set in /etc/apache2/envvars                                  
User ${APACHE_RUN_USER}                                                         
Group ${APACHE_RUN_GROUP}                                                       
                                                                                
#                                                                               
# AccessFileName: The name of the file to look for in each directory            
# for additional configuration directives.  See also the AllowOverride          
# directive.                                                                    
#                                                                               
                                                                                
AccessFileName .htaccess                                                        
                                                                                
#                                                                               
# The following lines prevent .htaccess and .htpasswd files from being          
# viewed by Web clients.                                                        
#                                                                               
<Files ~ "^\.ht">                                                               
    Order allow,deny                                                            
    Deny from all                                                               
</Files>                                                                        
                                                                                
#                                                                               
# DefaultType is the default MIME type the server will use for a document       
# if it cannot otherwise determine one, such as from filename extensions.       
# If your server contains mostly text or HTML documents, "text/plain" is        
# a good value.  If most of your content is binary, such as applications        
# or images, you may want to use "application/octet-stream" instead to          
# keep browsers from trying to display binary files as though they are          
# text.                                                                         
#                                                                               
DefaultType text/plain                                                          
                                                                                
                                                                                
#                                                                               
# HostnameLookups: Log the names of clients or just their IP addresses          
# e.g., www.apache.org (on) or 204.62.129.132 (off).                            
# The default is off because it'd be overall better for the net if people       
# had to knowingly turn this feature on, since enabling it means that           
# each client request will result in AT LEAST one lookup request to the         
# nameserver.                                                                   
#                                                                               
HostnameLookups Off                                                             
                                                                                
# ErrorLog: The location of the error log file.                                 
# If you do not specify an ErrorLog directive within a <VirtualHost>            
# container, error messages relating to that virtual host will be               
# logged here.  If you *do* define an error logfile for a <VirtualHost>         
# container, that host's errors will be logged there and not here.              
#                                                                               
ErrorLog /var/log/apache2/error.log                                             
                                                                                
#                                                                               
# LogLevel: Control the number of messages logged to the error_log.             
# Possible values include: debug, info, notice, warn, error, crit,              
# alert, emerg.                                                                 
#                                                                               
LogLevel warn                                                                   
                                                                                
# Include module configuration:                                                 
Include /etc/apache2/mods-enabled/*.load                                        
Include /etc/apache2/mods-enabled/*.conf                                        
                                                                                
# Include all the user configurations:                                          
Include /etc/apache2/httpd.conf                                                 
                                                                                
# Include ports listing                                                         
Include /etc/apache2/ports.conf                                                 
                                                                                
#                                                                               
# The following directives define some format nicknames for use with            
# a CustomLog directive (see below).                                            
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwar
ded-For}i                                                                       
#                                                                               
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" v
host_combined                                                                   
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combine
d                                                                               
LogFormat "%h %l %u %t \"%r\" %>s %b" common                                    
LogFormat "%{Referer}i -> %U" referer                                           
LogFormat "%{User-agent}i" agent                                                
                                                                                
#                                                                               
# Define an access log for VirtualHosts that don't define their own logfile     
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined               
                                                                                
#                                                                               
# Customizable error responses come in three flavors:                           
# 1) plain text 2) local redirects 3) external redirects                        
#                                                                               
# Some examples:                                                                
#ErrorDocument 500 "The server made a boo boo."                                 
#ErrorDocument 404 /missing.html                                                
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"                                
#ErrorDocument 402 http://www.example.com/subscription_info.html                
#                                                                               
                                                                                
#                                                                               
# Putting this all together, we can internationalize error responses.           
#                                                                               
# We use Alias to redirect any /error/HTTP_<error>.html.var response to         
# our collection of by-error message multi-language collections.  We use        
# includes to substitute the appropriate text.                                  
#                                                                               
# You can modify the messages' appearance without changing any of the           
# default HTTP_<error>.html.var files by adding the line:                       
#                                                                               
#   Alias /error/include/ "/your/include/path/"                                 
#                                                                               
# which allows you to create your own set of files by starting with the         
# /usr/share/apache2/error/include/ files and copying them to /your/include/path
/,                                                                              
# even on a per-VirtualHost basis.  The default include files will display      
# your Apache version number and your ServerAdmin email address regardless      
# of the setting of ServerSignature.                                            
#                                                                               
# The internationalized error documents require mod_alias, mod_include          
# and mod_negotiation.  To activate them, uncomment the following 30 lines.     
                                                                                
#    Alias /error/ "/usr/share/apache2/error/"                                  
#                                                                               
#    <Directory "/usr/share/apache2/error">                                     
#        AllowOverride None                                                     
#        Options IncludesNoExec                                                 
#        AddOutputFilter Includes html                                          
#        AddHandler type-map var                                                
#        Order allow,deny                                                       
#        Allow from all                                                         
#        LanguagePriority en cs de es fr it nl sv pt-br ro                      
#        ForceLanguagePriority Prefer Fallback                                  
#    </Directory>                                                               
#                                                                               
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var                         
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var                        
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var                           
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var                           
                                                                               
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var                  
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var                    
#    ErrorDocument 410 /error/HTTP_GONE.html.var                                
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var                     
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var                 
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var            
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var               
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var              
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var               
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var                     
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var                         
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var                 
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var                 
                                                                                
                                                                                
                                                                                
# Include of directories ignores editors' and dpkg's backup files,              
# see README.Debian for details.                                                
                                                                                
# Include generic snippets of statements                                        
Include /etc/apache2/conf.d/                                                    
                                                                                
# Include the virtual host configurations:                                      
Include /etc/apache2/sites-enabled/                                             


```

$ vi /etc/apache2/sites-available/default
```

<VirtualHost *:80>                                                              
        ServerAdmin webmaster@localhost                                         
                                                                                
        DocumentRoot /var/www/                                                  
        <Directory />                                                           
                Options FollowSymLinks                                          
                AllowOverride None                                              
        </Directory>                                                            
        <Directory /var/www/>                                                   
                Options Indexes FollowSymLinks MultiViews                       
                AllowOverride None                                              
                Order allow,deny                                                
                allow from all                                                  
        </Directory>                                                            
                                                                                
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/                                 
        <Directory "/usr/lib/cgi-bin">                                          
                AllowOverride None                                              
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch              
                Order allow,deny                                                
                Allow from all                                                  
        </Directory>                                                            
                                                                                
        ErrorLog /var/log/apache2/error.log 
        # Possible values include: debug, info, notice, warn, error, crit,      
        # alert, emerg.                                                         
        LogLevel warn                                                           
                                                                                
        CustomLog /var/log/apache2/access.log combined                          
                                                                                
    Alias /doc/ "/usr/share/doc/"                                               
    <Directory "/usr/share/doc/">                                               
        Options Indexes MultiViews FollowSymLinks                               
        AllowOverride None                                                      
        Order deny,allow                                                        
        Deny from all                                                           
        Allow from 127.0.0.0/255.0.0.0 ::1/128                                  
    </Directory>                                                                
                                                                                
</VirtualHost>                                                                  
                                                                                
<VirtualHost *:443>                                                             
        SetEnvIf Request_URI "^/u" dontlog                                      
        ErrorLog /var/log/apache2/error.log                                     
        Loglevel warn                                                           
                                                                               
        SSLEngine On                                                            
        SSLCertificateFile /etc/apache2/ssl/apache.pem                          
                                                                                
        ProxyRequests Off                                                       
        <Proxy *>                                                               
                AuthUserFile /srv/ajaxterm/.htpasswd                            
                AuthName EnterPassword                                          
                AuthType Basic                                                  
                require valid-user                                              
                                                                                
                Order Deny,allow                                                
                Allow from all                                                  
        </Proxy>                                                                
        ProxyPass / http://localhost:8022/                                      
        ProxyPassReverse / http://localhost:8022/                               
</VirtualHost>   

```

$ vi /etc/apache2/ports.conf 
```

# If you just change the port or add more ports here, you will likely also      
# have to change the VirtualHost statement in                                   
# /etc/apache2/sites-enabled/000-default                                        
                                                                                
NameVirtualHost *:80                                                            
Listen 80                                                                       
                                                                                
<IfModule mod_ssl.c>                                                            
    # SSL name based virtual hosts are not yet supported, therefore no          
    # NameVirtualHost statement here                                            
    Listen 443                                                                  
</IfModule>                                                                     


```

```

$ /etc/apache2/conf.d# netstat -tulpn                              
Active Internet connections (only servers)                                      
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name                                                                
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4289/mysqld                                                                     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      19779/apache2                                                                   
tcp        0      0 127.0.0.1:8022          0.0.0.0:*               LISTEN      19590/python                                                                    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      4199/sshd                                                                       
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      19779/apache2                                                                   
tcp6       0      0 :::22                   :::*                    LISTEN      4199/sshd                                                                       
udp        0      0 0.0.0.0:68              0.0.0.0:*                           3855/dhclient3                                                                


```

---

### Post by cdenley on 2009-02-11
Even IF it were a configuration error with apache, it would still give some response such as a 403 error. As I already said, unless iptables is blocking non-lan IP's, your server is working correctly since it works from inside your LAN. Apache doesn't drop connections from non-lan IP's. You have a routing issue somewhere.

Just to be sure that you are in fact getting no response on port 80, post the output from running these commands from outside your network, or post your IP so someone else can.
```

nc -z -v [your ip] 80
nc -z -v [your ip] 443

```
Connecting to your WAN IP from inside your network is not always the same as connecting from outside your network, but since you said TCP 443 works and TCP 80 worked before, that probably isn't your issue.

---


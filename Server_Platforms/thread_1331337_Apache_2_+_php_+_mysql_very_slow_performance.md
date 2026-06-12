---
title: "Apache 2 + php + mysql very slow performance"
date: 2009-11-19
forum: Server Platforms
---

### Post by Abadon_ on 2009-11-19
Hello,

I have a virtual machine in one hosting company that will use to host my site. Since the installation do everything alone. OS is Ubuntu Hardy, Kernel 2.6.24-25-virtual, VMware tools the last version, the host machine is a VMware ESX 4 with processors Intel (R) Xeon (R) CPU E5405@2.00GHz. For my virtual machine are allocated 256MB of RAM, restricted to use up to 450 Mhz processor during a Xeon and I have a 100Mbit-flat channel to the Internet. Server work stable, but performance is terrible low.  
> root@host:~# ab -c 10 -n 100 [http://mysite.com/](http://mysite.com/)
This is ApacheBench, Version 2.3 <$Revision: 655654 $>       
Copyright 1996 Adam Twiss, Zeus Technology Ltd, [http://www.zeustech.net/](http://www.zeustech.net/)
Licensed to The Apache Software Foundation, [http://www.apache.org/](http://www.apache.org/)      

Benchmarking mysite.com (be patient).....done


Server Software:        Apache
Server Hostname:        mysite.com
Server Port:            80                  

Document Path:          /
Document Length:        39066 bytes

Concurrency Level:      10
Time taken for tests:   25.560 seconds
Complete requests:      100
Failed requests:        0
Write errors:           0
Total transferred:      3943400 bytes
HTML transferred:       3906600 bytes
Requests per second:    3.91 [#/sec] (mean)
Time per request:       2555.965 [ms] (mean)
Time per request:       255.596 [ms] (mean, across all concurrent requests)
Transfer rate:          150.67 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        1    1   0.5      1       4
Processing:   543 2534 752.4   2862    3198
Waiting:      539 2516 754.4   2854    3194
Total:        545 2535 752.2   2863    3199

Percentage of the requests served within a certain time (ms)
  50%   2863
  66%   2953
  75%   2997
  80%   3018
  90%   3070
  95%   3158
  98%   3179
  99%   3199
 100%   3199 (longest request)


My configurations are as follows:
**/etc/apache2/apache2.conf**
> ServerRoot "/etc/apache2" 
LockFile /var/lock/apache2/accept.lock
PidFile ${APACHE_PID_FILE}
Timeout 300 
KeepAlive On   
MaxKeepAliveRequests 100 
KeepAliveTimeout 2  

<IfModule mpm_worker_module>                                               
    StartServers          4                                                
    MaxClients           20                                                
    MinSpareThreads       2                                                
    MaxSpareThreads      20                                                
    ThreadsPerChild       5                                                
    MaxRequestsPerChild   1024                                             
</IfModule>   

User ${APACHE_RUN_USER}                       
Group ${APACHE_RUN_GROUP}  
AccessFileName .htaccess

<Files ~ "^\.ht">                                                      
    Order allow,deny                                                   
    Deny from all                                                      
</Files> 

DefaultType text/plain
HostnameLookups Off
ErrorLog /var/log/apache2/error.log
LogLevel warn
# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf       

# Include ports listing
Include /etc/apache2/ports.conf

LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined        
LogFormat "%h %l %u %t \"%r\" %>s %b" common                                             
LogFormat "%{Referer}i -> %U" referer                                                    
LogFormat "%{User-agent}i" agent   

ServerTokens Prod 
ServerSignature Off
# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/


**/etc/apache2/sites-enabled/000-default**
> NameVirtualHost *                                      
<VirtualHost *>                                        
        ServerAdmin [email]webmaster@mysite.com[/email]     

        DocumentRoot /var/www/
        <Directory />         
                Options +ExecCGI Indexes
                Options +FollowSymLinks 
                AllowOverride None      
        </Directory>                    
        <Directory /var/www/>           
                Options +ExecCGI Indexes +FollowSymLinks MultiViews
                AddHandler fcgid-script .php                       
                FCGIWrapper /usr/lib/cgi-bin/php5 .php             
                AllowOverride All                                  
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
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options +ExecCGI Indexes MultiViews +FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


In **/etc/php5/cgi/php.ini** I change this from default configuration, because I want to upload video files up to 200&#1052;&#1042;.
> post_max_size = 256M 
upload_max_filesize = 200M
max_execution_time = 300 ; Maximum execution time of each script, in seconds
max_input_time = 600 ; Maximum amount of time each script may spend parsing request data
memory_limit = 128M ; Maximum amount of memory a script may consume (16MB default)

I installed [eAccelerator](http://eaccelerator.net/) according to the instructions [here](http://www.howtoforge.com/eaccelerator_php5_debian_etch) My configuration in **/etc/php5/conf.d/eaccelerator.ini **is as follows:
> extension="eaccelerator.so"
eaccelerator.shm_size="16"
eaccelerator.cache_dir="/var/cache/eaccelerator"
eaccelerator.enable="1"
eaccelerator.optimizer="1"
eaccelerator.check_mtime="0"
eaccelerator.debug="0"
eaccelerator.filter=""
eaccelerator.shm_max="0"
eaccelerator.shm_ttl="10"
eaccelerator.shm_prune_period="10"
eaccelerator.shm_only="1"
eaccelerator.compress="1"
eaccelerator.compress_level="9"

In **/etc/mysql/my.cnf** I change this:
> max_allowed_packet = 128M

My file system is reiserfs mounted with the following options relatime,noatime,notail

When I test with **ab** and monitoring with **top** Observe the following:
> top - 14:57:04 up 8 days, 14 min,  2 users,  load average: 2.52, 0.56, 0.33
Tasks:  65 total,  13 running,  52 sleeping,   0 stopped,   0 zombie
Cpu(s): 77.6%us, 20.9%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  1.5%si,  0.0%st
Mem:    255764k total,   206372k used,    49392k free,    31600k buffers
Swap:   401400k total,        0k used,   401400k free,    76836k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                       
 8068 www-data  20   0 50732  20m  15m R  1.9  8.2   0:04.98 php5                                                                                          
 8076 www-data  20   0 49916  17m  12m R  1.9  7.0   0:06.52 php5                                                                                          
 8081 www-data  20   0 48864  12m 8960 R  1.9  4.9   0:01.16 php5                                                                                          
 8090 www-data  20   0 49160  13m 9932 R  1.9  5.5   0:01.30 php5                                                                                          
 8595 www-data  20   0 48864  12m 8780 R  1.9  4.8   0:00.22 php5                                                                                          
 8596 www-data  20   0 49400  12m 8780 R  1.9  5.0   0:00.20 php5                                                                                          
 8599 www-data  20   0 49396  12m 8780 R  1.9  4.9   0:00.18 php5                                                                                          
 8600 www-data  20   0 48864  12m 8780 R  1.9  4.8   0:00.18 php5                                                                                          
  810 mysql     20   0  130m  23m 2692 S  1.6  9.5   0:38.81 mysqld                                                                                        
 8597 www-data  20   0 49400  12m 8780 R  1.3  5.0   0:00.18 php5                                                                                          
 8598 www-data  20   0 49400  12m 8780 R  1.3  5.0   0:00.18 php5                                                                                          
 8611 root      20   0 34280 9960 6376 R  1.3  3.9   0:00.04 php                                                                                           
 6641 www-data  20   0 69420 4140 1640 S  0.6  1.6   0:00.23 apache2                                                                                       
 8604 www-data  20   0 48324 9.8m 7028 S  0.6  3.9   0:00.08 php5                                                                                          
    1 root      20   0  1800  280   68 S  0.0  0.1   0:01.54 init                                                                                          
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                      
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                   
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.32 ksoftirqd/0                                                                                   
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                    
    6 root      15  -5     0    0    0 S  0.0  0.0   0:02.66 events/0                                                                                      
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.28 khelper  

**mtop** show this:
> load average: 1.06, 1.07, 0.59 mysqld 5.0.51a-3ubuntu5.4 up 0 day(s),  4:53 hrs
1 threads: 1 running, 7 cached. Queries/slow: 1.1M/0 Cache Hit: 94.42%
Opened tables: 0  RRN: 1.7K  TLW: 0  SFJ: 0  SMP: 0  QPS: 4

ID       USER     HOST             DB           TIME   COMMAND STATE        INFO
7541     root     localhost                            Query                show full processlist


 Any suggestions ? Where is the problem?

Thanks in advance!

**[COLOR="Red"]&#1045;dited:[/COLOR]**
When a test html file in this way ab -c 10 -n 100 [http://mysite.com/phpMyAdmin/Documentation.html](http://mysite.com/phpMyAdmin/Documentation.html) Processed 2485.46 requests  per second and the network fills me run 2M&#1042;/sec ( This is my connection to the Internet from the machine that I run ab)
I tried to test with the following php file:
> <?php
    echo "Go";
?>

or just go into it without anything else and My result was a 99  requests  per second.

---

### Post by Abadon_ on 2009-11-20
This morning was released update of packages apache2-mpm-worker, apache2-utils and apache2.2-common. I decided to test again after update. Start  ab -c 20 -n 1000 [http://mysite.com/](http://mysite.com/) and watch result: 40.11 Requests per second in which the CPU is loaded of 1%. Change configuration in  /etc/apache2/apache2.conf like this:
> <IfModule mpm_worker_module>                                              
    StartServers          4                                                
    MaxClients          200                                                
    MinSpareThreads      20                                                
    MaxSpareThreads    200                                                
    ThreadsPerChild      50                                                
    MaxRequestsPerChild  1024                                            
</IfModule> 

And test with ab -c 200 -n 10000 [http://mysite.com/](http://mysite.com/) result is 156.70 Requests per second, CPU load is 2%. 

Most likely Apache can handle much more requests, but unfortunately connection of a computer that I run ab is only 10Mbps and fill in my channel.

---

### Post by angstsix on 2009-11-23
I'm having this same issue with the same setup. any help would be great!

---

### Post by Abadon_ on 2009-11-24
Now work fine I'm with this versions of packages:
> dpkg --list| grep apache
ii  apache2-mpm-worker                     2.2.8-1ubuntu0.14                 High speed threaded model for Apache HTTPD
ii  apache2-utils                          2.2.8-1ubuntu0.14                 utility programs for webservers
ii  apache2.2-common                       2.2.8-1ubuntu0.14                 Next generation, scalable, extendable web se
ii  libapache2-mod-fcgid                   1:2.2-1                           an alternative module compat with mod_fastcg
rc  libapache2-mod-php5                    5.2.4-2ubuntu5.7                  server-side, HTML-embedded scripting languag


---


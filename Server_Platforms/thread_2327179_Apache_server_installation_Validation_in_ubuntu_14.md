---
title: "Apache server installation Validation in ubuntu 14.04"
date: 2016-06-08
forum: Server Platforms
---

### Post by Rakesh_vijayan on 2016-06-08
I install apache for  web server by following method 
  > sudo apt-get update
sudo apt-get install libapache2-mod-fastcgi php5-fpm apache2-mpm-event
  Create the php5.fcgi file and give permission 
  > sudo touch /usr/lib/cgi-bin/php5.fcgi
sudo chown -R user:www-data /usr/lib/cgi-bin
  Then I create the file /etc/apache2/conf-available/php5-fpm.conf with the contents:
   > <IfModule mod_fastcgi.c> 
   AddHandler php5.fcgi .php 
   Action php5.fcgi /php5.fcgi 
   Alias /php5.fcgi /usr/lib/cgi-bin/php5.fcgi 
   FastCgiExternalServer /usr/lib/cgi-bin/php5.fcgi -socket /var/run/php5-fpm.sock -pass-header Authorization -idle-timeout 3600 
   <Directory /usr/lib/cgi-bin>
       Require all granted
   </Directory> 
</IfModule>
  Then enable the new mods and config: 
  > sudo a2enmod actions fastcgi alias
sudo a2enconf php5-fpm
sudo a2enmod mpm_event
sudo service apache2 restart
  And for the performance tuning I change the following values in 
  > sudo nano  /etc/php5/fpm/pool.d/www.conf

> listen = 127.0.0.1:9000
 to 
listen = /var/run/php5-fpm.sock
  Restart the php5-fpm service 
  > sudo service php5-fpm restart
  Apache thread value adjusted as follow , I don't know it correct or not 
  > sudo nano /etc/apache2/mods-available/mpm_event.conf
  Values 
  > # event MPM
# StartServers: initial number of server processes to start
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestWorkers: maximum number of worker threads
# MaxConnectionsPerChild: maximum number of requests a server process serves
<IfModule mpm_event_module>
        StartServers                     2
        MinSpareThreads          20
        MaxSpareThreads          85
        ServerLimit             8
        ThreadLimit                      64
        ThreadsPerChild          64
        MaxRequestWorkers         512
        MaxConnectionsPerChild   0
        KeepAlive On
        MaxKeepAliveRequests 50
        KeepAliveTimeout 4
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
  Restart apache and fpm
  > sudo service apache2 restart 
sudo service php5-fpm restart
  Checked the Configuration Error 
  > sudo apache2ctl configtest
Syntax OK
  Then I test the server load with apache ab with 30 concurrent user searching 20 pages .> 
  ab -l -r -n 600 -c 30 -k -H "Accept-Encoding: gzip, deflate" [http://rakesh.vjayan.com/index.php](http://rakesh.vjayan.com/index.php)
  Server Configuration was 2 vcps and 8 Gb Ram 
  Test Result was 
  > rvd@rvd ~ $ ab -l -r -n 600 -c 30 -k -H "Accept-Encoding: gzip, deflate" [http://rakesh.vijayan.com/](http://rakesh.vijayan.com/)
This is ApacheBench, Version 2.3 <$Revision: 1528965 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, [http://www.zeustech.net/](http://www.zeustech.net/)
Licensed to The Apache Software Foundation, [http://www.apache.org/](http://www.apache.org/)

Benchmarking  rakesh.vijayan.com (be patient)
apr_pollset_poll: The timeout specified has expired (70007)
rvd@rvd ~ $ 
  **MATE**  will you explain why this happen at first time with 30 user, 
  I run the test with 25 , 26 , 27 , 29 to 30 at the 30 user now server accept 30th  request and load look like this 
  > rvd@rvd ~ $ ab -l -r -n 600 -c 30 -k -H "Accept-Encoding: gzip, deflate" [http://rakesh.vijayan.com/](http://rakesh.vijayan.com/)
This is ApacheBench, Version 2.3 <$Revision: 1528965 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, [http://www.zeustech.net/](http://www.zeustech.net/)
Licensed to The Apache Software Foundation, [http://www.apache.org/](http://www.apache.org/)

Benchmarking rakesh.vijayan.com (be patient)
Completed 100 requests
Completed 200 requests
Completed 300 requests
Completed 400 requests
Completed 500 requests
Completed 600 requests
Finished 600 requests


Server Software:        Apache/2.4.7
Server Hostname:        rakesh.vijayan.com
Server Port:            80

Document Path:          /
Document Length:        Variable

Concurrency Level:      30
Time taken for tests:   583.798 seconds
Complete requests:      600
Failed requests:        0
Keep-Alive requests:    0
Total transferred:      13256758 bytes
HTML transferred:       12984958 bytes
Requests per second:    1.03 [#/sec] (mean)
Time per request:       29189.910 [ms] (mean)
Time per request:       972.997 [ms] (mean, across all concurrent requests)
Transfer rate:          22.18 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:       48   75 147.0     55    2253
Processing:  4130 28473 3265.4  28954   31724
Waiting:     4079 28355 3254.5  28867   31667
Total:       4179 28547 3265.7  29033   31779

Percentage of the requests served within a certain time (ms)
  50%  29033
  66%  29483
  75%  29698
  80%  29833
  90%  30325
  95%  30580
  98%  30966
  99%  31125
 100%  31779 (longest request)
rvd@rvd ~ $ 
  Load seems to this 
  > top - 11:40:55 up 20:42,  1 user,  load average: 4.37, 3.95, 2.39
Tasks: 115 total,   6 running, 108 sleeping,   1 stopped,   0 zombie
%Cpu(s): 96.3 us,  3.3 sy,  0.0 ni,  0.2 id,  0.2 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   8175632 total,  2076852 used,  6098780 free,   399728 buffers
KiB Swap:        0 total,        0 used,        0 free.   679668 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 1105 mysql     20   0 1792648 615616  10432 S  41.9  7.5   4:46.86 mysqld      
 3374 www-data  20   0  369576  57108  23348 R  40.9  0.7   1:34.77 php5-fpm    
 3373 www-data  20   0  371624  59444  23348 R  37.6  0.7   1:36.45 php5-fpm    
 3368 www-data  20   0  368296  56012  23348 R  27.6  0.7   1:44.35 php5-fpm    
 3352 www-data  20   0  368808  56324  23348 R  26.6  0.7   1:54.69 php5-fpm    
 3367 www-data  20   0  367528  55744  23596 R  24.3  0.7   1:48.01 php5-fpm 
  so I expand the cpu to 4cpu
 Thanks 
     
              [server]("http://askubuntu.com/questions/tagged/server") [permissions]("http://askubuntu.com/questions/tagged/permissions") [apache2]("http://askubuntu.com/questions/tagged/apache2") [php]("http://askubuntu.com/questions/tagged/php")

---

### Post by SeijiSensei on 2016-06-08
Have you tried using the standard PHP5 module for Apache instead of the cgi version?

Also what do you mean by "searching?"  Is the search run by PHP against the MySQL database? Do all the relevant queries have corresponding indexes in MySQL? Have you considered alternative search methods like [Sphinx]("http://sphinxsearch.com/")?

---

### Post by Rakesh_vijayan on 2016-06-09
Thanks for the replay .

 


> **SeijiSensei said:**
> Have you tried using the standard PHP5 module for Apache instead of the cgi version?

Also what do you mean by "searching?"  Is the search run by PHP against the MySQL database? Do all the relevant queries have corresponding indexes in MySQL? Have you considered alternative search methods like [Sphinx]("http://sphinxsearch.com/")?

When I tried with normal PHP5  which access php uses the cpu more than mysql .My live site getting crash in Apache mpm_prefork+php5 so many time 

Searching means 30 user accessing the page 


> Is the search run by PHP against the MySQL database? Do all the relevant queries have corresponding indexes in MySQL?
Yes all queires have the indexes in mysql  

I never heard about the sphinx .I need to dig about the product Thanks for the information bro ..

---


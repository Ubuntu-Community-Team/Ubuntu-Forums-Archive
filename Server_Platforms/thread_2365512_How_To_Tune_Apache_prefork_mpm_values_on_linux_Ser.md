---
title: "How To Tune Apache prefork mpm values on linux Server"
date: 2017-07-07
forum: Server Platforms
---

### Post by vicky219 on 2017-07-07
Currently I am on Apache/2.4.23 version and I am running multiple virtual host sites on my webserver behind an ELB. I have 4 instances under my ELB each with 8GB of total RAM. On these webservers I don't see any mpm directives set in my httpd.conf file where as I could see the default values of the mpm modules directives in httpd-mpm.conf file(at /usr/share/doc/httpd24-2.4.23). My webserver is using prefork mpm module


    ```
httpd -V | grep MPM
    Server MPM:     prefork

```

Currently all 4 webservers are having only around 200MB of free space left from 8GB and I see there are always around 60 httpd process are running. Below are the metrics


```
    [root@ip ~]# ps -ef | grep httpd | wc -l
    58
```
    
  ```
  [root@ip ~]# ps -ylC httpd | awk '{x += $8;y += 1} END {print "Apache Memory Usage (MB): "x/1024; print "Average Proccess Size (MB): "x/((y-1)*1024)}'
    Apache Memory Usage (MB): 1640.18
    Average Proccess Size (MB): 38.1438
    
    [root@ip ~]# free -m
                 total       used       free     shared    buffers     cached
    Mem:          7986       7755        231         51        114        233
    -/+ buffers/cache:       7407        579
    Swap:            0          0          0

```

Inorder to increase my server performance I am planning to update my httpd.conf file with below prefork mpm directives. The only thing I would like to change is MaxRequestWorkers value from 250 to 400.


  ```
  <IfModule mpm_prefork_module>
        StartServers             5
        MinSpareServers          5
        MaxSpareServers         10
        MaxRequestWorkers      400
        MaxConnectionsPerChild   0
    </IfModule>
```

[COLOR=#242729][FONT=Arial]**Edit**: Below are the default settings in httpd-mpm.conf file. But I dont see any prefork mpm modules settings in httpd.conf file thereby assuming that my webserver is using below default values
[/FONT][/COLOR]
```
<IfModule mpm_prefork_module>
    StartServers             5
    MinSpareServers          5
    MaxSpareServers         10
    MaxRequestWorkers      250
    MaxConnectionsPerChild   0
</IfModule>

```
 [COLOR=#242729][FONT=Arial]My webserver also runs the php scripts which are offen very slow, when all of the app&#8217;s PHP processes are busy executing requests, and additional requests is queued by Apache until PHP completes an existing request and is available for another[/FONT][/COLOR]

My Question is, will this change help my webserver to use less system memory and will it handle load efficiently. And as the free space is less on my webserver does changing value from 250 to 400 for MaxRequestWorkers will cause any further problem? Is there any better solution to optimize the memory consumption on my server?

---

### Post by slickymaster on 2017-07-07
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2017-07-07
Frankly I think the best solution is to increase the amount of physical memory from 8 to 16 GB.  Is that possible?

---

### Post by vicky219 on 2017-07-10
First I need to try tunning the apache config, such as tweeking the values of mpm modules. From the info I provided could I use worker mpm module instead of prefork to help reduce the RAM consumption. Orelse changing the value of MaxRequestWorkers from 250 to 400 in prefork module could help me?

---


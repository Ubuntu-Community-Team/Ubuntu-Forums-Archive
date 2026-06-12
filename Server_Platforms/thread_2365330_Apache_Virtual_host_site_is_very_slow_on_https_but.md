---
title: "Apache Virtual host site is very slow on https but fast on http"
date: 2017-07-05
forum: Server Platforms
---

### Post by vicky219 on 2017-07-05
**Backgroud**: I have a multiple virtual host site setup on two webservers behind an ELB. Each virtual host site has an ssl certificate and key(domain.key,domain.bundle.crt) under /etc/httpd/ssl. There is also a Route53 setup which direct the traffic to my ELB and the to these webservers.

**Issue**: I have a site say site1.com and site2.com is setup as an alias in site1.com config file. So when I access [http://site2.com(http)](http://site2.com(http)) then its considerably fast compared to [https://site2.com(https)](https://site2.com(https)).

I have checked the site1.com virtual host logs but didnt find any error also I have checked the 01-cgi.conf file under /etc/httpd/conf.modules.d but didnt find any MaxRequestWorkers setting

```
# This configuration file loads a CGI module appropriate to the MPM
# which has been configured in 00-mpm.conf.  mod_cgid should be used
# with a threaded MPM; mod_cgi with the prefork MPM.


<IfModule mpm_worker_module>
   LoadModule cgid_module modules/mod_cgid.so
</IfModule>
<IfModule mpm_event_module>
   LoadModule cgid_module modules/mod_cgid.so
</IfModule>
<IfModule mpm_prefork_module>
   LoadModule cgi_module modules/mod_cgi.so
</IfModule>


```

[COLOR=#242729][FONT=Arial]I am measuring the site speed online and the site with https is taking bit long(5secs more) time to load when compared to https.
I did some research and found that I may need to increase the MaxRequestSettings in http.conf file but neither I find MaxRequest or MPM, prefork directives in my conf file.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How could I resolve this issue.[/FONT][/COLOR]

---

### Post by slickymaster on 2017-07-05
Thread moved to **Server Platforms** for a better bit

---

### Post by Habitual on 2017-07-05
> **vicky219 said:**
> I am measuring the site speed online and the site with https is taking bit long(5secs more) time to load when compared to https.
I did some research and found that I may need to increase the MaxRequestSettings in http.conf file but neither I find MaxRequest or MPM, prefork directives in my conf file.
How could I resolve this issue.

Research? Got links?
```
grep -i MaxRequestWorkers /etc/apache2/ -Rl
``` spews
```
/etc/apache2/mods-available/mpm_prefork.conf:# MaxRequestWorkers: maximum number of server processes allowed to start
/etc/apache2/mods-available/mpm_prefork.conf:	MaxRequestWorkers	  150
/etc/apache2/mods-available/mpm_worker.conf:# MaxRequestWorkers: maximum number of threads
/etc/apache2/mods-available/mpm_worker.conf:	MaxRequestWorkers	  150
/etc/apache2/mods-available/mpm_event.conf:# MaxRequestWorkers: maximum number of worker threads
/etc/apache2/mods-available/mpm_event.conf:	MaxRequestWorkers	  150
/etc/apache2/mods-enabled/mpm_prefork.conf:# MaxRequestWorkers: maximum number of server processes allowed to start
/etc/apache2/mods-enabled/mpm_prefork.conf:	MaxRequestWorkers	  150
```

so it is one of those files 

/etc/apache2/mods-enabled/mpm_prefork.conf is my guess.

Any apache rewrites? 
What have  you tried and please cite your references.
Is this "speed test" the only the only measurement you've tried?

I use defaults (mostly) in my AWS instances and I don't rely on "speed test" sites as I can manage and test response times from here.
Mixed content perhaps? https and non-https URIs?
database stored links using mix?

Content Management System involved?

---

### Post by vicky219 on 2017-07-05
Thanks for you response

I am a linux user and when I use below command I am not getting the config file where MaxRequestWorker setting is configured.

**grep -i MaxRequestWorkers /etc/httpd/ -Rl**

Neither there are any module(prefork, worker, event) directives in httpd.conf file.

I just see that my server is using prefork mpm

httpd -V | grep MPM
[B]Server MPM:     prefork

[/B]How could I configure the prefork mpm in my webserver. I just see the default values of all mpm modules under **/usr/share/doc/httpd24-2.4.23/httpd-mpm.conf file. **Below is the httpd-mpm.conf file. ```
#
# Server-Pool Management (MPM specific)
#


#
# PidFile: The file in which the server should record its process
# identification number when it starts.
#
# Note that this is the default PidFile for most MPMs.
#
<IfModule !mpm_netware_module>
    PidFile "/var/run/httpd/httpd.pid"
</IfModule>


#
# Only one of the below sections will be relevant on your
# installed httpd.  Use "apachectl -l" to find out the
# active mpm.
#


# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxRequestWorkers: maximum number of server processes allowed to start
# MaxConnectionsPerChild: maximum number of connections a server process serves
#                         before terminating
<IfModule mpm_prefork_module>
    StartServers             5
    MinSpareServers          5
    MaxSpareServers         10
    MaxRequestWorkers      250
    MaxConnectionsPerChild   0
</IfModule>


# worker MPM
# StartServers: initial number of server processes to start
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestWorkers: maximum number of worker threads
# MaxConnectionsPerChild: maximum number of connections a server process serves
#                         before terminating
<IfModule mpm_worker_module>
    StartServers             3
    MinSpareThreads         75
    MaxSpareThreads        250
    ThreadsPerChild         25
    MaxRequestWorkers      400
    MaxConnectionsPerChild   0
</IfModule>


# event MPM
# StartServers: initial number of server processes to start
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestWorkers: maximum number of worker threads
# MaxConnectionsPerChild: maximum number of connections a server process serves
#                         before terminating
<IfModule mpm_event_module>
    StartServers             3
    MinSpareThreads         75
    MaxSpareThreads        250
    ThreadsPerChild         25
    MaxRequestWorkers      400
    MaxConnectionsPerChild   0
</IfModule>


# NetWare MPM
# ThreadStackSize: Stack size allocated for each worker thread
# StartThreads: Number of worker threads launched at server startup
# MinSpareThreads: Minimum number of idle threads, to handle request spikes
# MaxSpareThreads: Maximum number of idle threads
# MaxThreads: Maximum number of worker threads alive at the same time
# MaxConnectionsPerChild: Maximum  number of connections a thread serves. It
#                         is recommended that the default value of 0 be set
#                         for this directive on NetWare.  This will allow the
#                         thread to continue to service requests indefinitely.
<IfModule mpm_netware_module>
    ThreadStackSize      65536
    StartThreads           250
    MinSpareThreads         25
    MaxSpareThreads        250
    MaxThreads            1000
    MaxConnectionsPerChild   0
</IfModule>


# OS/2 MPM
# StartServers: Number of server processes to maintain
# MinSpareThreads: Minimum number of idle threads per process,
#                  to handle request spikes
# MaxSpareThreads: Maximum number of idle threads per process
# MaxConnectionsPerChild: Maximum number of connections per server process
<IfModule mpm_mpmt_os2_module>
    StartServers             2
    MinSpareThreads          5
    MaxSpareThreads         10
    MaxConnectionsPerChild   0
</IfModule>


# WinNT MPM
# ThreadsPerChild: constant number of worker threads in the server process
# MaxConnectionsPerChild: maximum number of connections a server process serves
<IfModule mpm_winnt_module>
    ThreadsPerChild        150
    MaxConnectionsPerChild   0
</IfModule>


# The maximum number of free Kbytes that every allocator is allowed
# to hold without calling free(). In threaded MPMs, every thread has its own
# allocator. When not set, or when set to zero, the threshold will be set to
# unlimited.
<IfModule !mpm_netware_module>
    MaxMemFree            2048
</IfModule>
<IfModule mpm_netware_module>
    MaxMemFree             100
</IfModule>



```

---

### Post by Habitual on 2017-07-05
Sorry, I am not sure about the CentOS/Redhat version of apache2

---

### Post by slickymaster on 2017-07-05
@vicky219:

I've again, swapped the quote tags for code tags, in your post [here]("https://ubuntuforums.org/showthread.php?t=2365330&p=13662699&viewfull=1#post13662699"). Please don't change it again for quote tags.

---


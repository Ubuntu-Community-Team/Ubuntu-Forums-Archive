---
title: "Apache2 with Tomcat6 on 9.10"
date: 2009-11-16
forum: Server Platforms
---

### Post by _M_ on 2009-11-16
Hi all, 
I can't get Apache2 and Tomcat6 work with each other using Mod_Jk on Ubuntu 9.10 Server Edition. No errors, only it doesn't redirect… 

Here is what I did:

- installed Apache2, Tomcat. Both are running, I can see apache "It works!" page at [http://myserver.org](http://myserver.org) the start page of my deployed tomcat webapplication "MyApp" at [http://myserver.org:8080/MyApp](http://myserver.org:8080/MyApp)

- installed mod_jk with apt-get install libapache2-mod-jk

- edited /etc/libapache2-mod-jk/workers.properties to:

> workers.tomcat_home=/var/lib/tomcat6
workers.java_home=/usr/lib/jvm/default-java
ps=/
worker.list=ajp13_worker
worker.ajp13_worker.port=8009
worker.ajp13_worker.host=localhost
worker.ajp13_worker.type=ajp13
worker.ajp13_worker.lbfactor=1
worker.loadbalancer.type=lb
worker.loadbalancer.balance_workers=ajp13_worker

- added the following to /etc/apache2/apache2.conf:

> JkWorkersFile   /etc/libapache2-mod-jk/workers.properties
JkLogFile       /var/log/apache2/mod_jk.log
JkLogLevel      debug
JkMount /MyApp ajp13_worker
JkMount /MyApp/* ajp13_worker


- added the following Connector to /var/lib/tomcat6/conf/server.xml:
>  <Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />

- restarted Tomcat6
- restared Apache2

- go to [http://myserver.org/MyApp](http://myserver.org/MyApp) --> 404 Not Found


Then I did some troubleshooting: 

- checked content of file /etc/apache2/mods-enabled/jk.load:
LoadModule jk_module /usr/lib/apache2/modules/mod_jk.so   

- checked that /usr/lib/apache2/modules/mod_jk.so exists

- looked at /var/log/apache2/mod_jk-log: no errors or warnings, all seems normal. See complete log output below.

Can someone help me with this problem?

Thanks, Mirko


> 

[Mon Nov 16 10:53:19.042 2009] [15974:1013569328] [debug] ajp_create_endpoint_cache::jk_ajp_common.c (2296): setting connection pool size to 1 with min 1[Mon Nov 16 10:53:19.042 2009] [15974:1013569328] [info] init_jk::mod_jk.c (2830): mod_jk/1.2.26 initialized[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_set_time_fmt::jk_util.c (430): Pre-processed log time stamp format is '[%a %b %d %H:%M:%S.000 %Y] '
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] uri_worker_map_open::jk_uri_worker_map.c (427): rule map size is 2
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] uri_worker_map_add::jk_uri_worker_map.c (387): exact rule '/MyApp=ajp13_worker' source 'JkMount' w
as added
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] uri_worker_map_add::jk_uri_worker_map.c (379): wildchar rule '/MyApp/*=ajp13_worker' source 'JkMou
nt' was added
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_set_time_fmt::jk_util.c (430): Pre-processed log time stamp format is '[%a %b %d %H:%M:%S.000 %Y] '
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] do_shm_open::jk_shm.c (402): Truncated shared memory to 28800
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] do_shm_open::jk_shm.c (447): Initialized shared memory size=28800 free=28672 addr=0x7fa13c695000
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] do_shm_open_lock::jk_shm.c (321): Opened shared memory lock /var/log/apache2/jk-runtime-status.15975.l
ock
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] init_jk::mod_jk.c (2780): Initialized shm:/var/log/apache2/jk-runtime-status.15975 (28672 bytes)
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] init_jk::mod_jk.c (2797): Setting default connection pool max size to 1
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_read_property::jk_map.c (492): Adding property 'workers.tomcat_home' with value '/var/lib/tomca
t6' to map.
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_read_property::jk_map.c (492): Adding property 'workers.java_home' with value '/usr/lib/jvm/def
ault-java' to map.
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_read_property::jk_map.c (492): Adding property 'ps' with value '/' to map.
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_read_property::jk_map.c (492): Adding property 'worker.list' with value 'ajp13_worker' to map.[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_read_property::jk_map.c (492): Adding property 'worker.ajp13_worker.port' with value '8009' to 
map.
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_read_property::jk_map.c (492): Adding property 'worker.ajp13_worker.host' with value 'localhost
' to map.
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_read_property::jk_map.c (492): Adding property 'worker.ajp13_worker.type' with value 'ajp13' to
 map.[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_read_property::jk_map.c (492): Adding property 'worker.ajp13_worker.lbfactor' with value '1' to
 map.
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_read_property::jk_map.c (492): Adding property 'worker.loadbalancer.type' with value 'lb' to ma
p.
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_read_property::jk_map.c (492): Adding property 'worker.loadbalancer.balance_workers' with value
 'ajp13_worker' to map.[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_resolve_references::jk_map.c (770): Checking for references with prefix worker. with wildcard (
recursion 1)
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_dump::jk_map.c (590): Dump of map: 'ServerRoot' -> '/etc/apache2'
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_dump::jk_map.c (590): Dump of map: 'workers.tomcat_home' -> '/var/lib/tomcat6'
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_dump::jk_map.c (590): Dump of map: 'workers.java_home' -> '/usr/lib/jvm/default-java'
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_dump::jk_map.c (590): Dump of map: 'ps' -> '/'[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_dump::jk_map.c (590): Dump of map: 'worker.list' -> 'ajp13_worker'
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_dump::jk_map.c (590): Dump of map: 'worker.ajp13_worker.port' -> '8009'
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_dump::jk_map.c (590): Dump of map: 'worker.ajp13_worker.host' -> 'localhost'
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_dump::jk_map.c (590): Dump of map: 'worker.ajp13_worker.type' -> 'ajp13'
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_dump::jk_map.c (590): Dump of map: 'worker.ajp13_worker.lbfactor' -> '1'
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_dump::jk_map.c (590): Dump of map: 'worker.loadbalancer.type' -> 'lb'[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] jk_map_dump::jk_map.c (590): Dump of map: 'worker.loadbalancer.balance_workers' -> 'ajp13_worker'
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] build_worker_map::jk_worker.c (241): creating worker ajp13_worker
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] wc_create_worker::jk_worker.c (145): about to create instance ajp13_worker of ajp13
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] wc_create_worker::jk_worker.c (158): about to validate and init ajp13_worker
[Mon Nov 16 10:53:19.053 2009] [15975:1013569328] [debug] ajp_validate::jk_ajp_common.c (2257): worker ajp13_worker contact is 'localhost:8009'
[Mon Nov 16 10:53:19.054 2009] [15975:1013569328] [debug] ajp_init::jk_ajp_common.c (2388): setting endpoint options:
[Mon Nov 16 10:53:19.054 2009] [15975:1013569328] [debug] ajp_init::jk_ajp_common.c (2391): keepalive:        0
[Mon Nov 16 10:53:19.054 2009] [15975:1013569328] [debug] ajp_init::jk_ajp_common.c (2395): timeout:          0
[Mon Nov 16 10:53:19.054 2009] [15975:1013569328] [debug] ajp_init::jk_ajp_common.c (2399): buffer size:      0
[Mon Nov 16 10:53:19.054 2009] [15975:1013569328] [debug] ajp_init::jk_ajp_common.c (2403): pool timeout:     0
[Mon Nov 16 10:53:19.054 2009] [15975:1013569328] [debug] ajp_init::jk_ajp_common.c (2407): connect timeout:  0
[Mon Nov 16 10:53:19.054 2009] [15975:1013569328] [debug] ajp_init::jk_ajp_common.c (2411): reply timeout:    0
[Mon Nov 16 10:53:19.054 2009] [15975:1013569328] [debug] ajp_init::jk_ajp_common.c (2415): prepost timeout:  0
[Mon Nov 16 10:53:19.054 2009] [15975:1013569328] [debug] ajp_init::jk_ajp_common.c (2419): recovery options: 0
[Mon Nov 16 10:53:19.054 2009] [15975:1013569328] [debug] ajp_init::jk_ajp_common.c (2423): retries:          2
[Mon Nov 16 10:53:19.054 2009] [15975:1013569328] [debug] ajp_init::jk_ajp_common.c (2427): max packet size:  8192
[Mon Nov 16 10:53:19.054 2009] [15975:1013569328] [debug] ajp_create_endpoint_cache::jk_ajp_common.c (2296): setting connection pool size to 1 with min 1
[Mon Nov 16 10:53:19.054 2009] [15975:1013569328] [info] init_jk::mod_jk.c (2830): mod_jk/1.2.26 initialized
[Mon Nov 16 10:53:19.065 2009] [15978:1013569328] [debug] do_shm_open::jk_shm.c (457): Attached shared memory [2] size=28672 free=28672 addr=0x7fa13c695000
[Mon Nov 16 10:53:19.065 2009] [15978:1013569328] [debug] do_shm_open::jk_shm.c (471): Reseting the shared memory for child 2
[Mon Nov 16 10:53:19.065 2009] [15978:1013569328] [debug] do_shm_open_lock::jk_shm.c (262): Duplicated shared memory lock /var/log/apache2/jk-runtime-status.15975.lock
[Mon Nov 16 10:53:19.065 2009] [15978:1013569328] [debug] jk_child_init::mod_jk.c (2735): Attached shm:/var/log/apache2/jk-runtime-status.15975 (28672 bytes)
[Mon Nov 16 10:53:19.065 2009] [15978:1013569328] [debug] jk_child_init::mod_jk.c (2745): Initialized mod_jk/1.2.26
[Mon Nov 16 10:53:19.065 2009] [15979:1013569328] [debug] do_shm_open::jk_shm.c (457): Attached shared memory [3] size=28672 free=28672 addr=0x7fa13c695000
[Mon Nov 16 10:53:19.065 2009] [15979:1013569328] [debug] do_shm_open::jk_shm.c (471): Reseting the shared memory for child 3
[Mon Nov 16 10:53:19.065 2009] [15979:1013569328] [debug] do_shm_open_lock::jk_shm.c (262): Duplicated shared memory lock /var/log/apache2/jk-runtime-status.15975.lock
[Mon Nov 16 10:53:19.065 2009] [15979:1013569328] [debug] jk_child_init::mod_jk.c (2735): Attached shm:/var/log/apache2/jk-runtime-status.15975 (28672 bytes)
[Mon Nov 16 10:53:19.065 2009] [15979:1013569328] [debug] jk_child_init::mod_jk.c (2745): Initialized mod_jk/1.2.26
[Mon Nov 16 10:53:19.065 2009] [15980:1013569328] [debug] do_shm_open::jk_shm.c (457): Attached shared memory [4] size=28672 free=28672 addr=0x7fa13c695000
[Mon Nov 16 10:53:19.065 2009] [15980:1013569328] [debug] do_shm_open::jk_shm.c (471): Reseting the shared memory for child 4
[Mon Nov 16 10:53:19.065 2009] [15980:1013569328] [debug] do_shm_open_lock::jk_shm.c (262): Duplicated shared memory lock /var/log/apache2/jk-runtime-status.15975.lock
[Mon Nov 16 10:53:19.065 2009] [15980:1013569328] [debug] jk_child_init::mod_jk.c (2735): Attached shm:/var/log/apache2/jk-runtime-status.15975 (28672 bytes)
[Mon Nov 16 10:53:19.065 2009] [15980:1013569328] [debug] jk_child_init::mod_jk.c (2745): Initialized mod_jk/1.2.26
[Mon Nov 16 10:53:19.066 2009] [15981:1013569328] [debug] do_shm_open::jk_shm.c (457): Attached shared memory [5] size=28672 free=28672 addr=0x7fa13c695000
[Mon Nov 16 10:53:19.066 2009] [15981:1013569328] [debug] do_shm_open::jk_shm.c (471): Reseting the shared memory for child 5
[Mon Nov 16 10:53:19.066 2009] [15981:1013569328] [debug] do_shm_open_lock::jk_shm.c (262): Duplicated shared memory lock /var/log/apache2/jk-runtime-status.15975.lock
[Mon Nov 16 10:53:19.066 2009] [15981:1013569328] [debug] jk_child_init::mod_jk.c (2735): Attached shm:/var/log/apache2/jk-runtime-status.15975 (28672 bytes)
[Mon Nov 16 10:53:19.066 2009] [15981:1013569328] [debug] jk_child_init::mod_jk.c (2745): Initialized mod_jk/1.2.26
[Mon Nov 16 10:53:19.066 2009] [15982:1013569328] [debug] do_shm_open::jk_shm.c (457): Attached shared memory [6] size=28672 free=28672 addr=0x7fa13c695000
[Mon Nov 16 10:53:19.067 2009] [15982:1013569328] [debug] do_shm_open::jk_shm.c (471): Reseting the shared memory for child 6
[Mon Nov 16 10:53:19.067 2009] [15982:1013569328] [debug] do_shm_open_lock::jk_shm.c (262): Duplicated shared memory lock /var/log/apache2/jk-runtime-status.15975.lock
[Mon Nov 16 10:53:19.067 2009] [15982:1013569328] [debug] jk_child_init::mod_jk.c (2735): Attached shm:/var/log/apache2/jk-runtime-status.15975 (28672 bytes)
[Mon Nov 16 10:53:19.067 2009] [15982:1013569328] [debug] jk_child_init::mod_jk.c (2745): Initialized mod_jk/1.2.26                       


---

### Post by sicn on 2009-11-16
First things first, you may try with mod_proxy_ajp instead. It's much simpler to configure.

However, even mod_jk should work.

One of the most common mistakes you already eradicated (not activating the module by creating a link to mods-available). Another common mistake is to not point out the workers.properties correctly.

Mine used to be (before I switched to mod_proxy_ajp) very minimal:

worker.list=tomcat
worker.tomcat.port=8009
worker.tomcat.host=localhost
worker.tomcat.type=ajp13

Besides that, most things are correct.

However, since you go directly to the "Welcome page" I am wondering if you use name-based virtual hosts?

If perhaps that is the case, you could try to create a file called myserver-www in sites-available that contains the following

<VirtualHost *:80>
  ServerAdmin [email]webmaster@myserver.org[/email]
  ServerName [www.myserver.org](www.myserver.org)

  JkMount / tomcat
  # logging stuff
</VirtualHost>

Try that and tell me if it works. If not, I can check in my old backed up mod_jk files and see if I can help you further.

---

### Post by _M_ on 2009-11-16
Hi sicn,
I wasn't aware of mod_proxy_ajp. I switched to that and it works - thanks a lot! 

One thing I still have to figure out is how to except certain requests from being redirected. For example, I want the request [http://myserver.org/phpmyadmin](http://myserver.org/phpmyadmin) *not* to be redirected to Tomcat.

Do you have a configuration example for that? Below is my current configuration.

Thanks, Mirko


> <VirtualHost *:80>
   ServerName localhost
   ErrorLog /var/log/apache2/ajp.error.log
   CustomLog /var/log/apache2/ajp.log combined

   <Proxy *>
     AddDefaultCharset Off
     Order deny,allow
     Allow from all
   </Proxy>

   ProxyPass / ajp://localhost:8009/
   ProxyPassReverse / ajp://localhost:8009/
</VirtualHost>

---

### Post by EdUbun on 2009-12-04
Hi

I'm having exactly this too. My configs are equal to the first post. All the applications in the list of the tomcat manager will resault in the requested resource is not available. 

Only I can't switch and must stay with mod_jk.

Where to continue solving?

Could it be that the port 8009 is listening to ipv6? I don't use that...

---


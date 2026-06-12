---
title: "Apache2 Mutliple Processes Running"
date: 2011-05-17
forum: Server Platforms
---

### Post by coljohnhannibalsmith on 2011-05-17
Hello,

I have LAMP on my unit as a development sandbox; and I have 6 Apache2 processes running.  Is this normal???

How do I get it to just launch one or two of these. My site's not busy at all; because it's just a sandbox on my laptop; and all the extra processes seem to actually slow my web apps way down...

Is this a setting in **/etc/init.d** ???  Where can I change this setting???



Thanks Hannibal

---

### Post by hawkmage on 2011-05-17
If you run:
```
apache2 -V
```
There is a line that starts with "Server MPM", it will say "worker" or "prefork" rarely "event".

Look in the /etc/apache2/apavhe2.conf file and there are sections for each of the server MPM types.  The values in those sections control the processes that are spawned.

---

### Post by coljohnhannibalsmith on 2011-05-18
Thank you,

**I found it; and I have set the values as follows:**

```
[COLOR=Blue][B]<IfModule mpm_prefork_module>
    StartServers                 1
    MinSpareServers          0
    MaxSpareServers          0
    MaxClients                  10
    MaxRequestsPerChild   0
</IfModule>[/B][/COLOR]
``````
[COLOR=Blue][B]<IfModule mpm_worker_module>
    StartServers                 1
    MinSpareThreads         0
    MaxSpareThreads         5 
    ThreadLimit                25
    ThreadsPerChild           5
    MaxClients                  10
    MaxRequestsPerChild   0
</IfModule>[/B][/COLOR]
``````
[COLOR=Blue][B]<IfModule mpm_event_module>
    StartServers                 1
    MinSpareThreads         0
    MaxSpareThreads         5 
    ThreadLimit                25
    ThreadsPerChild           5
    MaxClients                  10
    MaxRequestsPerChild   0
</IfModule>[/B][/COLOR]
```Based on these settings Apache2 should start with 1 sever; but starts with 2.  This is an improvement; but is there any way to get it to start with only one; and 'not' spawn any addition children???



[B]
Thanks Hannibal[/B]

---


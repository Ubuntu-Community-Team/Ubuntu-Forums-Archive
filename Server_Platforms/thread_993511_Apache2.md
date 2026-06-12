---
title: "Apache2"
date: 2008-11-25
forum: Server Platforms
---

### Post by Drezard on 2008-11-25
Im getting these errors when I 'cat /var/log/apache2/error.log':

> 

[Tue Nov 25 17:44:04 2008] [alert] (12)Cannot allocate memory: apr_thread_create: unable to create worker thread
[Tue Nov 25 17:44:04 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Tue Nov 25 17:44:04 2008] [alert] (12)Cannot allocate memory: apr_thread_create: unable to create worker thread
[Tue Nov 25 17:44:06 2008] [alert] No active workers found... Apache is exiting!



I 'apt-get install apache2-mpm-worker', and I have this entry in my apache2.conf:

```


<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>


```

Whats wrong?

Daniel

---

### Post by RealPSL on 2008-11-26
Can you provide the output of ```
free -m
``` when the problem is occurring? Your system could be running out of memory to create additional processes.

---


---
title: "Apache2 MPM version"
date: 2008-06-18
forum: Server Platforms
---

### Post by theonegod on 2008-06-18
How can I tell which MPM apache is configured to use? I can't find a command for this on google nor a reference to which is default in an Ubuntu Server LAMP installation.

---

### Post by hexanol on 2008-06-20
```
apache2 -l
```
or
```
apache2 -V
```
Is that what you wanted to know ?

---

### Post by theonegod on 2008-06-20
Yes thank you. I am learning apache as I go. I take it from the following output.

Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  prefork.c
  http_core.c
  mod_so.c


That I am using the prefork MPM.

I have modified my default prefork settings to those below

<IfModule mpm_prefork_module>
    StartServers          15
    MinSpareServers       10
    MaxSpareServers      20
    MaxClients          250
    MaxRequestsPerChild   0
</IfModule>

For an IBM Duel Core Blade Server with 2gigs of ram can I increase these any more for better handling of incomming connections or should this be fine? Our server hosts about 40 domains on a lead generation platform that gets tens of thousands of leads a day.

---

### Post by hexanol on 2008-06-20
> I have modified my default prefork settings to those below

<IfModule mpm_prefork_module>
StartServers 15
MinSpareServers 10
MaxSpareServers 20
MaxClients 250
MaxRequestsPerChild 0
</IfModule>

For an IBM Duel Core Blade Server with 2gigs of ram can I increase these any more for better handling of incomming connections or should this be fine? Our server hosts about 40 domains on a lead generation platform that gets tens of thousands of leads a day.

Well, this is a totally different question that I can't answer! :p

But 2 GB of memory looks quite "small" (geez, I have a desktop computer with twice memory as that ;)). I mean, for better performance, I guess you want the OS to cache/buffer as many files as possible, which means a good amount of memory, and you certainly doesn't want your server to start using virtual memory (ie, using the swap), but it's just supposition, I really know nothing about server in general.

---

### Post by theonegod on 2008-06-20
2gig is not alot for a workstation but isn't to bad for a apache server. The machine is not having to do as much as a workstation that may be playing games, office apps, and several other applications at once. 

Used and buffered memory is seldom over 20% on this box. Though cached is certainly high :)

---


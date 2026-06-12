---
title: "/var/run/apache2 gets deleted automatically!!"
date: 2010-01-14
forum: Server Platforms
---

### Post by upengan78 on 2010-01-14
Hi,

This is JEOS 8.04 and kernel 2.6.24-24

Apache2 version is 2.2.8. I have ssl mod enabled in mods-enabled directory but when I restart apache2, error.log shows below error,

```

[Thu Jan 14 10:14:44 2010] [error] (2)No such file or directory: Cannot create SSLMutex with file `/var/run/apache2/ssl_mutex'
Configuration Failed
[Thu Jan 14 10:21:13 2010] [error] (2)No such file or directory: Cannot create SSLMutex with file `/var/run/apache2/ssl_mutex'
Configuration Failed

```Apache2 never start due to this. Therefore I found a solution, mkdir /var/run/apache2 then apache2 restart will make apache2 start and server requests.

The main problem why I am opening thread is that whenever system is rebooted , (init 6 or reboot) then when system comes up apache2 does not start again due to the error I copied above. I have to create /var/run/apache2 again.

I'm not sure if this is a bug or not but if there is a clean fix like using some other directory or making system not delete /var/run/apache2 will be really useful

```
lsb_release -rd
Description:    Ubuntu 8.04.3 LTS
Release:    8.04
```Default options in ssl.conf in mods-enabled directory

```
SSLSessionCache        shmcb:/var/run/apache2/ssl_scache(512000)
SSLMutex  file:/var/run/apache2/ssl_mutex
```Please advise.

---


---
title: "Nginx won't start, can't decipher the problem"
date: 2020-06-12
forum: Server Platforms
---

### Post by jscooper22 on 2020-06-12
Hi,

I broke nginx already? It's only been a day!:-(


I was trying to do the last step of the LAMP, and after I installed PHP, Nginx will not restart. I'm not sure what I did but I think it has something to do wit trying to install Webmin because that's where I issued the only commands having to do with jcameron-key.asc. I'm not even positive I"m reading these right and this is the problem:


```
systemctl status nginx.service
&#9679; nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Fri 2020-06-12 21:11:51 EDT; 32s ago
       Docs: man:nginx(8)
    Process: 80402 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=1/FAILURE)


Jun 12 21:11:51 testubuntu systemd[1]: Starting A high performance web server and a reverse proxy server...
Jun 12 21:11:51 testubuntu nginx[80402]: nginx: [emerg] unexpected end of file, expecting ";" or "}" in /etc/nginx/sites-enabled/jcam>
Jun 12 21:11:51 testubuntu nginx[80402]: nginx: configuration file /etc/nginx/nginx.conf test failed
Jun 12 21:11:51 testubuntu systemd[1]: nginx.service: Control process exited, code=exited, status=1/FAILURE
Jun 12 21:11:51 testubuntu systemd[1]: nginx.service: Failed with result 'exit-code'.
Jun 12 21:11:51 testubuntu systemd[1]: Failed to start A high performance web server and a reverse proxy server.
admin@testubuntu:/var/www$ journalctl -xe
Jun 12 21:12:20 testubuntu multipathd[762]: sda: failed to get udev uid: Invalid argument
Jun 12 21:12:20 testubuntu multipathd[762]: sda: failed to get sysfs uid: Invalid argument
Jun 12 21:12:20 testubuntu multipathd[762]: sda: failed to get sgio uid: No such file or directory
Jun 12 21:12:25 testubuntu multipathd[762]: sda: add missing path


(the above repeats several times)


Jun 12 21:13:10 testubuntu multipathd[762]: sda: failed to get udev uid: Invalid argument
Jun 12 21:13:10 testubuntu multipathd[762]: sda: failed to get sysfs uid: Invalid argument
Jun 12 21:13:10 testubuntu multipathd[762]: sda: failed to get sgio uid: No such file or directory



```

jcameron-key.asc looks to me like a certificate, so I'm not sure what ; or } it's missing.

Thanks,

Jeff

---

### Post by QIII on 2020-06-12
Your problem lies here, but not seeing it I can't tell you exactly what is wrong:

```
Jun 12 21:11:51 testubuntu nginx[80402]: nginx: [emerg] unexpected end of file, expecting ";" or "}" in /etc/nginx/sites-enabled/jcam>
```

Somewhere you have a semi-colon missing or an unmatched curly bracket.

By the way, if you have set this up the recommended way, ***/etc/nginx/sites-enabled/jcam*** should be a symbolic link to /***etc/nginx/sites-available/jcam***.

---

### Post by TheFu on 2020-06-13
i know nothing about running a LEMP setup, but use nginx extensively.
Use **sudo nginx -t **to check the config and 
**sudo nginx -T** to have all the configs shown as see by nginx.  sudo is necessary due to log file stuff typically.

if you are new to Linux, please reconsider using webmin.  Often it is setup in a way that is bad for security and opens many attack vectors.  if you are an expert, then be certain to lock it down so only localhost connections are possible.

The sda problem is probably in the fstab config.

---

### Post by jscooper22 on 2020-06-15
Hi, thanks for that. But I double-checked and the full error is 

nginx[164432]: nginx: [emerg] unexpected end of file, expecting ";" or "}" in /etc/nginx/sites-enabled/jcameron-key.asc:25

but jcameron-key.asc is a key file, not code. So I don't know why it's looking for ";" or "}".

---

### Post by TheFu on 2020-06-15
Any files in sites-enabled/  are config files.  Put it somewhere else.  i put ssl certs in /etc/nginx/ssl/  under subdirs  based on the website URL.

Hopefully, all your sites-enabled/ files are just symlinks from files in sites-available/

---

### Post by jscooper22 on 2020-06-17
I got it going by completely removing Webmin and everything associated with it. Site is up and working. It's on  a VM so I'll tinker with a clone at another time to see what's up Thanks for the help & advice all!

Jeff

---


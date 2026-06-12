---
title: "Install nginx alongside Apache, to use port 8443"
date: 2018-07-25
forum: Server Platforms
---

### Post by Heeter on 2018-07-25
Hi all,

Trying to install nginx alongside my mature installation of Apache. This is for 16.04LTS. Apache currently working properly for the last couple of years.

Trying install nginx alongside, but the install always fails. something about nginx-core.
```

apt install nginx

```

How can I get both to work side by side, but restrict nginx to port 8443.

Regards

---

### Post by izznogooood on 2018-07-26
One option is Docker, another is to post the error...

---

### Post by Heeter on 2018-07-27
Here ya go:

```

root@mail:/home/adminpc# apt-get install nginx-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nginx-core is already the newest version (1.10.3-0ubuntu0.16.04.2).
nginx-core set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Setting up nginx-core (1.10.3-0ubuntu0.16.04.2) ...
Job for nginx.service failed because the control process exited with error code. See "systemctl status nginx.service" and "journalctl -xe" for details.
invoke-rc.d: initscript nginx, action "start" failed.
&#9679; nginx.service - A high performance web server and a reverse proxy server
   Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2018-07-27 15:00:21 MDT; 8ms ago
  Process: 4353 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=1/FAILURE)
  Process: 4349 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/SUCCESS)

Jul 27 15:00:18 mail nginx[4353]: nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)
Jul 27 15:00:19 mail nginx[4353]: nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)
Jul 27 15:00:19 mail nginx[4353]: nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)
Jul 27 15:00:20 mail nginx[4353]: nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)
Jul 27 15:00:20 mail nginx[4353]: nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)
Jul 27 15:00:21 mail nginx[4353]: nginx: [emerg] still could not bind()
Jul 27 15:00:21 mail systemd[1]: nginx.service: Control process exited, code=exited status=1
Jul 27 15:00:21 mail systemd[1]: Failed to start A high performance web server and a reverse proxy server.
Jul 27 15:00:21 mail systemd[1]: nginx.service: Unit entered failed state.
Jul 27 15:00:21 mail systemd[1]: nginx.service: Failed with result 'exit-code'.
dpkg: error processing package nginx-core (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nginx:
 nginx depends on nginx-core (>= 1.10.3-0ubuntu0.16.04.2) | nginx-full (>= 1.10.3-0ubuntu0.16.04.2) | nginx-light (>= 1.10.3-0ubuntu0.16.04.2) | nginx-extras (>= 1.10.3-0ubuntu0.16.04.2); however:
  Package nginx-core is not configured yet.
  Package nginx-full is not installed.
  Package nginx-light is not installed.
  Package nginx-extras is not installed.
 nginx depends on nginx-core (<< 1.10.3-0ubuntu0.16.04.2.1~) | nginx-full (<< 1.10.3-0ubuntu0.16.04.2.1~) | nginx-light (<< 1.10.3-0ubuntu0.16.04.2.1~) | nginx-extras (<< 1.10.3-0ubuntu0.16.04.2.1~); however:
  Package nginx-core is not configured yet.
  Package nginx-full is not installed.
  Package nginx-light is not installed.
  Package nginx-extras is not installed.

dpkg: error processing package nginx (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 nginx-core
 nginx
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@mail:/home/adminpc# 

```

I do have Docker installed, how do I install nginx docker if this direct install method doesn't work? I have zero knowledge of how nginx works.

Regards

---

### Post by izznogooood on 2018-07-27
Nginx does not fail to install, it fails to start.

You need to change the config file:

```
/[SIZE=2][FONT=arial][COLOR=#586069]etc/nginx/sites-available/default[/COLOR][/FONT][/SIZE]
```

look at "listen 80", im guessing it tries to listen to the same port as Apache...

change it and:

 ```
sudo systemctl restart nginx
```

Then start reading manuals :)

---

### Post by Heeter on 2018-07-27
That did it!!!!!!!!!!!!

Thanks a million!

---


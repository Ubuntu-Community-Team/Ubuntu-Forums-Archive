---
title: "Monit Apache2 restart and Apache status"
date: 2017-04-27
forum: Server Platforms
---

### Post by waqt on 2017-04-27
I am practicing using linux/Ubuntu (Ubuntu 16.04 LTS)

I have installed apache2 on my cloud server (Lightsail). I have also installed Monit to monitor Apache2. The monitoring is working correctly and Monit restarts Apache2 when it's down (I did _sudo /etc/init.d/apache2 stop_ to test it). The IP (in browser) went unavailable and then came back online.

The issue I am facing is that when Monit restarts apache the sudo /etc/init.d/apache2 status shows the service as down, but apache is running (IP checked on browser).

```
ubuntu@webserver:~$ sudo /etc/init.d/apache2 status
&#9679; apache2.service - LSB: Apache2 web server
   Loaded: loaded (/etc/init.d/apache2; bad; vendor preset: enabled)
  Drop-In: /lib/systemd/system/apache2.service.d
           &#9492;&#9472;apache2-systemd.conf
   Active: inactive (dead) since Thu 2017-04-27 22:21:17 UTC; 2min 51s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 22026 ExecStop=/etc/init.d/apache2 stop (code=exited, status=0/SUCCESS)
  Process: 20709 ExecReload=/etc/init.d/apache2 reload (code=exited, status=0/SUCCESS)
  Process: 21958 ExecStart=/etc/init.d/apache2 start (code=exited, status=0/SUCCESS)
    Tasks: 0
   Memory: 0B
      CPU: 125ms


Apr 27 22:17:25 webserver systemd[1]: Starting LSB: Apache2 web server...
Apr 27 22:17:25 webserver apache2[21958]:  * Starting Apache httpd web server apache2
Apr 27 22:17:26 webserver apache2[21958]:  *
Apr 27 22:17:26 webserver systemd[1]: Started LSB: Apache2 web server.
Apr 27 22:21:17 webserver systemd[1]: Stopping LSB: Apache2 web server...
Apr 27 22:21:17 webserver apache2[22026]:  * Stopping Apache httpd web server apache2
Apr 27 22:21:17 webserver apache2[22026]:  *
Apr 27 22:21:17 webserver systemd[1]: Stopped LSB: Apache2 web server.

```
This is what _sudo vim /etc/monit/monitrc_ has:
```
check process apache2 with pidfile /run/apache2/apache2.pid
    start program = "/etc/init.d/apache2 restart" with timeout 15 seconds
    stop program  = "/etc/init.d/apache2 stop"

```

How do I make sure that Apache2 is restarted correctly so that _sudo /etc/init.d/apache2 status_ shows the correct status?

---

### Post by waqt on 2017-05-03
Anyone?

---

### Post by SeijiSensei on 2017-05-03
You don't tell us what version of Ubuntu Server you are using.  From looking at the output I'm going to guess it is 16.04 or later.

In 16.04 Ubuntu adopted **systemd** to replace the SysV init process it had used to manage services in the past.  The commands you list seem to be from that now deprecated method.

I'd change monitrc to read like this:
```

check process apache2 with pidfile /run/apache2/apache2.pid
    start program = "**systemctl restart apache2.service**" with timeout 15 seconds
    stop program  = "**systemctl stop apache2.service**"

```

You should try using systemctl for everything.  For instance, you can check Apache's status with
```
sudo systemctl status apache2.service
```.

---

### Post by waqt on 2017-05-03
@SeijiSensei Thank you. I have updated my main post with the version number of Ubuntu server. Yes, it is 16.04.

I tried your suggestions but it seems that monit does not like it;

```
ubuntu@webserver:/var/log$ sudo monit -t
/etc/monit/monitrc:197: Program does not exist: 'systemctl'
/etc/monit/monitrc:198: Program does not exist: 'systemctl'
```

If I run this on command line/ssh it works
```
ubuntu@webserver:/var/log$ systemctl status apache2.service
&#9679; apache2.service - LSB: Apache2 web server
   Loaded: loaded (/etc/init.d/apache2; bad; vendor preset: enabled)
  Drop-In: /lib/systemd/system/apache2.service.d
           &#9492;&#9472;apache2-systemd.conf
   Active: inactive (dead) since Wed 2017-05-03 15:32:33 UTC; 21min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 1815 ExecStop=/etc/init.d/apache2 stop (code=exited, status=0/SUCCESS)
  Process: 30257 ExecReload=/etc/init.d/apache2 reload (code=exited, status=0/SUCCESS)
  Process: 1804 ExecStart=/etc/init.d/apache2 start (code=exited, status=0/SUCCESS)


May 03 15:32:32 webserver systemd[1]: Stopped LSB: Apache2 web server.
May 03 15:32:32 webserver systemd[1]: Starting LSB: Apache2 web server...
May 03 15:32:32 webserver apache2[1804]:  * Starting Apache httpd web server apache2
May 03 15:32:32 webserver apache2[1804]:  *
May 03 15:32:32 webserver apache2[1815]:  * Stopping Apache httpd web server apache2
May 03 15:32:33 webserver apache2[1815]:  *
May 03 15:32:33 webserver systemd[1]: Started LSB: Apache2 web server.

```
Suggestions?

[B]EDIT:
[/B]
After some Googling, the following fixed the issue:
```

check process apache2 with pidfile /run/apache2/apache2.pid
   start program = "/bin/systemctl restart apache2.service" with timeout 15 seconds
   stop program = "/bin/systemctl stop apache2.service"
```

---


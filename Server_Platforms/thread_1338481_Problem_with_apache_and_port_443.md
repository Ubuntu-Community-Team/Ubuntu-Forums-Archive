---
title: "Problem with apache and port 443"
date: 2009-11-26
forum: Server Platforms
---

### Post by bprof on 2009-11-26
When I start apache I get the following error:

(98 )Address already in use: make_sock: could not bind to address [::]:443

I ran 
```
netstat -an | grep :443
``` nothing showed up.

I ran ```
lsof -i :443
``` also nothing showed up.

I ran ```
killall -9 apache2
``` then tried to start apache again but got the same error.

I don't have any service other than ssh running on the server.

I edited /etc/apache2/ports.conf commented out Listen 443 and started apache2. It worked just fine.

Then I re-enabled Listen 443 and did
> /etc/apache2 reload and now HTTPS works.

My question what could be binding the port? How can I find it if netstat and lsof are not showing it?

I just don't won't to keep using this work around.

thx

---

### Post by munky99999 on 2009-11-26
> When I start apache I get the following error:

(98 )Address already in use: make_sock: could not bind to address [::]:443
My first thought would be selinux. Perhaps you have installed it?

> netstat -an | grep :443
Should show up as webserver. Unless you changed the port. It not showing up pretty much says it's not running.

> lsof -i :443

also nothing showed up.
Even if everything was running perfectly. I wouldnt expect this to show anything.

> then tried to start apache again but got the same error.

I don't have any service other than ssh running on the server.

I edited /etc/apache2/ports.conf commented out Listen 443 and started apache2. It worked just fine.

Then I re-enabled Listen 443 and did
Quote:
/etc/apache2 reload 
Wierd. IF selinux... that's a pretty nasty workaround by the sounds of things. If not selinux; im really not sure.

---

### Post by bprof on 2009-11-27
Thank you munky99999!

I don't have selinux enable on this server. 

I have the ports set as default (80, 443). The process based on netstat and ps is not running, but apache for some reason thinks it is.

---

### Post by AquaQuieta on 2010-03-24
I ran into this problem today...at first I thought it was because of the upgrade I just did...but this post helped me figure it out, and I figure I'd share my experience...

I did not have the problem of duplicate "Listen" entries in ports.conf (or duplicate ports.conf files), so I was a little perplexed by the posts which were "SOLVED"

The problem for me stems from the fact that I am using an SSL certificate
with a passphrase. Whenever I restart apache, I am prompted for this password. I assume this happens when you reboot the machine as well...but I am accessing this remotely, so if it did prompt for this password, I didn't get a chance to enter it.

So when I attempt to stop the apache service, it would claim that apache is not running. When I tried to start it, I would get the "Address already in use" error.

I notice that user above did not include "sudo" in front of his lsof command. If I run that command without sudo privileges, I get nothing, but running with sudo shows that apache is running. I made a note of the PID and killed the process. Once I did that, I was able to start the apache service again (and I was prompted for my SSL password). Like the poster above said, "killall -9 apache2" should do the trick too :-)
 
So for me, I think it was the apache init script waiting for user input that was never going to come. Since the init script hadn't actually finished starting the service, the init script couldn't shut down the service, and there were no open connections for netstat to show. 

Just my two cents...hope it helps somebody.

---


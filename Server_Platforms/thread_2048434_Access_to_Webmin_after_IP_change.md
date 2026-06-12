---
title: "Access to Webmin after IP change"
date: 2012-08-26
forum: Server Platforms
---

### Post by bmwisme on 2012-08-26
Sorry for the idiot question but just started with Linux (ubuntu server 12.04).  I have vSphere 5 host running a couple Windows 08 servers and now ubuntu server.  Plan is to use ubuntu for a simple web webserver (save $$$)

I just finished a ubuntu LAMP server install and followed with a Webmin install. All went as expected and I was able to connect to Webmin.  I then changed to a static IP using Wedmin but now cannot connect to the Webmin website using the new IP.  
I did restart the server and checked the IP - was changed to my static.

Any ideas, what am I missing?

---

### Post by tomski on 2012-08-26
check the ip you provided in /etc/webmin/miniserv.conf for webmin to listen on or if you didn't edit that file then use [https://localhost:10000](https://localhost:10000) on the ubuntu box.

If you want webmin to listen on the static ip you will need to edit /etc/webmin/miniserv.conf & change localhost to the static ip

default config (for ARCHLINUX) is here:
[https://gist.github.com/3482861](https://gist.github.com/3482861)

at the bottom you will see:
allow=127.0.0.1

this is what you need to check/edit

---

### Post by bmwisme on 2012-08-26
Thanks for the suggestions tomski but I added the "allow" for the static IP of the ubuntu server but still cannot access.  I also tried the IP of my workstation.

Being being a green-horn I am not sure how to troubleshoot - that is why I have stayed away from Linux.  As I said, I had no problem accessing Webmin from my workstation after the initial install and all I did was change the IP.  DHCP had assigned 10.16.10.170, I changed to 10.16.10.90 - simple change.

Would re-installing get me back to where I was?

---

### Post by lisati on 2012-08-27
Sometimes restarting a service does magic. The following should do the trick:
```
sudo service restart webmin
```

---


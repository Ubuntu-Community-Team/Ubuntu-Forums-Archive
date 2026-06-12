---
title: "Apache2"
date: 2011-04-20
forum: Server Platforms
---

### Post by captnjohne on 2011-04-20
This may belong in an apache forum however perhaps there is a quick fix to my problem that some one can help me with .

In a nutshell I have been testing the waters running apache to do a simple web page from home.  I had a spare laptop that I'm using before I upgrade to something better.  Basically I had everything running over wireless.  Today I went and bought a cat-6 cable.  I"m able to connect to the internet so everything on that end is good to go.  ifconfig gave me my local address on the router which I used for port forwarding and then restarted the router.  I can no longer get on my website from another source.  When I reconnect to my wireless and switch the port forwarding back the site works again. 

Any suggestions?

---

### Post by ttshivers on 2011-04-20
Does it work when you access your site inside your network when the port forwarding is on.  Also, some ISPs may block port 80, which is the default port for apache web servers. You can specify a port in the url bar by typing something like this: [http://www.websitename:8080/index.html](http://www.websitename:8080/index.html). Replace 8080 with your port number. This might help you with changing the default port [http://httpd.apache.org/docs/2.0/bind.html](http://httpd.apache.org/docs/2.0/bind.html)

---

### Post by captnjohne on 2011-04-20
No it's not working locally when I'm "plugged in" however when I go back  to wireless it works perfectly both locally and externally.   Fortunately port 80 is open by my ISP too.  I'm going to keep messing  with it.  I'm sure it's something simple that I'm over looking.

---

### Post by ttshivers on 2011-04-20
Are you changing your ip on your router for your computer for port forwarding when you plug in.  Your internal ip address will be different when you plug in vs when you are wireless

---

### Post by captnjohne on 2011-04-20
Yes I am.  On wireless it's 192.168.1.6 wired-- xxx.xxx.x.9  I've reset the router several times and also apache to no avail.  Confirmed the address via ifconfig

---

### Post by ttshivers on 2011-04-20
Do you have a firewall running?  Check to see if you have firewall configuration (System -> Administration -> Firewall configuration)

---

### Post by ttshivers on 2011-04-20
Also, check your apache logs to see if there are any errors.  The error log is at: /var/log/apache2/error.log.  Just type ```
sudo /var/log/apache2/error.log
``` to see it

---

### Post by captnjohne on 2011-04-20
nothing unusual in the log file, other than can't find a "favicon" that I have linked in a test page.  I disabled the firewall (something I didn't even think about) and it now works on the local network, just not externally.

---

### Post by volkswagner on 2011-04-20
Do you have any ip address binding in your apache virtual host files, or /etc/hosts?

Check the output of the following both wired and wireless to see if there is a difference.

```
route
```

---

### Post by fenderr357 on 2011-04-20
It should be working.. Maybe in the beginning you set your router to forward for IP x.x.x.9(wireless), and not x.x.x.6(wired). 

Since it is working internally, It seems the problem is something with the router.

---

### Post by captnjohne on 2011-04-20
@ volkswagner-- that was it!!!  I followed a tutorial on installing bind which recommended uninstalling network manager and steps to reconfigure the host file.  After doing that it works flawlessly... 

I want to say thank you to both you and [ttshivers]("http://ubuntuforums.org/member.php?u=1053561") for your help/suggestions.  I'm new to all of this and you've been a great help.

---

### Post by captnjohne on 2011-04-20
.

---

### Post by d3v1150m471c on 2011-04-20
> **captnjohne said:**
> Yes I am.  On wireless it's 192.168.1.6 wired-- xxx.xxx.x.9  I've reset the router several times and also apache to no avail.  Confirmed the address via ifconfig

If you're plugging it in directly, you're no longer on the network, judging by the fact your ethernet ip is no longer a class C address. Thus, you'd have to queue up apache by the ip address while you're plugged in. On a network, ie your wireless, going to 192.168.1.6, should pull up your homepage in a browser. Plug your ethernet cable into your router and not directly through the modem and see if it works like it does on wireless. technically it should.

---


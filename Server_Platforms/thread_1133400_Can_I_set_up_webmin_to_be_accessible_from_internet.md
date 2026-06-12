---
title: "Can I set up webmin to be accessible from internet?"
date: 2009-04-22
forum: Server Platforms
---

### Post by cmwslw on 2009-04-22
The title pretty much says it all. I can use webmin through LAN, but I would like to be able to access it from any computer. (password protected of course)!

-Cory Walker

---

### Post by Yashiro on 2009-04-22
Don't.

If you must run webmin, access the server using SSH and run it over that.

---

### Post by juancarlospaco on 2009-04-22
Yes you can.

---

### Post by kustomjs on 2009-04-22
if you trust it yes you can do it all you have to do is do port forwarding on your router. like say ip address 254.65.142.55:10000  just make sure you port 10000 in your router or whatever you using.

---

### Post by spynappels on 2009-04-23
> **Yashiro said:**
> Don't.

If you must run webmin, access the server using SSH and run it over that.

Just out of interest, how would you do that? I'm a little hazy on running other programs or services through SSH, am ok with using CLI on SSH.

---

### Post by cmwslw on 2009-04-23
> **kustomjs said:**
> if you trust it yes you can do it all you have to do is do port forwarding on your router. like say ip address 254.65.142.55:10000  just make sure you port 10000 in your router or whatever you using.

Thank, you. That's what I needed. I will only forward the port when  I need remote access. Any advice on how to make it more secure when I forward the port, or is the password sufficient? Also, is webmin served by apache? I imagine it's not since there would be problems restarting and the port would be 80.

In addition, can I ssh when I'm not connected through a LAN?

---

### Post by spynappels on 2009-04-23
You can make the setup a little more secure by using a non standard port picked at random such as 52482 and forwarding that to port 10000 on the local server. This can be set up in your router normally and will avoid having a "standard Webmin" port number showing as open if you are scanned.

Dont forget to use the https:// when you access it from the outside world, using non standard ports can confuse your browser.

PS It does use Apache, it sets up a virtual server using https on port 10000. You can have more than one website being served by Apache at any one time on different ports or using different domains.

---

### Post by bigbearomaha on 2009-04-23
[LEFT]changing the ports removes it from view of the script kiddies, primarily. it's akin to keeping the front door shut and using the side or back door instead. 

Almost anytime you are accessing a server for configuration or admin purposes over the web, you should definitely use ssh and then forward the port to your local machine.  You can also arrange to use ssl keys instead of password to access Webmin.

there are a few steps you can take to access Webmin over the web if you find it necessary.

Big Bear
[/LEFT]

---

### Post by spynappels on 2009-04-23
That's why I said a "Little" more secure......

Could you give me some info on using a SSH tunnel? That would appear to be the safest option, as you would not need to allow remote config on your router to open ports when required? port 22 could be disguised, I presume...

---

### Post by bigbearomaha on 2009-04-23
[http://pclosbe.org/mwiki/index.php?title=The_SSH_VPN#Setting_up_the_connection](http://pclosbe.org/mwiki/index.php?title=The_SSH_VPN#Setting_up_the_connection)

That article may be helpful in setting up an ssh tunnel to webmin.

Big Bear

---

### Post by kustomjs on 2009-04-23
well a other thing you can do is you dont have to do port forwarding just setup vpn if you want to do remote login if your not at home. then once your connected to your network then you can use putty to access your internet servers and stuff.

---


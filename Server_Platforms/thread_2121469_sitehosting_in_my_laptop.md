---
title: "sitehosting in my laptop"
date: 2013-03-02
forum: Server Platforms
---

### Post by Rakeshvijayan on 2013-03-02
Hi friends 


I tried to host my website in own my computer  (only for testing )by the  help of god and people like you ,help me to achieve this one ......I  used virtual hosting on apache but when when I give my website name with  out www it will shown my www folder on my laptop , is this cause any  vulnerable of my Laptop ?if it is  vulnerable ? How to know or where I  can see hackers trying to access my laptop .... Hope some one will ping  me soon Thanks

---

### Post by Mr. Shannon on 2013-03-02
Unless you have done something special to map a name to your IP address you need to access your site with [http://localhost](http://localhost) from the same machine or [http://your-ip-address](http://your-ip-address) in your browser.

Also, if you are going to install server software on your laptop you should probably enable a firewall.  The easiest way is:
```
sudo ufw enable
```
that will deny all incoming traffic, which should be fine unless you ssh into your laptop or actually want to host your site.  In that case read the documentation at [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) for information on how to open those ports.

---

### Post by Rakeshvijayan on 2013-03-02
> **Mr. Shannon said:**
> Unless you have done something special to map a name to your IP address you need to access your site with [http://localhost](http://localhost) from the same machine or [http://your-ip-address](http://your-ip-address) in your browser.


my testing web site is [www.myveena.tk]("http://www.myveen.tk") its works popper for me another site is main website if I give name eg: abc.tk it shows my www on /var/www how to privent this .if I enable UFW is this cause for any problem for torrent  DELUGE any other application that I am currently using

---


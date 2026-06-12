---
title: "help getting started"
date: 2009-08-02
forum: Server Platforms
---

### Post by rhythmiccycle on 2009-08-02
i used Ubuntu desktop, but i never ran a server before.

my goal is to host a website, that can run php, mysql, and flash (maybe java later on).

i've put up a site at awardspace.com, but i want to host my own site.

I've installed xampp on my computer before, and used the localhost website. I thought when i installed ubuntu sever it would work like that, but be a actual online site, not just the local host.



I installed it with DSN and LAMP.

now when i start my computer it is just a prompt, there is no GUI.

I've never hosted a website before, i would my computer to work like a normal desktop GUI, but also host the website, 

please help.

---

### Post by LepeKaname on 2009-08-02
Hi rhythmiccycle,

Did you installed Ubuntu Server? If so, then you will not have GUI. If you want to have GUI and host your websites its just fine, no problem, but you will need Ubuntu Desktop instead. I guess you just need to setup your domain DNS to your external IP. Do you know how to do it? 
Then, I would suggest to use ufw firewall, add port 80 (and any other port you may need) and you will be ready. You don't need to enable MySQL port as it will be running locally.

If you have further questions please feel free.

---

### Post by rhythmiccycle on 2009-08-02
thanks for your help, LepeKaname,

ok, so you are saying i can host a website using ubuntu desktop. I didn't know that.

so after I install ubuntu desktop, how do I: 
>  setup your domain DNS to your external IP. 

i'm assuming after i install ubuntu desktop, i need to install DNS and LAMP, is that correct?

---

### Post by wstout on 2009-08-02
If you already have a server install that is what you need. Everything will be there. If you want a GUI you can install one by```
sudo apt-get install ubuntu-desktop
``` I would actually suggest some middle ground by using webmin. It allows you to manage your server through a web interface. I am not a pro but it really helps especially setting up samba shares and lots of other stuff. You can check webmin out here [http://www.webmin.com/](http://www.webmin.com/)

---

### Post by wstout on 2009-08-02
here is a good link on installing webmin... you will need to correct the version to get the newest version. [http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html]("http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html")

---

### Post by LepeKaname on 2009-08-02
Yes. Follow these steps:

1) Install LAMP. 

2) try it in "http://localhost", and ensure everything works fine (mysql, php, etc.).

3) add to your /etc/hosts your test domain, for example:
```
192.168.0.1    mytestdomain.com www.mytestdomain.com
```

4) add your domain to your virtual hosts in /etc/apache2/sites-enabled/000-default:

```
<VirtualHost *>
    ServerName  mytestdomain.com
    ServerAlias www.mytestdomain.com
    DocumentRoot /var/www/test
</VirtualHost>
```

5) try [http://www.mytestdomain.com](http://www.mytestdomain.com).
   if it doesn't work, check again your virtual host settings.

6) At your domain registrar I suggest to use "Host Records" setting:
```
Host Name       Record Type   Address
www             A (Address)   200.100.200.100 [COLOR="DimGray"](your external IP)[/COLOR]
@               A (Address)   200.100.200.100
*               A (Address)   200.100.200.100

```
Note: These settings may differ from your registrar.

7) IMPORTANT: Remove from your /etc/hosts the line we added in 3)

8 ) Wait (sometimes changes to your registrar may take some time)

9) test: [http://www.mytestdomain.com](http://www.mytestdomain.com) and it should work.

If it doesn't work run:

**sudo nmap localhost**
(if you don't have it, install it: **sudo aptitude install nmap**)

and check port 80 is open. Also you may try form an external computer.

If its not open, then add to your firewall: (**sudo ufw allow 80**) and enabled it: (**sudo ufw enable**)

If you have a problem, post it here.

---

### Post by rhythmiccycle on 2009-08-03
thanks for your help.

everything seems to be working.

the other questions i have will be posted on other threads

---


---
title: "FTP, Web, Email Server Setup Guidance"
date: 2008-09-26
forum: Server Platforms
---

### Post by raihansdg on 2008-09-26
Hi everyone, I am new to linux specially Ubuntu. I used Fedora and Debian before but for some reason I really like Ubuntu. 

Couple of my friends had bought some domain names from godaddy and they are not using them. They asked me if I could host their web site, give them email addresses (like [email]john@site1.com[/email]) and FTP so that they can transfer files. 

**REQUIREMENTS**
There are 3 different sites lets say site1.com site2.com and site3.com.

1. They need to access(change, update their website) their sites remotely.
2. Sperate emails (as I mentioned before)
3. Separate FTP for file transfer.

**THIS IS WHAT I DID:**
1. I have a static IP
2. I installed LAMP
3. Installed PHPMYADMIN

**THIS IS WHERE I AM STUCK**
1. Aache2 works fine, when I type in localhost in mozilla it says "it works". What I cannot do is that I cannot resolve the IP address to site1, site2 and site3 domain names respectively. 

I followed this link tried to do setup site 1 but no luck: [http://www.techotopia.com/index.php/Configuring_an_Ubuntu_Linux_Based_Web_Server](http://www.techotopia.com/index.php/Configuring_an_Ubuntu_Linux_Based_Web_Server)

The connection times out.

2. What software(possibly free) will I use so that my friends can connect to the server and update/change their sites. Also, how can I give them an allocated space like site1 will have 5gb, site 2 will have 2gb etc...

3. Email: I have no idea how to setup email server some links and guidance will be highly appreciated!

Again, free email server software is preferred.

Thank You please help me dont tell me to go to
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

---

### Post by volkswagner on 2008-09-26
The link you provided includes instructions to install ISPconfig.  
[http://www.ispconfig.org/]("http://www.ispconfig.org/")
Did you install it.  I have limited experience with it.  I am sure that this will allow you to act a s the provider and your friends can have accounts.  You will be the reseller.  

I am not sure about hosting several FQD names.  I can only guess you would need to set up virtual hosts for each site, in Apache2.  You would also have to tell godaddy to direct each site to your static ip.  You may need to run your own DNS and tell godaddy where the DNS is (your ip).

Did you follow the Perfect server instructions?

[QUOTE-From Perfect Server]POP3/IMAP: I will use Maildir format and therefore install Courier-POP3/Courier-IMAP[/QUOTE]
 
I had a heck of a time configuring the above.  The instructions kind of leave ya hanging.

---

### Post by raihansdg on 2008-09-26
volkswagner, thank you for the insight, I had already configured godaddy to direct all the domain names to my static IP then I followed  [http://www.techotopia.com/index.php/...sed_Web_Server](http://www.techotopia.com/index.php/...sed_Web_Server) but still it does not work. When I type in site1.com in mozilla the connection times out.
If i cannot successfully host one website I cannot even think of virtual host. I was also reading the docs of apache for Virtual Host.

---

### Post by devonps on 2008-09-26
> **volkswagner said:**
> ...you would need to set up virtual hosts for each site, in Apache2.

Have you done as the poster mentioned?

Are you using a router infront of your webserver or do you connect directly to the internet?

---

### Post by raihansdg on 2008-09-26
I connect directly to the internet there is no router! I did not setup virtual hosts yet, this is because I would like to host site1.com first. If that works I will be able to figure out virtual host.

---

### Post by volkswagner on 2008-09-26
> **raihansdg said:**
> I connect directly to the internet there is no router! I did not setup virtual hosts yet, this is because I would like to host site1.com first. If that works I will be able to figure out virtual host.
Daring, no router.  Can you access via local host or internal ip?

---

### Post by raihansdg on 2008-09-26
I can access via localhost but internal ip dont work. If i type in the ip in mozilla it times out...
DO i need to setup BIND9 ?

---

### Post by volkswagner on 2008-09-26
You may be able to enter you ip address in /etc/hosts

```
sudo nano /etc/hosts
```

Here is a portion of mine.  I am behind a firewall/router so I use internal addresses.  Perhaps you need to enter your ISP provided ip address along with the loopback.

127.0.0.1       localhost localhost.localdomain
192.168.1.110   [www.volkswagner.com](www.volkswagner.com)
192.168.1.110   ServerName.volkswagner.com     ServerName

---

### Post by raihansdg on 2008-09-28
Thanks that seems to be working!!!

---


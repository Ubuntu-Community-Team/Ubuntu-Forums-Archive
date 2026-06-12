---
title: "What To Install For A Simple Home Server?"
date: 2009-09-11
forum: Server Platforms
---

### Post by umechanism on 2009-09-11
I'm running Ubuntu 8.10 and wish to setup a simple home server that I can use to move files around and what not.  I'm not interested in sharing content to the web (yet).  I've installed LAMP but I just can't seem to figure out the configurations.  I looked at Ubuntu Home Server which looks simple to config but I'm not sure if I can install it over my existing Ubuntu installation.  I mean, is Ubuntu Home Server a separate operating system or is it a program that I can install in Ubuntu 8.10.

My end goal is to have a simple server.

Tks!

---

### Post by wojox on 2009-09-11
Ubuntu Server is a different OS. There is no GUI. What you have done so far is installed LAMP on Ubuntu Desktop, so what are you having trouble configuring?

---

### Post by cosine352 on 2009-09-11
to make it a server you just need to install some applications. For example in case of SSH server 
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

---

### Post by gordintoronto on 2009-09-11
> **umechanism said:**
> 

My end goal is to have a simple server.

Tks!

A file server, or some other kind?

The simplest file server is just to set up a Share, and you can do that on Ubuntu or Windows, wherever you have spare hard drive space -- without needing server software.

LAMP lets you host complex web sites.  Just installing Apache would let you host simple web sites, such as displaying information.

---

### Post by umechanism on 2009-09-11
> **wojox said:**
> Ubuntu Server is a different OS. There is no GUI. What you have done so far is installed LAMP on Ubuntu Desktop, so what are you having trouble configuring?

Well, I'm running Apache 2.2 and it is up and running because I can type "http://localhost" and I see the page, "It Works!".  However, I can't reach the server from any other computer on my LAN.  The static IP address of the machine on which Apache is installed is 192.168.2.102.  I used other computers on my LAN to try to reach that IP but I can't.  The browser says it is connecting but it never does.

The machine that I have installed Apache on is my old reliable machine that I do a lot of testing with.  This machine has OpenSSH installed on it and I've used it in the past as a method of moving files from my office to home via the Internet.  Now I just want to lean a bit about Apache and I want to start by setting up the server to work on my LAN.  After I figure that out, I'll open it up to the WWW with a few web pages but, for now, everything is on the LAN.

Thanks!

---

### Post by umechanism on 2009-09-11
> **gordintoronto said:**
> A file server, or some other kind?

The simplest file server is just to set up a Share, and you can do that on Ubuntu or Windows, wherever you have spare hard drive space -- without needing server software.

LAMP lets you host complex web sites.  Just installing Apache would let you host simple web sites, such as displaying information.

Yeah, I've done that before.  I have shares between Windows and Linux machines on my LAN now but now I want to learn about Apache and try to share files through it.  Just for fun.  I just need to figure out the config.

---

### Post by umechanism on 2009-09-12
I guess a more simple way to ask is, "What settings are needed so that my machine, which is running Apache2, can be reached from any machine on my LAN?"

I'm reading [this]("https://help.ubuntu.com/9.04/serverguide/C/httpd.html") but I'm still having trouble.

All help is appreciated.

tks!

---

### Post by Josh1 on 2009-09-12
Hello.

I'm thinking about writing up a tutorial for Ubuntu HomeServers, as I setup Ubuntu Server as my Gateway Machine (INTERNET <--> MODEM <--> GATEWAY <--> SWITCH <--> PCs), and have found it to be perfect for my needs.

Basically I'm a Web Developer/Software developer and wanted the following features:
[LIST]
[*]Webserver - Apache2/MySQL5/PHP5
[*]NAT/Internet Connection Sharing (Replace Router) - Squid Proxy Server
[*]File Sharing - SAMBA
[*]Print Server - Haven't added a printer yet as we have one in the study.
[*]Firewall
[/LIST]

I installed Ubuntu Desktop over server as I like using VNC with windows spread out to monitor everything. Is that what you wanted to know about? I can write something up if you want ASAP.

---

### Post by umechanism on 2009-09-12
Yes.  That would help a lot as long as it is in Noob language.:D

In the meantime, I'm still struggling trying to connect to the server.  I have the server machine sitting right next to the client machine at my desk.  The server is running and its static ip IP address is 192.168.2.102.  From the client machine, I enter that IP address into my browser but it does not connect to the server.  I expected to see the default web page (the one in Apache that reads, "It Works!") but I never get a connection.

Do I need to setup Apache to accept LAN side connections or something?  I've not really changed the default configuration.  :confused:

---

### Post by cosine352 on 2009-09-12
do you have any firewall running ?

---

### Post by umechanism on 2009-09-12
> **cosine352 said:**
> do you have any firewall running ?

Well, I do use Dansguardian on the computer where the server is installed and it uses "TinyProxy" but, to my knowledge, I'm not running any other firewall than the default one that comes with Ubuntu.

Is there a way to check to see if a Firewall is enabled?

---

### Post by abaden on 2009-09-12
Try running
```
sudo /etc/init.d/ufw stop
``` to stop the "uncomplicated" firewall that is bundled with every ubuntu distribution. 

Can you ping this machine from your LAN computer? Can you ping your LAN computer from this machine? Double check to make sure that all your networking settings are correct. You could also go into the apache2 vhost config file (/etc/apache2/sites-enabled/000-default) and make sure you are listening on the correct IP. For example...
```

NameVirtualHost 10.0.0.1 
<VirtualHost 10.0.0.1>

```


HTH,
Alex

---

### Post by umechanism on 2009-09-12
I stopped the firewall as directed then opened Firefox and typed "http://192.168.2.102:80" but it would not connect.  Am I typing the correct address?  I've not configured any IP address in Apache2.  Could that be the problem?

---

### Post by confusedstingray on 2009-09-12
it you can ping the machine you should be able to see it. For a test add the ip of the apache machine to the host file of another on your land and see if you can see it.
Also tiny proxy might be redirecting you requests to the internet. 
this can be set in the tiny proxy setup to all internal request to the apache machine to stay internal and all other request to go to the internet. i will check my setup and post it. if you need any more help let me know.
I have what your trying to setup running 9 machines and 2 servers all internal all sharing video and files and music

---

### Post by abaden on 2009-09-12
> **umechanism said:**
> I stopped the firewall as directed then opened Firefox and typed "http://192.168.2.102:80" but it would not connect.  Am I typing the correct address?  I've not configured any IP address in Apache2.  Could that be the problem?

What does your default virtual host (/etc/apache2/sites-enabled/000-default) look like?


Alex

---

### Post by umechanism on 2009-09-13
> **abaden said:**
> Try running
```
sudo /etc/init.d/ufw stop
``` to stop the "uncomplicated" firewall that is bundled with every ubuntu distribution. 

Can you ping this machine from your LAN computer? 
[/code]


HTH,
Alex

Ok, I stopped Tinyproxy on the host and tried to ping the host from a computer on my LAN.  No success.  I then stopped Dansguardian and retried the ping.  Still no success.  I then stopped the firewall as suggested above and was able to ping the server.  I turned Tinyproxy and Dansguardian back on and pinged it again with success!  
  I then typed 192.168.2.102 in my browser and saw the default apache2 page, "It Works!" which means I can now connect to the server.

So I guess my problem is firewall related or at least "configuration" related.  Do I modify my firewall or do I change some setting in Apache?

---

### Post by cosine352 on 2009-09-13
could you please post the output of
> ifconfig | grep 192.

---

### Post by umechanism on 2009-09-13
Here's the output:
```
 inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0

```

---

### Post by cosine352 on 2009-09-13
you can istall 'firestarter'. Firestarter can modify the iptables in GUI way. 

> sudo apt-get install firestarter

then open up firestarter

> sudo firestarter

I guess for the first time it will promt a welcome massage. click 'forward' and chose the detected device for wireless or wired (eathernet) connection. now click 'forward' untill you reach the last step. click 'save'. 
Now go to 'policy' tab and and chose 'inbound traffic policy' from the drop down box. at the bottom right click and add the service you want to allow.

---

### Post by cariboo on 2009-09-13
Firestarter is no longer the recommended tool to set up firwall rules, as it is no longer maintained, gufw is the preffered tool now.

---

### Post by umechanism on 2009-09-14
Thanks for the tips.  gufw is installed and working.  I can now connect as needed.  Thanks!

---

### Post by umechanism on 2009-09-19
> **Josh1 said:**
> Hello.

I'm thinking about writing up a tutorial for Ubuntu HomeServers, as I setup Ubuntu Server as my Gateway Machine (INTERNET <--> MODEM <--> GATEWAY <--> SWITCH <--> PCs), and have found it to be perfect for my needs.

Basically I'm a Web Developer/Software developer and wanted the following features:
[LIST]
[*]Webserver - Apache2/MySQL5/PHP5
[*]NAT/Internet Connection Sharing (Replace Router) - Squid Proxy Server
[*]File Sharing - SAMBA
[*]Print Server - Haven't added a printer yet as we have one in the study.
[*]Firewall
[/LIST]

I installed Ubuntu Desktop over server as I like using VNC with windows spread out to monitor everything. Is that what you wanted to know about? I can write something up if you want ASAP.

I just thought I had it figured out.  I can connect on the LAN side but not via the internet.  Got that tutorial ready?  I'd love read it.

Thanks!

---

### Post by AlexanderDGreat on 2009-09-20
Yeah, pls. make a HOWTO! I would love to learn and pick up your brain. =)

Hey in your setup: 

Ubuntu Server as my Gateway Machine (INTERNET <--> MODEM <--> GATEWAY <--> SWITCH <--> PC

Can you also show us using 2 NIC's?

Because when there's no work in the office during weekends, I don't want to TURN ON the server just to have Internet access.

Many thanks! =)

---


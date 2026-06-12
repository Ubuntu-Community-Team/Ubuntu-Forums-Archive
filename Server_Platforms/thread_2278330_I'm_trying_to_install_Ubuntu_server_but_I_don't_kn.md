---
title: "I'm trying to install Ubuntu server but I don't know what to choose?"
date: 2015-05-15
forum: Server Platforms
---

### Post by remmas-sido on 2015-05-15
Hello guys 
I'm trying to install Ubuntu Server edition 12.04, everything runs fine until I came to software selection which gives a list of options :
Open SSH server, DNS server, LAMP server, Mail server, PostgreSQL, Print server, Samba file server, Tomcat Java server, Virtual Machine host, Manual package selection.
My intention of installing the Server edition is to use it as a seed-box later, so what's the most suitable option for me? and is there an option with it you can hit two birds with one stone what I means is to benefit from multiple options and not just a single option?

---

### Post by Tadaen_Sylvermane on 2015-05-15
I wouldn't select any of it and install stuff yourself later. That part installs packages but I always have had to manually install them afterwards anyway. I don't think it works to be honest.

---

### Post by Kenneth_Benson on 2015-05-15
What do you mean by seed-box?
-->curious<--

---

### Post by remmas-sido on 2015-05-15
> **Kenneth_Benson said:**
> What do you mean by seed-box?
-->curious<--

that thing that download torrents for you in a very high speed.

---

### Post by remmas-sido on 2015-05-15
Hello guys 

I know that this question may sound completely stupid, but I need to clear my doubts, can I use the Desktop edition for server purposes as well as I can use the Server edition for desktop purposes?

---

### Post by sudodus on 2015-05-15
Yes, you can. For example, Install ***openssh-server*** into your main computer and use it as a file server for your local network. But if you intend to have a server for the internet, I think that you should start with Ubuntu Server. That will be more efficient and safer too.

---

### Post by remmas-sido on 2015-05-15
I'm thinking of use it as a seed-box which means torrent server, is it okay?

---

### Post by sudodus on 2015-05-15
I think so. Many people do it. But you should realize that there is a security risk. It might be a good idea to have a separate computer for this service (and not use the same computer as your main 'production system').

---

### Post by QIII on 2015-05-15
Merged and moved to Server Platforms.

---

### Post by remmas-sido on 2015-05-15
> **sudodus said:**
> I think so. Many people do it. But you should realize that there is a security risk. It might be a good idea to have a separate computer for this service (and not use the same computer as your main 'production system').

For example? I'm talking about the security risks.

---

### Post by darkod on 2015-05-15
For torrents during the installation select only OpenSSH server. That will allow you remote administration especially if the machine will be running headless (no monitor, no keyboard connected all the time). You don't need any of those roles for torrents. You can add any role/package you want later too.

For torrents install transmission and transmission-daemon packages.

Depending if and how you want to access the downloaded files over your home network, you might use Samba, in which case you can also select the Samba server role during installation, or simply add it later.

Also, is there a specific reason you want to install 12.04 LTS? Why not the latest 14.04 LTS? For servers you would usually stick to the latest LTS version, not the latest ubuntu version.

The security risks mainly depend on whether you will connect this machine directly to the internet with a public IP (unlikely for home setup), or it will have a private IP in your home network behind your home router. If it's behind your home router the router firewall is the first line of defense from outside attacks, and usually most routers can do that job fine.

---

### Post by remmas-sido on 2015-05-15
> **darkod said:**
> For torrents during the installation select only OpenSSH server. That will allow you remote administration especially if the machine will be running headless (no monitor, no keyboard connected all the time). You don't need any of those roles for torrents. You can add any role/package you want later too.

For torrents install transmission and transmission-daemon packages.

Depending if and how you want to access the downloaded files over your home network, you might use Samba, in which case you can also select the Samba server role during installation, or simply add it later.

Also, is there a specific reason you want to install 12.04 LTS? Why not the latest 14.04 LTS? For servers you would usually stick to the latest LTS version, not the latest ubuntu version.

The security risks mainly depend on whether you will connect this machine directly to the internet with a public IP (unlikely for home setup), or it will have a private IP in your home network behind your home router. If it's behind your home router the router firewall is the first line of defense from outside attacks, and usually most routers can do that job fine.

So what you're saying that public wifi such as universities and school are the real threat and the home network?

---

### Post by darkod on 2015-05-15
Are you asking about your particular case or we are starting to turn this thread into a general security discussion? There is plenty security info on google I guess.

As for university or shool public wifi, I hope you are not planning to run a torrent box in such a network. Not from security perspective, but because that institution might have something to say about it. And of course a public wifi where you have bunch of other people connected together with you can not be considered secure.

Your home LAN is secure behind your router, in general. Just make sure you do not open or forward any ports that are not needed. Just forward the transmission port to the ubuntu server private IP and that should be enough.

---

### Post by remmas-sido on 2015-05-16
> **darkod said:**
> Are you asking about your particular case or we are starting to turn this thread into a general security discussion? There is plenty security info on google I guess.

As for university or shool public wifi, I hope you are not planning to run a torrent box in such a network. Not from security perspective, but because that institution might have something to say about it. And of course a public wifi where you have bunch of other people connected together with you can not be considered secure.

Your home LAN is secure behind your router, in general. Just make sure you do not open or forward any ports that are not needed. Just forward the transmission port to the ubuntu server private IP and that should be enough.
One last question, can I install Open SSH server, Transmission daemon and Samba in Ubuntu desktop which means can I install the torrent server in the desktop edition without the need to install the server edition, because the server edition is all command line and that scares me. I'm afraid I might end up screwing up everything.

---

### Post by darkod on 2015-05-16
Yes you can. Almost all packages and roles without exception can work on the Desktop version too. The recommendation to use Server is because that version is optimized for using maximum of the resources (it does not have the GUI or other similar parts taking memory etc). Also the Server version is more difficult to attack, especially for servers directly on the internet. If the machine is inside your home LAN the attack possibility is already reduced as we discussed earlier. So using the Desktop is not too risky.

Also you have to consider whether you actually want to learn more about Ubuntu Server or not. Using the server version and only command line will help you learn because you will have to learn how to do things on the command line. Having the GUI will prevent that from happening.

As always, the choice is absolutely yours. If you prefer the Desktop version, use that one...

---

### Post by remmas-sido on 2015-05-16
> **darkod said:**
> Yes you can. Almost all packages and roles without exception can work on the Desktop version too. The recommendation to use Server is because that version is optimized for using maximum of the resources (it does not have the GUI or other similar parts taking memory etc). Also the Server version is more difficult to attack, especially for servers directly on the internet. If the machine is inside your home LAN the attack possibility is already reduced as we discussed earlier. So using the Desktop is not too risky.

Also you have to consider whether you actually want to learn more about Ubuntu Server or not. Using the server version and only command line will help you learn because you will have to learn how to do things on the command line. Having the GUI will prevent that from happening.

As always, the choice is absolutely yours. If you prefer the Desktop version, use that one...

Thank you for answering, maybe with time I will learn how to do server stuffs, but for the mean time I'm going to go with the desktop, because it's easier for me.

---

### Post by LHammonds on 2015-05-16
I have a how-to thread for installing and configuring a basic Ubuntu Server for production use.  I have other tutorials for making more-specific servers such as a database or FTP server.

[ How to Install and Configure an Ubuntu Server 14.04.2 LTS ]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=210")

Read through that and you might learn a few things about how to do various tasks.  I commonly refer back to it for doing things like increasing volume/file system space and so on.

LHammonds

---


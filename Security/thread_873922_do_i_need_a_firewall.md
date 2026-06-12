---
title: "do i need a firewall ?"
date: 2008-07-29
forum: Security
---

### Post by smooth3006 on 2008-07-29
im not behind a router so i take it i will need some sort of firewall to run on ubuntu ? can you recommend a good one that is easy to use ? im new to linux still.

---

### Post by Vorian Grey on 2008-07-29
I am paranoid enough to say that I think everyone needs a firewall. The internet is a dangerous place. 

Check out UFW (Uncomplicated Firewall) found in Ubuntu. Easy to configure and easy to use. 

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by smooth3006 on 2008-07-29
> **Vorian Grey said:**
> I am paranoid enough to say that I think everyone needs a firewall. The internet is a dangerous place. 

Check out UFW (Uncomplicated Firewall) found in Ubuntu. Easy to configure and easy to use. 

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

according to my system it says it's already installed. how do i configure it ?

---

### Post by ajgreeny on 2008-07-29
Forgetting paranoia for a moment, unless you are running any server environments, eg a mail server or a server with a website on it, you don't really need to do anything other than use the default that is installed in ubuntu, iptables, which is actually the firewall.  UFW is not a firewall, but merely the means by which you can if needed configure your firewall (iptables).

When I first started running ubuntu with Hoary Hedgehog 3 years ago, I always had bith firestarter and clamav, the virus checker, installed and ran them both.  Now I don't have either and see no reason to install them on my desktop only machine.  If you want to check your computer current situation go [here]("http://www.grc.com/intro.htm") for a port scan.  Hopefully you will find that it passes and is, in effect, invisible on the net.

---

### Post by kevdog on 2008-07-29
Only if you plan on running servers do you need a firewall.  Is this in your future?

---

### Post by tuxxy on 2008-07-29
You can install **Firestarter** to configure it

---

### Post by smooth3006 on 2008-07-29
> **tuxxy said:**
> You can install **Firestarter** to configure it

so firestarter will allow me to configure the firewall ?

---

### Post by tuxxy on 2008-07-29
[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

---

### Post by brian_p on 2008-07-29
> **smooth3006 said:**
> im not behind a router so i take it i will need some sort of firewall to run on ubuntu ? 

Heavens above, what gave you that idea? With a default install there is nothing to connect to on your machine. You are unreachable from the internet.

---

### Post by hyper_ch on 2008-07-29
generally you don't need a firewall or rather you don't need to alter its default rules.

---

### Post by tuxxy on 2008-07-29
Unless you plan on running some services on your machine

---

### Post by brian_p on 2008-07-29
> **tuxxy said:**
> Unless you plan on running some services on your machine

Exim4 is operating quite happily and very securely on this machine without having the slightest need for a firewall.

---

### Post by mdsharp24 on 2008-07-30
sudo ufw default deny
sudo ufw enable

If you need port 80 open:

sudo ufw allow 80

To remove:

sudo ufw remove allow 80

---

### Post by linux_tech on 2008-07-30
With the Internet its good to be redundant and have layered protection
both hardware and software.  Besides that its good to get to know firewalls
and ports management.   Firestarter is a good one to start with because its already included.  Just start synaptic package manager and it should already be in the list.  This links explains more fully how to set this up.  [http://useopensource.blogspot.com/2007/03/how-to-setup-firewall-in-ubuntu.html](http://useopensource.blogspot.com/2007/03/how-to-setup-firewall-in-ubuntu.html)

---

### Post by hyper_ch on 2008-07-31
> **linux_tech said:**
> With the Internet its good to be redundant and have layered protection both hardware and software.]
and totally unneeded in most cases in linux.

---

### Post by linux_tech on 2008-07-31
FYI Link for Firestarter setup guide pdf- 
[http://www.fs-security.com/docs.php#docsdownload](http://www.fs-security.com/docs.php#docsdownload)

---

### Post by smooth3006 on 2008-07-31
i know ubuntu comes with iptables now, i didn't know that before. i went gufw as the graphical interface for the firewall. i have one question, im in stealth mode but do i have to open a port for transmission "p2p" ? if so which one should i allow ?

---

### Post by mdsharp24 on 2008-07-31
smooth3006, it depends on which port you configure your p2p client to run on. In the settings portion of your client it will tell you, however, most people recommend you run it on the non standard port. Then, open that port in your firewall.

---

### Post by smooth3006 on 2008-07-31
> **mdsharp24 said:**
> smooth3006, it depends on which port you configure your p2p client to run on. In the settings portion of your client it will tell you, however, most people recommend you run it on the non standard port. Then, open that port in your firewall.

im in the transmission settings right now and it shows the port it will use as 51413 and it's status says "closed". should this be the port i allow from my firewall ?

---

### Post by mdsharp24 on 2008-07-31
Correct, then you can check it with an online port check site such as [http://www.canyouseeme.org/](http://www.canyouseeme.org/)     Just put the port you want checked it and if transmission is running it will say "I can see your service on whatever port"

---

### Post by smooth3006 on 2008-07-31
> **mdsharp24 said:**
> Correct, then you can check it with an online port check site such as [http://www.canyouseeme.org/](http://www.canyouseeme.org/)     Just put the port you want checked it and if transmission is running it will say "I can see your service on whatever port"

thanks i did it and transmission shows the port as open now. i also ran a firewall test and it still says im totally protected and stealth. :)

---


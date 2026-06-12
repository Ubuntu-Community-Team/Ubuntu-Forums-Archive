---
title: "help, Firestarter blocking firefox browsing"
date: 2008-09-19
forum: Security
---

### Post by Drizzel on 2008-09-19
I am terrible with firewalls, I'll be the first to admit it. Can someone help me configure firestarter so I can browse the net, but block everything else? When firestarter is enabled no pages load.. I tried looking through the settings but couldnt figure out how to do it. I'm using firestarter 1.0.3 and I'm on Ubuntu Hardy.

---

### Post by lovinglinux on 2008-09-19
Go to Policy tab and select "Outbound traffic policy" from the "Editing" drop-down list. Then you have two options:

1 - Select "Permissive by default, blacklist traffic", which means all outgoing connections will be allowed, unless you create a specific rule for blocking an IP or port.

2 - Select "Restrictive by deafult, whitelist traffic", which means all outgoing connections will be blocked, unless you create a specific rule to allow an IP or port. If you opt for this method you need to create a rule to allow outgoing connections on port 80 (HTTP). Right click in the bottom window and select "Add rule", then select "HTTP" in the "Name" field and hit OK. This will create a rule that will allow outgoing connections on port 80, which is required to browse web sites. You might also want create a rule for port 443, which is "HTTPS" (required to browse safe web addresses like Gmail).

You don't have to use only "Permissive" or "Restrictive". For instance, I use "Permissive" while downloading with p2p, otherwise I would have to create a rule for every single peer IP my torrent client try to connect. While not using a torrent client, I choose "Restrictive" and allow those ports I know I will need like HTPP and HTTPS for browsing and Ircd for using an IRC client.

BTW, you should learn how to use a Firewall properly, otherwise you can make more damage than protect your system. You don't have to run Firestarter all the time, because it is just gui to configure iptables. Once you configure it properly you can close it and you will be protected all the time, even after a reboot.

Read Firestarter manual at [http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by Vivaldi Gloria on 2008-09-19
> **Drizzel said:**
> Can someone help me configure firestarter so I can browse the net, but block everything else? 

Actually there is nothing to block in a default ubuntu desktop install because there are no services listening to any port. So changing the firewall settings (and using firestarter) is completely unnecessary unless you install a server application.

---

### Post by lovinglinux on 2008-09-19
> **Vivaldi Gloria said:**
> Actually there is nothing to block in a default ubuntu desktop install because there are no services listening to any port. So changing the firewall settings (and using firestarter) is completely unnecessary unless you install a server application.

I have seen a lot of posts like this and I really don't like them. There is nothing to block on a default install, but people like to install stuff from web sites and sometimes a software install a service that listen to some port you don't even know about. So what's the problem if people like to use Firewalls? If they screw up installing some listening service or get something that like to phone somewhere without their knowledge at least they will be protecting their network before bad things happen.

For example, my machine was trying to contact a mysterious server through Samba ports and if I didn't have Firestarter enabled I wouldn't even notice this.

---

### Post by Vivaldi Gloria on 2008-09-19
> **lovinglinux said:**
> but people like to install stuff from web sites

Then a firewall is the least of their worries.

---

### Post by lovinglinux on 2008-09-19
> **Vivaldi Gloria said:**
> Then a firewall is the least of their worries.

:) You can't be convinced, can you?

---

### Post by Drizzel on 2008-09-19
Thanks so much for the informative post :) I did what you said, but still couldn't browse.. I was looking through the preferences in Firestarter and was just trying unchecking different things. Under advanced options, if I uncheck "Block broadcasts from external network" I can browse just fine. If I leave it checked(default) then I cant browse.. Is that something important that should be checked? I just dont know what it means.

---

### Post by lovinglinux on 2008-09-19
> **Drizzel said:**
> Thanks so much for the informative post :) I did what you said, but still couldn't browse.. I was looking through the preferences in Firestarter and was just trying unchecking different things. Under advanced options, if I uncheck "Block broadcasts from external network" I can browse just fine. If I leave it checked(default) then I cant browse.. Is that something important that should be checked? I just dont know what it means.

You should read the manual to understand how it works. Checking or checking things randomly is a VERY BAD IDEA.

---

### Post by Drizzel on 2008-09-19
Yeah I know.. I was trying to track down what was blocking me from browsing the net. I always put things back like they were. I will get around to reading the manual, I'm just swamped with classes right now and dont have the patience to learn all about firewalls at the moment. So, do I need "Block broadcasts from external network" checked or not?

---

### Post by lovinglinux on 2008-09-19
> **Drizzel said:**
> Yeah I know.. I was trying to track down what was blocking me from browsing the net. I always put things back like they were. I will get around to reading the manual, I'm just swamped with classes right now and dont have the patience to learn all about firewalls at the moment. So, do I need "Block broadcasts from external network" checked or not?

Leave it [COLOR="Red"]**checked**[/COLOR] and follow my instructions in the previous post, using "Permissive" in the Outbound settings and you should regain access to the Internet.

---

### Post by cariboo on 2008-09-19
IF you feel you really need a firewall why not clear all the changes you have made and dump firestarter as it is only a gui interface to iptables and use the default firewall ufw. Right now there is only a text interface, but that is the best way to learn about configuring a firewall. A gui can not cover all the different configurations. Hve a look at this page:

[http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html](http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html)

This will walk you through setting up ufw. Now just because you are behind a firewall doesn't mean that you should just ignore what is going on with your computer, I would suggest installing something like logwatch just to keep an eye on what your computer is doing.

Jim

---

### Post by mike1234 on 2008-09-19
I use Firestarter. Once setup properly check this site. You should (I feel safer) pass with 100% true stealth mode. Do a port test.

_[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)_

M.

---

### Post by lovinglinux on 2008-09-20
> **cariboo907 said:**
> IF you feel you really need a firewall why not clear all the changes you have made and dump firestarter as it is only a gui interface to iptables and use the default firewall ufw. Right now there is only a text interface, but that is the best way to learn about configuring a firewall. A gui can not cover all the different configurations. Hve a look at this page:

[http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html](http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html)

This will walk you through setting up ufw. Now just because you are behind a firewall doesn't mean that you should just ignore what is going on with your computer, I would suggest installing something like logwatch just to keep an eye on what your computer is doing.

Jim

There is a GUI for ufw and it's called Gufw.

Gufw is easier than Firestarter, because there is no outbound configuration. All outgoing connections are allowed by default.

---

### Post by lumitoro on 2009-02-07
Reading this thread and finding linux users saying that standard install it's just fine, made me worry about what ppl think the firewall is for.
Linux is only safe if we use the tools that come with the package (naming it: iptables). Every firewall(well...maybe not all) tools in linux are front-end's for iptables. This is meant to keep broad scanners and hackers to access sensitive data in your box. Even thought it might protect you from some viruses, your best protection against viruses is our policy towards unknown email sources, removable devices auto-execute and secure browser in the system. Opening ports in our system is always a risk, since no security system is bullet proof being it digital or not :D:p:D, but once it's necessary, we have to be selective on witch ones we open and always be aware that they are open and thoughtful use of such services are in order.
Having said that, I found this thread very helpful. Thanks, good luck.;)

P.S.: Has I said Firestarter is a front-end to iptables so you dont need to start it on boot. Every rule you create with Firestarter and similar will be saved to iptables. I find useful to have Firestarter to start on boot because it's easier to find out witch service or IP is being blocked by the firewall giving me the opportunity to change it very easily.
By the way, it's not bad to have a anti-virus available...just in case ;)

---

### Post by hyper_ch on 2009-02-08
in most cases you don't need to think about a firewall in linux. Even less so if you're behind a router.

---


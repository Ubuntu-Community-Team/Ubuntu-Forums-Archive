---
title: "Configuring Ubuntu as gateway router"
date: 2005-04-10
forum: Server Platforms
---

### Post by Prospero424 on 2005-04-10
This is my first real experience with Linux, and so far I have to say that Ubuntu's very impressive.

After a couple of hours mucking around, I already have Samba, remote desktop, and a couiple of other things working properly with both my Windows Server 2003 and Windows XP machines/shares.  This is more than I've been able to do easily with other distros.

Ok, enough butt-kissing ;)

What I need is a step-by-step explanation on how to configure my Ubuntu box as a gateway router doing IP forwarding and NAT/IP masquerading/whatever and perhaps running as a DHCP server, although that's not necessary.  I'm using the Hoary release, have two NICs (eth0 and eth1) installed and working (as far as I can tell; they both show up in the Network configuration tool), and everything seems to work great.

I've scoured these forums and the internet, and so far I haven't been able to find anything clear and accurate enough to be useful to a relative newcomer like me.  I'm desperately hoping that someone here can at least point me in the right direction.  Because right now, I'm just plain stuck.

A thousand thanks.

-Prospero

---

### Post by Gandalf on 2005-04-10
[QUOTE=Prospero424]This is my first real experience with Linux, and so far I have to say that Ubuntu's very impressive.

After a couple of hours mucking around, I already have Samba, remote desktop, and a couiple of other things working properly with both my Windows Server 2003 and Windows XP machines/shares.  This is more than I've been able to do easily with other distros.

Ok, enough butt-kissing ;)

What I need is a step-by-step explanation on how to configure my Ubuntu box as a gateway router doing IP forwarding and NAT/IP masquerading/whatever and perhaps running as a DHCP server, although that's not necessary.  I'm using the Hoary release, have two NICs (eth0 and eth1) installed and working (as far as I can tell; they both show up in the Network configuration tool), and everything seems to work great.

I've scoured these forums and the internet, and so far I haven't been able to find anything clear and accurate enough to be useful to a relative newcomer like me.  I'm desperately hoping that someone here can at least point me in the right direction.  Because right now, I'm just plain stuck.

A thousand thanks.

-Prospero[/QUOTE]
 why not using [IPCOP router](http://www.ipcop.org)???

---

### Post by Prospero424 on 2005-04-10
Well, I don't want this machine to exclusively be a router.  I want to use it for media storage, as an emule client, and a few other things I haven't thought of yet :)

basically, I want to have a full-featured Linux machine that I can use normally but have it also be the gateway router for my home LAN.

---

### Post by Gandalf on 2005-04-11
[QUOTE=Prospero424]Well, I don't want this machine to exclusively be a router.  I want to use it for media storage, as an emule client, and a few other things I haven't thought of yet :)

basically, I want to have a full-featured Linux machine that I can use normally but have it also be the gateway router for my home LAN.[/QUOTE]
 that will be a lot of work to do iptables and etc... anyway i don't know iptables yet, maybe someone do

---

### Post by tonym on 2005-04-11
There are a number of packages that let you configer iptables to do this sort of job.  The one I use is shorewall.  Seems to work fine although you configure it via a number of text files rather than a nice gui.

---

### Post by az on 2005-04-11
Shorewall is great.  Be sure to install the shorewall-doc package and copy the example files to your /etc/shorewall directory.

You can also use firestarter for NAT.  I think that guidedog does NAT, too.  Guarddog does firewalling with iptables.

apt-cache search firewall
apt-ccache search masquerade

Do not forget about dns.  You will also have to do dns forwarding.

dnsmasq is excellect.  It also serves as a dhcp server.  Just what you need!

---

### Post by Prospero424 on 2005-04-11
Thanks guys, that gives me a good place to start.  I'm researching and absorbing those apps right now.

I've had Shoreline recommended to me several times now, I think that's going to be very helpful.

---

### Post by jobezone on 2005-04-11
[QUOTE=Prospero424]Thanks guys, that gives me a good place to start.  I'm researching and absorbing those apps right now.

I've had Shoreline recommended to me several times now, I think that's going to be very helpful.[/QUOTE]
 There is also guidedog (with a couterpart firewall called guarddog, although I prefer firestarter). It's a QT application, and very easy to use..

---

### Post by Prospero424 on 2005-04-11
Just wanted to let ya'll know that I'm making good progress with Shorewall right now.

Oh, and this machine is one that I scavenged a bunch of pretty decent parts for, then slapped them into the best case I had laying around, which just so happened to be a fairly recent ATX mid-tower from a cannibalized Gateway desktop.

So it's going to be my Gateway gateway!

Ah, geek humor.  So very lame. ;)

---

### Post by bvidinli on 2008-05-16
i used firestarter, it was easiest way..
i  connected my desktop pc to my notebook which is in turn connected my adsl router via wireless..

this way i am able to connect desktop pc to internet, through my notebook...
if you ask, why not to connect desktop directly to adsl modem ? answer is simple, 
desktop pc has no wireless card, and modem is away from desktop... :)

firestarter was very simple, with wizards...

---


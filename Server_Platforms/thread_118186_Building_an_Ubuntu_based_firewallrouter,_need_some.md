---
title: "Building an Ubuntu based firewall/router, need some direction....."
date: 2006-01-16
forum: Server Platforms
---

### Post by s1gnAl on 2006-01-16
Ok my linksys WRT54G has officially made me mad for the last time, no matter what I do, WPA will not work correctly on this box and I am tired of having to reboot it at least once every two days. 

So I am determined to build an Ubuntu based box to replace this, but did not know where to start as I don't really know a whole lot about iptables and such.

Here are the functionalities that I need(which I undoubtedly assume are doable):

1. DHCP/NAT for my local LAN
2. QoS
3. Use a PCI wireless card as an access point 
4. MAC address filtering for the wireless segment
5. WPA pre-shared key
6. PPTP server 
7. Web based interface? (would be nice, but not necessary)

That's all I can think of at the moment. That is pretty much what I use my linksys box for now. I am building a box with 2 ethernet cards(or ports, if the mobo has them onboard) and putting a PCI wireless card in to serve as an access point for mine and my wife's laptop. 

I know there are plenty of pre-built firewall distros out there based on linux, I have used Smoothwall in the past(great firewall), but I am wanting to get my hands dirty and learn iptables in the process. 

Would iptables be a good solution for this kind of setup? I should mention this is for a home LAN connected to the internet via a cable modem. 

Suggestions appreciated, and if you could point me to some good beginner tutorials on iptables and/or using Ubuntu as a firewall that would be great :D

---

### Post by s1gnAl on 2006-01-16
Anyone!!!??? I know someone out there has done this! (well hopefully anyhow lol)

---

### Post by slow learner on 2006-01-18
Hi,

I am looking to setup a similar box, minus wireless. Have you tried clark connect?

I like smoothwall, but need something that will permit an all in one print & file server(s).


If anyone can shed some light on setting up ubuntu as a standalone gateway I'd really appreciate it  :KS

---

### Post by Peter76 on 2006-01-19
Have a look at the ipmasq package ( sudo apt-get install ipmasq )... I have a box with four nics, and ipmasq handles all this for me. Try it and post some questions if you want more info

---

### Post by tuprox on 2007-08-01
I have the same question.  I finally got fed up with my WRT54G as well.  I have asked and people point to some tutorials, but the tutorials leave a lot to be desired.

Can Someone help us and I will make a tutorial that WILL work?  I think this should be one of the most "solid" area of the linux groups.  I have found many articles about building a Fedora router, PLEASE don't make me have to go to Fedora to make this work!  

I started a new [thread here]("http://ubuntuforums.org/showthread.php?p=3113950#post3113950")

---

### Post by John.Michael.Kane on 2007-08-02
Either of these should give you a start point.
[Ubuntu As A Firewall/Gateway]("http://www.howtoforge.com/ubuntu6.10_firewall_gateway")
[ Setup Your Computer to be a Router]("http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html")

Theres also these.
[IPCop]("http://www.ipcop.org/modules.php?op=modload&name=phpWiki&file=index&pagename=IPCopDocumentation")
[pfSense]("http://doc.pfsense.org/index.php/HOWTO_Install_pfSense")

---


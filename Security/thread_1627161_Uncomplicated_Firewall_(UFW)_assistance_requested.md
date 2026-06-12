---
title: "Uncomplicated Firewall (UFW) assistance requested"
date: 2010-11-21
forum: Security
---

### Post by Scunnered on 2010-11-21
As I regularly share my printer with a Windows system I decided to add Uncomplicated Firewall (UFW) to my armoury. When I look to access the shared folders on Windows I find that without disabling the firewall I am unable to access the folders.

Looking at the documentation I have been unable to follow exactly what I need to do to let me access the shared items.  I attempted to add an action to let Samba be permitted. This will only work in part in that it will let me by using Network > Windows Network display MSHome but at that point access is denied.  

So far I have been unable to access the USER folder within MSHome and my question is how do I set access permissions.

I used Shields UP to see how secure my system is and all the tests confirm that things are working perfectly but I am unhappy at the thought of opening things up needlessly to access shared folders.

Whoever called this UFW had not taken my level of incompetence into consideration.  All contributions will be gratefully received.

---

### Post by The Cog on 2010-11-21
Moved to Security Discussions forum.

If you are connected to the internet by a NAT router, then personally I would not bother with a firewall. 

If your PC is directly connected to the internet via modem rather than a NAT router, then your print server is visible to the internet and you really do need a firewall to only allow the local network in. But I don't know what might be stoping samba from working, I'm afraid,

---

### Post by cariboo on 2010-11-21
If you are behind a router, you really don't need a firewall, it's sort of a belt & suspenders approach. I would suggest you try gufw, it's in the repositories, to setup the firewall rules. See the screenshot.

---

### Post by bodhi.zazen on 2010-11-21
> **Scunnered said:**
> As I regularly share my printer with a Windows system I decided to add Uncomplicated Firewall (UFW) to my armoury. When I look to access the shared folders on Windows I find that without disabling the firewall I am unable to access the folders.

Yep, that is how firewalls work =)

> Looking at the documentation I have been unable to follow exactly what I need to do to let me access the shared items.  I attempted to add an action to let Samba be permitted. This will only work in part in that it will let me by using Network > Windows Network display MSHome but at that point access is denied.  

So far I have been unable to access the USER folder within MSHome and my question is how do I set access permissions.

What documentation ? And how are you sharing your printer ? Samba ?

> I used Shields UP to see how secure my system is and all the tests confirm that things are working perfectly but I am unhappy at the thought of opening things up needlessly to access shared folders.

Shields up scans your router and is unlikely to help your current dilemma.

> Whoever called this UFW had not taken my level of incompetence into consideration.  All contributions will be gratefully received.

See:

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

From your post I am guessing you are using Samba, here is a post which reviews the ports you need to allow for samba:

[http://troy.jdmz.net/samba/fw/](http://troy.jdmz.net/samba/fw/)

Just allow access to those ports from your LAN.

---

### Post by Scunnered on 2010-11-22
My thanks to you all for your assistance.

Following the links provided by bodhi.zazen I appear to have followed the community documentation for the setup of a firewall and GUFW documents.

Having checked and re-checked I still have the same problem.

I understand that the purpose of the firewall is to keep unwanted things out but believed that having set a permission for Samba that I should then therefore access the required folders.  

I use Samba to let my partner print from her XP system to my usb printer on Lucid.  I also use it to copy all the files in her shared folder over to my system as a backup of hers.

In the rules section of the firewell I see that 135, 139 & 445/tcp and 137 & 138/udp are shown as allow in from anywhere.  I noted one difference in the examples in that there is now an incoming and outgoing options and wonder if both should be set as allow or left alone?

I access the internet via a cable modem via a wireless connection as does my partner. Could this cause problems or should I totally forget the firewall. 

It is just a bit frustrating that just when I think that I am improving with Ubuntu that I get a large kick in the rear to bring me back to reality.  I am ever hopeful of getting there eventually.

Again my thanks for your kind assistance

---

### Post by HermanAB on 2010-11-22
Howdy,

You are confusing Samba with Printing.

Yes, Samba has the ability to distribute printer drivers and synchronize passwords that make printing easier, but mainly Samba is for file sharing and CUPS is for printing.

Samba uses mainly port 445 for file sharing.

CUPS uses port 631. 
The Internet Printing Protocol (IPP) uses port 9100.
The older LPR uses ports 721 to 731.

Hope that helps.

---

### Post by Scunnered on 2010-11-22
Thanks Herman

Before I installed the firewall I could access shared files and was able to copy them over to my system OK.  The way things are going with this problem I think unless someone comes up with a quick solution I shall abandon this idea.

---

### Post by bodhi.zazen on 2010-11-22
At this point you need to provide more details.

Post your rules and logs at the logs for denials.

But simply stating that it is not working is not likely to be of much benefit.

---

### Post by Scunnered on 2010-11-22
Sorry folks but I am getting into deeper water and am struggling to achieve my aims.

I think that it will be best that I abandon things at this time rather than waste yours

My thanks for all your assistance

---


---
title: "Gufw"
date: 2010-01-01
forum: Security
---

### Post by Silvertones on 2010-01-01
VERY GREEN to Ubuntu. My setup:
1. computer A connects to the internet through usb dial up modem
2. computer A & B are wirelessly networked through an ADHOC network.
3. computer B doesnot need to connect to the internet.

I've installed the GUFW. If I enable it I can not see the other computer files. I use static IPs for both. I tried setting a rule but I get stumped were it asks for the port. I'm not all that familiar with ports.

Thanks

---

### Post by Silvertones on 2010-01-01
VERY GREEN to Ubuntu. My setup:
1. computer A connects to the internet through usb dial up modem
2. computer A & B are wirelessly networked through an ADHOC network.
3. computer B doesnot need to connect to the internet.

I've installed the GUFW. If I enable it I can not see the other computer  files. I use static IPs for both. I tried setting a rule but I get  stumped were it asks for the port. I'm not all that familiar with ports.

Thanks

---

### Post by Silvertones on 2010-01-01
VERY GREEN to Ubuntu. My setup:
1. computer A connects to the internet through usb dial up modem
2. computer A & B are wirelessly networked through an ADHOC network.
3. computer B doesnot need to connect to the internet.

I've installed the GUFW. If I enable it I can not see the other computer   files.Meaning I click on network,click on win network and my workgroup icon is missing.  I use static IPs for both. I tried setting a rule but I get   stumped were it asks for the port. I'm not all that familiar with ports.I can set the IP OK what do I set for port.

Does this setup even need a Firewall? I do have files that are shared.

Thanks

---

### Post by gordintoronto on 2010-01-01
If you don't mind switching to Firestarter, here is a tutorial:
[http://my.opera.com/ubuntunerd1/blog/h-2](http://my.opera.com/ubuntunerd1/blog/h-2)

---

### Post by gsmanners on 2010-01-01
Sounds like you're using Samba. In that case you need to allow these ports:

135, 137, 138, 139, and 445 (udp and tcp)

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html#firewallports](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html#firewallports)
[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

---

### Post by Iowan on 2010-01-01
[Here]("http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html") is one How-To for **gufw**. I haven't used it.

---

### Post by bodhi.zazen on 2010-01-01
> **Silvertones said:**
> VERY GREEN to Ubuntu. My setup:
1. computer A connects to the internet through usb dial up modem
2. computer A & B are wirelessly networked through an ADHOC network.
3. computer B doesnot need to connect to the internet.

I've installed the GUFW. If I enable it I can not see the other computer files. I use static IPs for both. I tried setting a rule but I get stumped were it asks for the port. I'm not all that familiar with ports.

Thanks

No need for firestarter, and installing firestarter does not address the question of what ports to allow.

Basically every server, http, ftp, ssh, DNS, Samba, etc has a default port or ports.

You can see them listed in several places, 

[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

You may want NAT , or portforwarding.

/can you describe what it is you are wanting to do and what you are wanting to restrict with a firewall ?

---

### Post by Silvertones on 2010-01-02
First thanks for the reply.
What do I want to restrict? Well bad stuff! I know this is simplistic but thought you should always run a firewall. Remember I'm coming new from Windows. So I want to block what should be blocked coming from the internet but I want to allow my two computers to communicate freely over my addhoc network.
This works fine in Windows using PCTools firewall Plus. I just put in a rule specifying what IP address and subset mask to allow and it works.

---

### Post by Silvertones on 2010-01-02
Thanks I'll give it a try

---

### Post by Silvertones on 2010-01-02
I've made some progress but there may be a bug in the FW. Not sure I'll describe.

Comp. A = Ubuntu & connects to the internet via dialup
Comp. B = Windows no internet needed
A & B are networked via adhoc wirelessly and can see back and forth perfectly.
Engage the FW fron GFUW and I can no longer see shared files back and fort as expected.

It's been determined that I need ports 135,137,138,139,445 Both TCP & UDP
My workgroup in Windows is called BOBO.
If I make simple rules in GFUW allowing the above ports the results are:

I can go from comp.B ( windows) to computer a perfectly.
On comp. A ( Ubuntu) If I click network I see "windows network" click on that I see " BOBO" my work group click on that the screen changes but is blank. I should see Comp. B listed.
So it's getting to a point

---

### Post by Silvertones on 2010-01-02
I've made some progress but there may be a bug in the FW. Not sure I'll   describe.

Comp. A = Ubuntu & connects to the internet via dialup
Comp. B = Windows XP no internet needed
A & B are networked via adhoc wirelessly and can see back and forth   perfectly. I can see all shares from either comp.The trouble comes from  engaging the GUFW
Engage the FW fron GFUW and I can no longer see shared files back and   forth as expected.

It's been determined that I need ports 135,137,138,139,445 Both TCP   & UDP
My workgroup in Windows is called BOBO.
If I make simple rules in GFUW allowing the above ports the results are:

I can go from comp.B ( windows) to computer A (Ubuntu) perfectly.I can  access the shared folder on the Ubuntu comp.
On comp. A ( Ubuntu) If I click network I see "windows network" click on   that I see " BOBO" my work group  and "Workgroup" the Ubuntu  group.Click on "BOBO" and the screen changes but  is blank and says 0  items. I should see Comp. B listed but don't.
So it's getting to a point the FW is not stopping me from seeing the  "BOBO" group but won't let me see the Comp. in that group.

---

### Post by Silvertones on 2010-01-02
_Redundant_

---

### Post by dmizer on 2010-01-02
> **Silvertones said:**
> 
So it's getting to a point the FW is not stopping me from seeing the  "BOBO" group but won't let me see the Comp. in that group.

Actually, I would suggest removing all rules. They will allow anyone from the Internet (over your dial up connection) to access your samba shares.

Instead, you should make sure that UFW is enabled only for the ppp connection and not the LAN adapter. I'm too tired to find out how, but my experience with GUFW suggests that this shouldn't be too hard.

---

### Post by Silvertones on 2010-01-02
OH!! Thanks I'll remove the rules. The only real reson for the network is to be able to:
1. Backup Comp. A to an external drive on Comp. B
2. To move downloaded files ( minimal ) from A to B.

I can do this while off line and disable the FW.

BTW I only used the simple rule of allowing access to those ports as a testing measure. I was off line at the time. My intent is to only allow access to those ports from the static IPs of my 2 comp. This should be fine right?

I guess we still don't know why the FW is sort of blocking me though.

---

### Post by Silvertones on 2010-01-02
Set it up like this and then just right click on the folder and set to share. That's it. Should I have done something different?
[http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html](http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html)

---

### Post by Silvertones on 2010-01-02
[URL="http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html"]Redundant
[/URL]

---

### Post by Silvertones on 2010-01-02
> **gsmanners said:**
> Sounds like you're using Samba. In that case you need to allow these ports:

135, 137, 138, 139, and 445 (udp and tcp)

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html#firewallports](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html#firewallports)
[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

Set it up like this and then just right click on the folder and set to  share. That's it. Should I have done something different?
[http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html](http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html)

---

### Post by gsmanners on 2010-01-02
Looks about right. Yeah, even with a set of firewall rules you still need the interface set up. I forgot about that (probably because I'm used to thinking of Firestarter in that situation, which does both at the same time).

---

### Post by cariboo on 2010-01-02
Please don't create multiple threads on the same subject, I have merged your three threads.

---

### Post by bodhi.zazen on 2010-01-03
> **Silvertones said:**
> First thanks for the reply.
What do I want to restrict? Well bad stuff! I know this is simplistic but thought you should always run a firewall. Remember I'm coming new from Windows. So I want to block what should be blocked coming from the internet but I want to allow my two computers to communicate freely over my addhoc network.
This works fine in Windows using PCTools firewall Plus. I just put in a rule specifying what IP address and subset mask to allow and it works.

Linux is not windows and you can not apply windows mentality to Linux blindly.

First on Windows, a default installation has a number of open ports, both documented and undocumented, and since Microsoft refuses to close such ports (this is not unreasonable, there is a trade off between security and ease of use), one needs to rely on third party applications such as firewalls to harden Windows.

Now that is an oversimplification, but this is your stated mentality.

On Ubutnu, with a default installation, there are no open ports so a firewall is unnecessary.

If you are installing a server, in this case Samba, this implies you have a router. All routers have a firewall built in, so you probably do not need to configure yoru firewall.

Now if you prefer to restrict access to clients on your LAN, or you simply wish to understand how firewalls work, then by all means go for it =)

So you have 2 issues:

1. Install and configure Samba. Wheil you do this I suggest you turn your firewall OFF.

2. Once Samba is working if you wish to enable your firewall I suggest you go with ufw or gufw. ufw is the default application to configure your firewall and if you prefer gufw is available as a graphical front end.

You can restrict access to your LAN or specific clients quite easily with ufw =)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

---

### Post by Silvertones on 2010-01-03
Sorry about multiple posts.
Let me first back up a bunch of steps. I originally had these two computers connected peer to peer ( adhoc) with Windows on both. After I installed Ubuntu within Widows there was a message " network available" so using the Network Manager I clicked on the wireless tab and configured the security, Ip address, subsetmask and gateway to the same settings as in Windows Voila I was up and running. That simple. I added a folder to the desk top, right clicked on it and checked "share". That's it .That simple. Note: I had previously downloaded "Network Manager" & " file Sharing Service" via the download manager.

Everyone keeps saying SAMBA. I have no knowledge of SAMBA and how to use or access it. Is the Network Manager a GUI for SAMBA?

I appreciate the help BUT no one appears to be carefully reading what I posted.
My network is Peer to peer wireless ( adhoc) There is no router. One of the computers connects to the Internet via a DIALUP modem.The other computer does not connect to the Internet at all. My network is 2 computers both mine and sit side by side.
File sharing between the two computers works fine UNTIL I engage the GUFW.
I added rules to UFW via GUFW to allow traffic TO ports 135, 137,138,139,445 UDP,TCP FROM XXX.XX.X.X/24 ( the range of the static Ips of both computers)
When I do this the Windows computer can now access the shared files on the Ubuntu computer. So far so good.
PLEASE READ THIS NEXT PART CAREFULLY
The name of my Windows workgroup is " BOBO"
From the Ubuntu Computer I press-- Places--->Network---> ( I then see two folders 1. BOBO & 2.Workgroup)----> press BOBO and the screen goes to the next page  that should show an icon of a computer named "music" but it doesn't. It's blank.
If I disengage the FW the Music computer does show.I can the progress on to the shared files on the Windows ( music) computer.
Please note: If I don't put rules into UFW and engage the FW I don't get beyond Network. I can't see "workgroup" icon nor "BOBO" icon.

QUESTIONS:
1. With this setup do I still not need a firewall
2. Why is the FW on the Ubuntu comp. blocking itself from seeing the Windows computer beyond the BOBO workgroup.
3. I see I have SAMBA installed but am not sure that I've ever done anything with it:confused:
Maybe that's the issue. If so PLEASE steer me in the right direction.

THANK YOU ALL VERY MUCH:)

---

### Post by Silvertones on 2010-01-03
> **gsmanners said:**
> Looks about right. Yeah, even with a set of firewall rules you still need the interface set up. I forgot about that (probably because I'm used to thinking of Firestarter in that situation, which does both at the same time).

OK so I:
1. set up the network per the link
2. Entered rules into the UFW

Are you saying there's a third step to "set up the interface"?

---

### Post by Silvertones on 2010-01-03
OK so now I'm embarrassed. I was making things too complicated in my  rules.
KISS KISS KISS KISS
What I did to fix:

1. Open the GUFW
2. set allow both udp & tcp
3. In the from I put in the IP address of comp.B
Repeated this for comp. A 

ALL IS WELL The FW will block everything except from these two IPs and  there IPs assigned for LAN only and also have subset maskes.

THANKS ALL.

---


---
title: "Things to know about opening your server to the world"
date: 2010-06-23
forum: Server Platforms
---

### Post by Rhemat on 2010-06-23
Hello All,
I just recently opened my server to the internet with SSH ports open (in my modem and router), and I will soon set it up to do various other tasks (Quake 3 Server, e-mail probably).  So far no problems, but a couple of questions:

I know that by default, the OS and many network devices use DHCP for IP address handling.  However, it seems every time I turn on my computers, they have the same IP address every time.  I don't even know how to set up a static address in Linux (yet), nor have I done so with my Linksys WRT54G2 Router.  I will eventually do so, but what are the odds of the router handing the machines the same IP address over, and over for months, even a year on end?

Also, are there any security concerns I should know about?  I know that the potential for someone getting into my network are there, but I wonder if it would only take a few minutes, or hours of dedicated attack.

Thanks in advance for your replies.

-Rhemat

---

### Post by Lucky. on 2010-06-23
There's a pretty big chance of the same IP addresses being used over and over.  I imagine for most DHCP servers, they simply dish out the first free IP address in the range they're instructed to use.  For example:

My DHCP server dishes out IP addresses in the range of 192.168.1.150 - 192.168.1.200

I turn on my computer, and I get 192.168.1.150.
I turn on my laptop, and I get 192.168.1.151.

If I turn off both machines and wait a little, then turn on my laptop...it will probably have 192.168.1.150.  I doubt any devices on my network have ever received an IP address as high as 192.168.1.195 or anything close.  I only have 3 computers at home.

There's no reason for the DHCP server to randomly dish out IP addresses in its range.  It doesn't do much for increasing security.

In fact, if you are hosting a server that is public to the Internet, you don't want that IP address changing or else people won't be able to contact you!  Pretty much every server in the world just sits there at the same IP address year after year.  Security is in strong passwords, keys, limiting open ports, keeping software up to date, blocking IP addresses, etc.

You mentioned SSH.  Seems like about once a week I see a thread in here from somebody that got broken into via SSH because they used a weak password and a dictionary attack broke it.  Be careful and good luck!

---

### Post by WinstonChurchill on 2010-06-23
> **Rhemat said:**
> I know that by default, the OS and many network devices use DHCP for IP address handling.  However, it seems every time I turn on my computers, they have the same IP address every time.  I don't even know how to set up a static address in Linux (yet), nor have I done so with my Linksys WRT54G2 Router.  I will eventually do so, but what are the odds of the router handing the machines the same IP address over, and over for months, even a year on end?
Most DHCP server implementations will try to give DHCP clients the same IP when it is possible. However, there's no guarantee. If you're doing port-forwarding from your router, you should probably make your server's address static: you could either configure the DHCP settings on your router to always give your server the same address (static DHCP lease), or you could just set a static IP in /etc/networking/interfaces on the server and not worry about DHCP - just be sure that the static address you assign the server isn't in the range of addresses the DHCP server on your router hands out, or you might have issues down the road.

In regards to SSH, just use public key authentication - don't allow passwords at all. Yes, it can be a little less convenient, but the security benefits are too big to ignore. SSH with only public key authentication enabled is probably the most secure server daemon on Earth.

---

### Post by Deadpan110 on 2010-06-23
It is worth remembering that opening any external connections to your system is a potential security threat - but if everyone didn't do that, then there would be no point of an internet.

As the replies above, assigning a static IP to your box is important and can be done either in dhcp or /etc/network/interfaces (or network manager if you use it)

Most home modems have port forwarding so:

External IP:port 22 -> Internal IP:port 22 (for ssh)

I always like to have access externally to at least one machine inside my network via ssh and use passwords but make sure I have denyhosts installed (it is in the Ubuntu repositories).

By default, it is very strict and works out of the box - 5 num of failed log ins means that the user attempting to log in is blocked indefinitely - this thwarts dictionary attacks from 1 IP.

Be warned though, its default configuration is very strict and can lock you out of your own system when accessed remotely!

---

### Post by Rhemat on 2010-06-23
Okay, I had thought that it was random, like rolling dice.

I'm trying to set a static IP for my server via the Network Manager, and I get this when I issue sudo /etc/init.d/networking restart:

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPOFFER of 192.168.1.103 from 192.168.1.1
DHCPREQUEST of 192.168.1.103 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.103 from 192.168.1.1
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
bound to 192.168.1.103 -- renewal in 40922 seconds.

A bit more info:  My server has two networking devices in it; processor built-in to the Compaq mother board (which I thought I disabled), and a Standard Microsystems 83c170 EPIC/100 PCI card.  They both appear as greyed out options when I click the NM icon, yet I have access to the internet and my own network.  Any suggestions?

Thanks again for your replies.

---


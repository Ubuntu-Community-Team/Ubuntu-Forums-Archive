---
title: "old computers as dedicated firewalls"
date: 2008-07-07
forum: Security
---

### Post by rated727 on 2008-07-07
Please post your experiences and impressions about the software/hardware combinations that you may be using to implement a dedicated hardware firewall.  "Inquiring minds want to know"

I am using an old PC with SmoothWall software as a dedicated hardware firewall (mostly because I have a couple of MS Windows machines in my peer network).  Graphically, my home office looks like this:

  ___internet provider
 | 
 |_Cable modem
.   .   |
   SmoothWall box 
.   .   | 
   Network hub
.   .   |
 Peer networked computers (3)

My SmoothWall computer consists of:
AMD K6 processor 200X2 mHz - 192 Mb RAM - 4.0Gb HDD - 4X CD ROM
If I couldn't use it as a firewall, this computer would only be useful as a boat anchor.
In addition to serving as a firewall, the SmoothWall software includes Clam Antivirus.  Installation (text only, no mouse) was almost entirely automagic, and once installed, there's no more need for monitor or keyboard.  Interface with the SmoothWall box is done through the internet browser of one of the computers in its protected (green) zone.  The potentially dangerous WWW is on the red zone.  With a 3rd NIC you can also set up a computer to serve up web content on the orange zone, and I didn't even start to find out about the purple zone.  There is more functionality in SmoothWall that I have need.  I believe that it is configurable to serve a far more complex network than I have.
After installation, SmoothWall is totally transparent.  I check and install updates twice monthly, but with that as the only exception, I never need to touch it ... and isn't that the way software is supposed to work?

How safe and secure do I feel?  About 96% covered.  Do I relax?  No.  Would I give up my SmoothWall box?  Not on your life!

  --  I want to die in my sleep like my grandfather.  I don't want to die screaming in terror like the passengers in his car.

---

### Post by antikristian on 2009-04-27
I'm playing with vyatta in a virtual machine. It's got a nice configuration interface for networking and routing (xorpsh).

---

### Post by lensman3 on 2009-04-27
The hardware should work fine.  The only problem I see, is that the hardware being so old that drivers are out of date or unavailable. (Such as it having a bootable CDROM).

 If you use the GUI interface through a KLM switch, the system would be very slow.  I access my firewall via ssh and the command line.  I would setup the boot so that it only goes as far as run-level 3, the command line interface.  Finding a small hard drive of about 8 Gbytes is hard anymore.  

My last firewall was a 500 Mhz mid '90s machine.  On a full download it wouldn't even break 5 percent usage.  My iptables script is about 800 lines as I block all of Asia, South American, Africa and Eastern Europe.  I also run a fetchmail, ftp site, and a sendmail daemon.  

The firewall barely breaks a sweat!  I would suggest trying it.  It is a great learning experience.  The dual Ethernet cards are the hardest part, mainly making sure that one of the cards stays eth0 and the other as eth1.  You don't want them to switch between boots!

Hope this helps.

---


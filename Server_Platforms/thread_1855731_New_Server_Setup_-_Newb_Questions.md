---
title: "New Server Setup - Newb Questions"
date: 2011-10-06
forum: Server Platforms
---

### Post by svtguy88 on 2011-10-06
My original plan was to turn my Powermac G4 into my router with a 4-port NIC PCI card.  Unfortunately, I wasn't careful enough when ordering the card, and it won't work on my Mac (it has universal PCI slots, and the card is for a different type of slot....oops).

Fast forward a bit.  I bought a Dell Poweredge 1800, and am having some fun setting it up.  It's a dual processor Xeon 3.0 ghz with 2 GB RAM.  I've got Ubuntu 11.10 installed, and have configured it has my gateway/router/samba server (Webmin was indispensable for this process - awesome program).  I have a very basic rule set for IPTABLES right now, that I got while following [this]("http://ubuntuforums.org/showthread.php?t=926001") forum post.  

Now I want to see what else I can do with it (besides a local file server/other home use).  I'm thinking of signing up with no-ip.com and running some sort of a web site/mail server.  

How should I go about securing my system?  Do I need to strengthen the rules for IPTABLES?  The web server would have to run in a DMZ, but how would I configure that?  I would like to run everything on the same box - do I need/should I virtualize a machine, and run the webserver there?

---

### Post by svtguy88 on 2011-10-10
No one has any input?  Any links for me to read as far as general server setup/config?  

I've got my system up and running, but I want to make sure that I'm doing everything the "right" way.

---

### Post by Dangertux on 2011-10-10
As far as no-ip goes, I use it and really like it, just be careful the client usually ends up with a buffer overflow vulnerability coded in every few versions. (the version in repo's is compiled -O2 with -fstack-protector) so it's ok to use.

Also in terms of security just remember that the security of a system drops proportionally as you add more services to it. Since you have a really nice server perhaps consider virtualization and building multiple virtual servers for your network to seperate resources better?

Those are my thoughts on the subject, as far as iptables goes, I didn't look through all the screenshots in that tutorial (I prefer not to use webmin) so if you post your completed iptables rules I will gladly comment on those.

---

### Post by robvas on 2011-10-10
One good thing about virtualization is that you can set up new servers and remove them without having to actually reboot or re-install the OS on the physical server itself. Maybe load up VMware ESX (free edition) on it. I would add more RAM, it should be cheap to find another 2GB or even 4GB.

You can always search for 'securing Ubuntu' or 'securing Linux' on the web and find lots of tutorials. As for things to do, register a domain for $10/year and point the DNS to your machine. Get a mail server and Apache web server going.
Setup Wordpress or Joomla, and make sure you secure it as well!
Another fun thing to setup is  a squid web cache for your LAN.
Set up a VPN so you can access your home machine from school/work/coffee shops.

---

### Post by svtguy88 on 2011-10-11
I was planning to add more RAM, especially considering how cheap PC-5300 ECC stuff can be had for on eBay now.  

Originally, I was going to do some virtualization, but I'm not sure where it's necessary/advantageous to do so.  Right now the machine acts as my router/gateway and SMB server.  I'm thinking if I do a web server, I would set up a virtual machine for that (along with email)?  Or is it considered *safe* to do this without virtualizing?

And I suppose a good ol' Windows VM is always handy to have.

---


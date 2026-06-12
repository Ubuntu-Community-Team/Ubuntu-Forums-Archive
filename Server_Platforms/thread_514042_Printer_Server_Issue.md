---
title: "Printer Server Issue"
date: 2007-07-31
forum: Server Platforms
---

### Post by hmhmhm on 2007-07-31
Hi, 

I'm new here and trying my first server install. I already thought I was bullet-proof (RAID no problem, NIC bonding no problem) and now this ... I can't get my printer working. Anyway, here is my configuration:
Dell Poweredge 1650, Ubuntu 7.04 Server, HP Officejet 5510 (multifunction printer), Server IP is 192.168.2.10

The printer is connected to the server via USB and I have a local network up an running. I don't want to install a GUI on the server, but am happy to use remote admin tools (SWAT or Cups in browser). From what I've been reading so far, Samba & Cups should be able to do the trick. Here is what I've tried so far:

-	sudo apt-get install samba smbfs 
-	sudo apt-get install swat netkit-inetd tcpd
-	sudo passwd root
-	sudo apt-get install cupsys*
-	sudo nano /etc/cups/cupsd.conf
        I've added "Listen 192.168.2.10" to the file and made sure that <Location>, <Location /admin>, <Location /admin/conf> all contain a "Allow @LOCAL" entry

-	sudo /etc/init.d/cupsys restart

At this stage, I can start a browser on a network computer and access 192.168.2.10:631
It detects my printer and I can install it without a problem. However, it doesn't print a test page.

I then tried to print a textfile from the server command line, again without success.

I did some further reading on the internet and decided to download hplip-2.7.6.run, which supports a HP Officejet 5500 (mine is a 5510 but that's close enough).

I did then:
-        sudo apt-get install lsb
-        sudo sh hplip-2.7.6.run
-        sudo hp-setup

Again, it detects the printer and installs it. Again, I can't print. I thought it might be the .ppd file so I tried different ones. No success.

Now I'm stuck. 

I have this printer working fine connected to a Fedora Core 4 computer (I did setup there with the standard graphical printer tool).

Is it worth copying config files from the Fedora machine to the Ubuntu one? Any other clues? I'm happy to supply config files or other information.

Thanks heaps!

hmhmhm

---


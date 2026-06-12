---
title: "USB, Windows95A"
date: 2010-06-18
forum: Virtualisation
---

### Post by col48 on 2010-06-18
Running 8.04 Hardy.
With Windows95A as a virtual machine (VirtualBox).

W95A does not know about USB; unlike later W95 there is no support.
But someone recently said to me, that there must be some software out there....

I'd quite like to access my printer, DVD drive (to read data CDs) and my Zip drive, all of which are USB2 devices known to the host.

Any hope?

---

### Post by TheFu on 2010-06-19
For the printer, certainly.  Connect it to a Linux machine and setup CUPS and/or SAMBA. Samba can provide automatic driver installations for MS-Windows clients and a PDF conversion printer.  CUPS is an easy to use** network print server** that ties into lp to do the actual spooling.

You won't be accessing any USB devices directly from W95. You can access the data via a Linux server that happens to connect to the devices with USB.

BTW, these questions aren't related to virtualization at all. Any Linux machine can share directories or folders or optical devices for read via samba.  Any linux machine can share printers via CUPS over the network too.

---

### Post by col48 on 2010-06-19
Thanks for your encouragement, TheFu.  I can see how it isn't a virtualisation issue, but it looks rather like one in that it's a matter of communication between host and guest.

I *think* my Ubuntu uses CUPS to control the printer already.  I've looked at the Samba site and it looks more complicated than I want to contemplate.  It seems to say that I would need to install a relevant printer driver in W95 so the Ubuntu system (acting as the server) could just pass the print data unchanged to the printer.  I believe this won't do - the printer is too modern for anyone to have provided for W95.

I think I'd need a step-by-step in simpler terms than Samba provides to have any confidence it would work out.

The DVD (reading CDs) and Zip are more important.

---

### Post by new_tolinux on 2010-06-19
About the printer driver: most _HP laser_ printers work on the generic HP Laserjet 4-driver provided that the printer is connected to ubuntu and shared properly. Other brands/inktjets depends.

About the other USB-stuff: I really doubt there's a suitable driver for the VirtualBox hardware. Even if there is, there's probably no Win95 driver for the hardware itself (USB-DVD). Maybe there is an old driver disk around somewhere which makes your ZIP drive work.

---

### Post by TheFu on 2010-06-19
> **col48 said:**
> Thanks for your encouragement, TheFu.  I can see how it isn't a virtualisation issue, but it looks rather like one in that it's a matter of communication between host and guest.

In this situation, you'll be using network communications, not internal VM communications, therefore, the networking needs to be bridged so the client OS can ping the hostOS and send print jobs to it.

If your hostOS is already using CUPS, then you just need to tell CUPS to share the printer on the network. Then tell the W95 client to use the network printer.  If worst comes to worse and W95 printer drivers don't work, you can send generic PCL or generic PostScript or PDF to the CUPS driver and it can print it.  If there's any issue with that, check out Ghostscript translations. On my latest 10.04 install, I don't recall having to do anything special for PDF or PS printing to "just work" besides installing CUPS.

Samba appears complex to the new user because it is very configurable. For a simple setup to share folders, it is really easy. There are many HowTo guides.  Below is a working Samba config. I can not guarantee it is of any use to you or others. Be certain to compare it with the version installed by your package manager and make necessary changes for your situation - the network especially.

[global]
   unix extensions = no
   workgroup = WORKGROUP
   server string = %h server
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes
[homes]
    hosts allow = 127.0.0.1 192.168.1.0/24
    hosts deny = 0.0.0.0/0
   follow symlinks = yes
   wide links = yes
   comment = Home Directories
   browseable = yes
   writable = yes
   create mask = 0644
   directory mask = 0755
   valid users = %S
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

> The DVD (reading CDs) and Zip are more important.To read a DVD/CD, just use the VirtualBox CD/DVD Device settings on the Vbox menu from inside the VM to get access. The menu I mean is the "Machine --- Devices --- Help" menu across the top. 

For the "Zip" - I haven't a clue, but suspect samba is the best way. You might try sharing it via vbox folder sharing.

Good luck. This stuff isn't very hard and you'll see that once it works for you too.

---


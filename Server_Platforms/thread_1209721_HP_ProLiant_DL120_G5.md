---
title: "HP ProLiant DL120 G5"
date: 2009-07-10
forum: Server Platforms
---

### Post by deejross on 2009-07-10
We are about to purchase two HP ProLiant DL120 G5 servers to use as file servers. We plan to run Ubuntu Server on them and run SAMBA. Is there anything I should know about this hardware that might be a problem? Will I need any special drivers or anything, or should Ubuntu run out-of-the-box?

I tried Googling, but there are virtually no pages with "ubuntu" and "ProLiant DL120" on them together.

And while I'm asking, is eBox the best way to configure a server for file sharing?

---

### Post by windependence on 2009-07-10
Linux != Windoze. Drivers are built into the kernel. I have two ML115 G5 servers I'm about to load VMware ESXi on and then Ubuuntu 8.04 LTS with Zimbra. I don't anticipate any problems. HP supports Red Hat, SuSE and some others on that server. They all have the same basic kernel so I can't see that you will have any problems.

The BEST way to configure file sharing is nano plus a bit of editing. ;-)

-Tim

---

### Post by Wim Sturkenboom on 2009-07-11
Maybe it will give you some confidence that Ubuntu 6.06 server installed without a hitch on a DL380. 

I did throw it off after that because applications that I consider crucial for my use were not available by default and on a box without internet connection that is a problem.

---

### Post by deejross on 2009-07-11
Thanks for the input. Glad to know that Ubuntu supports the hardware. As for nano, I like it, but I don't know enough about Samba to be doing it by hand. I tried it a couple times before and totally screwed it up. That's why a GUI of some sort is a good thing for a complicated piece of software such as Samba ;)

---

### Post by Lem on 2009-07-24
I have 5 DL120s used for vmware, firebird servers and file sharing. All run Ubuntu 8.04 without a hitch.

For setting up the server easily use ebox (8.04 only without extra work) or use webmin (a bit more complicated but generally installs on anything), or give ebox's own iso (with 8.04 built-in) a whizz.

I've not tried the last option, but I'm about to build up a new server with it.

---

### Post by deejross on 2009-07-24
Glad to know that it's working out well for you. It's also good to know that eBox works well for you as well, as this seems to be the only thing that can be used for system management without breaking the system (like Webmin does).

---

### Post by rubenlindgren on 2010-05-03
Hi
I have an HP ProLiant DL120 G5 Server with Integrated Intel ® 82801IR Serial ATA Host Controller who can not find the disk during the installation. 

It should be noted this is the first time I install ubuntu with RAID.

If 2 identical HP drives, set up with RAID Bios, but would not identify the installation of any version of ubuntu. (Have tried with 9.10 and 10.04)

Look at my attachments - Printscreen's..

Any tips / suggestions on what might be wrong? Not supported hardware raid?

Thanks for all help

---

### Post by deejross on 2010-05-03
@rubenlindgren:

This is a year old, dead thread about general questions for future plans. You are asking for technical support. Please create a new thread for your issue.

---


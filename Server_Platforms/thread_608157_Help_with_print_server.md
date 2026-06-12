---
title: "Help with print server"
date: 2007-11-09
forum: Server Platforms
---

### Post by xyvian on 2007-11-09
To begin, I am not the most fluent with linux, so please bear with me.

Ok, so I recently install ubuntu server 7.10, and after hours of blundering I have finally set up file sharing over samba just the way I want it. the next on my agenda is to connect my HP PSC 1315 to it so i can print from my XP machines.

I have been using Webmin, and I have been through their walkthrough but I still can't seem to work it. So is there a command i can run to find out if the server detects the printer for one, and has assigned drivers for two? Are these drivers available on ubuntu and even more specifically ubunter server?

thanks for any help :)

---

### Post by xyvian on 2007-11-10
ok, so I seemed to have fell upon CUPS and a walkthrough for that, which was wonderful. I have added my printer, and even gotten it to print a test page. So next I attempted to print a test page from microsoft word. I realized I had to add the printer to my list, so I go to add printers, locate my HP on the server, it prompts me to install a driver, I say Ok and it says that the driver installed is incorrect.

HP PSC 1310 Foomatic/hpijs (recommended)     is the driver I am using on the server.

hp:/usb/psc_1310_series?serial=CN43O151F2O2  is the default URI it gave me and seemed to work.

so i go through the list of drivers Windows gives me and my printer isn't there. I have installed it on this system, which is strange. So I tell it to look in the CD but I do not know where in the CD the driver would be.

if any more information is needed that is relevent please let me know. Thanks in advance.

---

### Post by MJN on 2007-11-10
This is a Windows issue. I'm surprised that as the printer has already been installed the driver is not still present on the system - XP is usually quite good for that sort of thing.

It should be fairly self-explanatory where on the CD the driver is, if not then download one from HP. You're probably better off doing this anyway as it'll likely be a newer version than that on the original CD.

Mathew

---

### Post by xyvian on 2007-11-11
Ok, so I solved the problem, but I had to make a kind of workaround. So when it tells me that the driver that is installed is incorrect and whether I wanted to install a driver from a list, I said yes. In the list I selected the driver "HP PSC 950" which is far to old to work with my printer. 

I then accessed the printer, which in my case was \\server\HP and I hit properties. Under the advanced tab I could then select the driver "hp psc 1310 series". It complained about the wrong driver still, but I ignored it. I have printed both text and photos since then.

I actually would not have had this idea were it not for you, MJN. I give you my thanks.

And I hope this helps people in the future who have the same issue I did. :)

---


---
title: "Need Ideas - Cool Network Projects"
date: 2008-09-14
forum: The Cafe
---

### Post by MaindotC on 2008-09-14
I'm in my final networking class for my degree and I'd like some suggestions for demonstrating some cool projects that a network or system administrator would encounter.  We have a set of base projects that must be completed (the minimum):

Part I: Core network, 2 routers, 2 switches, DNS, DHCP, Firewall (PIX), VPN, intranet

Part II: Blackberry server, voip, email, print service, captive portal, wireless w/ 802.1x, net admin website

Part III:  distribute software w/ group policy, automatic updates, linux clients into AD using LDAP

Part IV: LAN traffic analysis, WAN analysis, configure network attached storage, Backup Exec, IDS, IPS, Virus Detection System, ticketing service, and disaster recovery from DRPlan.

So I'm looking for some ideas - something to wow the classmates and professor.  One thing I've never done is set up an image server that sends an image to a node via PXE and I've already learned how to do that with Windows Deployment Services.  Is there anything you'd suggest that based on what I've typed I should be able to implement?  We have loads of equipment on which to practise - plenty of routers and switches to add additional networks - and lab machines to install and use as we please.

Even if you suggest an uncommon method of implementing a simple service or an expansion upon something I've already typed - that's perfectly fine.  Suggest away.  Thanks!

---

### Post by MaindotC on 2008-09-15
bum p

---

### Post by pp. on 2008-09-15
Terminal server serving Linux or Windows applications to thin clients

---

### Post by mips on 2008-09-15
Are the base projects part of what you are trying to do or are you looking at something additional to that? A bit confused here.

---

### Post by MaindotC on 2008-09-15
The base projects are what I'm doing to meet the requirements of the course.  My team pretty much already knows how to do them.  I'm looking for someting additional - something sexy - to show the others :)

---

### Post by mips on 2008-09-15
How about something like a streaming audio/video server utilising mulitcast or something like that.

I'm struggling to think of ideas here...

---

### Post by MaindotC on 2008-09-15
That's a good idea that I didn't even consider!  I can definitely set up some streaming media of like tutorials that users can watch in the event of assistance (instead of calling the helpdesk).  I could even set up a skype server or other type of voice/video/data for communication.  I was going to set up Asterisk but why not go the full 9 yards and put in video as well :)  Only thing is I'll have to buy some webcams...

---

### Post by mips on 2008-09-15
> **strAlan said:**
>  Only thing is I'll have to buy some webcams...

Just make sure they are well supported by linux ;)

---

### Post by MaindotC on 2008-09-15
Forget linux - usually don't have any problems there - it's Vista clients that I should be concerned with.  Probably going to need some new updated drivers that I can't understand how they work because the code is closed-source and diassembly is meaningless to me at this point.

---

### Post by MaindotC on 2008-09-23
Any other ideas anyone?  Tell me this - what does your helpdesk or IT office not provide that you'd really like to see?

---

### Post by MaindotC on 2008-09-27
I've been looking at setting up an image server for clients to automatically install an image on a "virgin" PC using FAI.  Is there a way to allow the user of the virgin PC to select which packages to install before the image is deployed?

---

### Post by ValiumMm on 2010-02-17
I no this is late, but wondering OP, what you eventually decided to do. Im in the same situation at the moment and need  a good idea, is their anything you thought of later or anyone can think of now, sorry to hijack thread :P but its kinda on same topic :D

---

### Post by Richard1979 on 2010-02-17
You could try something like this.

I once had to set up a multi-user fax system in a call centre so what I did was hook up a bunch of modems to a PC running Windows 2000 (one will do in your case) and have it answer incoming faxes and dump the .tif files into a folder.
Then a Scheduled Task would run with would resize all of the images by using Irfanview on the command line, convert them to JPG and upload them to a "new" folder on the webserver.
From this, I ran a heavily modified PHP image gallery script so the call centre agents would be able to view the new faxes over the intranet.
They could also move faxes to other folders such as "queried" and "completed" when they were done with them.
Sure it was incoming-faxes only but they didn't need to send, only receive.

The system worked beautifully and it was a lot of fun to do.

---

### Post by firefly2442 on 2010-02-17
How about programming a distributed rendering system for Blender?

[http://www.blender.org/](http://www.blender.org/)

---


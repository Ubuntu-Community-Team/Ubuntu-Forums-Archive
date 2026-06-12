---
title: "rogue Ativirus 2009  in Ubuntu ?"
date: 2008-11-09
forum: Security
---

### Post by UbuntuNerd on 2008-11-09
Hi anybody out there I have a home network of 4 pc's two Ubuntu desktop 8.4 and 8.10 also an Ubuntu server and a windows vista. Yesterday after my girl got off the vista machine I saw a virus pop up call "antivirus 2009" and immediately started to install itself, I stopped it before it could finish and removed it after researching online how to get rid of it. This morning I got on Ubuntu 8.4 and the same thing pop up only it was only a message saying your computer was infected with spyware please download "antivirus 2009" only it didn't try to install itself, also in this machine I run Virtualbox with xp and when I open it the virus also pop up but avg detected it and remove it but some how I don't think is gone.
My question is do I have to worry that this crap is going to spread to all my computers especially the server also is this going to affect the Ubuntu boxes in any way and Im wondering if it has something to do with firefox also how do I check Ubuntu for spyware? 

any ideas will be much appreciated thanks !!!

Ps: all the linux boxes are working fine I scanned with clam antivirus and checked for rootkits

virus screenshot:

---

### Post by handydan918 on 2008-11-09
You have little to fear from any virus ever recorded on a Linux machine. They simply cannot get past the Unix permissions model and either replicate or execute. So you may have a virus on you Ubu box, but it will just sit there, much like a kangaroo on the moon. 
you know, less gravity, but no oxygen...

---

### Post by a2lkulkarni on 2008-11-09
Rest assured! It won't impact your either server machine or any other ubuntu boxes. No antivirus is required for any of the linux falvors AFAIK, though there VERY FEW available in the market.

---

### Post by UbuntuNerd on 2008-11-09
I hate the thought of having a virus just floating around and this makes me wonder if there is any chance it could spread back into my vista box?

---

### Post by FreewheelinFrank on 2008-11-09
The scam works by showing you a fake 'virus scan' web page, usually from a hacked web site. This is what you probably saw on the Ubuntu box. How do the Ubuntu boxes connect to the internet? Check DNS settings haven't been hijacked on the router or gateway computer.

---

### Post by Skripka on 2008-11-09
"Antivirus 2009" is one of the more ugly and virulent malwares out there....I'd be worried too about a windows box, until you know you nuked the bug.  The Linux boxes you don't have to worry about hurting (they can onyl carry the bug and maybe pass it on, not get taken out by it), but who's to say if any bug they carry couldn't take out your Windows box?

---

### Post by UbuntuNerd on 2008-11-09
they're all connected by wired and they access the internet via a linksys router how do I check to see if my router go hijacked?

---

### Post by UbuntuNerd on 2008-11-09
Skripka I think you have a point and that was my worry was if the virus just hangs in the ubuntu boxes I believe there is a chance that it could spread back into the vista machine or the xp that I run in virtualbox.

---

### Post by Skripka on 2008-11-09
> **UbuntuNerd said:**
> they're all connected by wired and they access the internet via a linksys router how do I check to see if my router go hijacked?

Go into your router settings, also check your mahcine settings to make sure they aren't doing anything goofy DNS wise, and see what DNS servers it calls.  I use OpenDNS:

[http://208.67.219.60/](http://208.67.219.60/)

For all my DNS.

---

### Post by Skripka on 2008-11-09
> **UbuntuNerd said:**
> Skripka I think you have a point and that was my worry was if the virus just hangs in the ubuntu boxes I believe there is a chance that it could spread back into the vista machine or the xp that I run in virtualbox.

It is rather unlikely, as for windows to get effected, t would need to call the *Buntu box on the same port, and that same port would need to be open on both ends, and whatever anti-virus/firewall etc on both ends would need to allow it.  It is rather unlikey.


I had an executable I ran under Wine that was infected with AntiVirus 2009, I didn't know it and it ran fairly well, albeit buggy (I figure it was Wine).  I was in a hurry and once ran the same .EXE on my When-All-Else-Fails-And-You-Need-A-Real-Windows-OS-drive....well it wasn't pretty.  Antivirus 2009 killed Windows into bluescreen in less than 5 minutes:shock::shock::shock:

---

### Post by cariboo on 2008-11-09
You have to be able to run the executeable in oder for it to spread itself. If it is just sitting on the hard drive it can't spread it self. As a test unplug the network cable and try running antivirus2009 and see what happens.

Jim

---

### Post by UbuntuNerd on 2008-11-11
cariboo907 thanks for responding, about the virus I have not seen it pop up anymore since I remove it from my vista machine and I don't think I want to run it, the idea of floating around in my Ubuntu machine is more than enough.

---

### Post by albinootje on 2009-04-25
> **UbuntuNerd said:**
>  This morning I got on Ubuntu 8.4 and the same thing pop up 
Sounds like the DNS-servers you're using have been manipulated.

---

### Post by calebk on 2009-04-25
hmmm,strange

---


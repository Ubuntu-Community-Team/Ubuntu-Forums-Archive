---
title: "Picked up a server, need your help on linux distro"
date: 2008-06-28
forum: Server Platforms
---

### Post by mechanicalmetal on 2008-06-28
Hey guys,

I picked up a compaq proliant 3000 from my job. Kind of an older machine, dual p3 motherboard with 3 raided scscii drives. Has LCD panel and all, pretty nice machine, especially when its free :D!

I am going to add a few controllers and devices and make it regognize some modern harddrives and hardware. I want to use this machine for a data server. I LOVE Ubuntu, but I wanted to get your recommendations on your Linux preference distro that you think will suit my needs best.

Thanks guys,

-Brandon

---

### Post by hyper_ch on 2008-06-28
you don't say what your needs are ;)

---

### Post by mk1w86 on 2008-06-28
My personal preference on servers is Debain because I find it to be very stable and the packages do not change as much as they do in Ubuntu.  

If you do choose Debian use Debian 4.0 (etch) which is the latest stable release.

Although for a file server Ubuntu should be just fine and is mostly similar to Debian.

Also Ubuntu Server 8.04 (the latest release) is an LTS release so it gets updates for the next 5 years on the server version as opposed to the normal 18 months so you will not have to upgrade the OS for a while. :)

---

### Post by mechanicalmetal on 2008-06-28
I was actually thinking of Debian as well. I don't know too much about Ubuntu server edition, all I can remember is installing it on a buddies computer. I know it had NO GUI you installed the OS, but I had to leave and never found out the end results. Im gonna check out Debian though.

Thanks man! 

And all other input is open :D

---

### Post by mechanicalmetal on 2008-06-28
> **hyper_ch said:**
> you don't say what your needs are ;)

Ahh, just a file storage server for personal use. Maybee some FTP access, not quite sure yet. I got this machine thats been sitting for a few days and I wanna do something with it.

---

### Post by hyper_ch on 2008-06-28
debian

---

### Post by |{urse on 2008-06-28
really doesn't matter what distro, it's what software you use.. i guess some distros come preloaded with better security (like selinux (fedora)) so long as iptables is set up correctly, there are security updates in place and you have a decent hardware firewall, you could even run knoppix and it would rock. I personally would use fedora (fc7 or fc8 not 9), but stick with what you are most comfortable with ^^ why not ubuntu? \\:D/

---

### Post by cariboo on 2008-06-28
If you use the minimal install cd, it is the same as the Debian netinst, you can pick what you want to install.

Jim

---

### Post by Lapp-Same on 2008-06-28
Well, it doesen't matter wich distro you are using, Linux are very simple working anyway you can have the server on for years if you want dosen't matter it JUST ******* Works! Thats why noeone use a windows to a server... it would have to being re-startet every freaking day because of a update, or "going it self slow"!

---

### Post by mechanicalmetal on 2008-06-28
> **|{urse said:**
> really doesn't matter what distro, it's what software you use.. i guess some distros come preloaded with better security (like selinux (fedora)) so long as iptables is set up correctly, there are security updates in place and you have a decent hardware firewall, you could even run knoppix and it would rock. I personally would use fedora (fc7 or fc8 not 9), but stick with what you are most comfortable with ^^ why not ubuntu? \\:D/

I don't have beef with Ubuntu, I just want to try something alittle different. I will probably just install Ubuntu Server edition since I have the new distro burned and ready to go :/ How to I load the GUI? I know that is a dumb question, but I never got past installation complete. How do you load gnome, or KDE?

Im still learning Linux. I have actually came a LONNNNNG way in just 4 months, and I am hooked. If I could actually get Ubuntu desktop to get WEP and WPA working for my laptop, I would be in business!!! Once Linux grabs you, its like your hooked, and you never want to go back.

I am really interested in Debian though..... 

I am running an IPCop dedicated firewall for my network right now, and just standard "firestarter" firewall on my desktop, so fill on a good security setup if you want.

Also, the other con I have with Ubuntu, is that I am running 5 computers on a 5 port KVM switch, everythings working flawlessly, but they provide you with NO options to change your resolution, or adjust your screen so that I can see my entire desktop. I am running a 29" flatscreen HDTV for a monitor. 

Thanks all

---

### Post by Lapp-Same on 2008-06-28
> **mechanicalmetal said:**
> I don't have beef with Ubuntu, I just want to try something alittle different. I will probably just install Ubuntu Server edition since I have the new distro burned and ready to go :/ How to I load the GUI? I know that is a dumb question, but I never got past installation complete. How do you load gnome, or KDE?

```
sudo apt-get install ubuntu-desktop
```

---

### Post by windependence on 2008-06-28
Personally I have experience with that box. I have a 3000 and a 4000 in my storage cube if you need parts. :) 

You should load that thing with memory as much as possible. Again, if you need some, PM me. I also have RAID cards for that one.

If it was me, I would NOT run a GUI on that. I would run FreeBSD because it will work well with the older hardware. Linux is gonna be heavy on the 3000 unless you stipr it down and definitely don't run a GUI. You don't need it for what you want to do. 

Debian would be my second choice after FreeBSD or OpenBSD.

-Tim

---

### Post by mechanicalmetal on 2008-06-29
Nice,

went to install Ubuntu Server for my compaq proliant 3000 series, and it cannot detect the CD rom....

With Installation, SWEET

---

### Post by windependence on 2008-06-29
First, you need a copy o smart start 5.5. I have the ISO if you need it and could point you at the file. It is very hard to find on the net. The BIOS in those machines is accessed by loading the bootable Smart Start CD and changing the parameters there. It isn't for the faint of heart, but I can help you get it done. You should do this after you get all your RAID cards installed.

Here is a link to the Smart Start CD:

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=15351&prodSeriesId=254864&prodNameId=257759&swEnvOID=181&swLang=8&mode=2&taskId=135&swItem=MTX-597d7cb6b45d493285e27c1412](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=15351&prodSeriesId=254864&prodNameId=257759&swEnvOID=181&swLang=8&mode=2&taskId=135&swItem=MTX-597d7cb6b45d493285e27c1412)


Here is a link to some other useful downloads:

[http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?lang=en&cc=us&prodNameId=257747&taskId=135&prodTypeId=15351&prodSeriesId=254910&submit.y=0&submit.x=0&lang=en&cc=us](http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?lang=en&cc=us&prodNameId=257747&taskId=135&prodTypeId=15351&prodSeriesId=254910&submit.y=0&submit.x=0&lang=en&cc=us)

If you need any help let me know.

-Tim

---

### Post by hyper_ch on 2008-06-29
you do not want to load a gui on a server.

---

### Post by mechanicalmetal on 2008-06-29
> **windependence said:**
> First, you need a copy o smart start 5.5. I have the ISO if you need it and could point you at the file. It is very hard to find on the net. The BIOS in those machines is accessed by loading the bootable Smart Start CD and changing the parameters there. It isn't for the faint of heart, but I can help you get it done. You should do this after you get all your RAID cards installed.

Here is a link to the Smart Start CD:

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=15351&prodSeriesId=254864&prodNameId=257759&swEnvOID=181&swLang=8&mode=2&taskId=135&swItem=MTX-597d7cb6b45d493285e27c1412](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=15351&prodSeriesId=254864&prodNameId=257759&swEnvOID=181&swLang=8&mode=2&taskId=135&swItem=MTX-597d7cb6b45d493285e27c1412)


Here is a link to some other useful downloads:

[http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?lang=en&cc=us&prodNameId=257747&taskId=135&prodTypeId=15351&prodSeriesId=254910&submit.y=0&submit.x=0&lang=en&cc=us](http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?lang=en&cc=us&prodNameId=257747&taskId=135&prodTypeId=15351&prodSeriesId=254910&submit.y=0&submit.x=0&lang=en&cc=us)

If you need any help let me know.

-Tim


Hey man,

Thanks so much for the info. I actually have all the CDS for this machine. I am going to send you a PM.

---

### Post by mechanicalmetal on 2008-06-29
> **hyper_ch said:**
> you do not want to load a gui on a server.

Ehh? Im a noob man, why wouldn't I want to run a GUI on a server?

---

### Post by jrusso2 on 2008-06-29
Compaq's were great servers but they are very proprietary so I would personally use a distro that has support for the hardware.  I think RedHat probably has the best hardware support for it, but CentOS is free.

---

### Post by hyper_ch on 2008-06-29
> **mechanicalmetal said:**
> Ehh? Im a noob man, why wouldn't I want to run a GUI on a server?

because a gui doesn't help you at all to setup a server ;)

---

### Post by Wharf Rat on 2008-06-29
> **mechanicalmetal said:**
> Ehh? Im a noob man, why wouldn't I want to run a GUI on a server?

I had the bright idea of setting up a GUI on my home server. 
I have three users, and an older Desktop to be used for a home server to house files, shared data, shared printer/scanner.  The machine has plenty of horsepower so having an idle GUI was not a problem.

My idea was not only to have access to the server's printer and data but be able to use the machine for a desktop in the event someone needed to access the net or their files locally.  Sounds like a good idea ---- wrong.

So  far I have manged to bugger up a working shared printer and Samba files to the point you cannot access anything.  My wife is pretty PO'd and keeps reminding me of how nice it was to have a working printer BEFORE I got involved.

FYI- There appears to be a bug in Samba/Hardy with shared folders and Netbios. Or, it could just be my inexperience.  In any event my next attempt will be with Debian.

---

### Post by hyper_ch on 2008-06-29
well, if you want to use the computer also as desktop there speaks nothing against a gui... but if you want to operate a server - then no gui is required and a gui won't help with anything.

---

### Post by john_spiral on 2009-02-01
someone might find this useful:

How to Change the Boot Order on the Compaq ProLiant 3000

   1. Press the "F10" key for System Partition Utilities
   2. Go to: System Partiton Utilities > System Configuration > Power-on Defaults > Set Standard Boot Order
   3. Select the order you want to allow booting from.
   4. After the firmware has been updated and the OS has been installed on the server, then set drive C: as the first device.

got the above from:

[http://adultednyc.info/support/systems.html#compaq](http://adultednyc.info/support/systems.html#compaq)

---

### Post by R.Bucky on 2009-02-01
[DesktopBSD]("http://www.desktopbsd.net/") or [FreeBSD]("http://www.freebsd.org/")

---


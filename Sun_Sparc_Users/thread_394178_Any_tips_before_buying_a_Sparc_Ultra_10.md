---
title: "Any tips before buying a Sparc Ultra 10?"
date: 2007-03-26
forum: Sun Sparc Users
---

### Post by reidms on 2007-03-26
I plan to buy a used Sparc Ultra 10 3D Creator to use for a Linux web server.
(256MB RAM, 333MHz Processor, 9GB Hard Drive)

Since I know nothing about Sparc, do you guys have any tips/advice on buying one?

---

### Post by OnyxOD on 2007-03-26
Ive just started using sparc about 2 months ago, currently I have an Enterprise 450 Server, an ultra 5, 2x ultra 10s and an ultra 60. I am really starting to like these systems, for the reliability (I run a LAMP, DNS, SSH Server on the 450) and easiness of the configuration. If you are a gui type person, I don't recommend having the sparc platform as I think its impossible to install. Make sure you get a keyboard w/ the computer, as its not ps2... unfortunatly I only have one keyboard to use for all of those.. thats where ssh comes in handy.. Don't quote me, but I don't think ubuntu is not compatible with the ultra 10 it kept giving me an illegal instruction error, but I have not tried to install edgy eft only tried dapper on the 10, so you might look into getting a ultra 5. I have not yet installed ubuntu on the ultra 60. but dapper will work on the ultra 5

edit:: Seems there is a way to get graphics on the sparc platform: its been a while since I read this forum heres the link [http://ubuntuforums.org/showthread.php?t=307406](http://ubuntuforums.org/showthread.php?t=307406)

---

### Post by netztier on 2007-03-27
> **reidms said:**
> I plan to buy a used Sparc Ultra 10 3D Creator to use for a Linux web server.
(256MB RAM, 333MHz Processor, 9GB Hard Drive)

Since I know nothing about Sparc, do you guys have any tips/advice on buying one?

One issue that always arises is booting the CD-ROM. If you can, throw an Ubuntu CD into the drive and do a **boot cdrom** at the OBP's **ok>** prompt. To get there, you hit **Stop+A** on the sun keyboard or send a BREAK signal through the console cable during bootup.

Maybe you're lucky and the thing just works. A fallback way is to *netboot* with RARP/BOOTP/TFTP. For that, you need a system you can install these deamons on in your network. There's guides around in this forum about how to netboot a (SPARC) machine.

With that amount of RAM, don't consider running GNOME or KDE. But for a server, you don't actually need it anyway. The X11 issues in Edgy the other poster mentionned are mainly related to the onboard (ATI) graphics chip in U5s and U10s - with the Creator 3D (such as I have in my Ultra 60), there's no such problems. You may have to figure out which graphics card is considered "primary" by the U10's OBP and toggle the setting to get X working, however.

The hint with the keyboard is good, but if no keyboard is connected, the Sun will output it's console to the serial port. You can connect a nullmodem cable to that port and work the console from another system. The setup dialogs might look a bit weird, though ;-) If you do get a keyboard, make sure you configure it as a standard PC104/105 key, *not* as sun type 5. Strange, yes. But correct.


best regards

Marc

---

### Post by OnyxOD on 2007-03-27
What about the Elite 3D? one of the 10s I own is that type.. and the other does not specify so I assume its has the ati chipset. Now, the Ultra 60 does have the Creator 3D.. I'll have to figure out the network booting for it does not have a CD drive.

---

### Post by netztier on 2007-03-27
> **OnyxOD said:**
> What about the Elite 3D? one of the 10s I own is that type.. and the other does not specify so I assume its has the ati chipset.

There was a thread only a few days ago about the Elite3D: [Ultra 60 Elite3D xorg problem]("http://www.ubuntuforums.org/showthread.php?t=383785"). You didn't even need to use the search function, the thread was **four** entries before this one. And had you used the search function, you'd certainly have found that **afbinit** is the software package you're most probably looking for when running a Elite 3D card.

Elite 3D and Creator 3D are UPA cards and optional in the Ultra 10. The onboard graphics chip is ATI based.

best regards

Marc

---

### Post by reidms on 2007-03-27
Thanks for the replys guys- That ultra 10 sold for about $120(with shipping)- so I did not buy(I personally think that is too much for that Ultra 10)

I am now thinking about buying an Ultra 5 locally with these specs-

360 Mhz Sparc II
256mb RAM(I may upgrade)
8gb HD
NIC
CDROM
Floppy
Sun keyboard, mouse, and monitor

Does that seem good?  As I said before all I want to do is run a small Linux web server


Also, since I want one as a server- should I be looking for server models- or will the workstations work fine?

I am eager to get into the Sparc architecture!!!

---

### Post by reidms on 2007-03-27
I ended up paying 70 USD for the Ultra 5 described above- That seem about the right price?

Also- would you reccomend updating openboot?  The version on it is 3.11(I heard you have to install solaris to do that)

---

### Post by netztier on 2007-03-28
> **reidms said:**
> I ended up paying 70 USD for the Ultra 5 described above- That seem about the right price?

Hm, not too bad. I used to pay CHF 150 for all my U2s and U60s here. But if your price actually included a monitor, it's perfect.

> **reidms said:**
> Also- would you reccomend updating openboot?  The version on it is 3.11(I heard you have to install solaris to do that)

Check first what is installed. If some Solaris version is on it, upgrade the OBP at once. Last available for the U5 is 3.25, if I am not mistaken. Installing a minimal Solaris is easy, you can download the .iso from sun and do a minimal installation, then ftp the package from another host in your subnet.

For a server install, a Sun keyboard is good. But with U5s and 10s, you don't actually need a Sun monitor. They don't have the 13W3 connectors, but normal D-SUB 15 outlets vor VGA. Almost any normal PC monitor should work here, as long as it's able to display Sun's default resolution of 1152x900 .. or was it 1152x876? ehm... :confused: 

An since Server installs are text-only and don't have X.org, you don't actually need a mouse. Once the Box runs, you very probably won't even need a screen anymore. 

Oh - and make sure you have enough RAM. The more, the better. Modules should be available on ebay.

best regards

Marc

---

### Post by reidms on 2007-03-28
It turns out that the guy was out of Sun monitors :/.  But I do not have to pay for shipping(no worry of it being DOA either)



The seller has a form of Fedora Core 3 installed along with X.

> then ftp the package from another host in your subnet.

What do you mean by this?

> Oh - and make sure you have enough RAM. The more, the better. Modules should be available on ebay.

Think I should upgrade the current amount of RAM(256mb current) for a low traffic(100 hits in a day would be high- 10 hits would be low) web server?
If so- does this seem like a good deal?```
http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=170086489289
```
(2x128MB sticks including shipping for 16USD or 19.46CHF)

---

### Post by netztier on 2007-03-28
> What do you mean by this?

If I remember correctly, the file you need is an executable, and needs to be in the root directory of the Solaris partition you boot from. From the **ok>** prompt, you'll upgrade with boot **disk :<upgrade-program>** (or similar). There's been a very long thread about OPB upgrades in this forum, with links to Sun's documentation web sites, you'll find the details there

What I meant is this: install a minimal Solaris to the disk, then somehow make sure that the file finds it's way to the / directory. Getting it via ftp from another computer in your LAN is one possible way. Copying via Floppy or CD-ROM is of course possible, but alway depends on hardware availability. Sorry for having been so short ;-)

> Think I should upgrade the current amount of RAM(256mb current) for a low traffic(100 hits in a day would be high- 10 hits would be low) web server?


Well, you have a web server up and running - and then you get the hang of it, add mail services and a MySQL backend, some server-side processing and while you're at it ... etc. You get the picture, don't you? ;-)

> If so- does this seem like a good deal?```
http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=170086489289
```
(2x128MB sticks including shipping for 16USD or 19.46CHF)

Wow! USD 10.- for 256MByte of RAM? Well, I paid considerably more for my upgrade to 512MByte RAM. Ok, that was with cross-atlantic P&P ;-)


best regards

Marc

---

### Post by reidms on 2007-03-28
Thanks mate for the help!


I have read documentation on updating openboot.


Do you think this is dangerous?(I have never used Sun hardware before)

---


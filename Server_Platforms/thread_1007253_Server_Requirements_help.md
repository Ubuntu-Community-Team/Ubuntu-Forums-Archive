---
title: "Server Requirements help"
date: 2008-12-10
forum: Server Platforms
---

### Post by neomaximus2k on 2008-12-10
hey peeps, I am looking to setup a home server and at the moment linux would be the cheaper option.

First of all network background, I have an N range router (wireless) running 3 PC Systems, 3 laptops and 1 notebook.

2 of the pcs are wired, one is wireless, the laptops are all wireless running XP (same with pcs) and notebook is an Acer Aspire One so running Linpus

Also have an Xbox 360 on the network

What I wanted is to setup a central server to make my life easier, I work at various locations and always have to dial in to home (Real VNC used) to my machine there to grab files and so on.

What I want to be able to do is share files and folders over the network (SAMBA i beleive) share a USB printer across the network, run an Apache, MySQL, PhP development enviroment (this isn't an issue I set these up all the time)

But then what I also need to be able to do is to dial in to the server in some form and access other machines on the network for desktop sharing (I check emails this way while out of the office)

Stream + transcode video files to my Xbox 360 (Twonkyserver i beleive) 

I think thats about it, I would like to use something similar to Microsoft Exchange but unsure how that would work.

So what i need to know is how would I go about doing this mammoth task and what spec system would I need?  I was thinking of ditching the laptop as I have the notebook and use that (Dell D600 2Ghz processor with 2Gb ram)

Once I have the answer I am then looking at putting a tutorial online for it!

Oh forgot to add should I run ubunto in text / shell mode or gui?

Any help is greatly received.

---

### Post by hyper_ch on 2008-12-10
(1) samba is quite simple... stormbringer or a nickname like that has written a wonderful howto on that in the tutorials section

(2) is it just one webpage you want to host or multiple? If it's just one, then
```

sudo taskel

```
and selecting lamp there should be fine.

(3) the rest - no clue :)

---

### Post by neomaximus2k on 2008-12-10
would be multiple sites not just singular (would be used as a development platform as i'm a website developer and internet applications developer)

---

### Post by hyper_ch on 2008-12-10
Then I'd suggest you set the computer up according to the Perfect Howtos to be found on [http://www.howtoforge.com](http://www.howtoforge.com)

That will install a full-lamp enviornment and you can also add a free "isp" management tool called ISPConfig.

---

### Post by neomaximus2k on 2008-12-10
thanks for the link, the configuration of virtual hosts and apache isn't a problem as I have experience in this already, what Spec would people recommend for a home server tho?  I was geared towards 2Ghz processor with 2Gb ram (PC World business have a decent G5 server at £219 + VAT for this spec)

Also would people recommend sticking to the GUI version or just installing the CLI (Comand Line Interface) version

---

### Post by hyper_ch on 2008-12-10
if you want to operate it as server, use a cli...

---

### Post by neomaximus2k on 2008-12-11
Yeah and since i'm no stranger to CLI would be better for me :)

I'm toying with the idea of getting a HP ProLiant ML115 G5 Server
2Gb DDR2 SDRAM - Advanced ECC - 800 MHz - PC2-6400
1 x 250Gb SATA Drive (I have a 1Tb drive SATA II that will go in here as well)
1 x Third-Generation Opteron 1352 / 2.1 GHz ( Quad-Core )
1 x DVDRW
6 x USB Connectors
1 x Serial ATA Controller 4 channel supports RAID 0, RAID 1, RAID 5, RAID 10

Its prob a little overkill but my one pc at present acts as a server as such (running vista bah) and thats a 4.8 with 4Gb RAM and that struggles sometimes :(

---

### Post by hyper_ch on 2008-12-11
well, it is overkill... but you don't really get much lower specs anymore.

I mean the price addition of 2gb compared to 1 gb is close to 0.-

the 250gb drives seem to be low though... you can still buy that. the last time I checked there wasn't anything offered below 500gb anymore.

ok, the cpu is huge... dual core would be cheaper ;)

why not use software-raid?

---

### Post by neomaximus2k on 2008-12-11
well i chose this one as its only £169+vat (194.35 inc vat) and its the cheapest there is :)

---

### Post by Iowan on 2008-12-11
> **neomaximus2k said:**
> Also would people recommend sticking to the GUI version or just installing the CLI (Comand Line Interface) versionIf you install the server version, you're gonna get the CLI version.  If you *want* a GUI, it can be added afterwards.

---

### Post by gtdaqua on 2008-12-12
> **neomaximus2k said:**
> thanks for the link, the configuration of virtual hosts and apache isn't a problem as I have experience in this already, what Spec would people recommend for a home server tho?  I was geared towards 2Ghz processor with 2Gb ram (PC World business have a decent G5 server at £219 + VAT for this spec)

Also would people recommend sticking to the GUI version or just installing the CLI (Comand Line Interface) version

How can a GUI make a difference in administering a server? You still would be using the terminal or the Konsole to administer it.

---

### Post by neomaximus2k on 2008-12-17
In some cases a GUI would make things clearer / easier.  There are advantages to using the gui over cli however you would loose memory and cpu resources thats why 99% of servers stick with CLI

---

### Post by hyper_ch on 2008-12-17
in what case would a gui make things clearer?

---

### Post by Ferret-Simpson on 2008-12-20
The GUI would allow you to manage your network settings, that's about it.

A WEB CONTROL panel is hosted over a web server and gives Server application control, lessening use of the terminal. Gnome/XCE/KDE etc are about as useful as a rotten turnip.

---

### Post by neomaximus2k on 2008-12-22
lol well sadly there are some pieces of software i use (newsleecher) that I cant find linux alternatives to so the GUI would have to be installed in my case but the hole purpose of a GUI IS to make things easier and shorter to do, just by saying it isn't doesn't make it so, of course this isn't always the case but the purpose of a GUI is to make it easier to maintain.

---


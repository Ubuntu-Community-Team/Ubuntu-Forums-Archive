---
title: "what should I do w/ my late P2/early P3 PC w/ 64MB of RAM?"
date: 2007-04-07
forum: The Cafe
---

### Post by billdotson on 2007-04-07
Well, I built my own PC a few months ago and since then have gotten really interested in computers.. mainly after I started using Linux :) , and anyway the other day I found a an old AOpen PC with 64MB of RAM and a late P2/ early P3 processor.  I don't even know what the HDD is (in terms of space).  I tried booting from the xubuntu LiveCD and it would not boot.  I have a Windows 95 CD upstairs but it would not boot it as it said that there were "no system files found- cannot boot."  When I got it apparently what was installed on it was ruined or there just isn't an OS on it.  

I was wondering what could I do with such an old machine to make it at least a little bit useful?  I put a 10/100 Mbps ethernet card in there and hooked it up to the wireless router. 

I would at least like to have it so it can run a GUI web browser if nothing else.  Maybe I can install puppy linux to the HDD so that the RAM can actually be used for programs instead of the OS.  

I was also thinking that I could possibly set it up as FTP server (I am assuming it would have to be command line) and hook it up to my PC through ethernet.  Then I (being hopeful) could hook up my external HDD to it and then use ghost for unix to clone some of my partitions and send it to the external HDD.  

Although I do not know if I am shooting in the dark, I would like to make some use of it as I spent about an hour digging it out of a storage closet.  

Also, would there be any other "cool" things I could do w/ it?  By cool I mean something Linux-related, something that would be a learning experience, or both.

---

### Post by solar george on 2007-04-07
I would suggest that you use [Debian Linux]("http://www.debian.org") on that machine.

---

### Post by billdotson on 2007-04-07
are any of the things I mentioned going to be possibilities?

---

### Post by Mathiasdm on 2007-04-07
> **billdotson said:**
> Well, I built my own PC a few months ago and since then have gotten really interested in computers.. mainly after I started using Linux :) , and anyway the other day I found a an old AOpen PC with 64MB of RAM and a late P2/ early P3 processor.  I don't even know what the HDD is (in terms of space).  I tried booting from the xubuntu LiveCD and it would not boot.  I have a Windows 95 CD upstairs but it would not boot it as it said that there were "no system files found- cannot boot."  When I got it apparently what was installed on it was ruined or there just isn't an OS on it.  

I was wondering what could I do with such an old machine to make it at least a little bit useful?  I put a 10/100 Mbps ethernet card in there and hooked it up to the wireless router. 

I would at least like to have it so it can run a GUI web browser if nothing else.  Maybe I can install puppy linux to the HDD so that the RAM can actually be used for programs instead of the OS.  

I was also thinking that I could possibly set it up as FTP server (I am assuming it would have to be command line) and hook it up to my PC through ethernet.  Then I (being hopeful) could hook up my external HDD to it and then use ghost for unix to clone some of my partitions and send it to the external HDD.  

Although I do not know if I am shooting in the dark, I would like to make some use of it as I spent about an hour digging it out of a storage closet.  

Also, would there be any other "cool" things I could do w/ it?  By cool I mean something Linux-related, something that would be a learning experience, or both.

Puppy Linux should run fine on that (I had a P2 with 64MB RAM, but it died :( ).
Other options are Damn Small Linux or one of the other small distributions.

I would actually advise Debian Linux or Ubuntu Server, with Fluxbox.
Possibilities:
-Fluxbox as a Window Manager will run fast enough. As a web browser, you can use Dillo (it's much more lightweight than Firefox, but has less options).
-SVN server
-FTP server
-MP3 server
-VOIP server

Just experiment:)

---

### Post by billdotson on 2007-04-07
so I could use ethernet to connect to the internet with that old box?  Could I use it as an FTP server so that I could hook up my USB external HDD to it and send my disk images to it using ghost 4 unix?

I do not know to set up any of those things- fluxbox, e17, FTP server, any type of server as I have never had another PC to do so.. could someone "show" me how or direct me to some simple tutorials?  

I know I am not going to be running Firefox or some hardware intensive program like Photoshop or something but I would like to at least do something cool w/ it

---

### Post by Compucore on 2007-04-07
Have you gone into the BIOS to see if it can detect the hard drive itself. If it is slightly larger than 6 gigs itself. I would probably put in hoarty hedgehofg in it. I still have an older version of Ubtuntu n hand here for such an ocassion for a system like that. I had to do it for a Aptiva from IBM over here then upgrade it to at least breezy badger over here. And tweak the menu list to irqpoll for the AMD K6-2 400 I think that is what is running inside the machine itself. Or just go to freecycle.org and make a request for some extra ram for it and just bump it up sightly on the machine itself and run a flavou of ubuntu on it. But that is just me over here. 

Compucore

---

### Post by billdotson on 2007-04-07
I think it is an AMD 333MHz processor, with an ISA soundcard and 64MB of RAM.  I am currently connecting to the internet on it with the latest version of Puppy Linux.  It only has 4GB total.  I set 1GB of an ext2fs for puppy (in case I want to put a bunch of apps on it) 150MB for swap, and left the remainder be a fat32 partition.

I am thinking of setting up an FTP server if it is possible.

Right now I am trying to get ALSA to detect the ISA sound card that is in it.  Hopefully it will work.

Hmm, on [http://www.memoryx.net/pc100memory.html]("http://www.memoryx.net/pc100memory.html")

PC100 memory is a mere $7 for 32MB and only $15 for 64.  I think my AOpen MB in that box has 4 RAM slots as it is.  Maybe I could make it a 128MB box, and possibly get a "newer" processor.  I am sure a processor for it wouldn't be expensive.

---

### Post by xdarkxanarchyx on 2007-04-07
Maybe you could by a video card or an adapter and hook it up to your TV and use it to watch some movies or something on? Or even set it up and have it just to download stuff on instead of having downloads from multiple computers, my old roomate and I did something like that. with Ubuntu 6.10 and Windows 2003 Server and rdesktop annnnnd I forgot the other app at the moment. Our internet speeds were horrible, this slightly fixed it. We also had bougth an external case for a regular IDE HDD.
Just some ideas.
 I have a computer similar to that one but no case for it so i can't do anything :(

---

### Post by xdarkxanarchyx on 2007-04-07
[www.newegg.com](www.newegg.com) has 128MB PC100 RAM is your mobo supports it for only $17.

---

### Post by SlayerMan on 2007-04-09
Put e.g. Puppy Linux on it and use it as a surf station.

---


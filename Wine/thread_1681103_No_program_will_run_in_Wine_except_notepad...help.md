---
title: "No program will run in Wine except notepad...help?"
date: 2011-02-03
forum: Wine
---

### Post by auzzie2112 on 2011-02-03
I'm fairly new to linux and just installed because i would like to join the linux community but am having trouble with wine.
 
I installed Wine using the Synaptic Package Manager and everything went smoothly but now when i try and run any .exe except notepad.exe nothing works. iexplore.exe opens up but hangs and never completely finishes loading. utorrent.exe simply does nothing.... although if i go to System Monitor and check the processes it says utorrent.exe is "sleeping" and using the majority of my CPU.
 
PLEASE HELP!!!
 
Thanks

---

### Post by cogadh on 2011-02-03
Did you actually install the applications in Wine or are you trying to run them from an existing Windows installation? Have you checked [Wine's Application Database]("http://appdb.winehq.org/") to see if they work in Wine (I can tell you Internet Explorer does not)?

---

### Post by auzzie2112 on 2011-02-03
well i guess where i'm going wrong is i dont know how to install them in Wine. What i would like to install is utorrent.exe and all i do is check the box in properties allowing to run as an executable and then open the .exe.
 
iexplore came in the program files folder when i installed Wine. 
 
How do i install them in Wine?

---

### Post by cogadh on 2011-02-03
All you need to do to install applications in Wine is run the application's installer, just like you would in Windows. You may need to mark the installer as executable first, but you seem to have already figured that one out.

The iexplore that comes with Wine is not really Internet Explorer, its really just there to "trick" applications that require IE into thinking it is actually there. You can use it as a semi-functional browser by opening a terminal and running "wine iexplore"

---

### Post by auzzie2112 on 2011-02-03
Ok that makes sense. Thanks. Ill go check that the site you linked me to for compatibility with utorrent.exe because after i double-click on the installer it does nothing but still shows the process as sleeping.
 
Thanks.

---

### Post by ronnielsen1 on 2011-02-03
There are plenty of torrent packages in  linux to not need to run utorrent in wine. There's  ktorrent, deluge,  &

[LIST]
[*][ABC]("http://pingpong-abc.sourceforge.net/") (Open source)
[*][BitBuddy]("http://www.softpedia.com/get/Internet/File-Sharing/BitBuddy.shtml") (freeware)
[*][BitSpirit]("http://www.bitspirit.cc/en/")  (down atm)
[*][BitTornado]("http://www.bittornado.com/") (Open Source, one  torrent per window)
[*][gTorrent]("http://sourceforge.net/projects/gtktorrent/") (Open Source, [[COLOR=#0072bc][COLOR=#0072BC ! important][FONT=inherit ! important][COLOR=#0072BC ! important][FONT=inherit ! important]Linux[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.ghacks.net/2007/02/20/alternatives-to-utorrent/#"))
[*][Halite]("http://www.binarynotions.com/") (still in early development, Open Source)
[*][XBT]("http://xbtt.sourceforge.net/client/")
[/LIST]
just to name a few

---

### Post by auzzie2112 on 2011-02-04
Thanks that helps. utorrent was probably the only thing i was going to use in wine. lol

---


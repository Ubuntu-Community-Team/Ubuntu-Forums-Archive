---
title: "My dad gives Ubuntu 6.06 a try!"
date: 2006-07-15
forum: The Cafe
---

### Post by PryGuy on 2006-07-15
Hello everybody!
I will tell you how my dad has given Ubuntu 6.06 a try today and what he loved most about it:

The story began in the morning when I came to my dad's room to try out how Ubuntu 6.06 will work on my dad's computer hardware. I didn't even want to convince my dad of giving Ubuntu a try or something I just wanted to test how it'll work on his PC. If there's an end-user on Earth-that's my dad without any doubt. :) I was absolutely confident that one shouldn't even start trying confessing him in Linux superiority. He surfs the net a little (Firefox), listens to music a lot (iTunes) and translates scientific articles (many Windows based dictionaries and Word). So I gained access to his computer, put the Ubuntu CD into drive and started booting into Live session. But soon I've noticed that my dad watches all my actions carefully. He knew about Ubuntu a little 'cause I've been telling him about it earlier, but I really couldn't expect such interest. "What are you doing?" he asked. "I'm going to test how Ubuntu works with your computer hardware" was the answer. One of the main reasons was will the Ubuntu 6.06 detect his [AudioTrak Prodigy 7.1 sound card]("http://www.audiotrak.net/prodigy71.htm") properly 'cause one of the prevoius Ubuntu versions couldn't do it. It's a semi-professional sound card by the way. 

So I froze listening to the sounds going from the speakers as the Live CD booted into graphics. And I heared them! Yet it seemed to me that the sounds are deeper and clearer than in Windows. But I thought that I was wrong about that and father was not in the room at the moment so I couldn't ask him.

I've been playing with Ubuntu Live session as my dad came back. "Is there anything similar to calculator?" he asked. "Yes, of course!" I answered and launched calculator for him and switched it into a scientific view. I knew he was not satisfied with it's analogue in Windows so i hoped that he would like it. And he did! "Do you want me to install it on your hard disk permanently?" I asked jokingly. "Yes, why not!" he answered. So I did.:) The installation went smooth as usual so I will not go into details about it. 

I have configured Ubuntu after the installation and started showing it to my dad. He was very familiar with Firefox so it was not a problem for him. Next thing was Rythmbox, "The Ubuntu iTunes". I have shown to the Rythmbox a folder where all the MP3s were (over 20Gb of music, classics mostly) and we started listening to the music. And suddenly after the first seconds of listening my dad said: "The sound got better!". And that was true, the Prodogy 7.1 Ubuntu drivers really sounded better; the sound was deeper, brighter and you could hear more details. That was hard to believe, Open Source drivers sound way better than the native commercial AudioTrak Windows drivers! Then there were Joan Baez, Pink Floyd... The sound was really better!!!

I also shown him OpenOffice and opened one of the documents from the NTFS partition that Ubuntu mounted during the install process. He was really fond about it!

So my father loved Ubuntu, it's really hard to believe that! There's only one thing that stopped him from making a switch. He has so many dictionaries that run under Windows. :(

---

### Post by mips on 2006-07-15
Unfortunately dictionaries are not one of linuxs strong points. It does have some excellent scientific writing software though.

---

### Post by RAV TUX on 2006-07-15
is there anyway to get the dictionaries to run through Wine?

or could you run Ubuntu along side windows with coLinux?

(I just picked up the "Ubuntu Hacks" book by O'Reilly that has a chapter on how to do this, I'm thinking of doing this myself.)

---

### Post by PryGuy on 2006-07-15
Well, I am thinking about it actually. Do you have experience running Wine?

---

### Post by Thenotsowyzewun on 2006-07-15
I've been running Ubuntu on top of Windows Server for the last few weeks, admittedly it lags occasionally (e.g. if I press and hold scroll on a webpage my rhythmbox internet radio'll stutter and pause, and OpenOffice hangs on exit occasionally, but on the whole it runs very smoothly (to the extent that it's easy to forget windows is running underneath).
Until you need to do something that Linux can't anyway (like connect to my N70 and transfer some MP3s or auto-install a new Symbian program).
Still, Nokia're thinking about creating a Symbian clone ('cos it'd save them about $270 million in royalties to Symbian a year!), and if they make one it'll be based on Linux :D (can't see it not having Linux connectivity then!).

Just my two cents :).

BTW, Colinux looks interesting, but the WINE idea sounds better (I'd rather run Windows programs on Linux than Linux on Windows).

---

### Post by RAV TUX on 2006-07-15
> **PryGuy said:**
> Well, I am thinking about it actually. Do you have experience running Wine?

Yes Wine is quite easy to set up.

Open your Terminal and enter the command:

> $ sudo nano /etc/apt/sources.list

put your password in, the nano editor will open sources.list
Enter this line at the end of the file:

> deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/

Save the file (press Ctrl-O), then open Terminal again and run:

> $ sudo apt-get update

This will update the package cache.
Now you can install Wine:

> $ sudo apt-get install wine

you then want to configure wine:

> $ winecfg

this will create the Wine configuration directory in:

/home/username/.wine

it will also bring up the Wine configuration interface

you may find it helpful to add a new Windows drive (via the 'Drives' tab) that maps to your CD-ROM drive.

click Add button to create a new Windows D drive then click 'Browse' to select the path to your CD-ROM (such as /media/cdrom0/).
Click the 'Apply' button to finish.

you now need to install 'Microsoft TrueType fonts' and 'cabextract'.

open your Terminal use this command:

> $ sudo apt-get install msttcorefonts cabextract

Now that you have Wine, msttcorefonts, and cabextract installed you can install windows applications.

---


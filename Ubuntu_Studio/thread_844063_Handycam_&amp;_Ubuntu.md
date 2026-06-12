---
title: "Handycam &amp; Ubuntu"
date: 2008-06-29
forum: Ubuntu Studio
---

### Post by commbba on 2008-06-29
Hello , this is my first topic at Ubuntu forums and because English aren't my native language , even though I'm using it quite well (I assume),many mistakes about syntax are possible and forgive me for the long lasting topic.

First of all I must get to know you my system:Acer F3000 series(Acer Aspire 1450 platform) laptop with AMD Athlon M 2500+ Ghz(1.8 Ghz real speed) , 512 MB Ram , 55 GB HDD , 128 MB Graphic card Ram ,USB & Firewire ports and runs only Ubuntu.(previous OS Windows XP English SP3 with a lot of crushes).

Now the problem is between my digital camcorder(Sony Handycam DCR-TRV 355E D8 recording format)and my laptop and the program I'd like to use for editing my own movies , Kino.Without knowing it , I first plug in my camera via the firewire port(it has 2 digital ports(firewire & USB) and 1 analog)and the program (Kino) didn't recognized it.I tried also with USB port(same result) and after that I searched Help in Kino and understood that recognizes only firewire connection.Then , when I press ''capture'' button , it informing me that "" raw1394 kernel module not loaded or failure to read/write /dev/raw1394'' , and the same message pops out from the submenu ''AV/C DEVICE'' in preferences of Kino.I did an explore in file system and found a folder named /dev/dv1394 witch contains a file called ''0'' but I didn't found a folder named /dev/raw1394.I searched also with Synaptic Package Manager for ''raw1394'' and it resulted me some files called ''libraw'' that i have already installed.

I searched also on the net and fell into that site [www.bxlug.be/en/articles/220.I](www.bxlug.be/en/articles/220.I) followed the first step adding the second option(modprobe raw1394/modprobe video1394) , i saved it and created a script containing the contents that suggests and saved it in /etc/init.d folder as ''firewire''.Now , I've tried to make it executable using gksudo chmod +x /etc/init.d/firewire command(probably succeded because doing right click uppon it , pop-up menu asks me to execute it in konsole) , but also my camera didn't recognized .
After that I stick around , I can't do this autostart , and of course I don't know if all of these will have good ending and a possitive result.
If you have any ideas of resolving this problem , please write it down but be as more as you can specific , because my konsole level is very low , I'm using Ubuntu for about 2 months now and is my first attempt about Linux based OS's.
I published this problem to the local site of an International computer magazine ,and nobody answers me , so I think the solution might be very difficult , more for me who I'm a nubbie.

Thank you for your answers (if any).

---

### Post by alegallo on 2008-06-30
Check [here]("https://help.ubuntu.com/community/Firewire"), I think you will find a solution to your problems.

I'm a newbie too, but I found a lot of help in the community docs ;)

---

### Post by commbba on 2008-07-02
Thank you my friend and co-explorer in Ubuntu (strange) world.You have the skills to become an Ubuntu power user.
Just for the history , to help newer users , I've tried all the methods the documentation suggested me , none help except opening Kino as root.Recognised my videocamera just in a flash.

---

### Post by alegallo on 2008-07-02
Well, back in the ol' days of Edgy Eft I remember a younger version of me installing Kino and having to start it as sudoer to grab video from my Sony as well :D

If my memory still works, it should have been a problem in the privileges for the firewire port, which could be solved using method 2, "raw1394" (I guess "1396" should be wrong).

Of course it implied a potential security issue, but I was not using my firewire port for anything else, so I could use it without any problem.

Well, good luck, friend!

---


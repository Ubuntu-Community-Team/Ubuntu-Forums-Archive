---
title: "Problems with Dapper Drake Server Edition, please share your thoughts"
date: 2006-06-04
forum: The Cafe
---

### Post by patrick295767 on 2006-06-04
SERVER INSTALL
=============
  
Hi, 

I am very very happy user of Breezy (breezy 5.10), this Linux Distro is really amazing.
  
I wanted today to go into the Dapper World 6.06   :
I downloaded the Dapper SERVER ISO 
  
1/ Installation on the first PC (recent Tower) : Problem with the Display ... 
I used there a non brand new screen... 
  
2/ What is this LAMP SERVER
I didnt have time to look in details ? What's the difference with Server install ? Why 3 cds (desktop, server and ...) ?? 

3/ Then, installation went ok.  After the installation, I run an huge script to install the Linux Server. It's working like with the previous Hoary and breezy distro ... then after some time ... the script is getting kind of crazy :
when installing a program I can see that there is sthg wrong ... 
LOW MEMORY 
How can it be possible ?? PC freezes ... 
  
I reboot, relaunch the script ...
then can see that in processes ps -A gives: 
```
sh
tar
tar
tar
sh
xxextract.tmp
sh
tar
tar
tar
sh
xxextract.tmp
sh
tar
tar
tar
sh
xxextract.tmp
...
``` 
(or maybe its realplayer install prob)
(I should read apt-get sthg)
  
4/ I started to play around with rlogin with the Dapper Beta last time, and could see that after a rlogin & exit 
we are kicked out the console (ALT F1)  
a clear is done and that's it !!
we have to relog from the beginning and connectino to the distant PC is gone 
 
5/ after logout of console in dapper 6.06, the clear is really annoying for LINUX SERVERS !!
  
6/ I thought : ok, that 's very unlucky ...
I'll try on another PC ... Ok, installation went fine (old laptop)
display OK, 
installation done, reboot, then I see the linux starts, hang, then reboot
hangs, reboot , hangs reboot
  
That's finished for me.
  
I have enough already of Dapper !
 
===========
  Result of my Dapper Linux Server Experience :
My LINUX SERVER wont be Dapper, I can take any kind of risks !
I keep Breezy
     
  
===========
  
Please could you stop temporally the downloading of this ISO file because some users can certainly find same problems and this will not be good for the image of Linux Ubuntu, that I really appreciate a lot .
  
MAC OS X = No BUGs, fast, and  highly reliable ...
Windows world = Thousand bugs, getting worst and worst (example : windows XP) ... and slower
  
I hope you will not mind my problems encountered with Dapper 
  
Greetings, 
Patrick
  
=======
References:
[http://www.ubuntuforums.org/showthread.php?t=188978](http://www.ubuntuforums.org/showthread.php?t=188978)

---

### Post by kaamos on 2006-06-04
Uh, where to start? This is the strangest of your threads so far (and that's a lot ;))

If you have no idea what LAMP [1.] is, why on earth did you dl the server iso?

[1.] [http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29](http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29)

---

### Post by angkor on 2006-06-04
[QUOTE=kaamos]Uh, where to start? This is the strangest of your threads so far (and that's a lot ;))
[/QUOTE]

*nods* Quite incoherent. :)

What's realplayer got to do with a server install? What huge script are you talking about?

Sorry to hear you haven't had a pleasant experience with dapper. Glad you like breezy though.

---

### Post by tribaal on 2006-06-04
The 3 CDs are to adress 3 different needs:

* The desktop CD is probably what you were looking for. It's a liveCD with an "install to disk" option (there is a shortcut on the liveCd's desktop).

* The server CD is intended for people who want to deploy Ubuntu 6.06 as a server, hence the name and the special LAMP deployment option.

* The alternate Cd gives more installation options, such as OEM preconfiguration.

Hope this answers some of your post.

- trib'

---

### Post by disturbed1 on 2006-06-04
Anyone watch Carlos Mencia ](*,)

---

### Post by confused57 on 2006-06-04
I've seen quite a lot of posts with people having problems with the Dapper6.06-server iso burned to CD.  Try the alternate-CD and do a server install from that.

---

### Post by prizrak on 2006-06-04
[QUOTE=disturbed1]Anyone watch Carlos Mencia ](*,)[/QUOTE]
I do, what does he have to do with anything? Or are you saying the OP is a little Tut Ta Da ;)

---

### Post by Iandefor on 2006-06-05
I know exactly where you went wrong.

You tried to use a server install CD (which actually installs a server now, not just the base system ;)) when you wanted a full desktop. No wonder. Try it again with the actual desktop CD before you give up, eh?

---

### Post by Harold P on 2006-06-05
[quote=disturbed1]Anyone watch Carlos Mencia ](*,)[/quote]
De de dee? No...

---

### Post by Sushi on 2006-06-05
Huh? You installed server on a laptop? You wanted a server,yet you don't even know what LAMP means? I think that this is a case of PEBKAC. You obviously wanted a desktop, and then you install a server, and whine when things don't work.

I installed Dapper Server on my Mac Mini (which acts as a server) and I haven't seen any issues. Maybe the difference here is that I actually have a vague idea as to what I'm doing ;).

"please stop distributing this ISO because I had some problems". Well, that's a good one :).

---

### Post by hesee on 2006-06-05
I downloaded desktop cd, tried to do graphical install since i couldn't do text-mode install like in breezy. Installation hanged during partitioning! Then I found out there is alternate cd, which looks pretty much like regular breezy cd. I downloade it, now good old text-mode install went fine. But I think this is a perfect example that good text-modeinstall is better than nice-looking but crappy gui install. [-(

---

### Post by curuxz on 2006-06-05
Well he has loads and loads of posts so either he knows what he is doing or DAMN has he been asking alot of support questions :S

This kind of server CD is very new for Ubuntu im suprised if anyone gets it working smoothly.

---

### Post by Sushi on 2006-06-05
[QUOTE=curuxz]This kind of server CD is very new for Ubuntu im suprised if anyone gets it working smoothly.[/QUOTE]

I did :). No problems during install, and it serving files just fine. And it consumes about 20MB less RAM after boot than Fedora Core 5 does ;).

---

### Post by curuxz on 2006-06-05
Cool Sushi, how do you admin it tho, I was going to install it then found out that webmin was obsoleted and I need a stable LAMP system for my webdesign work.

---

### Post by tseliot on 2006-06-05
**patrick295767**
Does saying "Dapper Sucks" seem constructive criticism to you?

I think that a more polite way to say that you don't like Dapper's Sever edition does exist.

Anyhow, before starting this thread:

1) Did you read the documentation about the Server version?

2) Did you ask for help on the forums?

---

### Post by Sushi on 2006-06-05
[QUOTE=curuxz]Cool Sushi, how do you admin it tho, I was going to install it then found out that webmin was obsoleted and I need a stable LAMP system for my webdesign work.[/QUOTE]

I didn't install the LAMP-stack, but Dapper apparently has a "turn-key" LAMP-installation for those who want it.

I do my administration through SSH :).

---

### Post by patrick295767 on 2006-06-05
[QUOTE=tseliot]**patrick295767**
Does saying "Dapper Sucks" seem constructive criticism to you?

I think that a more polite way to say that you don't like Dapper's Sever edition does exist.

Anyhow, before starting this thread:

1) Did you read the documentation about the Server version?

2) Did you ask for help on the forums?[/QUOTE]
    
  

**My sincere apologies** for the way of expressing my problems. I am sure that Dapper will have lot of issues corrected and better hardware support.
 
Since I was in a damn rush, I got quickly peaced. On the first PC, I did the server install, then ran a script to get a desktop. I'll have to understand why pc hangs and gives low memory
On the second one, the pc is definitely not working. I checked again. No recovery console working :-( 
  
SO, I'll take my time to look at this Dapper with more positive sight !! via maybe not only Server CD, as mentioned above...

---

### Post by tseliot on 2006-06-05
[QUOTE=patrick295767]**My sincere apologies** for the way of expressing my problems. I am sure that Dapper will have lot of issues corrected and better hardware support.[/QUOTE]
No problem. I can change the title of the thread for you. Think of a new one and I'll do it.
 
[QUOTE=patrick295767]Since I was in a damn rush, I got quickly peaced. On the first PC, I did the server install, then ran a script to get a desktop. I'll have to understand why pc hangs and gives low memory[/QUOTE]
Desktop and Server editions use different kernels. Perhaps the kernels of the Server edition are not compatible with you hardware.

---

### Post by localzuk on 2006-06-05
What do you mean 'admin it'? If you mean change config files, the most people would use the terminal to do the job. Else, you can still use webmin by downloading it from webmin.com (although I do not like webmin).

---

### Post by localzuk on 2006-06-05
What script are you running to get a desktop?

---

### Post by patrick295767 on 2006-06-05
[QUOTE=localzuk]What script are you running to get a desktop?[/QUOTE]
  
I always prefered to install the linux from server install to know and control what is installed. I like this way very much, which could be giving some troubles like I experienced.
example:
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)
  
And the Server (no Desktop), from Server Install :-)
  
This time, it's different than previous ones (breezy, hoary ...)

---

### Post by localzuk on 2006-06-05
That script would only work with warty as it asks you to install xfree86. The xserver is now xorg. I would recommend that you install something like xubuntu if you want it to be lightweight.

---

### Post by tseliot on 2006-06-05
Ok, I have changed the title of the thread to:
"Problems with Dapper Drake Server Edition, please share your thoughts"

I know it's not that original but I've got an exam tomorrow (and a bad headache today) :)

---

### Post by patrick295767 on 2006-06-05
[QUOTE=localzuk]That script would only work with warty as it asks you to install xfree86. The xserver is now xorg. I would recommend that you install something like xubuntu if you want it to be lightweight.[/QUOTE]
 
Yes yes, it's just an example ( [http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html) )... (Xorg for ubuntu)

---

### Post by patrick295767 on 2006-06-05
[QUOTE=tseliot]Ok, I have changed the title of the thread to:
"Problems with Dapper Drake Server Edition, please share your thoughts"

I know it's not that original but I've got an exam tomorrow (and a bad headache today) :)[/QUOTE]
 
Thank you !!!!

---

### Post by angkor on 2006-06-05
[QUOTE=patrick295767]
I didnt have time to look in details ? What's the difference with Server install ? [/QUOTE]

Well, it seems like you need to make some time to look into the details. When you run a 'huge' script and just expect it to magically work on every new install you do, you're mistaken as your experience has shown.

> Please could you stop temporally the downloading of this ISO file because some users can certainly find same problems and this will not be good for the image of Linux Ubuntu, that I really appreciate a lot .

This is not an Ubuntu problem. You are trying to do a highly customized installation of Dapper that doesn't work correctly. It has nothing to do with the .iso.

My guess is you don't want the server installation iso but the plain desktop .iso and install that without gnome. But since you don't explain clearly what iso you have and what exactly you are trying to accomplish...it's indeed just guessing.

Before you run that huge script of yours check to see if everything in there is compatible with the dapper system and repositories.

Good luck.

---

### Post by fuscia on 2006-06-05
patrick, why don't you just do a full installation and then use synaptic to dump all the programs you don't want? you could then use deborphan to get rid of all the wtfisthis? stuff left over.

---

### Post by imnotrich on 2006-10-17
I have downloaded both the regular and alternate dapper server iso's and can't get them to install either. 
Both were burned on different burners, and both fail at the same packages claiming they are corrupt. 
They also do not detect my network card, and I'm having trouble with cd rom detection too though that may be a jumper issue-I am still experimenting with that. 
All I want is a no-gui server on a pc with 96mb ram and a 350Mhz pentium 2, so I can teach myself (and my kids) about server administration. 
Not as easy as I thought it'd be. Dapper with Gnome runs quite well on my other Pentium 2 300Mhz (320mb ram) so I thought the server install would be a nobrainer. I guess it's back to the drawing board. Anybody know where I can find a copy of the download that is not corrupt?

---


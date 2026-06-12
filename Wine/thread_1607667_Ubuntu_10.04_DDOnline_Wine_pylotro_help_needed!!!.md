---
title: "Ubuntu 10.04 DDOnline Wine pylotro help needed!!!"
date: 2010-10-28
forum: Wine
---

### Post by Eldorian on 2010-10-28
Hi. I am new to everything linux since chunking windows out of my life forever and I love it and will never go back but I am having an issue with DDOnline and I hope someone can help me with it. :)

My system is a Pentium Dual-Core E5300, 2GB RAM, 700GB SATA HD and an NVidia GeForce 9500 GT with 1GB RAM.

I have installed Ubuntu 10.04 Lucid Lynx with Gnome desktop, Wine 1.3.5, Winetricks 20100917 which I used to install dxdx9_xx, vcrun2005 and vcrun2008. I also installed Python 2.6, pylotro from Alan Jacksons site and copied the latest DDO patchclient.dll into the DDO directory replacing the old one after installing DDO which I downloaded from Turbine. I used the DDO-US-Mod8-Downloader to download the full game before installing it through Wine. I also used a couple of registry changes that seemed appropriate and have followed all the good advice I found in the forums to the letter and it helped emmensly. Everything went as planned until I got to the login screen and tried to log in after fully patching. When I type in my account name and password the following message pops up:

Screenshot:[ATTACH]173718[/ATTACH]

Here is the DDO login screen:

Screenshot:[ATTACH]173719[/ATTACH]

As you can see by the login screen the initiallization persists and remains that way. I have searched so long for the error message about dll's on the internet that my eyes are crossing. I have found references to it but no answers as to what might be the cause or how to fix or work around it. This is my first post on the forums and I have high hopes that someone out there can help me. Thanks so much in advance for your help. I am looking forward to learning all I can about Linux to better understand and work with it cuz windows is a thing of the past, in my opinion. :)

---

### Post by Eldorian on 2010-10-28
Removed duplicate post.

---

### Post by buzzmandt on 2010-10-28
is it safe to assume you don't have any access to a windows machine that can install it and copy the post installation folder to linux?

---

### Post by Eldorian on 2010-10-28
> **buzzmandt said:**
> is it safe to assume you don't have any access to a windows machine that can install it and copy the post installation folder to linux?


Hi Buzz. That is correct. I have no windows anymore period. Are you suggesting installing ddo in windows to copy it into linux? I hope there is another way of fixing this since the whole idea was to get away from windows and its hold on so many. I realize that with a windows based program that the creators have not actively ported for linux is not an easy thing to work around but there must be a way I have not seen yet since many are running ddo on their linux boxes. I think I may have missed something when following all the steps to get to this point. I do have World of Warcraft working great on this same box using the instructions I found in the forums so there has to be a way to get ddo to work as well.   Any suggestions?  :)

---

### Post by buzzmandt on 2010-10-28
It's my understanding (and personal experience) that the ddo installer doesn't work with wine.  I'm playing ddo on maverick with a very good user experience but i followed the wine appdb install method. I had a friend of mine install it on his win 7 machine and gave me the folder on a thumb drive. he doesn't even play it i just wanted the post install folder.  I wish I could help you more than that, hopefully someone else will have something more for you, good luck.

---

### Post by Eldorian on 2010-10-29
> **buzzmandt said:**
> It's my understanding (and personal experience) that the ddo installer doesn't work with wine.  I'm playing ddo on maverick with a very good user experience but i followed the wine appdb install method. I had a friend of mine install it on his win 7 machine and gave me the folder on a thumb drive. he doesn't even play it i just wanted the post install folder.  I wish I could help you more than that, hopefully someone else will have something more for you, good luck.


Thank you Buzz. You are correct that the ddo installer will not work with Wine which is the reason for the full game download then use Wine to install it from your desktop. That worked perfectly as well as the processes for installing and using the pylotro launcher and replacing the patchclient.dll file so the game could be patched current. It has to be something I missed so I am going back through all the steps I took and the forums I got the info from to trace what I did wrong or did not do. Thanks again for your responses. I will post a solution if/when I figure this out. :)

---

### Post by ajackson on 2010-10-29
The DDO downloader does now work with Wine (you need version 1.3.4 or greater and you need to install the Visual C++ 2008 run-times).

The installer also works.

However the error you are seeing about umbra.dll is a strange one. Doing a quick google of just the dll gave me [this]("http://www.spydig.com/file-diagnosis/umbra-dll.html") which suggests that it is malware. That might mean that your DDO install is infected or somehow you've managed to infect your wine install.

---

### Post by brndndvr on 2010-10-29
> **Eldorian said:**
> ...and copied the latest DDO patchclient.dll into the DDO directory replacing the old one after installing DDO which I downloaded from Turbine.
 
...I also used a couple of registry changes that seemed appropriate and have followed all the good advice I found in the forums to the letter and it helped emmensly. 

...I am looking forward to learning all I can about Linux to better understand and work with it cuz windows is a thing of the past, in my opinion. :)

I agree, not a fan of windows either :D

First off, I probably know less than you about ubuntu, so perhaps this won't help at all but I figured i'd at least try :p

1) the winehq database instructs you to rename the patchclient.dll to something else and then adjust your advanced settings to patch from that newly named .dll file. Did you do that?

2) perhaps the registry changes you made messed up something vital to running ddo?  

Hopefully it's something simple, and not some sort of computer infection.  Good luck!

---

### Post by Eldorian on 2010-11-20
I had to give up on this since my pc has been infected with something and I deleted the .wine bottle and have to start over. I'm going to start a new thread on the virus issues I had. Thanks to everyone who tried to help with this.

---


---
title: "mircosoft installer"
date: 2007-11-28
forum: Windows
---

### Post by tadcan on 2007-11-28
A strange problem has occurred when I try to download .iso files.

I have XP. The firefox download box gives me the countdown of time and shows me how much of the file has been downloaded etc. I also click on the option to save as.  

However when the download is complete Microsoft wont save the file because it cant read it. I recently upgraded the windows installer. I suspect the problem is there because before I was able to download Ubuntu. The failed downloads were with Mandrivia and Knoppix.   

Any thoughts?

---

### Post by jken146 on 2007-11-28
Do you mean that you can't save a downloaded file with Firefox for Windows?  Or that you can't read the file once downloaded (and saved)?

If you downloaded a Ubuntu iso I really don't see how this would have caused your problem.  It's like downloading any other kind of file, be it a pdf, exe or whatever.  Your problem lies with Windows or Firefox or something to do with them, but I'm sure not Ubuntu.

Try to clear your download history in Firefox (Tools>Downloads) and clear your cache (Options>Privacy>Clear Private Data) and temporary files (I think this is in Disk Clean-up or some such in Windows.  Then try to download your file again.

This really is the wrong forum to ask this though.

---

### Post by tadcan on 2007-11-28
Since its an MS problem, didn't see where else it would go.

The problem is that I cant save a the file once downloaded. I have two icons  with the name. One has 0 bytes and the other 15MB. I was making a few attempts. 

I called a friend who suggested I download with IE as a comparison. I'll see what happens, do a disk clean up and try after IE is finished.

Anyway I still think it could be the installer since that was upgraded. I doubt its the new .net file.

---

### Post by jken146 on 2007-11-28
Sorry about that, I must have misread which forum you put it in... duh.

What i would *guess* is going on is that Firefox if downloading the file to /tmp (well, whatever its windows equivalent is) and then when it's done, trying to move the file to the location you told it to save to.  You could find the temporary files folder and see if the complete file is lurking there.

You could always try a reboot :p

---

### Post by tadcan on 2007-11-28
LOL. I have rebooted and the problem persists. One day I'll be able to get linux on my system. Its a conspiracy I tells ya....

Its set to download to the desktop. That's where I have the I'll have bits of files. I found C:\windows\Temp not sure if that is related to downloaded files.

I realise you are not an MS person so wont know either. 
The connection to the server was reset so IE stopped the download. Stupid IE.

---

### Post by SonicSteve on 2007-11-28
> **tadcan said:**
> A strange problem has occurred when I try to download .iso files.

I have XP. The firefox download box gives me the countdown of time and shows me how much of the file has been downloaded etc. I also click on the option to save as.  

However when the download is complete Microsoft wont save the file because it cant read it. I recently upgraded the windows installer. I suspect the problem is there because before I was able to download Ubuntu. The failed downloads were with Mandrivia and Knoppix.   

Any thoughts?

Can you download anything? Driver.exe installers, other programs like firefox and thunderbird or openoffice etc.?

---

### Post by tadcan on 2007-11-28
yes. I had to download the installer to get the new .net to get cdburner xp.

I just re-downloaded cdburnerxp which is an .exe file.

I am getting damn small linux to double check if its still hapening. current.iso is the file name

---

### Post by SonicSteve on 2007-11-28
> **tadcan said:**
> LOL. I have rebooted and the problem persists. One day I'll be able to get linux on my system. Its a conspiracy I tells ya....

Its set to download to the desktop. That's where I have the I'll have bits of files. I found C:\windows\Temp not sure if that is related to downloaded files.

I realise you are not an MS person so wont know either. 
The connection to the server was reset so IE stopped the download. Stupid IE.
windows\temp is used for a temporary place for programs to use while installing usually. Sometimes for zip type programs to extract to etc. It has nothing to do with temp internet files though. THose are stored in docs and settings\user account name\local settings\microsoft\ 
Though for firefox it will be different and I doubt you'll find you downloaded files in there. Firefox does something weird to it's temp files.  You can't actually read them like you can with internet explorer.

---

### Post by SonicSteve on 2007-11-28
> **tadcan said:**
> yes. I had to download the installer to get the new .net to get cdburner xp.

I just re-downloaded cdburnerxp which is an .exe file.

Can you post the exact error message you get when you try to open an ISO file. It might be more file extention related than error related.

---

### Post by tadcan on 2007-11-28
I'm not surprised it couldn't find a temp file for firefox. Not sure it exists because everything is directed to the desktop.

---

### Post by tadcan on 2007-11-28
> **SonicSteve said:**
> Can you post the exact error message you get when you try to open an ISO file. It might be more file extention related than error related.

As soon as the file has downloaded I'll do that. It will take an hour since I burned my cap getting .iso's I couldn't keep. :(

---

### Post by SonicSteve on 2007-11-28
> **tadcan said:**
> 

I just re-downloaded cdburnerxp which is an .exe file.



Are you downloading this because you don't have a CD burning program installed? If you don't windows doesn't know what an ISO file is unless you install a program that can handle them. It just sees them as data with a .iso extension.

---

### Post by SonicSteve on 2007-11-28
> **tadcan said:**
> As soon as the file has downloaded I'll do that. It will take an hour since I burned my cap getting .iso's I couldn't keep. :(

Did you delete these files? are they still in the recycle bin hopefully. I'm just wondering if you got them and now you just need a program that can burn them. I hope CDburnerxp works for you. It gave me errors when I tried to use it a few months ago.

EDIT 
OK little rant by steve now. 
We need to port a program like K3B or Gnomebaker to windows. It has just occured to me that not all windows computers will have a good CD/DVD burning program. How do we expect these people to burn the ISO's to try Linux? To my best efforts I haven't found a good free CD/DVD burning program for windows yet and it's not for lack of looking. We really need to do this.

---

### Post by tadcan on 2007-11-28
I still have the files one is 0 KB the other is 15MB and strangely both have the same.

My internet connection has speeded up. Should have a error report in 5 minutes.

 
Since I have your attention. I wouldn't be in XP if I could solve this problem

[http://ubuntuforums.org/showthread.php?t=602957](http://ubuntuforums.org/showthread.php?t=602957)

---

### Post by tadcan on 2007-11-28
It downloaded fine. Maybe it just needed a disk clean or firefox  clear.

I'll try the bigger files overnight. I might as well burn damn small linux and try it. :) 

Thanks for your help.

---

### Post by SonicSteve on 2007-11-28
> **tadcan said:**
> I still have the files one is 0 KB the other is 15MB and strangely both have the same.

My internet connection has speeded up. Should have a error report in 5 minutes.

 
Since I have your attention. I wouldn't be in XP if I could solve this problem

[http://ubuntuforums.org/showthread.php?t=602957](http://ubuntuforums.org/showthread.php?t=602957)

OK it doesn't sound like an extension problem though if you don't have a proper burning program that would end up being your next problem even if you had the files.

so my next suggestion is this. download and install shareaza it can handle torrent files, and is a great downloading tool. THen go to [www.mininova.com](www.mininova.com) and search for ubuntu or ku or xu. then let shareaza dowload it. Thus avoiding other issues from browsers.

---

### Post by tadcan on 2007-11-28
I have just been on the DSL live CD. The very first time I have been able to get linux to work on my machine! Granted I've only tried ubuntu and Gos.

Dont know if you have read my other thread. I'm told its a problem with the IDE HDD. 

I'm getting shareaza now. Since my ISP blocks torrent ports, straight downloads are normally faster. I've used deluge on mandrivia but it was really slow.

---

### Post by SonicSteve on 2007-11-28
Do you know exactly what kind of problem with your HDD. I've never heard of Linux or anything have a specific problem with IDE HDD's. In fact at this point your more likely to have problems with Sata and even then its' the controller not the drive itself usually. 
I'll read your other thread and see.

---

### Post by SonicSteve on 2007-11-28
> **tadcan said:**
> I still have the files one is 0 KB the other is 15MB and strangely both have the same.

My internet connection has speeded up. Should have a error report in 5 minutes.

 
Since I have your attention. I wouldn't be in XP if I could solve this problem

[http://ubuntuforums.org/showthread.php?t=602957](http://ubuntuforums.org/showthread.php?t=602957)

I read the thread, why do you think that burning the CD again will solve this? There must be somthing strange about this system. It's most likely the chipset that has something about it that is not compatible with the Linux kernel in ubuntu. I doubt that re-burning the CD will have any effect.

---

### Post by tadcan on 2007-11-29
I tried to download Knoppix and got an error. The fact that I have been checking the download really early in the morning when I'm still asleep  has added to my lack of understanding about computers.

Its C:\Documents and settings\******\Desktop\Knoppix_v5.1.1.CD-2007-01-04-EN.iso.part could not be saved because the source could not be read.

So in the end it was probably a drop in the connection. My connection speed changes drastically from .8KBs to 120KBS if its peak or off peak. Hense trying it at night.

I started it again this morning and have had a consistent high speed, (100-127kbs).  Its almost half way through and now low signal strenght. 


Since I was able to load the DSL live cd I wonder could it be Debian not liking my system?

I should really learn the whole investigation thing before I post. :)

---

### Post by SonicSteve on 2007-11-29
There is an outside shot that updating your mainboards BIOS to the latest version could solve this. I should stress a few things though.
1. It is an outside shot
2. If the power goes out while you're updating you may render your mainboard useless. This depends on whether or not you have a BIOS that can be recovered or not. Some can, some can't.
3. You may already have the latest BIOS version, some manufacturers release very few updates even if updates are needed. Others release numerous updates.

Know what your doing before you start, and if you live in an area that looses power frequently you may not want to do it.

A second thought is this. 
If your mainboard has Sata and your not using it, disable it in the BIOS. I had trouble installing Ubuntu on a system not long ago on a mainboard that IDE and SATA. It was getting confused because I only had IDE devices plugged in, once I disabled the SATA ports I was able to install. It may have been different if I was trying to install to a drive connected to the SATA but all I had was a 30GB IDE.

---

### Post by tadcan on 2007-11-29
I checked the Bios updates online. To get the right one I needed to know the socket number. The BIOS for a similar type of board had updates dating to before date on the driver cd. I updated the chipset drivers, it didn't have any effect when I put the ubuntu CD in.

In the booklet of the motherboard I saw no mention of sata. Its over five years old so maybe pre-date sata. 

I'll keep on trying to download other types of Linux.

EDIT: Strange thing happened. I checked for updates with a program that scans your HDD. Told me my ethernet/wireless adpater thing! had an update. Except after I installed and set it up I saw a laptop icon beside the desktop one. However I was able to get the Knoppix iso no hassle. Windows just gotta love those quirks! ;)

---

### Post by SonicSteve on 2008-01-13
I found a simple ISO burner for windows that is free and it works well.

[http://www.ntfs.com/iso_burner_free.htm](http://www.ntfs.com/iso_burner_free.htm) 

It's very simple but effective.

---

### Post by tadcan on 2008-01-26
hey SonicSteve

Thanks for all your help. It turns out my interpretation of the situation was waaaaaay off. It was something simple like how I choose run instead of save in the download box.

---


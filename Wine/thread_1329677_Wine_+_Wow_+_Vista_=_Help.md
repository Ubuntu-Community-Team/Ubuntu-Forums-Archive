---
title: "Wine + Wow + Vista = Help"
date: 2009-11-17
forum: Wine
---

### Post by clim2f88j on 2009-11-17
First of all I'm a complete noob to the Ubuntu world and need really clear help for this and thanks to everyone!

I have Ubuntu and Vista but i don't use Vista cause somehow after uninstaling Norton my ineternet stopped working there so i decided to switch to Ubuntu. (i still have Vista installed)

Well i installed Wine and did winecfg and set up my windows version to windows vista and did an auto detect of drives. 

I've try copying the World of Warcraft files from the DVD to my Ubuntu but there only is 7.4MB in it (and yes i did
sudo umount /dev/cdrom
  sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/

[FONT=Verdana]for the 'unhide' files) and it still shows the same files and size.

i also downloaded WoW from the website to find out that when i try to install it,
it says that i dont have 7GB of space avaliable on my ubuntu for it[/FONT].

[FONT=Verdana]i need help with configuring Wine the right way for Vista and either copying WoW's DVD to my Ubuntu or 
running WoW from Vista with Wine in Ubuntu or installing the WoW Download i did.
I know there's a lot of help out there but i been trying for over 1 week and couldn't find anywhere to fix this problem.

Thanks![/FONT]

---

### Post by Alatar1 on 2009-11-17
You may not have 7GB free on your ubuntu partition for it, all depends on how big you made the partition for ubuntu. and chances are Windows is hogging the majority of your HDD space...
May I also recommend switching over completely to 1 OS or the other (Ubuntu has my vote, switched to the opensource movement over a year ago and havent had a single regret yet, i love it to death). 2 Operating systems on the same hard drive has always been a big no no for me, but thats personal preferrance. Dual booting is just awesome with multiple hard drives though (different OS's on different drives)

         And I also do not understand the need for the sudo mount and umount commands? i never needed any of that to install WoW...you manually run the install by browsing to the cd/dvd-rom drive with the install cd in, or use the download.( i highly recommend the download)

   And as for configuring wine you can use Applications>wine>configure wine to configure it as well, I have mine set for WINXP rather than Vista, but I don't think it much matters for WoW as long as its XP or above seeing as how WoW launched during XP's reign of dominance int he windows world.

---

### Post by clim2f88j on 2009-11-17
so is there anyway of making ubuntu partition bigger without reinstaling the whole thing?
 
and how can i complealte delete vista without deleting ubuntu?

---

### Post by beastrace91 on 2009-11-17
Alrighty - first off I think you are confused as to what Wine actually does. Wine does not use your currently installed Windows to run applications from - it creates a fake "C" drive on your Ubuntu to run Windows applications from - this means you need to reinstall your applications on Ubuntu under Wine. (You can run them right off the Windows hard drive but this can be complicated and lead to further issues so it is best to just install it under Wine on Ubuntu). 

That being said how much space do you have open on your Ubuntu partition? If it is telling you you do not have enough room - this might be the case, if it is no worries we can walk you through expanding the partition. 

You should not need to copy the DVD/Installer to your hard drive - just insert it and open the folder viewer to the contents of the disc and right click on the setup.exe and select "run with Wine".

Also another option for a new user is installing via [PlayOnLinux](playonlinux.com/) - it will take care of much of this work for you, even walks you through downloading the installer files for WoW and several other online games.

Regards,
~Jeff

---

### Post by beastrace91 on 2009-11-17
> **clim2f88j said:**
> so is there anyway of making ubuntu partition bigger without reinstaling the whole thing?
 
and how can i complealte delete vista without deleting ubuntu?

You do NOT need to fully remove Vista - there is nothing wrong with dual booting if you need Windows still for some reason. That being said, to resize the partitions (or remove Vista partition all together) boot from an Ubuntu LiveCD and select **System->Administration->Partition Editor** and it will give you a nice GUI for adjusting/resizing your hard drive partitions.

Regards,
~Jeff

---

### Post by Alatar1 on 2009-11-17
Well if you installed ubuntu on your windows partition I don't THINK theres a way to change the size of it without wiping, you CAN try a partition manage of some kind, 
BUT I HIGHLY RECOMMEND that you wait for more opinions from more experience ubuntu users than I  BEFORE DOING ANYTHING as major as wiping or messing with paritions....they know more on the subject I'm sure, I have never messed with things in this exact situation...I just completely reformatted and installed ubuntu, never looked back.
*edit*
heh see, I had no idea of that tool on the live CD lol

---

### Post by clim2f88j on 2009-11-17
> **beastrace91 said:**
> 

That being said how much space do you have open on your Ubuntu partition? If it is telling you you do not have enough room - this might be the case, if it is no worries we can walk you through expanding the partition. 




it says that i have 5.4 gb left so a total of around 7 gb on ubuntu..plus 30 gb on windows and a 500 gb external hd....im looking for my ubuntu cd cause i have no idea where i put it

THANKS EVERYONE!!(hope i can make this work soon)

---

### Post by beastrace91 on 2009-11-17
Wow! You only have a 40gig primary hard drive huh? If you are truly not using Vista any more (and would not mind losing it) then I would recommend expanding Ubuntu to use the entire drive (as it is not very large in the first place)

Regards,
~Jeff

---

### Post by clim2f88j on 2009-11-17
> **beastrace91 said:**
> Wow! You only have a 40gig primary hard drive huh? If you are truly not using Vista any more (and would not mind losing it) then I would recommend expanding Ubuntu to use the entire drive (as it is not very large in the first place)

Regards,
~Jeff

well the primary hard drive is 110gb but i only have 30some left...if i uninstal windows will ubuntu take the remaining space by it self? and if i keep vista is there anyway i can expand my ubuntu partition without the cd? cause i dont know where i put it

---

### Post by beastrace91 on 2009-11-17
No - you need a the cd because you cannot adjust the size of mounted partitions (meaning if you are booted in Ubuntu your Ubuntu partition is mounted). If you boot of the cd and load the partition manager as I described above you will see your Vista and Ubuntu partitions and should be able adjust them easily.

~Jeff

---

### Post by Alatar1 on 2009-11-18
so make a new cd...which version of ubuntu are you on?
because you can just download the image and burn yourself a new copy, after all, it is free and opensource

---

### Post by clim2f88j on 2009-11-19
ok so now i have ubuntu as the only OS and it works great. installed WoW and i have the files in my ubuntu that i copied early from vista to my external hd because playonlinux for some reason cant open my wow dvd saying 'error: unable to find the CD-ROM!' then when i tried to run wow to play i get an error message that reads 'could not launch 'world of warcraft' failed to change to directory '(my directory)' (permission denied)'

---

### Post by beastrace91 on 2009-11-19
I see you already posted in [this thread](http://ubuntuforums.org/showthread.php?t=1330927) here but have you tried this:> **Alatar1 said:**
> ***Problem***"Permission Denied" error when attempting to run the game. OR When the WoW Launcher comes up, the "play" button is greyed out and cant be used. (both are stemming from the same problem)

***Solution*** The easiest and least technical way to fix this would be to first browse on over to /home/<yourusername>/.wine/drive_c/Program Files/World of Warcraft ,
 There will more than likely be an X on the world of warcraft folder, simply right click on it,go to properties, click the "permissions" tab, right under where it says owner: username-group, change the drop down box to "create and delete files".
    Now that that is set, In the World of Warcraft directory, Run the game via the "WoW.exe" file , NOT LAUNCHER.EXE (the launcher is whats causing it, it will lock you out everytime!!) once your on the title/login screen, UN-check the little box on the bottom left that says "show launcher".
    DO NOT USE THE LAUNCHER! it WILL lock you out again!!! this should fix this issue.

IF while working on the issue above, you cannot change file permissions due to it telling you the owner is "root"... 
you will need to change the permissions as root,
     the way i know how to do this is go to terminal and enter ```
sudo nautilus
``` or whatever file browser you use (nautilus is the default for ubuntu) this will allow you browse files as root,
         BE VERY CAREFUL HOWEVER, Tinkering with files as root can have very bad consequences and compromise your machine possibly, that being said...
     simply browse to the directy as stated above and change the permissions that way...there are also console commands to do it manually, but for the sake of the not so savvy, I've omitted those.

Regards,
~Jeff

---

### Post by clim2f88j on 2009-11-19
^yup, i've already done that

---

### Post by beastrace91 on 2009-11-19
Does your stand user account have read/write access to the WoW directory like it should? (EG can you create/paste a file into it and sub folders)

~Jeff

---

### Post by clim2f88j on 2009-11-19
so i decided to move from ubuntu 9.10 to 9.04...still playonlinux cant open the dvd but i copied the wow files from my external hd. everything is going good so far only that wow moves really slow on the tittle page (havent started playing yet).

---

### Post by beastrace91 on 2009-11-19
Whats your video hardware and what driver do you have installed for your gfx card?

~Jeff

---


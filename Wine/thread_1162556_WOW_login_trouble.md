---
title: "WOW login trouble"
date: 2009-05-17
forum: Wine
---

### Post by Frostsniper on 2009-05-17
Ok, so I'm kinda new at this so please bare with me. 
I installed Ubuntu (Jaunty Jackalope 9.04) yesterday went fine and great, I wanted to install WOW- my favorite game. Anyhow I worked through some problems with graphics and such and installations issues but i got it installed completely and patched. Now, when i get to the log in screen i can see everything do everything easy the problem comes when i type in my password and user account i get the error that---

"Your account is authorized for the wrath of the lich king expansion, but the computer you are playing on does not contain Wrath of the lich king data. To play on this machine with this account, you must install the wrath of the lich king. Additional data is available at: [www.worldofwarcraft.com/lichking/download/]"

MY question is, is there a command line fix--to this or something? Or any other info you might need to help me with my problem? 

I HAVE poured over other guides looking for my problem and no luck =/, I to understand and hate people who don't try to fix the problem 1st there self but I assure you I have looked high and low. 

**i might add i don't have my Burning Crusade Disks any more But i do have Original wow (disks) and WOTLK disk. **

thanks alot for any help =)
-Frost

---

### Post by I_Ditched_Windows on 2009-05-18
Hi,

I did you just install WoW from just the original disks and the wrath disks? If so I believe that you need to have burning crusade installed as well.

I myself lost my original disks and the BC disks and had to go download the game data from blizzard.

---

### Post by Frostsniper on 2009-05-18
no, no I used the blizzard down loader and had it run on its own, it patched itself clear up to 3.1.1.9835

---

### Post by Rodamar on 2009-05-18
[http://us.blizzard.com/support/article.xml?locale=en_US&articleId=21058](http://us.blizzard.com/support/article.xml?locale=en_US&articleId=21058)
 

 > Are you having problems installing the game? (PC)
 

If you are using Windows XP/2000 please be sure you are logged on as an administrator account when installing the game. If the game is not installed on an administrator account, computer permissions can prevent the installation from completing. We cannot support the game on a non-administrator account.
I found the above advice at the WoW website cited above.  Might it be that you need run WoW under Linux via sudo or su?  



Please note:  that may not be a good idea.  (see the sticky advice entries within this forum warning against following advice to use dangerous or even explicitly malicious commands:  

[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

It is also generally to my understanding not advisable to do more than absolutely necessary from within and administrator user account under Linux.  )

Are there more experienced Ubuntu or other Linux users present and able to comment on this suggestion?  Eventually it might be possible to run WoW as a normal user after all?

I shall try researching the WoW forums for appropriate further advice.  If I find more I'll post it as soon as I can.

---

### Post by Dimarchi on 2009-05-18
Hm...let's start with the size of your WoW folder and try to determine whether you really have all that is needed. Can't get any more basic that that, I figure. :)  As far as I can tell, patch number in itself does not tell much.  Around 4 gigs? Vanilla. 7? Plus the Burning Crusade. 11? All that and WotLK, too. You do need to have all the previous stuff installed before you can get to the next one in line. In other words, no Burning Crusade without vanilla, and no WotLK without both vanilla and the Burning Crusade.  And, heck, no...never use sudo or su to run WoW. Ever. Like so totally not needed. :)

---

### Post by Rodamar on 2009-05-18
Thanks for that advice, Dimanchi.  I thought so.  

In the meanwhile I found this other advice at a WoW  support forum.  There the concern was a failure to rename certain files during an install/update.  But rename or creation, both actions require appropriate rights within the target directory at least. 

 (Right, Dimanchi?  I am, myself, rather new at using Ubuntu. Let alone wine.  )

      > 
**Are you receiving an error message indicating the game cannot rename a file to "x.x.Trash" when installing Burning Crusade? (PC)**



[...]
Please first verify World of Warcraft is not running on the system while you are attempting to install the expansion. If the game is closed and the problem persists, please try right clicking on your World of Warcraft folder and select the [COLOR=blue]"Properties"[/COLOR] option. Under this section, please uncheck the [COLOR=blue]"Read Only"[/COLOR] option and try again.
       

**Solution ID: **21063

---

### Post by Hairy_Palms on 2009-05-18
the Blizzard Downloader just patches whatever u currently have installed so if u didnt install the Burning crusade yourself its just patched vanilla to 3.1.1 the patches dont install the data files for the expansions, you either gotta download the TBC installer or borrow a set of disks.

---

### Post by Hairy_Palms on 2009-05-18
> In the meanwhile I found this other advice at a WoW support forum. There the concern was a failure to rename certain files during an install/update. But rename or creation, both actions require appropriate rights within the target directory at least

you will have full permissions to your wine folder as its stored inside your home directory

---

### Post by Rodamar on 2009-05-18
Well, yes.  I would have thought so, too.  But do please check out this comment made at the PlayOnLinux site.  

[http://www.playonlinux.com/en/topic-2302-wow.html](http://www.playonlinux.com/en/topic-2302-wow.html)

> The latest expansion for World of Warcraft installer has permissions on it that require some maneuvering before you can install it.I hope this helps, too.  

As for my misgivings about missing rights within the normally presumably unobstructed rights construction within the users own directories, I have had such problems in the meanwhile under Ubuntu Linux before with other applications.  

It became necessary at times for me to change the ownership of certain files to oneself instead of to the administrator account (for awhile I had been toying with using such a one instead of sudo, the command.)  But then, I am preferably a user of alpha or beta versions of Ubuntu, hopefully in however humble service to the developers by way of doing so.  Presumably, that is how I got involved with such issues to start with.

---

### Post by Frostsniper on 2009-05-18
WOW! i expected 1 maybe 2 replies! you guys are really awesome!

Currently my file size of WOW is 12.2Gigs so i think i have it all, I think i'll just try reinstalling it again, just this time i think i will use all the disks and not the blizzard Downloader. But to do that i'll have to hunt down my freind at school and steal his disks....

I'll post back when i have results good =) or bad =( 

Thanks once again for the thoughts and ideas! 
and i found this guide here - i think i'll try it--
[http://www.sysadminwiki.net/wiki/index.php?title=How_to_install_and_configure_World_of_Warcraft_in_Ubuntu_9.04](http://www.sysadminwiki.net/wiki/index.php?title=How_to_install_and_configure_World_of_Warcraft_in_Ubuntu_9.04)

-Frost

---

### Post by Dimarchi on 2009-05-19
Looks like you have installed all you need to have, and all - in theory - should be in working order. Please do try re-installing, it may solve the problem...or at least, we can move to the next one or stay at the same one. :D

At the moment I can not see the solution you quoted applying to your case, Frostsniper.

Do note: you can install it anywhere you like within your home folder. For example, I have it in /home/dimarchi/World of Warcraft (yes, at the same level as Examples, Documents, and the other folders that are created when installing Ubuntu...was too lazy to create a specific folder for games, will probably do that some day).

Another option: if you still have the Windows partition with the WoW installed there and you can access the partition, you can copy the whole folder to the Ubuntu side. It neatly sidesteps any ownership problems to files you may encounter (my experience). Just trash the Config.wtf file in the WTF folder so that the game will create a new one for you and you can start adjusting it.

Adjusting wine to work with WoW is another thing to solve, possibly. In preparation to that what does

```
lspci | grep VGA
```tell you? Type it into console (Applications - Accessories - Terminal).

---

### Post by Frostsniper on 2009-05-20
Although i haven reinstalled yet i will try hopefully Thursday (dam class)  
> **Dimarchi said:**
> 

Adjusting wine to work with WoW is another thing to solve, possibly. In preparation to that what does

```
lspci | grep VGA
```tell you? Type it into console (Applications - Accessories - Terminal).

but this is what it dose...

$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)

pretty sure there all up to date i just installed like last Friday and got all the updates then

---

### Post by Frostsniper on 2009-05-21
All right here we go, so i was able to nab my friends BC Disks and fist I tried copying all of them except WOTLK to my hard drive as a ISO img Via, right-click/Copy disc/ re dircet were to go and presto. But that failed probably because of me, you see when i went to the file they were put in after carefully making separate folders for each as to not get confused and such. The file turned out to be "brasero"(772.2 MB) and "brasero.toc" (50 bytes). So it was not only not a iso img but it was complete crap... didn't help me. Yes I tried renaming it brasero.iso (with little if any hope) I almost expected it to fail. And yes it did. When trying to mount it via Applications-->System Tools-->Gmount-iso. 
So what did i do!?

I opened up each disk as I found on **[ this]("http://www.wowwiki.com/Wine")**, site. Then proceeded as instructed to 
> Create a new folder on your computer. Copy all of the files from the first CD and all but the Installer.exe file from the rest to this directory on your hard drive (overwrite when prompted). Copying the Installer.exe from the other CD's will cause the install to fail.Next I did the same for BC (Actually I did BC while the install for WOW was running because it was not using my CD drive =) ) 

*Note* No need to run patching or anything between original WOW and BC it worked fine just using the CD's- after you have BC installed you SHOULD be at 2.0.0.6080

Then came WOTLK.... EVIL!

Ok So here is where I'm stuck now =/ I went to **[this]("http://www.sysadminwiki.net/wiki/index.php?title=How_to_install_and_configure_World_of_http://www.sysadminwiki.net/wiki/index.php?title=How_to_install_and_configure_World_of_Warcraft_in_Ubuntu_9.04")** site, because it was updated to 9.04 =). Anyhow i'm stuck on the command line for WOTLK where it says 

> 
# mount -t udf -o ro,unhide,uid=1000 /dev/scd0 /mnt/lich (replace /dev/scd0 with your cdrom)So, i typed in this 

> # mount -t udf -o ro,unhide,uid=1000 /media/cdrom0 /mnt/lichand receive this 
> 
# mount: /media/cdrom0 is not a block deviceHow do i find out where in the world my CD drive is and what its called? ect... ](*,)

The full text it tells me to enter for the command line is this 
> $ sudo mkdir /mnt/lich
$ sudo su -
# mount -t udf -o ro,unhide,uid=1000 /dev/scd0 /mnt/lich (replace /dev/scd0 with your cdrom)
# exit
$ cd /mnt/lich
$ wine Installer.exe


---

### Post by Dimarchi on 2009-05-22
Meh...way too complicated for me. :)  If you see the game cd mounted on your desktop, open the Installer.exe, autorun.exe, or whatever exe it was that is needed to start the installation - it is on that cd.  I would recommend using the method number 4 if you did not stash the downloaded installation you had somewhere else. It is the least painless (also the most time consuming). The Blizzard Downloader advice can be skipped over, unless you did install Firestarter.

Sneaker net way: find a friend who has all that stuff you need working. Copy the working folder to an external hard drive or usb stick. Copy that stuff to your computer. This can be done in parts, as long as the end result is the same (not sure about the validity of this piece of advice, can somebody confirm this?).

The easiest: you have a windows partition on your computer and can copy the installed version of WoW straight from there. 

I really recommend the least painful ways available to you to do this, rather than go with command lines and such.

---

### Post by Frostsniper on 2009-05-22
> **Dimarchi said:**
> Meh...way too complicated for me. :)  If you see the game cd mounted on your desktop, open the Installer.exe, autorun.exe, or whatever exe it was that is needed to start the installation - it is on that cd.  I would recommend using the method number 4 if you did not stash the downloaded installation you had somewhere else. It is the least painless (also the most time consuming). The Blizzard Downloader advice can be skipped over, unless you did install Firestarter.

Sneaker net way: find a friend who has all that stuff you need working. Copy the working folder to an external hard drive or usb stick. Copy that stuff to your computer. This can be done in parts, as long as the end result is the same (not sure about the validity of this piece of advice, can somebody confirm this?).

The easiest: you have a windows partition on your computer and can copy the installed version of WoW straight from there. 

I really recommend the least painful ways available to you to do this, rather than go with command lines and such.

ok well 1st the cd is protected in such a way it says regardless if i am admin or w/e on the computer, it says "i don't have the permission" i can't get "Just" the WOTLK files from someone w/ a working game because they are all blended together, unless i just wanted to straight patches

I DO have a windows partition but I'd rather not get wow on it because I've read it harder to configure the windows partition to play nice w/ ubuntu and run WOW - resulting in lower FPS and not so good play. 

and the sneaker net way i don't think will work at all, (but i could be wrong)  thanks though, any uber ubuntu people (?) that can help me understand what that command line is saying and or telling me what to do? (with regards to the third line, I understand the 1st 2nd and rest just not the 3rd )

---

### Post by Dimarchi on 2009-05-23
> I DO have a windows partition but I'd rather not get wow on it because I've read it harder to configure the windows partition to play nice w/ ubuntu and run WOW - resulting in lower FPS and not so good play. Just to clarify this part in case I have misunderstood you...Windows is Windows - it does not matter what you do with it as long as you can get a working WoW installation on that side. All that matters is that you can access the partition where WoW folder is and you can copy it to Ubuntu side. You do nothing else with the Windows partition, nor with the Windows installed WoW (unless you wish to play WoW in Windows). The Windows WoW and Ubuntu WoW have nothing to do with each other, and can be run separately. Never run the WoW installed in Windows partition using Ubuntu. Only run the WoW you copied to Ubuntu side.

I have both Vista and Ubuntu installed, with both having WoW. Vista version I can copy to Ubuntu side if I wish to and run the copied version in Ubuntu. I do nothing else with the Vista version. Vista side does not know anything about me even having Ubuntu installed...it can not see Ubuntu. Ubuntu, however, can access the Vista side if I wish to (the partitions are visible in the Nautilus browsing view, for example).

Whatever you may end up doing to get your WoW working, I wish you good luck in the effort. :)

---

### Post by Frostsniper on 2009-05-23
Right.... just... nvm... 
i found around WOTLK problem i just copied all the files over to a folder when i dual booted into windows and then grabed them via ubuntu and presto started to install! and so far so good *crosses fingers*

---

### Post by Frostsniper on 2009-05-23
ok i got it working now and its running great so far ! going to see how it holds up in some heroics tonight, that should be fun, well thanks again for all your help!

I LOVE UBUNTU!!

---


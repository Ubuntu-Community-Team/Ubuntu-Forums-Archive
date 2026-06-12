---
title: "New Ubuntu User Observations..."
date: 2013-03-18
forum: Testimonials &amp; Experiences
---

### Post by artphotodude on 2013-03-18
I come from a background of Mac/PC (20 years as tech-support consultant, custom system/software design and maintenance).  This year, have decided to really get into Linux and Ubuntu seems to be the flavor of choice from most users.  Here are a few observations from a new user:

1. I see why people call it OSX without the BS.  Very user friendly, well laid-out, fast and functional.

2. The system seems pretty hardy (have installed both 32 and 64 bit versions), and have done multiple hard-resets during installs, processes and so forth and have been amazed at how well the system recovery worked.  One time the sound failed to come up on reboot, but a second pass through the system recovery fixed it right up.

3.  LOVE the security options available.  Would be nice if things like **secure virtual memory** **swap space** didn't have to be done through terminal, but am glad nonetheless that they are there.


Now the not so great stuff:

4. HATE the repository system.  Would be nice to have it as a casual option, but there is no excuse for not being able to download pkgs and install them directly.  Adding PPAs failed with errors twice through terminal, and even when adding them through the Software Center Gui, took almost an hour to refresh.  THIS IS LAME.

5. The partitioner needs to be able to deal with newer hard drives better.  When using the install partitioner, it failed to see the format of the laptop drive I was installing on and wound up miss-matching somewhat.  **Gparted** needs to be in the initial install setup (or at least a light version of it). One of the systems I created will forever read as 'Not Clean' in the Gui Disk Utility because of this - though the Terminal version seems to be able to see everything is OK.  Also, there needs to be a way to commit to partition changes from the installer, without having to install at that time.  It seems impossible to setup swap space AND do full-disk encryption.  

6.  I can deal with not having a real **Applications/Programs **folder, but not having an **Application Data** or **Application Support** folder is ludicrous.  I have Stellarium on OSX and the extra Star Maps are well over 1GB, but I cannot copy these (universally compatible) files to Ubuntu because there is no way to identify where Ubuntu stores extras, dependences and support files.  

7. Ubuntu isn't alone in this these days, but it is never cool to have  the clipboard clear copied data when the source is closed.  It should  persist long enough to be copied to where it is going.


Overall Ubuntu is a great system for average users and those both sick of the propriety nonsense from MS and Apples as well as those really interested in security.  But for power users and admins used to having precise control over their systems it is a bit too 'nanny'.

Overall rating:  70%  :)

---

### Post by QIII on 2013-03-18
*Moved to **Testimonials & Experiences***

---

### Post by alphacrucis2 on 2013-03-18
> **artphotodude said:**
> 
4. HATE the repository system.  Would be nice to have it as a casual option, but there is no excuse for not being able to download pkgs and install them directly.  Adding PPAs failed with errors twice through terminal, and even when adding them through the Software Center Gui, took almost an hour to refresh.  THIS IS LAME.





You can download and install packages directly. You download your deb file and install it via 'sudo dpkg -i <path/name of package>' or if you double click on the deb file from nautilus it will install it using the sw centre. You can also install a program called gdebi if you want a lighter weight gui program to install your debs. The main advantage of the apt package system is that it keeps all the packages in managed repos which is presumably a bit more trust worthy than downloading debs from random websites. I've no idea why your sw updates are taking an hour. Maybe you should try different mirrors. There are large number of different mirrors you can choose. By default it will choose one that is in your own country if there is one but your local one might be slow.

---

### Post by tejpatel98 on 2013-03-18
> [COLOR=#000000]2. The system seems pretty hardy (have installed both 32 and 64 bit versions), and have done multiple hard-resets during installs, processes and so forth and have been amazed at how well the system recovery worked. One time the sound failed to come up on reboot, but a second pass through the system recovery fixed it right up.[/COLOR]

I agree with this statement. I have also done many unexpected shutdowns with no errors or failing.

---

### Post by mastablasta on 2013-03-19
> **artphotodude said:**
> 6. I can deal with not having a real **Applications/Programs **folder, but not having an **Application Data** or **Application Support** folder is ludicrous. I have Stellarium on OSX and the extra Star Maps are well over 1GB, but I cannot copy these (universally compatible) files to Ubuntu because there is no way to identify where Ubuntu stores extras, dependences and support files. 

Have you read the manual or checked the wiki? It says where to look for this and what the file structure is. also i think there is a command that will show all linked files. application settings are often in hiden files in home folder. For example: [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

> 
7. Ubuntu isn't alone in this these days, but it is never cool to have the clipboard clear copied data when the source is closed. It should persist long enough to be copied to where it is going.

Huh? never happened to me. in fact the clipboard i use saves a couple (i think 10) copies. so i can even retreive a clipboard i created 2 hours ago.

> 
Overall Ubuntu is a great system for average users and those both sick of the propriety nonsense from MS and Apples as well as those really interested in security. But for power users and admins used to having precise control over their systems it is a bit too 'nanny'.


huh? i guess that is why they use it on critical systems?
i am sure google for example is just an average user....

---

### Post by alphacrucis2 on 2013-03-19
> **mastablasta said:**
> 

Huh? never happened to me. in fact the clipboard i use saves a couple (i think 10) copies. so i can even retreive a clipboard i created 2 hours ago.


I think the default X clipboard has this issue but most people install much better ones.

---

### Post by mastablasta on 2013-03-19
i see. in that case the OP is right. I mean if it has a major bug like that then it shouldn't be a default clipboard or the bug should be fixed.

---

### Post by krishna.988 on 2013-03-19
This is a well known issue that has been documented here:


[https://wiki.ubuntu.com/ClipboardPersistence](https://wiki.ubuntu.com/ClipboardPersistence)

---

### Post by 3rdalbum on 2013-03-19
> **artphotodude said:**
> 4. HATE the repository system.  Would be nice to have it as a casual option, but there is no excuse for not being able to download pkgs and install them directly.  Adding PPAs failed with errors twice through terminal, and even when adding them through the Software Center Gui, took almost an hour to refresh.  THIS IS LAME.

Most people don't experience the problem you describe. Adding PPAs has always "just worked" for me, although it mystifies me why the terminal method is so ridiculously easy and the GUI method is so cumbersome. What PPAs have you been trying to add? If they no longer exist, that would explain the error messages.

Seriously, the repository system is fantastic. You don't need to go trawling through the web to find software, and then have to trust that it's not infested with malware. When there are new updates to your programs you will receive them through the normal update system, rather than have a dozen update daemons popping up (one for each program) as on Windows.

PPAs aren't ideal; it would be better to have finer-grained control over what packages you want to see from a particular PPA, and it would be better to get new major versions from the regular repositories instead of through PPAs. But it's a pretty good system, so much better than downloading software from websites manually, and this is the first time I've heard anyone say that they've had trouble with it.

You can download packages and install them manually. Dependencies will still be resolved through the repositories, if this isn't what you want you can download the dependencies manually too... but then it gets complicated. I won't go into it now, but there's some pretty good reasons why a program package doesn't contain everything it needs, hence dependencies. PM me if you really want to know.

> 5. The partitioner needs to be able to deal with newer hard drives better.  When using the install partitioner, it failed to see the format of the laptop drive I was installing on and wound up miss-matching somewhat.  **Gparted** needs to be in the initial install setup (or at least a light version of it). One of the systems I created will forever read as 'Not Clean' in the Gui Disk Utility because of this - though the Terminal version seems to be able to see everything is OK.  Also, there needs to be a way to commit to partition changes from the installer, without having to install at that time.  It seems impossible to setup swap space AND do full-disk encryption.  

I've never felt like I've had much confidence in the partitioner in the Ubuntu installer, either. Fortunately, my needs are simple.

> 6.  I can deal with not having a real **Applications/Programs **folder, but not having an **Application Data** or **Application Support** folder is ludicrous.  I have Stellarium on OSX and the extra Star Maps are well over 1GB, but I cannot copy these (universally compatible) files to Ubuntu because there is no way to identify where Ubuntu stores extras, dependences and support files.  

It's not ludicrous. It's just a different way of doing things; on Linux there are lots of places and everything has its place. You'll probably find that the extra star maps go into .stellarium (a hidden folder in your home directory) or, if there are multiple users on your computer who will all want the maps, into a folder like /usr/share/stellarium. That's a fairly standard place, BTW: /usr/share/programname for most of the files you would have found in Application Data or Application Support in OS X.

It makes it easier for all icons to be in one of two places, and all application launchers to be in one of two places, and all libraries to be in one of three places, and all manual pages to be in one place, etc. That way, the associated systems can find what they want without having to look through the whole disk.

Most of the time you won't need to delve into folders like this, either.

> 7. Ubuntu isn't alone in this these days, but it is never cool to have  the clipboard clear copied data when the source is closed.  It should  persist long enough to be copied to where it is going.

You're right, it's a ridiculous limitation. Application developers blame X, X developers blame the application developers, but the problem never gets fixed and it's been with Linux and Unix since the beginning. You can download a clipboard manager which will do what you want to do, but the fact that the Gnome desktop doesn't ship with one and Ubuntu doesn't ship with one is seriously embarassing.

---

### Post by stalkingwolf on 2013-03-19
i always use gparted either in the live session or the gparted disc to format my drive the way i want then during installation i select something else then the partition where i want to install.
i prefer synaptic over software center and make sure gdebi is installed.
I have 2 applications that i install on almost every install both are installed in terminal , only issue i have had with repositories was when a version was no longer supported.

---

### Post by rewyllys on 2013-03-19
> **3rdalbum said:**
> . . . . You can download a clipboard manager which will do what you want to do, but the fact that the Gnome desktop doesn't ship with one and Ubuntu doesn't ship with one is seriously embarassing.

Parcellite 1.0.2rc5 works beautifully for me as a clipboard manager, and it's available via the Synaptic Package Manager.

---

### Post by matt_symes on 2013-03-22
> But for power users and admins used to having precise control

That's what the terminal is for.

I have extensive experience with Windows and less experience with Linux but i can assure you, it's far easier to get a Linux box to do what you want than a Windows box :P

Me thinks this is only the unfamiliarity of Linux to you.

However, subjective feelings are important as they help you pick the right tool for you.

---

### Post by artphotodude on 2013-03-25
Thanks for all the feedback on the original post!  I did find that most of the application support files were in the home folder.  Am somewhat curious how it is able to share these with multiple users, but will give that a try later.  PS, to those that felt I had made light of Ubuntu as being good for "Casual Users" that was actually a compliment, because it is the unsavvy computer users that are always the most trouble, and the system has truly gotten 'easy' enough to serve even the least educated user.  The smart folks can usually make do on any system.

---

### Post by artphotodude on 2013-03-25
> **matt_symes said:**
> That's what the terminal is for.

I have extensive experience with Windows and less experience with Linux  but i can assure you, it's far easier to get a Linux box to do what you  want than a Windows box [IMG]http://ubuntuforums.org/images/smilies/icon_razz.gif[/IMG]

Me thinks this is only the unfamiliarity of Linux to you.

However, subjective feelings are important as they help you pick the right tool for you.
I am not saying it is difficult to customize on some levels, but things that are normally very simple on a Mac, for instance, like adding folders to the Launcher, Configuring Start-up Applications and activating secure virtual memory are pretty much beyond the reach of non-powerusers in Ubuntu. Probably just as well as most of them woundn't generally care about such things, but in say the case of a laptop, that might be stolen, encryption of discs and VM should either be easier to do or automatically done. home-disc encryption is pretty easy, but if a swap file isn't encrypted, there is a real danger of a criminal pulling your admin password from it.

---


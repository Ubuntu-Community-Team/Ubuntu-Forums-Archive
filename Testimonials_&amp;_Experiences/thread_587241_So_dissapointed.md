---
title: "So dissapointed"
date: 2007-10-22
forum: Testimonials &amp; Experiences
---

### Post by scorpiusmaximus on 2007-10-22
I've got to say that I am so very disappointed in my Linux experience so far. I started on the old Apple before it was Mac in the 80's in college. I've been with Windows since 3.0 and I know it forward an backward. 
I have heard so many great things about Linux and wanted to learn something new and enjoy a new experience but it is not working out for me. II was hoping to have a new Small Business system and some educational stuff for the kids. I installed 7.4 a few weeks ago and I was very impressed with the customizations but no hardware works. I had ATI 3D working and my Brother-8500 printing until I upgraded, now that does not even work. Video card does not work properly. No dual monitor support. (obviously) No printer or scanner. TV-tuner & FM radio do not work. I have installed and re-installed 'till I am blue, trying to get something productive. I have spent endless days in support. Now it appears that if I was able to print & scan, I can not find a good document manager. There is no financial software.
The only thing I am finding this good for is making my wife angry for being on the computer even more than usual, playing some games, checking E-mail & surfing the web. Am I missing something?!!
I have the patience of Job but this is no the experience I was hoping for. Can anyone offer any advice??

---

### Post by Coldkill on 2007-10-22
My advice would be to ask for help in the forum. Start a new topic for whatever questions you have for each thing that doesn't work for you.
I personally can't help because of my lack of knowledge but everyone else here is really helpful if you ask.

---

### Post by radovan01 on 2007-10-22
Sometimes I feel like you, but I have to admit  (even to myself) that I have spent with windows, let's say 14 years and with linux only 3 years. Quite a difference, don't you think? We have to get into it. I am happy with linux these days. FreeBSD, is what makes me unhappy right now.

---

### Post by ticopelp on 2007-10-22
If you want financial software, there's gnu-cash:

```
sudo apt-get install gnucash
```

It certainly depends on the hardware -- I've been fortunate in that all my hardware (scanner, iPod, digital camera) has worked out of the box, including my video card. Gutsy seems a bit twitchy, but I've had no significant problems with it.

I second the notion that if you want help with a particular issue, ask around in the forums and see if you can get help.

---

### Post by some_random_noob on 2007-10-22
If your printer originally worked, then you should be able to get it going again in the newer version. As for dual monitors I believe that 7.10 has such support.

Best of luck :) ... just remember that Ubuntu isn't perfect for everyone.

---

### Post by scorpiusmaximus on 2007-10-22
Thanks for all the support! I have not given up but I really think I have almost exhausted my options on some things, like the Brother MFC-8500. I've searched Brother and all of their resources (no support whatsoever,) CUPS, Google/Linux, forums. I have not personally posted problems but I have found same or similar problems.
I spent $50.00 on Andrew Hinson/Paul Hudson's Ubuntu Unleashed and read most of it, found some great advice (in addition to the forums) and I've tried everything thrown at me and just can't get some things to work. I am working with an already built system and the hardware was purchased without consideration of Linux compatability; apparently not. 
I was really hoping for something I did not have to spend endless hours & days on a problem that may not be solvable and having so many of these issues.  I know the resources of Linux are extensive and I have just only touched the surface but I feel like I am back in College. I just do not think I have the time for this. I wanted a hobby not another job. Know what I mean??

---

### Post by Jose Catre-Vandis on 2007-10-22
Here's the link for your printer
[http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/)
choose each of the links for lpr and printer and scanner and download
suggest you read through howtos for similar printer on the forum for what to do next
Brother is actually one of the better manufacturers for linux support

Tell me about your TV tuner card, hopefully can give you some pointers ( i had to wait 9 months before I got mine going :)

---

### Post by zero244 on 2007-10-23
Ive only been using Linux for about 10 months......I was able to learn the basics, mainly due to this and other forums. Ive started using Computers in DOS 5.0 till the present.
Linux in my opinion is a superior OS over Windows. My Windows install is completely locked down but I still have to worry about it.
I dont even think about security with Linux.
The Linux file system is more reliable than ntfs or fat32.
It is very easy to compromise a Windows machine if you don't use third party security software.
ID theft on a Windows machine is much more possible than on a Linux computer.
If you do online transactions is our financial future worth the risk of using Windows.
I use Windows for scanning and games.
My confidence in Linux and the fact that is a very cool looking OS, very stable and reliable has sold me on the whole open source movement.
If you learn the basics of one version of Ubuntu that will pretty much cover you for future releases.
Vista as a whole has a pretty big learning curve when compared to XP.
If Microsoft doesn't send Balmer back to the mail room........MS is going to go down hard.
The arrogance of Apple and Microsoft is why so many people are moving to Linux.

---

### Post by scorpiusmaximus on 2007-10-28
I definately get the Linux thing. I am drawn, compelled to keep coming back to my Ubuntu partition. I have the same worries and complaints about Windows.
It's that the few things that do (or did) not work are pretty dog-gone important (i. e. video, printing) and I am going to work on them till they are fixed.
Just a follow up; I downloaded the v. 7.10 Ubuntu and installed it from scratch. The restricted drivers module had the option to use ATI Proprietary Drivers already included. I just had to select and it downloaded and installed the needed drivers. Pretty easy after going thru all that former frustration. My 3D rendering works, now to figure out the Dual Monitors. Any suggestions would be greatly appreciated.
On the Brother MFC-8500 printer/scanner, I have followed all of the instructions many times and still have no printing. The printer is recognized, driver suggested is another because mine is not listed, even after downloading and installing drivers from Brother ( I have read and followed all the FAQ and suggestions) , the print que shows a job go thru, printer says "receiving data from computer"  then they both disappear but nothing prints.
TurboCash is the Quickbooks equivalent I was looking for. If I can get PaperPort 11 to work using Wine I will be a very happy camper.
Thanks much for the help. I see that community support is not lacking, whatsoever.

---

### Post by kellemes on 2007-10-28
Don't forget apple/mac ships there OS with there hardware.. driver support for devices - often apple too - will work out of the box.
I just bought a new printer and only get the Windows-driver, I had this printer working in no time but only because I figured it out before I bought it.
GNU/Linux comes from the serverside of town and clasicaly is setup and managed by people having no problem tweaking the system to get there "unsupported" device running.
GNU/Linux isn't *yet* idiot-proof, although *buntu is getting there.

---

### Post by markharding557 on 2007-11-01
I had a problem with printer drivers very much like yours where an upgrade to gutsy stopped the driver working
i solved this by:
1 uninstalling the printer
2 installing lpr driver as on fiesty
3 installing cupswrapper driver
these must be in this order
now my brother printer works

---

### Post by scorpiusmaximus on 2007-11-01
Thanks much for the advice but now I have a new printer problem. I did just that. Uninstalled and then re-installed, lpr first and then CUPS. I receive errors when I install the lpr now and it jams my packages managers, update and synaptics. It says mfclpr8500 needs to be re-installed but can not find the package for it. I can not update or install any packages. I can not re-install or uninstall the driver. I get errors doing so.
I have re-installed the OS, AGAIN, MANY TIMES, and the same thing happens. I am just without a printer until I either buy a different one to use with Ubuntu or I get some new direction to go in. 
The MFC8500 was purchased some time ago with a purpose in mind, home small business. I did not consider, at the time, using it with Linux.
I still think someone can help get me running but I have had to drop it for a while to get some work done, in WINDOWS. (ugh!)

---

### Post by markharding557 on 2007-11-01
if your package manager gets stuck all you need so is delete the offending deb from /var/cache/apt/archives you do that as root 'gksu nautilus on the console'and the package manager should work again
as for the printer double check you have the correct files,it's easy to get the wrong one in mistake
you have not posted the errors
so i can't comment on that

---

### Post by scorpiusmaximus on 2007-11-01
rhett@AthlonXP2100:~/Desktop$ sudo dpkg -i --force-all mfc8500lpr-1.1.2-1.i386.deb
Selecting previously deselected package mfc8500lpr.
(Reading database ... 88969 files and directories currently installed.)
Unpacking mfc8500lpr (from mfc8500lpr-1.1.2-1.i386.deb) ...
Setting up mfc8500lpr (1.1.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/MFC8500': No such file or directory
chown: cannot access `/var/spool/lpd/MFC8500': No such file or directory
chgrp: cannot access `/var/spool/lpd/MFC8500': No such file or directory
chmod: cannot access `/var/spool/lpd/MFC8500': No such file or directory
/var/lib/dpkg/info/mfc8500lpr.postinst: 4: /etc/init.d/lpd: not found
dpkg: error processing mfc8500lpr (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 mfc8500lpr

Any help would be greatly appreciated. Thanks.

---

### Post by scorpiusmaximus on 2007-11-01
Second try:

rhett@AthlonXP2100:~$ sudo dpkg -i --force-all mfc8500lpr-1.1.2-1.i386.deb 
(Reading database ... 88983 files and directories currently installed.)
Preparing to replace mfc8500lpr 1.1.2-1 (using mfc8500lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc8500lpr ...
/var/lib/dpkg/info/mfc8500lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc8500lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc8500lpr-1.1.2-1.i386.deb

---

### Post by scorpiusmaximus on 2007-11-01
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package mfc8500lpr needs to be reinstalled, but I can't find an archive for it.'

---

### Post by wolfen69 on 2007-11-02
> **scorpiusmaximus said:**
> I definately get the Linux thing. I am drawn, compelled to keep coming back to my Ubuntu partition. I have the same worries and complaints about Windows.
It's that the few things that do (or did) not work are pretty dog-gone important (i. e. video, printing) and I am going to work on them till they are fixed.
Just a follow up; I downloaded the v. 7.10 Ubuntu and installed it from scratch. The restricted drivers module had the option to use ATI Proprietary Drivers already included. I just had to select and it downloaded and installed the needed drivers. Pretty easy after going thru all that former frustration. My 3D rendering works, now to figure out the Dual Monitors. Any suggestions would be greatly appreciated.
On the Brother MFC-8500 printer/scanner, I have followed all of the instructions many times and still have no printing. The printer is recognized, driver suggested is another because mine is not listed, even after downloading and installing drivers from Brother ( I have read and followed all the FAQ and suggestions) , the print que shows a job go thru, printer says "receiving data from computer"  then they both disappear but nothing prints.
TurboCash is the Quickbooks equivalent I was looking for. If I can get PaperPort 11 to work using Wine I will be a very happy camper.
Thanks much for the help. I see that community support is not lacking, whatsoever.

if you have tried everything and still cant get your printer going, consider getting a new one. (HP has awesome support in linux) i kept windows around just because of my lexmark all in one. but when i bought an HP, i was able to give up windows completely. it was well worth it.

---

### Post by Johnsie on 2007-11-02
I'm sorry to hear that your hardware manufacturers haven't produced Linux support for their hardware. That's bad service on their part. Yes, Ubuntu has a long way to go to support all hardware.... The problem isn't really Ubuntu's fault though, it's the hardware manufacturers fault for not releasing the drivers in an open source format. That has been changing recently with more hardware manufacturers supporting open source and Linux.

If your hardware isn't working out of the box then I suggest that you go over to [http://launchpad.net](http://launchpad.net) and report that as a bug.  The developers at Ubuntu are committed to improving hardware support on Linux and hopefully someone will be able to resolve your problem. That might take some time but it's certainly important that hardware issues are raised so that Linux can be made better. Linux is community based to community members need to flag issues like this. There's also alot of other sites that centre around Linux driver development and hardware support. By reporting your issues you help Linux evolve and you will also be ahelping people who have similar issues.

I'm not suggesting getting rid of your old equipment, but maybe in the future you should vote with your wallet and buy hardware that you know will work well with Linux.

---


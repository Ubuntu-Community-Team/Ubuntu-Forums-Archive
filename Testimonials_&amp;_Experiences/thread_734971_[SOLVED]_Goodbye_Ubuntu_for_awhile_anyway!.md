---
title: "[SOLVED] Goodbye Ubuntu for awhile anyway!"
date: 2008-03-25
forum: Testimonials &amp; Experiences
---

### Post by John L on 2008-03-25
Hi folks

I've been using Ubuntu since 5.04 on a Dell Dimension 5150.  After getting over the initial scare of partitioning and finding my way round Ubuntu I was delighted that I took the plunge.  Spending time researching and solving small issues was a learning experience and thanks to these forums that was a bit of fun as well.  

However since 7.10 I've been having problems.  Mainly with my radeon x300 graphics card.  I tried Hardy and had the same problems.  Eventually I loaded up Linux Mint and found that I was able to get the desktop effects to work.  Unfortunately my computer stopped working last week and I decided to buy a new one.

Its a decent machine - Intel Core duo CPU E4500, nvidia 8600 GS, 500GB hard drive with 2GB ram and of course it came preloaded with vista. I thought great no more ATI drivers!  So I repartitioned the disk (the long way as I didn't know at that stage that I could shrink the disk in vista!!) and installed ubuntu.  Seemed painless enough.  

Problem was that I couldn't boot into vista.  Ubuntu loaded fine but I couldn't select vista (keyboard didn't seem to work).  I tried booting from my old hard drive which had XP and Linux Mint in grub but I ran into the same problem.  

It seems to me as an ordinary punter with an interest in Ubuntu that since 7.10 something has gone astray.  7.04 installed beautifully.  7.10 and 8.04 (alpha 6) have issues which for me has made the experience way too difficult.  For all the negative reviews I had previously read about vista it did install fairly quickly.  After I installed the various drivers it had no problem dealing with the hardware.  Sure I am running antivirus and spyware software but so far I've had no problems.

So I think I will give ubuntu a miss for awhile.  I am disappointed as my heart is with open source software and I begrudgingly have to accept that vista is probably my best option at this stage.  

Is there anyone else who has the same experience?

John

---

### Post by chewearn on 2008-03-26
You have post count of 2; why, may I ask, you not asking for help?


> **John L said:**
> Its a decent machine - Intel Core duo CPU E4500, nvidia 8600 GS, 500GB hard drive with 2GB ram and of course it came preloaded with vista. I thought great no more ATI drivers!  So I repartitioned the disk (the long way as I didn't know at that stage that I could shrink the disk in vista!!) and installed ubuntu.  Seemed painless enough.  

Problem was that I couldn't boot into vista.  Ubuntu loaded fine but I couldn't select vista (keyboard didn't seem to work).  
Vista refuse to load, and so it's ubuntu fault.

> For all the negative reviews I had previously read about vista it did install fairly quickly.  After I installed the various drivers it had no problem dealing with the hardware.  Sure I am running antivirus and spyware software but so far I've had no problems.But did you stop to ask, why vista is not allowing you to load ubuntu in the vista bootloader?  Double standard, no?

---

### Post by peitschie on 2008-03-26
Probably because we often seem like a judgemental bunch... 

Regarding the issue that caused you to abandon Linux, you said you couldn't select Vista from the boot menu... and said you had the same problem with your old XP / Mint hard drive... this seems to me to indicate a problem INDEPENDANT of linux.  I'm assuming you used to be able to boot your XP / Mint set up on your old computer?  On your new computer, you may have to enable the USB Keyboard support in the computer BIOS... this IS NOT A LINUX PROBLEM!!!  You'd get the same issue even in the Vista boot loader.

The bit I can't resolve however, is that it sounds like Ubuntu runs fine.  So your only gripe about the new setup is that you couldn't boot windows (which as I just said, is a non-linux related problem)?  Why has this caused you to quit so quickly?  Especially having been with things from 5.10!  Is this the last straw?  If so, what were the other problems you had with 7.10?  8.04 doesn't count yet by the way as it is still in beta.  Again, what issues are leading you to conclude things are getting harder rather than easier?

---

### Post by ukripper on 2008-03-26
> **John L said:**
> 

It seems to me as an ordinary punter with an interest in Ubuntu that since 7.10 something has gone astray.  7.04 installed beautifully.  7.10 and 8.04 (alpha 6) have issues which for me has made the experience way too difficult.  For all the negative reviews I had previously read about vista it did install fairly quickly.  After I installed the various drivers it had no problem dealing with the hardware.  Sure I am running antivirus and spyware software but so far I've had no problems.

John

You might want to open your grub menulist by ```
sudo gedit /boot/grub/menu.lst
``` 
and then add **vga=791** **pci=noacpi ** 

more option here [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

VISTA Business crashed on me 3 times within 2 days of my new laptop with BSOD so I guess everything is not for everyone.

---

### Post by John L on 2008-03-26
Hi guys

Fair comment Astala Vista re asking for help.  I guess I have been reluctant to jump right in.  Lots of my questions were answered by searching through the forum or the internet.  As I mentioned I had no big issues with installation until 7.10 and that was mainly due to the ATI driver problems.  I wasn't overly interested in desktop effects but I liked to play open arena and I spent hours trying to get it and some other games working properly.  Only got it going when I installed Mint.

I take your point about Vista as well.  However as time goes by more and more people will be facing the problem of trying to dual boot with vista. I had no problems with XP and while Microsoft seem to have made it more difficult to dual boot with a non-microsoft OS, it is still something I think that needs to be worked on.  Maybe it is as Peitschie suggests a non linux problem (thanks Peitschie - enabling usb keyboard support in BIOS sounds like it might help &#8211; I&#8217;ll have a go tonight) and I have been unfair in my comments.

I would love to be able to move over entirely to Linux but I still need to run windows programs eg; mobile phone software, webcam for skype and windows games that my daughter plays.

Overall, I think I was disappointed that the install didn&#8217;t go as easily as I had hoped.  I was really looking forward to seeing how ubuntu would react on a higher spec machine. While ubuntu loaded I couldn&#8217;t enable desktop effects and I got fed up and thought that this is a lot of hassle.  So I was letting off a bit of steam but I accept that, as Astala Vista points out, I could have asked for help.    

Hi Ukripper &#8211; thanks for that.  I&#8217;ll try to enable the usb keyboard first and if that doesn&#8217;t work I&#8217;ll edit grub as you suggested. 

I hope that I can manage to sort this out as I enjoy being part of the Ubuntu Community even if I have until now been anonymous!

Thanks for the replies.

John L

---

### Post by fourthofjuly on 2008-03-26
> **John L said:**
> Hi guys

Fair comment Astala Vista re asking for help.  I guess I have been reluctant to jump right in.  Lots of my questions were answered by searching through the forum or the internet.  As I mentioned I had no big issues with installation until 7.10 and that was mainly due to the ATI driver problems.  I wasn't overly interested in desktop effects but I liked to play open arena and I spent hours trying to get it and some other games working properly.  Only got it going when I installed Mint.

I take your point about Vista as well.  However as time goes by more and more people will be facing the problem of trying to dual boot with vista. I had no problems with XP and while Microsoft seem to have made it more difficult to dual boot with a non-microsoft OS, it is still something I think that needs to be worked on.  Maybe it is as Peitschie suggests a non linux problem (thanks Peitschie - enabling usb keyboard support in BIOS sounds like it might help &#8211; I&#8217;ll have a go tonight) and I have been unfair in my comments.

I would love to be able to move over entirely to Linux but I still need to run windows programs eg; mobile phone software, webcam for skype and windows games that my daughter plays.

Overall, I think I was disappointed that the install didn&#8217;t go as easily as I had hoped.  I was really looking forward to seeing how ubuntu would react on a higher spec machine. While ubuntu loaded I couldn&#8217;t enable desktop effects and I got fed up and thought that this is a lot of hassle.  So I was letting off a bit of steam but I accept that, as Astala Vista points out, I could have asked for help.    

Hi Ukripper &#8211; thanks for that.  I&#8217;ll try to enable the usb keyboard first and if that doesn&#8217;t work I&#8217;ll edit grub as you suggested. 

I hope that I can manage to sort this out as I enjoy being part of the Ubuntu Community even if I have until now been anonymous!

Thanks for the replies.

John L
since you have a superfast machine, you can try Virtualbox... don't know if it works with Vista, I use it for XP...

install Ubuntu, install Virtualbox, 

run Virtualbox & install Vista within... 

you will have Vista running under Ubuntu...!!! no need to dual boot...

do check out this link

[http://liferedux.wordpress.com/2008/01/01/howto-run-windowsxp-inside-ubuntu/]("http://liferedux.wordpress.com/2008/01/01/howto-run-windowsxp-inside-ubuntu/")

please let me know if it works....

regards,

devang.

---

### Post by wolfen69 on 2008-03-26
if you were going to buy a new computer, why didnt you get one with ubuntu pre-installed and add windows to it? (ding,ding, light goes on) didnt think of that? oh well.

---

### Post by peitschie on 2008-03-26
Hi again John,

Glad we haven't scared you off yet :-).  Definitely I agree linux has quite a few rough edges to work off... but in my opinion it is advancing far faster and far more usefully than windows!

Well, to shed some more light on a few of your queries, you can actually get native skype with video for linux (installed via repositories from Medibuntu), I've been using this for a few months now and it works a treat!

Mobile sync programs, as another person has pointed out, You can run an emulator inside linux running windows.  I have successfully done this to link up my  Sony Ericcsson programs.  If you can be patient a few years, there are a few other major projects (OpenSync for example) on the go that aim to be able to sync your mobile with linux in all sorts of creative ways (e.g., phone contacts with your evolution address book, or with gmail contacts!!!).  Either way, get back to us with more specific information and we can help!

What kind of games does your daughter play...?  You'd be surprised how many work under linux now (I play half-life 2, and team fortress 2 via "wine").

Regarding the ATi drivers, I had the same problem as you for a while (again, I agree the installation was rather difficult, but it wasn't insurmountable.  Fortunately I had a spare computer to search the net on).  There is a wonderful program called "Envy" ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)) that will actually download, compile & install the latest drivers for either Ati or Nvidia.  It has entirely saved my life as I was running an Nvidia 8800GTS on feisty which had no driver support.  Its a very simple program, requiring only 2 clicks or so to get the latest drivers.  Even a twit like me couldn't stuff it up very easily once I knew what type of graphics card I had.  This got me up and running Compiz without any extra hassles (p.s., it looks very very very nice with the flashy stuff)

Well, I do hope you'll stay around and be involved. It sounds a bit to me like you had a chunk of frustration that really put you off Linux... all I can say is don't start believing the grass is green on the (Microsoft) side!  I tried using windows a few weeks ago... uggh... so slow and restricting! Linux makes up for its rough edges on the software, by having a community with lots of soft edges :D.  I sometimes think programmers leave bugs in their software just so people will try and talk to them... :lolflag:

---

### Post by chewearn on 2008-03-26
> **John L said:**
> Hi guys
...
Thanks for the replies.

John L

Welcome back!  Glad we manage to get you to reconsider.

:popcorn:

---

### Post by John L on 2008-03-27
Hi Devang

That might also be a solution.  I think for the moment tho I'll try the dual boot route.  If I can't sort it out I'll give virtualbox a go.

John

---

### Post by John L on 2008-03-27
> **wolfen69 said:**
> if you were going to buy a new computer, why didnt you get one with ubuntu pre-installed and add windows to it? (ding,ding, light goes on) didnt think of that? oh well.


I'm not entirely sure whether you're having a dig or a laugh!  Preinstalled ubuntu probably would have brought me down the dell route and it was a dell machine that let me down (outside of warranty of course!).  So I bought a medion md8830. 

John

---

### Post by John L on 2008-03-27
Hi Peitschie

Thanks again. 

Its a while since I tried skype on linux.  I had problems getting the system to recognise my webcam so I gave up on the attempt.  Wammu for the mobile did the basics well enough but opensync sounds promising.  I also gave Envy a go in 7.10 but I still couldn't enable desktop effects after installing the latest ATI driver.  My daughter plays Sims with various add on packages.  I haven't gone any where near trying to install it in a linux environment!!

Of more immediate concern though relates to my attempts last night to install 8.04.  I downloaded the latest image and burned it to cd.  This time, however, I got as far as the install options but no further (up and down keys worked but when I pressed enter nothing happened).  I figured that the image on the cd was corrupt so I burned another but again it wouldn't install.  I have since downloaded the alternative image but it was too late in the night to try an install.  I'll try it tonight tho.

In relation to enabling usb keyboard support in bios, I checked my bios settings and it would appear that this was already enabled (there was no specific reference to a usb keyboard but all the references to usb support were enabled).  If I can do an install tonight I'll try Ukrippers suggestion to edit grub.

If I can get past the basic install I'm sure I'll have loads of follow up questions to annoy you guys with! Now look at what you started :lolflag:

John

---

### Post by fourthofjuly on 2008-03-27
> **John L said:**
> Hi Devang

That might also be a solution.  I think for the moment tho I'll try the dual boot route.  If I can't sort it out I'll give virtualbox a go.

John
for dual boot, if you have data on your disk, do take a backup before you undertake partitioning (please do not compromise on this)

if Vista is already installed and you do not have free space, please run defragmenter before you resize (reduce) its partition to make free space for Ubuntu

---

### Post by ukripper on 2008-03-27
for sync you might want to try grsync [http://packages.ubuntu.com/gutsy/x11/grsync](http://packages.ubuntu.com/gutsy/x11/grsync) and it is in gutsy repos

or what i use synkron [http://synkron.sourceforge.net/](http://synkron.sourceforge.net/). it is a top notch QT app

EDIT:
The reason why i use synkron is because it has scheduler inbuilt in there whereas grsync needs configure with cron.

---

### Post by pm124493 on 2008-03-27
Don't be hasty too leave. I have Vista and Ubuntu Hardy Heron Alpha 6 on the same machine. I could dual boot with both GRUB or Vista boot loaders. Since I do not trust Vista (MS) to properly leave GRUB alone I decided to use the Vista boot loader. I recommend you download BCDEdit and TweakVI for vista. They are freeware. Install GRUB to the partition or HD you have Ubuntu loaded. I use two HDs to keep things clean. Vista does not mind being installed on a second HD or partiton. The drive letter maybe other than C: though.

Use BCDEdit to modify the Vista Boot Loader. Just name the entry as Ubuntu and tell it what partition or HD and partition GRUB has been installed. The next time you boot Vista you will have an entry for Ubuntu and all will be well. 

The greatest thing about Ubuntu is this forum. Help is just a question away.

INTEL Q6600, 4GB DDR2 PC6400, 1x 500GB Sata HD, 1x 300GB Sata HD, 1x Plextor 712SA Sata DVD+RW, EVGA nVidia 9600GT, Gigabyte GA-P35-DS3L MB, ViewSonic 19" LCD

Pete

---

### Post by John L on 2008-03-27
> **fourthofjuly said:**
> for dual boot, if you have data on your disk, do take a backup before you undertake partitioning (please do not compromise on this)

if Vista is already installed and you do not have free space, please run defragmenter before you resize (reduce) its partition to make free space for Ubuntu

Good advice.  I have made a number of backups to be sure to be sure:)

John

---

### Post by John L on 2008-03-27
> **ukripper said:**
> for sync you might want to try grsync [http://packages.ubuntu.com/gutsy/x11/grsync](http://packages.ubuntu.com/gutsy/x11/grsync) and it is in gutsy repos

or what i use synkron [http://synkron.sourceforge.net/](http://synkron.sourceforge.net/). it is a top notch QT app

EDIT:
The reason why i use synkron is because it has scheduler inbuilt in there whereas grsync needs configure with cron.

Thanks for that.  If I manage to boot to ubuntu I definitely try both of them to see which works best for me.

John

---

### Post by John L on 2008-03-27
> **pm124493 said:**
> Don't be hasty too leave. I have Vista and Ubuntu Hardy Heron Alpha 6 on the same machine. I could dual boot with both GRUB or Vista boot loaders. Since I do not trust Vista (MS) to properly leave GRUB alone I decided to use the Vista boot loader. I recommend you download BCDEdit and TweakVI for vista. They are freeware. Install GRUB to the partition or HD you have Ubuntu loaded. I use two HDs to keep things clean. Vista does not mind being installed on a second HD or partiton. The drive letter maybe other than C: though.

Use BCDEdit to modify the Vista Boot Loader. Just name the entry as Ubuntu and tell it what partition or HD and partition GRUB has been installed. The next time you boot Vista you will have an entry for Ubuntu and all will be well. 

The greatest thing about Ubuntu is this forum. Help is just a question away.

INTEL Q6600, 4GB DDR2 PC6400, 1x 500GB Sata HD, 1x 300GB Sata HD, 1x Plextor 712SA Sata DVD+RW, EVGA nVidia 9600GT, Gigabyte GA-P35-DS3L MB, ViewSonic 19" LCD

Pete

Hi Pete

That seems very sensible and I've just finished having a go. It nearly worked for me but I keep hitting into the same problem. (maybe as I'm moving onto installation problems I should start a new thread in that forum but if its ok I'll continue on here)

I have a second sata drive hooked up so I decided to install ubuntu 8.04 beta (alternative image as I had problems with installing the main image - as I mentioned above the up down keys worked but it wont commence the selection - the f keys worked but "enter" had no effect!).  I disabled the main drive and made the 2nd drive the boot drive (not sure why I did this but it seemed a good idea at the time).  Anyway I inserted the new image cd and this time when I reached the install screen nothing at all worked!     

So I went back to a Mint Linux 4 image I had and this had no problems so I installed it on the second sata drive.  On the first reboot,  grub had picked up on Vista and I had no problems selecting between vista or Mint.   After booting to Mint I enabled the restricted drivers (feeling very confident at this stage!!) but when I rebooted the up/down keys again won't work and I was stuck on Mint! 

I re-enabled the first drive as the boot drive but I was still stuck on Mint.  So I edited grub so that Vista was the default.  I rebooted into vista and downloaded Tweak and EasyBCD.  I eventually set that up so that in the vista bootloader I had vista and Mint.  Happy that I had made progress I selected Mint and enabled the restricted drivers and rebooted BUT the up down keys again won't work (this time in vista bootloader!!) and I'm back to square one except now I'm stuck in Vista. 

I'm not sure where to go now.  Seems to be a keyboard thing but only in certain instances. Any ideas folks?  I definitely don't want to give up now.  I won't let it get the better of me!

John

---

### Post by azimuth on 2008-03-27
> **John L said:**
> 
I have a second sata drive hooked up so I decided to install ubuntu 8.04 beta (alternative image as I had problems with installing the main image - as I mentioned above the up down keys worked but it wont commence the selection - the f keys worked but "enter" had no effect!).

If I remember right from the last time I used an alternate install cd, The space bar and not the enter key was used to sellect the highlighted option.

---

### Post by John L on 2008-03-27
> **azimuth said:**
> If I remember right from the last time I used an alternate install cd, The space bar and not the enter key was used to sellect the highlighted option.

Hi Azimuth

Thanks for the suggestion.  I tried it and I'm afraid I had no luck.  However I changed my keyboard from a usb keyboard to a ps/2 model (which came with the new computer) and it started selecting again in the vista bootloader. (after discovering this I thought it had reverted but I was pressing the keys on the wrong keyboard!!).

So at least I've sorted that part out - I think.  Now need to think about why 8.04 is not working.  It could be the burn quality as I burned it at 48X in nero8.  I'll burn it again in linux at a slower rate and see if that makes a difference.

Cheers

John

---

### Post by ukripper on 2008-03-28
> **John L said:**
> 

So at least I've sorted that part out - I think.  Now need to think about why 8.04 is not working.  It could be the burn quality as I burned it at 48X in nero8.  I'll burn it again in linux at a slower rate and see if that makes a difference.

Cheers

John

Are you getting any specific error message during booting into hardy?

---

### Post by John L on 2008-03-28
> **ukripper said:**
> Are you getting any specific error message during booting into hardy?

No nothing at all - the install screen appears, the up down keys work, F4 etc works but when I press enter nothing happens.  Funny thing is that hitting enter on "boot from first hard drive" works.  

I tried burning it in brasero to a dvd but the same thing happened.

John

---

### Post by ukripper on 2008-03-28
> **John L said:**
> No nothing at all - the install screen appears, the up down keys work, F4 etc works but when I press enter nothing happens.  Funny thing is that hitting enter on "boot from first hard drive" works.  

I tried burning it in brasero to a dvd but the same thing happened.

John

Have you tried using hardy beta?

You need to try alternate install  CD, for some machines Live cd doesn't work properly.

Try downloading alternate cd from here [http://releases.ubuntu.com/releases/8.04/](http://releases.ubuntu.com/releases/8.04/)

and burn it.

---

### Post by John L on 2008-03-28
> **ukripper said:**
> Have you tried using hardy beta?

You need to try alternate install  CD, for some machines Live cd doesn't work properly.

Try downloading alternate cd from here [http://releases.ubuntu.com/releases/8.04/](http://releases.ubuntu.com/releases/8.04/)

and burn it.

Yeah I tried both.  In the alternative install screen I go do nothing at all - none of the keys worked.  

I'll try to install 7.10 tonight and wait for hardy 8.04 final.

John

---

### Post by ukripper on 2008-03-28
> **John L said:**
> Yeah I tried both.  In the alternative install screen I go do nothing at all - none of the keys worked.  

I'll try to install 7.10 tonight and wait for hardy 8.04 final.

John

Sounds like more of a keyboard not being detected at boot.

Is it a USB keyboard or PS2

---

### Post by John L on 2008-03-28
> **ukripper said:**
> Sounds like more of a keyboard not being detected at boot.

Is it a USB keyboard or PS2

I tried both (old usb keyboard and a new ps/2).  The USB keyboard was problematic when trying to boot Mint but when I changed it to the ps/2 it worked fine.  

It would seem that the usb settings in bios are enabled so its kinda surprising I'm having this problem.  

Thanks

John

---

### Post by John L on 2008-03-28
Hi folks

Glad to say that I've managed to install Gutsy and to dual boot with vista!!! I'm not entirely sure what exactly made the difference but I'm very glad I didn't give up.  Many thanks to those who made suggestions and encouraged me to stick with it.  It just got a bit frustrating.  I should have asked for help earlier.:)

Cheers

John

---

### Post by stalkingwolf on 2008-03-29
when burning your ISO's remember to burn them at 4x or slower.
for some reason that just works better.

---

### Post by lesemi on 2008-03-29
Hi John L

i ran into similar frustration at the beginning.  I find that often what blocks me with ubuntu or kubuntu is the video driver.

It seems you have purchased a pretty decent machine.
My advice and the simplest route is to do the following:

If you want dual boot - install windows first as it is greedy and will by default select your whole drive.
then install ubuntu or kubuntu (i prefer the latter) - and partition the drive using the gui.

once you have installed - first thing to do is open the /etc/apt/sources.list
and uncomment the multiverse.
type sudo apt-get update
type sudo apt-get upgrade.

You should have an uptodate fresh install.

then - this is the critical part if you want 3d acceleration and get the most of your video card.

download the debian package envy from [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

this will install ati or nvidia driver properly on your system.
this script works really nice.
note - i find it works best if you use the text 
in console 'envy -t'
Enjoy openarena.

for windows games  - my kids are always bugging me - 
i have installed wine for this purpose - wine has made significant progress in that respect  -  follow the guide at 'http://www.ubuntuguide.org' there are alot of goodies there.

My rule is to never use windows unless absolutely necessary!!

Don't give up

---

### Post by peitschie on 2008-03-29
Hi again :-)

I've been watching quietly... glad to hear you got things off the ground!  Hopefully its clear sailing from here... having said that, on the (likely?) chance it isn't, don't ever be to shy to ask for help again :-).  If nothing else it helps you remember you aren't alone in fighting computers lol!

Good luck and clear installing :-D

---

### Post by John L on 2008-03-29
Hi Stalkingwolf and Peitschie - Cheers:(

Hi Lesemi

Having the most up to date system definitely seems to help.  After installing gutsy last night I enabled multiverse and ran update manager.  All worked very well but I put off enabling restricted drivers until this morning.  

I was absolutely amazed this morning to find that enabling restricted drivers worked perfectly!!!  It seemed that the driver is the most up to date driver (version 100 something?).  The result is the most responsive ubuntu installation I have yet had the pleasure to use.:)  I'll save the advice you gave me re envy in case things break down.  

I'll have to have a serious go at running win games under wine.  Many thanks. 

John

---

### Post by chewearn on 2008-03-29
> **John L said:**
> Hi Stalkingwolf and Peitschie - Cheers:(

Hi Lesemi

Having the most up to date system definitely seems to help.  After installing gutsy last night I enabled multiverse and ran update manager.  All worked very well but I put off enabling restricted drivers until this morning.  

I was absolutely amazed this morning to find that enabling restricted drivers worked perfectly!!!  It seemed that the driver is the most up to date driver (version 100 something?).  The result is the most responsive ubuntu installation I have yet had the pleasure to use.:)  I'll save the advice you gave me re envy in case things break down.  

I'll have to have a serious go at running win games under wine.  Many thanks. 

John

If you have a spare harddisk, now is a good time to clone the entire ubuntu partition; just so, if you accidentally fubar, it an easy matter of swapping out the harddisk.

This is what I usually do every six months, before an ubuntu version upgrade.

---

### Post by John L on 2008-04-01
Just to update.  Gutsy installed lovelybut I managed to loose sound when I started messing around with my tv card.  The hardy live cd or alternative cd won't boot (I have a variety of linux distros (PCOS 07, Opensuse 10.1 etc) and hardy is the only one that won't boot.  However I upgraded Gutsy to the new kernal and then to hardy (I know - I was just messing around!)  Anyway to up shot is that the upgrade went very well - sound is back and I have hardy running well on my machine including desktop effects!!

I'll have to clone the partition as Astlavista suggested !

John

---

### Post by KasperJSN on 2008-04-01
I just installed Ubuntu one week ago. I follow exactly what was written in this thread : [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm) and it really works find for me for the partition of drive and installation.

The first pain comes when there are two Vista options in Grub, without understading one of them actually is Acer e-recovery which will reinstall the Vista again, and I ... choose it ! then :guitar:

But eventually after 2 days of searing web, finally know how to delete the e-recovery option in grub.

Now the second pain comes is Ubuntu dosen't seem to support my 1440x900 wide screen. There are numerous post here but I just simply do not know how to edit Screen, edit File etc, again :guitar:

Hope the second pain will be erased in coming 8.04. :popcorn:

---


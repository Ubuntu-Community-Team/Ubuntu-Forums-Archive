---
title: "Since ubuntu 9.10 a lot off very severy bugs appear."
date: 2010-08-11
forum: Testimonials &amp; Experiences
---

### Post by christophevr on 2010-08-11
Hello all and especially ubuntu maintainers.

I'm well aware that ubuntu is open system and free.

But as from ubuntu 9.10 a lot off very severy bugs appear.

First we have to audio The only improvement over there is that (if you can get it work) Is the better output volume support which was sometimes to low.

But The MOST Audio cards are not supported anymore. We end up having to put gnome alsa mixer togheter whit your Volume control program. After a search for more then a week finnally we can get it work a bit. But very imortant features like disabling speaker output when headset is plugged in and so on do not work.Which especially on laptops are a disaster.

The gdm login. Before we could use several way's whit list whitout list etc..Now anymore. Also it is impossible to hide some users from the list.(unless we give them a id below 1000) . Yes there are ways but then we need to recompile the whole stuf which often results in an ability to not be able to login at all. (and each upgrade sucks the whole stuff)

The automount option from file system like fat32 for usb stichs or so are gone and only hardcoded ?? again over here we have to change sources and recompile the whole stuf again at each upgrade it sucks.

Up to 8.10 everything whent fine Ok well bugs but always easy work arounds to find . Now anymore at all.

I don't now which way ubuntu goes but sometimes i've got the feeling that You're trying to beat windows in bugs ? 

Sorry  I prefere normally to give positif feedback but unfortunately I can not do that anymore about ubuntu. 

I'll hope that You change in future things again and that for audio at least follows the alsa-base.conf for example the option options snd-hda-intel model=asus-p5q will get the sound card to work whit gnome alsa mixer but the inputs to not show anymore into your volume control. The auto toggle when inserting headset do not work and so one ....

File systems fat32 needs to be mounted whit one user and off course the same rights for each file that's logic but. This general mount options needs to be changable again whit for example gconf-editor like before and NOT hardcoded. 

Hoping that future releases will be again on the right track

greetings christophe
:(

---

### Post by philinux on 2010-08-11
Moved to own thread and to T & E forum.

Ubuntu developers/maintainers do not usually frequent these forums. You need to create bug reports at launchpad.

[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by christophevr on 2010-08-11
> **philinux said:**
> Moved to own thread and to T & E forum.

Ubuntu developers/maintainers do not usually frequent these forums. You need to create bug reports at launchpad.

[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

Thank's for the reply, 

But the concerned problems I'm speaking about are already in many bug reports and remain unsolved in despit the fact that many repports are simply closed.(and unsolved) 

It's espacially the problem that to many stuff start's to be hard coded, Ok recompilling the source adapted for personal need's is alway's possible. But each update we have to restart, There as well can be say not to upgrade, But personnally I think that upgrading is very important,
not only for system's stability but ESPECIALLY FOR SECURITY reasons. 

So in fact's it's a general way of working from 9.10 and higher distros which causes lot's of trouble for many users easy work arounds just trough conf files or gconf xml files are very important in linux and one off the base things which make the difference between a good save working operating system and the crappy and particularly unsafe ones like windows for example.

Also It's very nice to have a polling and then an automatic selection of driver load at start up but since 9.10 more often wrong drivers are used,i2c does not work good anymore. Also the AUDIO is a disaster on a majority of hardware using HDA drivers. Via the alsa config file we can change that, but then also gnome-alsamixer is needed together with the new gnome-volume-control and this last one does not detect all the audio card input channels. Bringing a very confusing audio enviroment where a lot of spooky things are happening. Some hda options just don't work anymore at all and so on .... and yes they are all being filed in many bug repports, in despit of all the reports things get worser the higher the ubuntu distro is. 

Problems are there in almost ALL video,audio. But worse even in GDM file mount options and so one .. 

So yes ...

The problem is not an specific bug or so but the general followed way from 9.10 which causes the problems.

Again sorry for the so negatif comment but I'm just honnest and hope that for next ubuntu releases this way of work will change back into the good direction which ubuntu did up to hardy.

greetings christophe ;)

---

### Post by mastablasta on 2010-08-12
> **christophevr said:**
> Also the AUDIO is a disaster on a majority of hardware using HDA drivers. 
 
 
Wait, are you saying this HDA drivers thing worked better before? because i am having issues on this Lucid. Though 2nd day now no crash or error, but still... Audio is analog instead of digital...

---

### Post by christophevr on 2010-08-14
> **mastablasta said:**
> Wait, are you saying this HDA drivers thing worked better before? because i am having issues on this Lucid. Though 2nd day now no crash or error, but still... Audio is analog instead of digital...

Hello, 
Well I never even tried my digital out or inputs on my chipset, as all my in and out devices are still analog. But this HDA chipsets are doing analog and digital. And the problem is that the new volume control used (which should well handle digital audio as well and this was not into versions before 9.10) are not handling all the analog channels good anymore but it's quit possible that they do for the digital. The main problem are the in out channels handling I think. Like lucid does regognize my Chipset which is realtek 889A (azelia audio). It's build in in a MB gigayte extreme, So I do have internal cd in and line in connections. Then a plug for an audio 97A or HDA frontpannel (connected by me) then the standard out in puts on the back of the MB. Gnome alsa mixer does recognize all the channels if I put the extra options snd-hda-intel model=asus-p5q (which give me all the correct input and output channels since that MB has the same config from the same chipset as mine). But the new volume control just does not change any of his input output channels, There we have finnaly the bug. Or its seems just like the new volume control is not finished at all and even not ready for beta release. I don't now ??? Then when I put headset in front It's works yes but the analog back output should be toggled, And this does not happen. And there is now way the arrange it. On ubuntu before 9.10 this all worked fine. I'm not the only one with this problem and since 9.10 came out Already A tremendous amount of bug repports have been filled about this problem NONE of them have ever been solved But most off them are closed by now UNSOLVED. 

But that's live Ubuntu unfortunately goes down multimedia wise but also in more imprtant things like file handling and so. The user is not able any more to change mount options or so unless You go trough fstab but with usb stick's ?? not very practicale .

---


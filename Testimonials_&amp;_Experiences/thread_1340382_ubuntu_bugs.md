---
title: "ubuntu bugs"
date: 2009-11-28
forum: Testimonials &amp; Experiences
---

### Post by h4xor66 on 2009-11-28
[B]im new to linux ... Ive been testing mint7 for the last few weeks and i love it except that it will not work well with my sound card , so i thought I'd give ubuntu a try since ive seen so much chatter from the ubuntu users claiming that ubuntu is the greatest thing in the world ....


 installed ubuntu ( 1 hour to partition and install )  updated the repositories 108meg download and install ( about 15 mins ) updated firefox reloaded all of my bookmarks from a file  same with exrensions .. went into the software and installed pidgin a firewall and klam ... yay my sound card works on this .. then shut the computer down and restarted ... ERROR  ice something or other can not create directory ... Error nautilus can not create desktop ... then there is nothing but the wall paper cannot do any commands ... so im hosed ... OK time to start all over again


 reinstalled .. this time without encrypting my home directory like i did the first time in the installation where it asks to use password to unencrypt home directory ... did everything over again shut down the computer rebooted ah success cool ... shut it down for the night ... got up this morning and now it wont boot .. it gets to the login screen i enter my password and it blanks out the screen for a second and brings back the login screen ... so its just stuck at login .... so there i am im 8 hours into ubuntu and on my second failure   to say that im done with ubuntu is an understatement ....


 im the kind of guy that loves to tinker with my computer and figure things out but to have a system that just flat doesn't work is ridiculous, im not going to spend 40 hrs just trying to get ubuntu to boot ... and this is an alpha release ???[/B]

---

### Post by TenPlus1 on 2009-11-28
Why not give Xubuntu a try, it seems to work better than the standard gnome ubuntu...

---

### Post by Chargaff on 2009-11-28
Hi,

What machine are you trying to install ubuntu on ? We need more info if you want us to help !

Personaly, I nerver experienced a non working desktop with Ubuntu, but theses things can happen. Nothing's perfect, even Ubuntu !

---

### Post by mikewhatever on 2009-11-28
I see you've taken the time to sing up just to post a bash report. Well, Use what works for you, take it easy, and good luck.;)

---

### Post by h4xor66 on 2009-11-28
i might do that in the future .... right now im just pissed that i wasted hours of my life for something that should have been so simple ... i could understand if i had made some major changes to the system that maybe things would start going wrong but to just install and do only the most basic settings changes and have it blow up in my face is just to frustrating to deal with right now ...

---

### Post by h4xor66 on 2009-11-28
> **Chargaff said:**
> Hi,

What machine are you trying to install ubuntu on ? We need more info if you want us to help !

Personaly, I nerver experienced a non working desktop with Ubuntu, but theses things can happen. Nothing's perfect, even Ubuntu !



sorry if it sounded like im bashing ubuntu i really dont mean to ... i know that it works great for thousands of people .. just not for me in this instance ... to be fair i am using an ancient compaq presario 5400us  its 1.1 gig and 512megs of ram  ..... i can actually understand why it might not work well with my setup 

so ill just stick with mint for a while tilli get a newer rig ... then im sure ill try ubuntu again ... i just cant let it beat me , i have to get it working just to prove to myself that i can  ( im weird that way )

---

### Post by oldos2er on 2009-11-28
Mint is essentially the same as Ubuntu, but it installs some codecs and some other non open source software by default, that Ubuntu doesn't.

 The iceauthority error can probably be fixed by running **sudo chmod user:user /home/user/.ICEauthority** where "user" is your username. You can run this either after booting into recovery mode, or from Gnome failsafe login.

 You mentioned "alpha release" which I hope doesn't mean you're running Lucid.

---

### Post by h4xor66 on 2009-11-28
> **oldos2er said:**
> Mint is essentially the same as Ubuntu, but it installs some codecs and some other non open source software by default, that Ubuntu doesn't.

 The iceauthority error can probably be fixed by running **sudo chmod user:user /home/user/.ICEauthority** where &quot;user&quot; is your username. You can run this either after booting into recovery mode, or from Gnome failsafe login.

 You mentioned &quot;alpha release&quot; which I hope doesn't mean you're running Lucid.

   by alpha i meant whatever comes after an rc which i assumed was an alpha ...  how do you boot into recovery mode or failsafe when the computer wont do anything at all, no desktop no keyboard hotkey commands ?  from the live cd ?   like i said i definitely will try ubuntu again in the future ... i think i should just cut my teeth on mint for now because it is working for me ... when i get a little more experience ill dive into ubuntu again

---

### Post by mkvnmtr on 2009-11-28
You still have not said which release you installed. The last stable release is 9.10. Installing anything more recent is only for those with the experience to test a new distro.

---

### Post by oldos2er on 2009-11-28
> **h4xor66 said:**
> how do you boot into recovery mode or failsafe when the computer wont do anything at all, no desktop no keyboard hotkey commands ?

 That sounds like a hardware failure, if I'm understanding you correctly. Is your keyboard USB?

---

### Post by h4xor66 on 2009-11-28
it was version 9.10 the latest stable version .... and yes its a usb keyboard

---

### Post by twm3 on 2009-11-28
Hiya,

FWIW, I tried installing both Ubuntu 9.04 & 9.10 on a Fujitsu P2120 (Transmeta CPU - in emulates a Pentium, 256 MB RAM, and 30 GB drive). It didn't work. I wasn't hopeful of being able to resurrect this 5+ year old machine.

I then tried Puppy Linux. Ran like a charm. A very small Linux, it appears to be tailored to run on "ancient" machines. Check it out. Ubuntu seems to be great for reasonable current machines but for those machines that might be described as "mature" :-), you might want to check out Puppy. 

FWIW, I ran a Live CD of Puppy on my Ubuntu system. OMG, it is FAST. Puts Ubuntu to shame. But support appears to be better with Ubuntu.

~Tom

---

### Post by h4xor66 on 2009-11-29
> **twm3 said:**
> Hiya,

FWIW, I tried installing both Ubuntu 9.04 & 9.10 on a Fujitsu P2120 (Transmeta CPU - in emulates a Pentium, 256 MB RAM, and 30 GB drive). It didn't work. I wasn't hopeful of being able to resurrect this 5+ year old machine.

I then tried Puppy Linux. Ran like a charm. A very small Linux, it appears to be tailored to run on &quot;ancient&quot; machines. Check it out. Ubuntu seems to be great for reasonable current machines but for those machines that might be described as &quot;mature&quot; :-), you might want to check out Puppy. 

FWIW, I ran a Live CD of Puppy on my Ubuntu system. OMG, it is FAST. Puts Ubuntu to shame. But support appears to be better with Ubuntu.

~Tom

   i tried puppy a while back on an old laptop and didnt have any luck with it because it didnt mesh well with my video card ...   i installed mint 8 today and its working great except for one tiny little bug that i havent figured out yet ... i installed picasa and it is nowhere to be found , it says its installed in software manager and also in package manager and if i click on edit menu it shows that its in the graphics category of my programs ... but if i open that menu it is not there ... ill figure it out eventually

---

### Post by meindian523 on 2009-11-29
twm3:
Ubuntu Minimal: Add functionality as you go
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by jrrader on 2009-11-29
> **h4xor66 said:**
> i tried puppy a while back on an old laptop and didnt have any luck with it because it didnt mesh well with my video card 

puppy lets you choose between xvesa and xorg at start up.  Between the two, something should work.  I never had any luck with the standard puppy - too small, not enough drivers, assumes you have windows drivers to wrap - but if you go to puplets on the puppy website there is a puplet called "puppy crypt" which has never let me down.  Same guy also makes a light weight ubuntu (ubuntu crypt) that you might want to check out.

---

### Post by pehden on 2009-11-29
> **h4xor66 said:**
> it was version 9.10 the latest stable version .... and yes its a usb keyboard
Thats your problem there download 8.04 for that machine I bet it will work then upgrade from that to the latest

Well it should work, hell I have karmic running on a amd 900mhz 512mb sdram, with 180gb hdd. although its kubuntu it still runs super fast on that old box.

---

### Post by bapoumba on 2009-11-29
Moved to Ubuntu Testimonials & ExperiencesM

---


---
title: "Someone please hurry and put ubuntu on a ps3...i'm tired of the fedora videos."
date: 2006-11-20
forum: The Cafe
---

### Post by hikaricore on 2006-11-20
](*,) That is all.  =)

---

### Post by hikaricore on 2006-11-20
Forgot to post a link so you can all feel my pain: [http://www.youtube.com/watch?v=NnAn3h7kTM4]("http://www.youtube.com/watch?v=NnAn3h7kTM4")

---

### Post by Busch on 2006-11-20
im actually trying to get my hands on the nintendo wii myself :P im a nintendo kinda guy "fanboy" if you must lol

---

### Post by hikaricore on 2006-11-20
lol, don't feel bad, I still own a virtual boy

---

### Post by adamkane on 2006-11-20
ipodlinux doesn't even work on my 5G ipod yet. :(

---

### Post by tworkemon on 2006-11-20
I've been trying.... I think ubuntu will need its own bootloader or a kboot hack :(

---

### Post by LemonyVengeance on 2006-11-21
I'm about to attempt my first linux install on a PS3. I know what you're going to say.... that I'm really jumping in head first.... which is accurate. I'm going to have to be like a blind man at a strip club. *Feeling my way around.* I'll let you know how it goes.

---

### Post by mrgnash on 2006-11-21
Wii - the Gamecube with a bit more ram, and a lot more pointing.

Sorry, had to say it :P I don't think that the PS3 will be great for running Linux either... only 256mb RAM, no Flash 9 and many other 'missing' codecs for the PPC ed. and good luck getting anything like Beryl to run on it.

---

### Post by timbobsteve on 2006-11-21
It is true... the PS3 Dev Kit is yet to release any usable code for the RSX chip (graphics card if you will)... so beryl and alot of other high end graphic apps just won't work on the vesa driver until a proper RSX driver is written.

Also, like someone mentioned, alot of apps have a hard time compiling on the PPC arch because of endianness issues (read: drivers).. so alot of third party peripherals will fail to work on the PS3. 

Good luck to it though... If sony really do support Linux like they say they will, then it may turn into a usable platform for Linux peeps. If it is anything like PS2-Linux, then god help us all!

---

### Post by LemonyVengeance on 2006-11-21
Ok, here's an update.

The guy above me is right. The PS3 doesn't recognize the bootloader on the ubuntu image that this site provides. someone will have to make one and release it to the public. It will all be a matter of time.

---

### Post by Brunellus on 2006-11-21
> **LemonyVengeance said:**
> Ok, here's an update.

The guy above me is right. The PS3 doesn't recognize the bootloader on the ubuntu image that this site provides. someone will have to make one and release it to the public. It will all be a matter of time.
I called it:  free kernel, nonfree bootloader.

---

### Post by hikaricore on 2006-11-21
arg damn you fedora!  ubuntu is foiled again.  lol

---

### Post by darkhatter on 2006-11-21
Fedora is trying to pull a Debian and run on everything. They already officially support the intel-Mac's

---

### Post by adamkane on 2006-11-21
You can mod/hack Oblivion on the PC, but not on the XBOX360.

I'm glad that there will be mod-able Linux on PS3, so that users can become creators of their own gaming experience.

It'll also be nice to have Linux in the living room, instead of in the basement.

---

### Post by LemonyVengeance on 2006-11-22
ok, I was able to locate the mysterious Kboot file (called otheros.bld) and I'm at the kboot command line, but unsure of how to continue.

---

### Post by LemonyVengeance on 2006-11-22
ok. I'm back to my original stance. the Kboot file won't load the ubuntu disc... and I'm pretty sure it won't because the kboot is for fedora. If there was a way that we could have a bootloader made to install ubuntu.... I'm not brainy enough to do it. :(

---

### Post by kcy29581 on 2006-11-22
I'm about to try and have a look at the "install-fc" script used to install Fedora Core 5 on the PS3. I'm hoping all that is needed is to modify the script for Ubuntu, perhaps use alien on the PS3-specific RPM's and change the kernel being installed (so it's PS3 specific)

---

### Post by ago on 2006-11-22
What about installing fedora and than using debootstrap to install Ubuntu? Has anyone tried that?

---

### Post by cantormath on 2006-11-22
> **hikaricore said:**
> ](*,) That is all.  =)

has anyone tried droppin the cd in there?

---

### Post by Dual Cortex on 2006-11-22
> **cantormath said:**
> has anyone tried droppin the cd in there?

...!
Seems like you only read the first 2 posts of the thread!

---

### Post by cantormath on 2006-11-22
> **Dual Cortex said:**
> ...!
Seems like you only read the first 2 posts of the thread!

it happens......

---

### Post by Lord Illidan on 2006-11-22
Someone send me a ps3 and I will try it.:mrgreen:

---

### Post by LemonyVengeance on 2006-11-22
When going through the post on ps2.qj.net I realized a few things. when they say "You can only install via a DVD, CDs aren't supported!" they mean it, and that it is very well possible that because they're using Kboot, any kde based distro (like say...... KUBUNTU) would be able to install with no modification. pleas, correct me if I'm wrong.

I'm in the process of downloading both the dvd image of Kubuntu, as well as the DVD image of Fedora core 6 just in case it doesn't work. unfortunatly I'm going to be gone for the weekend (thanksgiving and all) so I won't be able to let you know how it goes until sunday at the earliest.

---

### Post by daynah on 2006-11-22
> **kcy29581 said:**
> I'm about to try and have a look at the "install-fc" script used to install Fedora Core 5 on the PS3. I'm hoping all that is needed is to modify the script for Ubuntu, perhaps use alien on the PS3-specific RPM's and change the kernel being installed (so it's PS3 specific)


Is what your saying is taking fedora's boot + ubuntu's kernel... and then put it on a DVD? Cause my over-simplistic mind that hasn't a clue how to code thinks that that would be the way to go about it.

I would also be greatly saddened if Kubuntu worked and Ubuntu didn't, and I could only fiddle with gnome on the PS3 with Fedora. I have a personal vendetta against KDE.

---

### Post by Johnsie on 2006-11-22
I'm glad people here are looking at getting this with Ubuntu. Good luck. If it's true and you can run Linux on a ps3 then it gives ps3 users more choice over what software they can use. 

It's early days yet so I hope this works out and we can have a Pubuntu Linux distro lol.

---

### Post by justin whitaker on 2006-11-22
> **Johnsie said:**
> It's early days yet so I hope this works out and we can have a Pubuntu Linux distro lol.

And then you guys can use your powers for good, by getting BF2 to run on Linux Natively. :mrgreen:

---

### Post by LemonyVengeance on 2006-11-22
ok, I think we might be going about this the wrong way... The instructions on sony's web site say > "Obtain the boot loader file for the "Other OS" you want to install from the provider. Then save the boot loader file in the "otheros" folder created in step 2 with the name, "otheros.bld"." What if we were to take the boot loader file off the ubuntu dvd and rename it to otheros.bld? (also, I'm not sure what the name of the bootloader file is on the PPC distro and where to find it)

---

### Post by hikaricore on 2006-11-23
One thing to remember is that a ubuntu live setup on cd uses a compressed filesystem image, I'm not sure if this is the same for the dvd images of ubuntu, but I'd imagine this could cause some issues with booting.

---

### Post by kcy29581 on 2006-11-23
> **daynah said:**
> Is what your saying is taking fedora's boot + ubuntu's kernel... and then put it on a DVD? Cause my over-simplistic mind that hasn't a clue how to code thinks that that would be the way to go about it.

I would also be greatly saddened if Kubuntu worked and Ubuntu didn't, and I could only fiddle with gnome on the PS3 with Fedora. I have a personal vendetta against KDE.
not sure how to do that... I'm trying to figure out a way to install this, perhaps via debootstrap

---

### Post by JurB on 2006-11-23
How about a [ps3 running XP in Qemu on Fedora]("http://video.google.nl/videoplay?docid=-8800244920606286092&q=ps3+linux") :-k

---

### Post by mips on 2006-11-25
[http://www.bsc.es/plantillaG.php?cat_id=96](http://www.bsc.es/plantillaG.php?cat_id=96)
[http://www.bsc.es/plantillaH.php?cat_id=115](http://www.bsc.es/plantillaH.php?cat_id=115)

---

### Post by hikaricore on 2006-11-26
> **JurB said:**
> How about a [ps3 running XP in Qemu on Fedora]("http://video.google.nl/videoplay?docid=-8800244920606286092&q=ps3+linux") :-k

rofl that just made my day

---

### Post by LemonyVengeance on 2006-11-26
(Double post. Deleted)

---

### Post by LemonyVengeance on 2006-11-26
It's been done. I don't thave the link right now, but ps3.qj.net posted a story saying that someone was able to set up xp by using qemu and boot to it (in fedora, of course). Of course the resources were maxed, but still it's a possibility. Now I can actually have a dedicated MCE box for my xbox 360! In your face, sony! Hahahhahahah

---

### Post by JurB on 2006-11-26
> **LemonyVengeance said:**
> It's been done. I don't thave the link right now, but ps3.qj.net posted a story saying that someone was able to set up xp by using qemu and boot to it (in fedora, of course). Of course the resources were maxed, but still it's a possibility. Now I can actually have a dedicated MCE box for my xbox 360! In your face, sony! Hahahhahahah

:confused:  just click the link!

---

### Post by LemonyVengeance on 2006-11-26
I'm on my sidekick 3 right now and their site doesn't play nice with the browser on this device. I'll post it as soon as I can.

---

### Post by JurB on 2006-11-26
I mean click the link in my previous post and watch the video...

---

### Post by LemonyVengeance on 2006-11-26
Oh. *smacks forehead* sorry. Didn't catch it. I blame it on the crappy device browser.

---

### Post by JurB on 2006-11-26
:wink:

---

### Post by tworkemon on 2006-11-28
Lets get this going ;)    *bump*

---

### Post by Ciego on 2006-12-15
It has been confirmed that you can install Ubuntu after installing Fedora, but I would still love to see a solution that will work without the extra step.  I currently do not have a functioning DVD burner so I cannot test this.  I have been trying for a few weeks now with my very minimal linux skills to get this to work without the Fedora install but have had little luck.  

Check out the link

[http://ubuntuforums.org/showthread.php?t=316047](http://ubuntuforums.org/showthread.php?t=316047)

---

### Post by Ciego on 2006-12-15
For those interested, I created a thread for sharing PS3 aliases for the Playstation network.

[http://ubuntuforums.org/showthread.php?t=319528](http://ubuntuforums.org/showthread.php?t=319528)

---


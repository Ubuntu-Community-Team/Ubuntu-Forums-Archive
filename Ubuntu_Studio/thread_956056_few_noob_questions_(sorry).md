---
title: "few noob questions (sorry)"
date: 2008-10-22
forum: Ubuntu Studio
---

### Post by MoonKid on 2008-10-22
i did my reseach but still cant seem to get  a grip on it... i had ubuntu for a few days now...

i got uTorrent & CSS to run on it... i want to keep making music (i usually use hardware, but im in school full-time had to sell it to pay classes)...

i looked into Ubuntu Studio... im willing to try it out.. but i CAN NOT seems to get how i use a ISO on Ubuntu...:confused:

i don't really want to burn it on a CD... are there any virtual drivers out for ubuntu?

same goes for LMMS those "deb" and "gz" files are killing me...

anyone has any links where that might be helpful??? keep in mind im fresh of windows... thank you.

and one more thing.... when i play Avi. files in Movie Player... it lags really bad and has no audio... any guesses?

---

### Post by richarglamb on 2008-10-23
Well, I'm new enough myself. I think you have to burn the ISO, and perhaps once it's installed there is no need for the disk. 

And for your last problem with AVI's, maybe try another media player, VLC seems to work the best. Try downloading a few media players, some work better with particular files. 

Also have you enabled the 
restricted formats? 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Hope that helps. Maybe limit your questions to one at a time and give details of the machine and version of the operating system you are using.

---

### Post by MoonKid on 2008-10-23
thanks ill check that out...

im running the newest Ubuntu 8.04??

and my mp3 arn't working aswell :mad:

---

### Post by Interpreter on 2008-10-24
Go to Audio-Multimedia- Set that to ALSA and hit test. if that works, youll notice how mp3s and avis work fine again.

if it doesnt. Come back for more. Has nothing to do with "a different movie player" or somesuch methinks.

---

### Post by tacticalbread on 2008-10-24
to install all the multimedia packages that Ubuntu Studio uses, type this command into the Terminal. (It will have to download a lot, so it could take a while.)

```
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

and for LMMS, try this.
```
sudo apt-get install lmms
```

---

### Post by Korijn on 2008-10-24
In order to install software you're generally better off using the "Install/Remove" application found in your main Ubuntu menu. Just use all the supplied search functions to find whatever you need. Check the boxes for the software you need and hit OK! Everything should happen automatically from there. To remove just uncheck and hit OK again.

As for installing .deb and .gz (and probably .bz2) files, this is generally speaking a bit harder to do but also quite manageable. If the file ends in (.tar).gz or .bz2 you'll have to extract its contents. It usually has a "INSTALL" file in there which will tell you how to proceed from there.

Video/audio problems should be solved by installing these: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) .

By the way, why are you running uTorrent (windows software) on a Ubuntu Linux system, when there are countless other pieces of BitTorrent software that work just as well made especially for Linux (or Ubuntu even)? Transmission, which is installed by default, works fine for me.

Edit: By the way! Ubuntu Studio is not a software package you install using that ISO, it's a different version of Ubuntu. So that means you have to burn it onto a disc in order to boot from it and install. The software is available for normal Ubuntu though, install it using tacticalbread's commands in the terminal. I reckon you can find all that in "Add/Remove" as well by the way.

---

### Post by MoonKid on 2008-10-25
OK!! thanks a lot im going to look into all of this right now...

thanks.

---


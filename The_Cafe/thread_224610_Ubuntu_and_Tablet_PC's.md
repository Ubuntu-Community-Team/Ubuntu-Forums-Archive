---
title: "Ubuntu and Tablet PC's"
date: 2006-07-28
forum: The Cafe
---

### Post by prizrak on 2006-07-28
Since I just got a tablet so did yozef's wife, I was wondering if Ubuntu will be doing anything to improve tablet compatibility (or come out with Tablet Edition a la MS). Now it works great on this and everything but some of the special keys is recognized (not a big problem since it's easy enough to assign shortcuts in Gnome). The three annoying things at the moment are:
1) No flip screen, the button doesn't work, which is fine and acceptable at this level, but the command fails as well. It may have something to do with proprietary nVidia driver not supporting it. However the FOSS driver has some issues with this card so it has to use the proprietary driver now. 

2) No handwriting recognition/on screen kbd. I installed the GOK but that was a damn confusing program which never gave me the actual kbd (or at least I couldn't find where it was) so it was canned. There is no real handwriting recognition program in the repos. I found something called xstroke on the net but their site didn't have a download link so that might be something that should make it to the repos. 

3) Bluetooth in Gnome sux, it just plain does. There is no "buts" or "depends" about it. The only way to get to bluetooth is installing the KDE tools for it. Something that is not a real solution as far as I'm concerned because the awesomeness of an integrated DE is in library sharing. Running KDE exclusively is also not something I want to do as I prefer Gnome. 

This is not one of those "Ubuntu sux and needs to improve" posts. I'm just kinda wondering if Canonical is considering the tablet market large enough to try and improve things or if it's going to be something that will have to wait until the market gets bigger. 

P.S. Would also be nice if the Wacom tablet was recognized OOTB and set up. It doesn't take very long to edit the file but not having to edit configs is alwasy nicer :)

---

### Post by bluenova on 2006-07-28
I know nothing about tablet pc, but I do know gnome bluetooth. I've been using it for a long time on both Fedora and Ubuntu for transfering files to and from the computer, so I'm not sure what the big problem is there.

Handwriting recognition would certainly be nice.

---

### Post by prizrak on 2006-07-28
> **bluenova said:**
> I know nothing about tablet pc, but I do know gnome bluetooth. I've been using it for a long time on both Fedora and Ubuntu for transfering files to and from the computer, so I'm not sure what the big problem is there.

Handwriting recognition would certainly be nice.

Oh? Hook me up with knowledge. All I found on bluetooth in Gnome is a litle file transfer program that doesn't seem to have any settings. I can't even check if my bluetooth turns on or not. 

I got handwriting recognition setup with xstroke right now (found a .deb on these forums actually thx to Google). It's a pretty nice program, sadly XP is better at it.

---

### Post by Henrik on 2006-08-02
We are working on a new on-screen keyboard that should be better for both tablets and accessibility. See: [https://wiki.ubuntu.com/Accessibility/Projects/SOK](https://wiki.ubuntu.com/Accessibility/Projects/SOK) and: [http://www.ubuntuforums.org/showthread.php?t=192758](http://www.ubuntuforums.org/showthread.php?t=192758)

Please help with testing! :)

---

### Post by 23meg on 2006-08-02
> **prizrak said:**
> 
1) No flip screen, the button doesn't work, which is fine and acceptable at this level, but **the command** fails as well. It may have something to do with proprietary nVidia driver not supporting it. However the FOSS driver has some issues with this card so it has to use the proprietary driver now. 
Which command? You should be able to flip the orientation with xrandr; if you're using the nvidia proprietary driver you need to add```
Option "RandRRotation" "True"
```to the "Device" section of your xorg.conf .
> 
2) No handwriting recognition/on screen kbd. I installed the GOK but that was a damn confusing program which never gave me the actual kbd (or at least I couldn't find where it was) so it was canned. There is no real handwriting recognition program in the repos. I found something called xstroke on the net but their site didn't have a download link so that might be something that should make it to the repos. 

xstroke looks like it's a dead project. There are RPMs of it floating around; do a search and you'll find one. I got it working in Ubuntu but it's more accurately defined as gesture recognition software than handwriting recognition. AFAIK there's no open source handwriting recognition software that has matured beyond xstroke's abilities to recognize written letters and words. 
> 3) Bluetooth in Gnome sux, it just plain does. There is no "buts" or "depends" about it. The only way to get to bluetooth is installing the KDE tools for it. Something that is not a real solution as far as I'm concerned because the awesomeness of an integrated DE is in library sharing. Running KDE exclusively is also not something I want to do as I prefer Gnome. I don't get why you think this is a tablet-specific problem and you didn't specify why it "sucks" so no ideas about that.
> 
I'm just kinda wondering if Canonical is considering the tablet market large enough to try and improve things or if it's going to be something that will have to wait until the market gets bigger.Canonical isn't the one that should try to improve things here, it's the Ubuntu developers and contributors.

---

### Post by prizrak on 2006-08-02
> Which command? You should be able to flip the orientation with xrandr; if you're using the nvidia proprietary driver you need to add
Code:

Option "RandRRotation" "True"

to the "Device" section of your xorg.conf .
Thanks, yes it was the xrandr command my bad :)
> xstroke looks like it's a dead project. There are RPMs of it floating around; do a search and you'll find one. I got it working in Ubuntu but it's more accurately defined as gesture recognition software than handwriting recognition. AFAIK there's no open source handwriting recognition software that has matured beyond xstroke's abilities to recognize written letters and words.
I got it working seems pretty nice (I think it might have been your .deb actually, found it on the forum) the only thing is it doesn't start with the system correctly not too sure why, it starts and is running but the icon is not present so no way to turn on gesture/handwriting recognition.
> I don't get why you think this is a tablet-specific problem and you didn't specify why it "sucks" so no ideas about that.

Hehe, ooops. I was posting from work during a break so was in a bit of a rush. It's not a tablet specific issue, just one I haven't had before since I had no bluetooth. Tho tablets tend to have bluetooth connectivity. The sucks part of it is that in Gnome there is only one bluetooth program that I found. All it can do is file sharing and all it does when I start it is put an icon in the notification area. The only thing that does is tell me my computer is ready to file share over bluetooth. The Bluetooth Manager that is associated with it just plain doesn't start from the menu (haven't tried it from the CLI). The little icon has no options or anything I don't even know if my bluetooth is working/recognized. I know that KDE has a pretty nice set of bluetooth tools, I don't like mixing my DE's though. (I don't have much need for bluetooth at the moment just wanted to play with it and don't wanna install KDE stuff just for that).
> Canonical isn't the one that should try to improve things here, it's the Ubuntu developers and contributors.
You are right, but I view them as a central authority on Ubuntu. I don't have enough skill (and lately time) to figure out hardware recognition.

---

### Post by prizrak on 2006-08-02
> We are working on a new on-screen keyboard that should be better for both tablets and accessibility. See: [https://wiki.ubuntu.com/Accessibility/Projects/SOK](https://wiki.ubuntu.com/Accessibility/Projects/SOK) and: [http://www.ubuntuforums.org/showthread.php?t=192758](http://www.ubuntuforums.org/showthread.php?t=192758)

Please help with testing! 
Awesome, thank you for the effort I'll check it out and see if I can give you any helpful feedback.

---

### Post by prizrak on 2006-08-02
23meg,
Didn't work. Thanks for the attempt.

---

### Post by 23meg on 2006-08-02
>  the only thing is it doesn't start with the system correctly not too sure why, it starts and is running but the icon is not present so no way to turn on gesture/handwriting recognition.
Weird, I didn't have that problem; it worked as supposed. Did you try it in another DE?
> You are right, but I view them as a central authority on Ubuntu. I don't have enough skill (and lately time) to figure out hardware recognition.
Canonical isn't, the technical board is, only to be overruled occasionally by SABDFL, which doesn't happen often. 

>  	23meg,
Didn't work. Thanks for the attempt.What didn't work? The xrandr command? What's the exact error, and how exactly did you issue it?

---

### Post by prizrak on 2006-08-02
> **23meg said:**
> Weird, I didn't have that problem; it worked as supposed. Did you try it in another DE?
Canonical isn't, the technical board is, only to be overruled occasionally by SABDFL, which doesn't happen often. 

What didn't work? The xrandr command? What's the exact error, and how exactly did you issue it?

1) No I didn't try in another DE I only have Gnome installed. It's not a real issue I just have a launcher on the panel so I can start it when in tablet mode. I'm sure when there is enough demand we'll get something, if anything the source is available so maybe when I got some time I will try to figure it out.

2) Oh I see, that's cool :)

3) Yep the xrandr didn't work I put the option you told me to in the xorg.conf. 

Here is the output for xrandr w/o arguments
```
prizrak@tablet:~$ xrandr
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 321mm x 241mm )  *60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none
prizrak@tablet:~$

```

Here is the command trying to invert the screen.
```
prizrak@tablet:~$ xrandr -o inverted
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

---


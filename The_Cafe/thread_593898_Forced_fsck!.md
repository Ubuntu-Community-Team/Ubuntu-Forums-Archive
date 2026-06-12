---
title: "Forced fsck!"
date: 2007-10-27
forum: The Cafe
---

### Post by RAV TUX on 2007-10-27
I was forced fsck'd!...I honestly have no idea what this is about can someone please explain it...links appreciated.

---

### Post by steveneddy on 2007-10-27
File System Check

It checks the file system for weird stuff.

:popcorn:

---

### Post by Vansinnesvisan on 2007-10-27
Watch your language, mister. This is a family site.

---

### Post by -grubby on 2007-10-27
doesn't it do that every 26 boots?

---

### Post by icechen1 on 2007-10-27
> **nathangrubb said:**
> doesn't it do that every 26 boots?
i think it is 30
BTW,FSCK is a program in Linux not the bad word.

---

### Post by RAV TUX on 2007-10-27
> **nathangrubb said:**
> doesn't it do that every 26 boots?I was forced fsck'd at my 34th reboot.

---

### Post by -grubby on 2007-10-27
OK then...I just can't remember the last time I got a check because I reboot about once a week

---

### Post by kostkon on 2007-10-27
Yeap, indeed, every 30 boots. Usual stuff, not to worry :lolflag:

And to [do the all work for you]("http://en.wikipedia.org/wiki/Fsck")... it also explains the profanity thing.

---

### Post by thelocust on 2007-10-27
Yea I really wish that they would make this optional. Like "sda1 will be checked in 5 second press Esc to continue" something like that would be nice.

---

### Post by Mazza558 on 2007-10-27
IIRC, Linux fscks your PC every 35 reboots. It can get quite annoying, especially if you're in a hurry to do work.

EDIT: I see it's every 30 reboots.

---

### Post by RAV TUX on 2007-10-27
> **kostkon said:**
> 

And to [do the all work for you]("http://en.wikipedia.org/wiki/Fsck")... it also explains the profanity thing.

Referencing your link, I have only heard it pronounced:
>  "F-suck"[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

I have never associated it with any kind of vulgarity.

The important thing here is why Force fsck users by default?

This is the first time I got forced fsck'd  and I agree with fellow post that would like an opt out option or delay function, especially for those who don't have time for it.

> **thelocust said:**
> Yea I really wish that they would make this optional. Like "sda1 will be checked in 5 second press Esc to continue" something like that would be nice.

> **Mazza558 said:**
> IIRC, Linux fscks your PC every 35 reboots. It can get quite annoying, especially if you're in a hurry to do work.

EDIT: I see it's every 30 reboots.

mine happened at 34, but I agree with the two post above it is annoying and there should be an opt out or delay function(meaning delay until a set number of reboots, ie 78...).

Forcing anything is not in the spirit of Linux or Ubuntu.

---

### Post by kostkon on 2007-10-27
> **RAV TUX said:**
> Referencing your link, I have only heard it pronounced:
[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

I have never associated it with any kind of vulgarity.


Not you, I know, but a previous poster did.

> **RAV TUX said:**
> The important thing here is why Force fsck users by default?

This is the first time I got forced fsck'd  and I agree with fellow post that would like an opt out option or delay function, especially for those who don't have time for it.





mine happened at 34, but I agree with the two post above it is annoying and there should be an opt out or delay function(meaning delay until a set number of reboots, ie 78...).

Forcing anything is not in the spirit of Linux or Ubuntu.

Yes, indeed, it's annoying, especially for people with laptops that boot their PCs more often than desktop PC users.

There is an ongoing discussion of making it optional; or at least starting it after 30 boots, but when the user is going to shutdown the PC. Although, even in this case the user has to be asked if it actually wants the *fsck* to start. In case the user postpones it then he/she will be asked again the next time.

I really hope that this will be implemented for 8.04.

---

### Post by RAV TUX on 2007-10-27
> **kostkon said:**
> Not you, I know, but a previous poster did.

My post was actually in response to that post also, I just forgot to include it in the qoute.


> **kostkon said:**
> 
Yes, indeed, it's annoying, especially for people with laptops that boot their PCs more often than desktop PC users.

There is an ongoing discussion of making it optional; or at least starting it after 30 boots, but when the user is going to shutdown the PC. Although, even in this case the user has to be asked if it actually wants the *fsck* to start. In case the user postpones it then he/she will be asked again the next time.

I really hope that this will be implemented for 8.04.

A better idea would be to just list it as an option in the Grub boot menu, ie:

Boot Xubuntu 7.10 with fsck

I think asking every time after each delay would be a further assault and annoyance. 

Of course if suspend worked fine this would not be an issue, I regret reinstalling I had Suspend working fine before but now it simply does not work.

I honestly think any kind of Forced fsck or even a delayed or prompted fsck is a step in the wrong direction. 

Again the ideal solution would be to just add a prompt at the boot menu.

---

### Post by floke on 2007-10-27
Rav - are you seriously telling us that you've never had this before?
In all the years you've been using Linux?

Man, you must get through a new distro a week to avoid this!

And the number of times before fsck-ing varies so that you don't get loads of partitions needing to be done at the same time - some of mine are set for 30, some for 34 etc...

---

### Post by BOZG on 2007-10-27
How do you know how many boots you've done?

---

### Post by floke on 2007-10-27
fsck knows!

(there is a way though - I'm off to google....)

---

### Post by aidanr on 2007-10-27
So turn it off, change the last number in the appropriate fstab line to 0

---

### Post by RAV TUX on 2007-10-27
> **floke said:**
> Rav - are you seriously telling us that you've never had this before?
In all the years you've been using Linux?

Man, you must get through a new distro a week to avoid this!

And the number of times before fsck-ing varies so that you don't get loads of partitions needing to be done at the same time - some of mine are set for 30, some for 34 etc...

Actually this was my very first fsck is it really in every distro?

> **BOZG said:**
> How do you know how many boots you've done?

fsck tells you.

> **aidanr said:**
> So turn it off, change the last number in the appropriate fstab line to 0I would rather not turn it off completely I would honestly like the option to fsck added to the boot menu.

...or if I turn it off can I just command line fsck?

That would be even better.

2 questions How specifically do I turn it off? meaning how and where do I make the edit at?

Also, then what is the command line prompt to boot with fsck?

---

### Post by aidanr on 2007-10-27
```
sudo touch /forcefsck
``` will force a check on the next boot

also you can change the ammount of boots until a check is done
[http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/](http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/)

---

### Post by FuturePilot on 2007-10-27
> **floke said:**
> Rav - are you seriously telling us that you've never had this before?
In all the years you've been using Linux?

Man, you must get through a new distro a week to avoid this!

And the number of times before fsck-ing varies so that you don't get loads of partitions needing to be done at the same time - some of mine are set for 30, some for 34 etc...

RAV switches distros so often it probably never gets a chance to fsck ;)

I think the number of boot depends on the size of the partition. It does it every 23 boots on my laptop. Last time it happened on my desktop it was 32 boots.:confused:

---

### Post by floke on 2007-10-27
Here we go... use

/sbin/tune2fs -l /dev/sda7

to see how often a partition is fsck-d - how many more boots to go etc. (obviously change sdaX)

Also found this...

[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

### Post by RAV TUX on 2007-10-27
> **aidanr said:**
> ```
sudo touch /forcefsck
``` will force a check on the next boot

also you can change the ammount of boots until a check is done
[http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/](http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/)

Awesome 411, this is most helpful Thank You.

> **FuturePilot said:**
> RAV switches distros so often it probably never gets a chance to fsck ;)

That and I only recently started to even shut my system down.

 I did get used to using Suspend, in fact I Love suspend but it isn't working properly.

Any way to fix the broken "Suspend" function?

> **floke said:**
> Here we go... use

/sbin/tune2fs -l /dev/sda7

to see how often a partition is fsck-d - how many more boots to go etc. (obviously change sdaX)

Also found this...

[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

Thanks for the 411, also. ;)

---

### Post by thelocust on 2007-10-27
Thank god for [AutoFsck]("https://wiki.ubuntu.com/AutoFsck") I am installing it as soon as I get home. Why doen't everybody know about this? :confused:

---

### Post by RAV TUX on 2007-10-27
> **thelocust said:**
> Thank god for [AutoFsck]("https://wiki.ubuntu.com/AutoFsck") I am installing it as soon as I get home. Why doen't everybody know about this? :confused:

Very nice but unfortunately it will not work with Xubuntu.


> 
At present, AutoFsck only works on Ubuntu, (not kubuntu and xubuntu). More specifically, AutoFsck requires you to be using GDM (the Gnome Display Manger) to log in.[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

---

### Post by jgrabham on 2007-10-27
> **RAV TUX said:**
> I was forced fsck'd!...I honestly have no idea what this is about can someone please explain it...links appreciated.

We just call it rape...

---

### Post by thelocust on 2007-10-27
>  
AutoFsck only works on Ubuntu, (not kubuntu and xubuntu). 

I think I'm going to cry.

---

### Post by sd.chen on 2007-10-27
> Any way to fix the broken "Suspend" function?
Once I reinstalled and (I think) forgot to set my swap partition. My suspend and hibernate started acting weird after that. Maybe check your fstab file and make sure the swap partition is defined.

---

### Post by RAV TUX on 2007-10-27
> **sd.chen said:**
> Once I reinstalled and (I think) forgot to set my swap partition. My suspend and hibernate started acting weird after that. Maybe check your fstab file and make sure the swap partition is defined.
Thanks for the suggestion, I will look into this when I get a chance.

---

### Post by kostkon on 2007-10-27
> **floke said:**
> Rav - are you seriously telling us that you've never had this before?
In all the years you've been using Linux?

Man, you must get through a new distro a week to avoid this!

And the number of times before fsck-ing varies so that you don't get loads of partitions needing to be done at the same time - some of mine are set for 30, some for 34 etc...

Let's assume someone who had never used Linux before, finds Ubuntu interesting and installs it.

Now, think the possibility that this person religiously reboots his/her system only one time every month. Assuming the fact that *fsck* is set to start after 30 boots, then more than *2 years* (!) will have to pass until this person sees for the first time such a check being taken!!

Thus, many people, like *RAV TUX* (who hibernates his system), will rarely see *fsck* in action.

---

### Post by floke on 2007-10-27
> **kostkon said:**
> Let's assume someone who had never used Linux before, finds Ubuntu interesting and installs it.

Now, think the possibility that this person religiously reboots his/her system only one time every month. Assuming the fact that *fsck* is set to start after 30 boots, then more than *2 years* (!) will have to pass until this person sees for the first time such a check being taken!!

Thus, many people, like *RAV TUX* (who hibernates his system), will rarely see *fsck* in action.

Good point!

---

### Post by Anessen on 2007-10-27
tune2fs reports that my main partition will be force checked in 6 months...

---

### Post by blastus on 2007-10-27
Automatic fsck in theory is a great idea. However, the way it is implemented is just downright annoying. The method of tracking when the file system was last fsckd is screwy (try installing two Linux distributions and multiboot between them a few times.) 

I just turn off fsck in /etc/fstab.

---

### Post by macogw on 2007-10-27
nevermind

---

### Post by RAV TUX on 2007-10-27
> **macogw said:**
> nevermindI remember when You and [[COLOR=#D40000]**Brunellus**[/COLOR]]("http://ubuntuforums.org/member.php?u=9506") were talking about fsck at the Davenport at our first Ubuntu Meet Up...but I honestly had no idea what you guys were talking about. 

...but I did learn how to pronounce fsck from [[COLOR=#D40000]**Brunellus.**[/COLOR]]("http://ubuntuforums.org/member.php?u=9506")
;)

---

### Post by FuturePilot on 2007-10-27
How *do* you pronounce fsck?

---

### Post by marco123 on 2007-10-27
> **kostkon said:**
> Let's assume someone who had never used Linux before, finds Ubuntu interesting and installs it.

Now, think the possibility that this person religiously reboots his/her system only one time every month. Assuming the fact that *fsck* is set to start after 30 boots, then more than *2 years* (!) will have to pass until this person sees for the first time such a check being taken!!

Thus, many people, like *RAV TUX* (who hibernates his system), will rarely see *fsck* in action.

I have this problem.  I reboot every 2 - 4 months to install any updates that have built up and clean dust out of the case, so I installed Bonager and I set it to check before every reboot.  I'd never see a fsck otherwise.

---

### Post by RAV TUX on 2007-10-27
> **RAV TUX said:**
> Referencing your link, I have only heard it pronounced:

> "f-suck"
[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

I have never associated it with any kind of vulgarity.



> **FuturePilot said:**
> How *do* you pronounce fsck?

see above...

---

### Post by FuturePilot on 2007-10-27
> **RAV TUX said:**
> see above...

Thank you ;)

---

### Post by RAV TUX on 2007-10-27
> **FuturePilot said:**
> Thank you ;)
I forgot to include the pronunciation...

---

### Post by macogw on 2007-10-27
> **RAV TUX said:**
> I remember when You and [[COLOR=#D40000]**Brunellus**[/COLOR]]("http://ubuntuforums.org/member.php?u=9506") were talking about fsck at the Davenport at our first Ubuntu Meet Up...but I honestly had no idea what you guys were talking about. 

...but I did learn how to pronounce fsck from [[COLOR=#D40000]**Brunellus.**[/COLOR]]("http://ubuntuforums.org/member.php?u=9506")
;)

Well I was pronouncing it fisk.

---

### Post by RAV TUX on 2007-10-27
> **macogw said:**
> Well I was pronouncing it fisk.
You were mis-pronouncing it, if you remember  [[COLOR=#d40000]**brunellus**[/COLOR]]("http://ubuntuforums.org/member.php?u=9506") corrected your pronunciation.

At least from a third party perspective, this is how I remember the conversation to be.

...or at least he had given his version of proper pronunciation and it is for me the only one I remember.

---

### Post by atlfalcons866 on 2007-11-01
In my experience with file Systems (ext2/3, jfs,xfs). Ext3 is the only one that forces a check every 30 mounts. JFS and XFS never forced a check

---

### Post by init1 on 2007-11-01
> **FuturePilot said:**
> How *do* you pronounce fsck?
I've been pronouncing it "Fuh-sheck"

---

### Post by mallow on 2007-11-10
Why oh why can`t I abort fsck?? There really should be an option to skip fsck if linux must be user friendly. Fsck can be really annoying when you are a laptop user. Take this situation for instance - I go on a meeting with client, want to show him my project and my laptop won`t start because of disk check. If there would be a prompt: "check now/ check on next boot" the problem would be gone. Forever. 
I know that many people write about that for at least couple of months now. Why nobody does anything about it? What bad will happen if I`ll postpone fsck and check disk at 31st, not the 30th boot?

And to all those "just hit ctrl+C during disk check": that doesn`t work!

cheers

---

### Post by CanonKen on 2007-11-10
all this talk of 30, 34 boots mines just done one at 20 :confused:

---

### Post by RAV TUX on 2007-11-11
> **atlfalcons866 said:**
> In my experience with file Systems (ext2/3, jfs,xfs). Ext3 is the only one that forces a check every 30 mounts. JFS and XFS never forced a check
I traditionally always use the [ReiserFS]("http://en.wikipedia.org/wiki/ReiserFS") File System.

This could be why I never experienced a forced fsck?

I think I will reinstall my OS and use [ReiserFS]("http://en.wikipedia.org/wiki/ReiserFS") again.

---

### Post by Anessen on 2007-11-11
I pronounce it "fisk", and use it on the college systems as a replacement for an expletive. Makes them look twice.

---

### Post by ssam on 2007-11-11
[AutoFsck]("https://wiki.ubuntu.com/AutoFsck") for the win.

---

### Post by notwen on 2007-11-11
[Bonager]("http://ubuntuforums.org/showthread.php?t=295262") !!

---


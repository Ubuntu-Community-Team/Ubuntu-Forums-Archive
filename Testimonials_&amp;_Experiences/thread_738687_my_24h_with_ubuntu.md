---
title: "my 24h with ubuntu"
date: 2008-03-28
forum: Testimonials &amp; Experiences
---

### Post by quasar277 on 2008-03-28
First of all, thank you all who invest(ed) their time and energy in bringing ubuntu to life and keep it up and running.
I've been meaning to dump Microsoft for some time and yesterday was the day. I wanted to make sure I had a reliable linux distribution to keep and after trying out a few different flavours of linux my gut feeling told me ubuntu would be it only after an hour with the live cd.

And what an experience it has been!

First of all, I must say I don't care about the "humanitarian" side of ubuntu. It works and that's why I like it. When it doesn't it work, it certainly boosts a large community that is very busy publicizing the problems and solutions so users like me, new to linux, can find a workaround them. And when that fails, well then I am the one who has to be persistent ;) but more on that later

It doesn't even bother me anymore that my Canoscan  4200F will have to be chucked out because of Canon's absolute refusal to supply hardware information to linux developers. I don't even use it so much anymore. 
At some point I'll be getting some cheap (linux-friendly) scanner.

Speaking of hardware support, my (also canon) Pixma 5200 was printing "ok", yesterday on a Debian OS. There was a little "shadow image" to the right of every image it would print. I thought it was funny but it didn't bother me much since most of what I print is text anyway. Today as I do a test page on Ubuntu, not expecting any difference (the drivers / printing service, at least apparently, are the same) when surprise! No shadow, no nothing. A nice smooth print, not as sharp as under Windows but hey, it's using drivers from the Pixma 4000...

A little problem I ran into was my secondary hard drive.
I like a bit of control over the system so I went for the "Manual" option when creation partitions in the Ubuntu installation. After a while of fiddling with it I found out the hard way what is the meaning of "mounting points" -  this is not very explained in the documentation.
But ok, something I should have looked at before installing the system.
Then, lo and behold, I can access the drive but can't write to it (it belongs to root) and this one drove me a bit nuts... I tried editing permissions in fstabs but to no avail and after a long time of looking for a solution the only way -that I could find- was to activate root, login and change the permissions like that. Very simple, very easy. No I don't recommend it, but not finding anything else working, that was the only solution.

The other major (ok, no more eufemisms) problem I had was... drumrolls: "filesystem = read-only"
For this there was a bit more information, in the forums and by googling. I tried running fsck (all was "clear"), remounting the drive, editing fstab from a live cd boot (no permission)... I'm just about to reinstall it when I figure it's probably possible to activate root from the live cd and edit fstab from there. And that's what i did - I don't recommend it as the system (live boot) got unstable, but it worked.
By the way what caused this problem was to mount a problematic mp3 player (i/o errors) and trying to copy music to it. After removing reference of it on fstab the problem was gone.

So now onto finishing to set up my system. Should be fun :)

C.

P.S: I've been learning these "boxes" (computers) since the time of the 8086 and I even had one - it had so little memory that it could not be installed an antivirus in order to clean the virus it was stuck with!
So I've learned my share of DOS commands back in the days, but I have other interests now and I'm not going to learn any more of linux/ubuntu than I need to. So please, guys, be nice to us newbies ;)

---

### Post by PmDematagoda on 2008-03-28
This thread has been moved to the Ubuntu Testimonials and Experiences section.

---

### Post by Sef on 2008-03-30
> At some point I'll be getting some cheap (linux-friendly) scanner.

Check out [OpenPrinting's Suggested Printers]("http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters").

---

### Post by quasar277 on 2008-03-31
Thanks Sef, the printer's fine - it's a new scanner I need but I'm not so much in a hurry for that.

An update: I sweat my eyebrows trying to get Google Earth to work until I gave up and had to try the proprietary ATI driver (which wouldn't work at all before). Somehow it went very smooth and now I have GE working - slower than under Windows but it works.
Wish the ATI driver would support desktop effects...
No, better - wish Google Earth would support the open source drivers - they ARE smoother and faster and more stable than the ATI one's (at least for general desktop work)

Also gave it a try with Wine for an app which does not exist for anything but windows and it works pretty good (for a beta) although it's tricky to move the "C:" drive to a new location AFTER installing an app - somehow links get lost in the process - so I had to completely remove Wine and install it from scratch.

A lot of learning these last few days and a clear feeling that everytime I'm hours around something the solution ends up being actually quite easy - by the way, kudos for the team who wrote the HOWTO guides - they're very helpful!

Now that the system is more or less set up I can go on to more normal things like updating a spreadsheet  :)

C.

---

### Post by hyper_ch on 2008-04-01
If the second harddrive is mounted, you can alter permissions there. Assume it's mounted at /media/sdb1 and that it's ext3 then you'd run:

```

sudo chown -R USER.USER /media/sdb1

```

Where USER is your actual username.

---

### Post by stchman on 2008-04-01
> **hyper_ch said:**
> If the second harddrive is mounted, you can alter permissions there. Assume it's mounted at /media/sdb1 and that it's ext3 then you'd run:

```

sudo chown -R USER.USER /media/sdb1

```

Where USER is your actual username.

Use $USER and you need a ':'.  $USER is the user currently logged in.

```
sudo chown -R $USER:$USER /media/sdb1
```

---

### Post by stchman on 2008-04-01
> **quasar277 said:**
> First of all, thank you all who invest(ed) their time and energy in bringing ubuntu to life and keep it up and running.
I've been meaning to dump Microsoft for some time and yesterday was the day. I wanted to make sure I had a reliable linux distribution to keep and after trying out a few different flavours of linux my gut feeling told me ubuntu would be it only after an hour with the live cd.

And what an experience it has been!

First of all, I must say I don't care about the "humanitarian" side of ubuntu. It works and that's why I like it. When it doesn't it work, it certainly boosts a large community that is very busy publicizing the problems and solutions so users like me, new to linux, can find a workaround them. And when that fails, well then I am the one who has to be persistent ;) but more on that later

It doesn't even bother me anymore that my Canoscan  4200F will have to be chucked out because of Canon's absolute refusal to supply hardware information to linux developers. I don't even use it so much anymore. 
At some point I'll be getting some cheap (linux-friendly) scanner.

Speaking of hardware support, my (also canon) Pixma 5200 was printing "ok", yesterday on a Debian OS. There was a little "shadow image" to the right of every image it would print. I thought it was funny but it didn't bother me much since most of what I print is text anyway. Today as I do a test page on Ubuntu, not expecting any difference (the drivers / printing service, at least apparently, are the same) when surprise! No shadow, no nothing. A nice smooth print, not as sharp as under Windows but hey, it's using drivers from the Pixma 4000...

A little problem I ran into was my secondary hard drive.
I like a bit of control over the system so I went for the "Manual" option when creation partitions in the Ubuntu installation. After a while of fiddling with it I found out the hard way what is the meaning of "mounting points" -  this is not very explained in the documentation.
But ok, something I should have looked at before installing the system.
Then, lo and behold, I can access the drive but can't write to it (it belongs to root) and this one drove me a bit nuts... I tried editing permissions in fstabs but to no avail and after a long time of looking for a solution the only way -that I could find- was to activate root, login and change the permissions like that. Very simple, very easy. No I don't recommend it, but not finding anything else working, that was the only solution.

The other major (ok, no more eufemisms) problem I had was... drumrolls: "filesystem = read-only"
For this there was a bit more information, in the forums and by googling. I tried running fsck (all was "clear"), remounting the drive, editing fstab from a live cd boot (no permission)... I'm just about to reinstall it when I figure it's probably possible to activate root from the live cd and edit fstab from there. And that's what i did - I don't recommend it as the system (live boot) got unstable, but it worked.
By the way what caused this problem was to mount a problematic mp3 player (i/o errors) and trying to copy music to it. After removing reference of it on fstab the problem was gone.

So now onto finishing to set up my system. Should be fun :)

C.

P.S: I've been learning these "boxes" (computers) since the time of the 8086 and I even had one - it had so little memory that it could not be installed an antivirus in order to clean the virus it was stuck with!
So I've learned my share of DOS commands back in the days, but I have other interests now and I'm not going to learn any more of linux/ubuntu than I need to. So please, guys, be nice to us newbies ;)

Glad to have you onboard.

HP printers are usually Linux friendly.

---

### Post by stchman on 2008-04-01
> **quasar277 said:**
> Thanks Sef, the printer's fine - it's a new scanner I need but I'm not so much in a hurry for that.

An update: I sweat my eyebrows trying to get Google Earth to work until I gave up and had to try the proprietary ATI driver (which wouldn't work at all before). Somehow it went very smooth and now I have GE working - slower than under Windows but it works.
Wish the ATI driver would support desktop effects...
No, better - wish Google Earth would support the open source drivers - they ARE smoother and faster and more stable than the ATI one's (at least for general desktop work)

Also gave it a try with Wine for an app which does not exist for anything but windows and it works pretty good (for a beta) although it's tricky to move the "C:" drive to a new location AFTER installing an app - somehow links get lost in the process - so I had to completely remove Wine and install it from scratch.

A lot of learning these last few days and a clear feeling that everytime I'm hours around something the solution ends up being actually quite easy - by the way, kudos for the team who wrote the HOWTO guides - they're very helpful!

Now that the system is more or less set up I can go on to more normal things like updating a spreadsheet  :)

C.

I have an ATI equipped laptop and GE runs fine on it.

Use Envy to install your proprietary ATI drivers.  Envy is a fantastic program.

---

### Post by quasar277 on 2008-04-01
Thanks for the command lines, guys :) I'll try that next time I need to install Ubuntu.

stchman, the first time I tried to get the proprietary ATI drivers to work I had problems BUT after installing the open-source drivers as per documentation instructions (step-by-step) the second time I tried ATI's drivers (pre-packed with ubuntu) it worked like a charm, then it was a matter of a bit of fine tuning.

But believe me, life was made much easier thanks to the community documentation (HOWTO docs) - a big thank you!

C.

---

### Post by hyper_ch on 2008-04-01
> **stchman said:**
>  and you need a ':

You don't need a column... a period just works fine ;)

---

### Post by wPwLUi3N on 2008-04-02
One more happy story to ubuntu.

---

### Post by quasar277 on 2008-04-04
Update:

Been installing some multimedia goodies lately and wow... far from straightforward!

audio editing - tried Audacity, found it unintuitive; tried Sweep - slow and prone to crashing = went back to Audacity

cd ripping (ahem, archiving) - tried sound juicer, it doesn't like mp3's - I like ogg too but my portable mp3 player doesn't want to know about it (lol); tried grip, works ok; tried banshee - now using it only for ripping, not playing (i dislike it when an application has no option to remove its icon from the tray!)

cd creation: poor serpentine can't handle vbr mp3s I think... tried brasero - looks good, staying with it

DVD playback - ok, Totem can play my "archived" DVDs but not the commercial ones?! Tried VLC, it works

So... 3 "native" Ubuntu applications: Sound Juicer, Serpentine and Totem, fail at their core functions (true, mp3 enconding isn't really the highest moral thing a linux system should be ready to do) and I was wondering if I should go for Hardy once it's out? No way :p

Again, a big thank you to all the people who participate in all the problem-solving at this and other forums - I'd have given up on Linux / Ubuntu if it wasn't for that :)

C.

P.S. what's up with gstreamer? it appears a lot of the issues I was bumping into had to do with a combination of gutsy + gstreamer apps

---

### Post by hyper_ch on 2008-04-04
for burning, try k3b....

haven't used SJ, Serp. and Totem ^^

---


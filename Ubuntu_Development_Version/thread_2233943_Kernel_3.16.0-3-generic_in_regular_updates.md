---
title: "Kernel 3.16.0-3-generic in regular updates"
date: 2014-07-11
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2014-07-11
I just got some updates and the 3.16.0-3-generic kernel was included with a dist-upgrade and it came with an added file **thermald**. :-s

---

### Post by Cavsfan on 2014-07-11
**thermald** might be a good thing. Although I'm not advocating doing anything at the bottom of this page. If you do you're on your own. 
I only supplied it for a description because I didn't know what it was.

[http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html](http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html)

BTW I don't have a laptop.

---

### Post by Smask on 2014-07-11
> **Cavsfan said:**
> I just got some updates and the 3.16.0-3-generic kernel was included

Now we wait for Xorg server 1.16, which will be released in a week.

---

### Post by craig10x on 2014-07-11
I think it's on by default (thermald) isn't it?  I have intel sandy bridge on my laptop and package manager shows it is installed...i think you don't need to configure anything on it, it has certain default presets...sounds like it will be an additional tool to keep intels running extra cool...
Just got the 3.16.0-3 kernel when i ran the updater this evening...runs smooth, snappy and just as cool as 3.15 did on my computer :D

---

### Post by Cavsfan on 2014-07-12
It just got installed on my pc when the kernel was installed because it took a **sudo apt-get dist-upgrade** to get the kernel and **thermald** as they were new packages.
I guess it just comes with everything else as I have a pc and not a laptop. I have been getting some other weird updates to things like cell phone images or something like that I can't recall now.

It just caught my eye is why I mentioned it.

---

### Post by craig10x on 2014-07-12
@cavsfan: for me, it came in the regular software updater updates...the kernel and a bunch of other things (i didn't read the whole list) so i wasn't looking out for it (in fact didn't even know about thermald until you mentioned it...lol) but after reading your post, i typed it into the search bar on package manager and saw it listed and it showed as being INSTALLED...

From what i read, it's in the repos on 14.04 but you have to install it...on 14.10  they just installed it by default with these updates, apparently ;)

---

### Post by Cavsfan on 2014-07-13
> **craig10x said:**
> @cavsfan: for me, it came in the regular software updater updates...the kernel and a bunch of other things (i didn't read the whole list) so i wasn't looking out for it (in fact didn't even know about thermald until you mentioned it...lol) but after reading your post, i typed it into the search bar on package manager and saw it listed and it showed as being INSTALLED...

From what i read, it's in the repos on 14.04 but you have to install it...on 14.10  they just installed it by default with these updates, apparently ;)

Good deal! I guess it will be a good thing for laptop users.

---

### Post by philinux on 2014-07-13
thermald is indeed in the 14.04 repo.

```
apt-cache policy thermald
thermald:
  Installed: (none)
  Candidate: 1.1~rc2-11ubuntu0.1
  Version table:
     1.1~rc2-11ubuntu0.1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
     1.1~rc2-11 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
```

---

### Post by Cavsfan on 2014-07-13
> **craig10x said:**
> @cavsfan: for me, it came in the regular software updater updates...the kernel and a bunch of other things (i didn't read the whole list) so i wasn't looking out for it (in fact didn't even know about thermald until you mentioned it...lol) but after reading your post, i typed it into the search bar on package manager and saw it listed and it showed as being INSTALLED...

From what i read, [COLOR=#0000ff]it's in the repos on 14.04[/COLOR] [COLOR=#0000ff]but you have to install it...on 14.10[/COLOR]  they just installed it by default with these updates, apparently ;)

> **philinux said:**
> thermald is indeed in the 14.04 repo.

```
apt-cache policy thermald
thermald:
  Installed: (none)
  Candidate: 1.1~rc2-11ubuntu0.1
  Version table:
     1.1~rc2-11ubuntu0.1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
     1.1~rc2-11 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
```

Yes sir, that is what craig10x stated that it is in the repos for 14.04 but is installed on 14.10.

@craig10x, BTW you still use update mangler to get your updates? :p That is what Ranch hand used to call it. 
He convinced me to use the CLI method of getting updates. It prevents any possibility of a partial update and you can see a little better what is going on.
**sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean** - to get regular updates.
**sudo apt-get dist-upgrade** - for when something is held back because other new file(s) will to be installed along with some updated files. This is how kernels get installed.

Then I added this one myself to save typing:
**sudo apt-get autoremove** - when unneeded files are installed and reported as unnecessary. 
To make that even easier someone else showed me how to put those in aliases:

```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'
alias ud3='sudo apt-get autoremove'

```

All I have to do is enter ud and then my password in terminal most of the time. ;)

---

### Post by craig10x on 2014-07-13
Yes i do still use the mangler...err update manager ;)
It's actually been working very smoooooth on 14.10 since i installed it...but i am glad you posted that terminal way of doing the updates because i remember that during 14.04 development, when i would occasionally run into a situation where the updater hung up, then doing the updates in the terminal always straightened it right out!  Perhaps they've made improvements in the updater because so far it's been great and as long as there is no problems, i will keep using it...

I have to say, that so far 14.10 development has been smooth as can be and VERY stable (and this is my ONLY install) Hard to believe it is still an Alpha 1...feels more like a Beta 2 :D
14.10 so far seems like a very refined version of 14.04...i like it a lot...and thermald seems to be helping in certain situations in keeping my i3 (sandy bridge) laptop cooler then ever, so i think it is excellent to have it now installed by default...

---

### Post by Cavsfan on 2014-07-13
> **craig10x said:**
> Yes i do still use the mangler...err update manager ;)
It's actually been working very smoooooth on 14.10 since i installed it...but i am glad you posted that terminal way of doing the updates because i remember that during 14.04 development, when i would occasionally run into a situation where the updater hung up, then doing the updates in the terminal always straightened it right out!  Perhaps they've made improvements in the updater because so far it's been great and as long as there is no problems, i will keep using it...

I have to say, that so far 14.10 development has been smooth as can be and VERY stable (and this is my ONLY install) Hard to believe it is still an Alpha 1...feels more like a Beta 2 :D
14.10 so far seems like a very refined version of 14.04...i like it a lot...and thermald seems to be helping in certain situations in keeping my i3 (sandy bridge) laptop cooler then ever, so i think it is excellent to have it now installed by default...

LoL :lol: Glad to hear! I have always used the CLI way since about Jaunty I think. I remember what a partial update can do to your system. Good that thermald helps keep laptops cool! Win Win!

---

### Post by cariboo on 2014-07-14
I'm not sure if this is a systemd problem, or something else completely, but after the kernel update and restart, I let the system go to sleep as  I normally do when I head of to bed. On trying to use the system in the morning, it was totally locked up. At the time I was running the nouveau driver, and nothing I did would get the system to start in a gui. After fighting it for a couple of hours, I decided to do a reinstall, and once the system was up and running the best resolution with the nouveau driver was 1024X768. I decided to try the latest Nvidia driver (nvidia-340), and the system came up with a blank screen, I edited the kernel line in grub, removing quiet splash $vt_handoff and init=/lib/systemd/systemd and the system came up as it should. System specifications:

[LIST]
[*]AMD FX(tm)-8350 Eight-Core Processor
[*]VGA compatible controller product: GM107 [GeForce GTX 750]
[*]16GiB Ram
[/LIST]

---

### Post by Cavsfan on 2014-07-14
> **cariboo907 said:**
> I'm not sure if this is a systemd problem, or something else completely, but after the kernel update and restart, I let the system go to sleep as  I normally do when I head of to bed. On trying to use the system in the morning, it was totally locked up. At the time I was running the nouveau driver, and nothing I did would get the system to start in a gui. After fighting it for a couple of hours, I decided to do a reinstall, and once the system was up and running the best resolution with the nouveau driver was 1024X768. I decided to try the latest Nvidia driver (nvidia-340), and the system came up with a blank screen, I edited the kernel line in grub, removing quiet splash $vt_handoff and init=/lib/systemd/systemd and the system came up as it should. System specifications:

[LIST]
[*]AMD FX(tm)-8350 Eight-Core Processor 
[*]VGA compatible controller product: GM107 [GeForce GTX 750] 
[*]16GiB Ram 
[/LIST]


I haven't had any problems and you have a much better system than I do. I just have: 
[LIST]
[*]Core 2 Quad Q9550 2.83Ghz 
[*]Nvidia Geforce 9800GT 1GB mem 
[*]4GB Ram 
[/LIST]

IDK but maybe it was the $vt_handoff. I left the quit splash in the boot line.
If you wanted to make a semi-permanent mod to allow booting with systemd just add this to a text file:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "[COLOR=#ff0000]Utopic Unicorn 14.10 systemd (Devel Branch)[/COLOR]" {
    set root=(hd[COLOR=#ff0000]0,5[/COLOR])
        linux /vmlinuz root=/dev/sd[COLOR=#ff0000]a5[/COLOR] ro quiet splash init=/lib/systemd/systemd
        initrd /initrd.img
}
```

Everything in red in the text can say whatever you want as you will be the only one to see it and it will identify the entry.
The red part hard drive and partition should be changed to where ever your Utopic install is.

Then save this as 06_custom and if it's in your home just move it with this **sudo cp ~/06_custom /etc/grub.d/06_custom **
Then make it executable **sudo chmod +x /etc/grub.d/06_custom** and of course **sudo update-grub**.
With the entry as it is nothing will be listed in the output of **sudo update-grub** to let you know it is there but it will appear as the first entry at boot time.

If you have your default line the top line no need to change anything else but if it is not 
edit the default line with **gksu gedit /etc/default/grub** and add one to whatever you have on **GRUB_DEFAULT=**.

Then if you wanted to get rid of it **sudo rm /etc/grub.d/06_custom** and **sudo update-grub**.

I just didn't like the option of typing that in a bootup so I made a special entry in grub for systemd. It's been running virtually flawless from my perspective.
And although systemd is available in Trusty with a ppa I myself do not recommend it. Been there and done that. It didn't work.
But, in Utopic it's the only way I have been running it since that systemd thread got started.

I hope this will better enhance your systemd experience. :)

I'm going to put this baby to sleep for a while and see what happens when I wake it.

---

### Post by Cavsfan on 2014-07-14
I just let it sleep for about 8 minutes or so but it woke from suspend perfectly.

A week or so ago I put it to sleep (suspend) and left for an hour or two. When I came back it was completely shut down. I had to press the power button and it went through the initial boot process.
I thought it was a problem with Utopic or systemd so I logged into Precise 12.04 ended up suspending it and leaving again. When I came back the same thing happened. Had to do the initial boot again.

It hasn't done that since and it may have been the power went off for a few seconds as I have it set in bios to stay off in the event of a loss of power.

I have bios set to S3 sleep mode. I noticed if I set that to S1 that it wil hibernate instead of suspend. Windows calls this "sleep". :)

---

### Post by DogMatix on 2014-07-15
Mmm.. after the 3.16 update I can't get a GUI either. I can get it to boot to GUI with 'nomodeset'. Also booting to systemd. Intel graphics here though.

It's late now. I'll wrestle with this in the morning.

EDIT: Had a further play this morning. nomodeset gets me a desktop but xrandr reports 800 x 600 screen resolution is all thats available. Booting without nomodeset shows garbled screen. I can see part of the lightdm screen but can't get any further. Booting into 3.15 and everything is OK. Will play again later.

---

### Post by cariboo on 2014-07-16
Since having the initial problem, I've rebooted twice without any problems.Cavsfan, I'll try your suggestion a bit later, as right now, I'm sitting on my deck typing this on my tablet, and enjoying a nice frosty beverage.:-D

---

### Post by Cavsfan on 2014-07-17
> **cariboo907 said:**
> Since having the initial problem, I've rebooted twice without any problems.Cavsfan, I'll try your suggestion a bit later, as right now, I'm sitting on my deck typing this on my tablet, and enjoying a nice frosty beverage.:-D

Enjoy! :D Let me know what happens if you do try my suggestion. It will work I'm pretty sure and I've probably repeated myself on that a few times now. :p

---

### Post by Cavsfan on 2014-07-17
> **philinux said:**
> thermald is indeed in the 14.04 repo.

```
apt-cache policy thermald
thermald:
  Installed: (none)
  Candidate: 1.1~rc2-11ubuntu0.1
  Version table:
     1.1~rc2-11ubuntu0.1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
     1.1~rc2-11 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
```

Sorry, I think I misinterpreted you and you were just confirming that thermald was available on 14.04. Instead I thought you were bringing it up.

Just got the 3.16.0-4-generic kernel, the Nvidia 331.89 driver and everything is moving along smoothly. Got all the updates via systemd too. :)

---

### Post by Cavsfan on 2014-07-17
> **cariboo907 said:**
> I'm not sure if this is a systemd problem, or something else completely, but after the kernel update and restart, I let the system go to sleep as  I normally do when I head of to bed. On trying to use the system in the morning, it was totally locked up. At the time I was running the nouveau driver, and nothing I did would get the system to start in a gui. After fighting it for a couple of hours, I decided to do a reinstall, and once the system was up and running the best resolution with the nouveau driver was 1024X768. I decided to try the latest Nvidia driver (nvidia-340), and the system came up with a blank screen, I edited the kernel line in grub, removing quiet splash $vt_handoff and init=/lib/systemd/systemd and the system came up as it should. System specifications:

[LIST]
[*]AMD FX(tm)-8350 Eight-Core Processor 
[*]VGA compatible controller product: GM107 [GeForce GTX 750] 
[*]16GiB Ram 
[/LIST]


Are you still having this problem? I suspended Utopic last weekend for a few hours while out of the house and it came back just like it should have. So, my problem appears that the electricity went off.

---

### Post by cariboo on 2014-07-17
> **Cavsfan said:**
> Are you still having this problem? I suspended Utopic last weekend for a few hours while out of the house and it came back just like it should have. So, my problem appears that the electricity went off.

I don't seem to be having any more problems, even after the kernel update yesterday. :-)

---

### Post by DogMatix on 2014-07-17
Problem still persists for me. I have discovered booting with upstart allows me to use the latest kernel. So my issue may be related to systemd. I was going to reinstall but I think I'll stick with it for now and see what the next few updates bring in.

---

### Post by Cavsfan on 2014-07-18
> **cariboo907 said:**
> I don't seem to be having any more problems, even after the kernel update yesterday. :-)

Good deal! I got another problem when cgmanager needed updating a little while ago. I could not boot into the latest kernel but was able to with 3.16.0-3-generic after booting with upstart and getting the update.
Need to find that thread to post the bug I created just now. Fun breakage! :)

---

### Post by Cavsfan on 2014-07-18
> **DogMatix said:**
> Problem still persists for me. I have discovered booting with upstart allows me to use the latest kernel. So my issue may be related to systemd. I was going to reinstall but I think I'll stick with it for now and see what the next few updates bring in.

If you are unable to boot into the latest kernel after an update to cgmanager which is what I currently have. Here is the bug for it [https://bugs.launchpad.net/ubuntu/+source/cgmanager/+bug/1344196](https://bugs.launchpad.net/ubuntu/+source/cgmanager/+bug/1344196)
I could not get the update without errors using systemd but it updated smoothly via upstart but after that I had to boot into the previous kernel to get in at all using 3.16.0-3-generic.

---

### Post by DogMatix on 2014-07-18
Thanks for the link. That pretty much sums up whats going on for me. I've 'also affects me' but there's not a lot else useful I could add besides at the moment.

Most reliable boot for me as things stand is the last 3.15 kernel as far as systemd go's.

---

### Post by Cavsfan on 2014-07-19
> **DogMatix said:**
> Thanks for the link. That pretty much sums up whats going on for me. I've 'also affects me' but there's not a lot else useful I could add besides at the moment.

Most reliable boot for me as things stand is the last 3.15 kernel as far as systemd go's.

You should have 3.16.0-3-generic and 3.16.0-4-generic as the latest 2 kernels. My 3.15 kernel is gone now.
I am pretty much just using upstart with the latest kernel 3.16.0-4-generic and plan to just wait it out before trying systemd again.

---

### Post by DogMatix on 2014-07-19
I've retained 3.15 for a while. I have 1.16.03 & 04 but neither are proving completely reliable with  either upstart or systemd. I think I may create a new partition tomorrow to do a fresh 'daily' install to compare and contrast what I have now. I've done a fair bit of 'fiddling' since I installed this 14.10 and I want to rule out other gremlins that may be playing a part in my troubles.

---

### Post by Cavsfan on 2014-07-20
> **DogMatix said:**
> I've retained 3.15 for a while. I have 1.16.03 & 04 but neither are proving completely reliable with  either upstart or systemd. I think I may create a new partition tomorrow to do a fresh 'daily' install to compare and contrast what I have now. I've done a fair bit of 'fiddling' since I installed this 14.10 and I want to rule out other gremlins that may be playing a part in my troubles.

Yes, we can be our own worst enemies at times by tweaking a little too much or adding this or that when we should leave it as it comes default. Been there and done that more than once.
Everything seems pretty stable here on upstart (normal boot) with the latest kernel. I'm leaving systemd alone for a while as it won't even boot. It's not coming with Utopic as default anyway.

---

### Post by craig10x on 2014-07-20
I went back to 14.04 for now...so i am no longer in development...planning on upgrading to Utopic when it's final released...Just wondering though, i know 14.04.1 point release comes out on thursday...will there be a change in the kernel for it? (which would be the utopic kernel of course) or does that not happen until 14.04.2 is release next January?
And, when it happens, would someone running Trusty automatically get the utopic kernel in the regular software updater updates or would you have to use some other method to get it?

Hope some of you development testers will be able to enlighten me ;)

---

### Post by Cavsfan on 2014-07-21
> **craig10x said:**
> I went back to 14.04 for now...so i am no longer in development...planning on upgrading to Utopic when it's final released...Just wondering though, i know 14.04.1 point release comes out on thursday...will there be a change in the kernel for it? (which would be the utopic kernel of course) or does that not happen until 14.04.2 is release next January?
And, when it happens, would someone running Trusty automatically get the utopic kernel in the regular software updater updates or would you have to use some other method to get it?

Hope some of you development testers will be able to enlighten me ;)

According to this the 14.04.1 point release will still contain the 3.13 kernel but the 14.04.2 point release will contain the 3.16 kernel.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support)

---

### Post by craig10x on 2014-07-21
Thanks Cavsfan...Nice Chart you linked to...:D
I was kind of hoping they'd have the utopic kernel for this point release but had a feeling it would not be until 14.04.2

---

### Post by craig10x on 2014-07-21
Update...using exton's compiled kernel package (3 deb files) i am now running the ubuntu patched version of 3.15.0-6 on my ubuntu 14.04...although instead of using his command to install, i installed each deb using gdebi and it worked perfect!  re-booted and using it now...so, now i have the lower temperatures of the patched ubuntu version (as opposed to the mainline version) and no multimedia stability problem like i was having with 3.13 kernel...

I will be using it right until final release of Utopic and then i will upgrade right into it....In case anyone is interested, they can see it here:  (exton to the rescue....lol) :mrgreen:
[http://extonlinux.wordpress.com/2014/06/23/kernel-3-15-0-6-exton-3-15-0-stable/](http://extonlinux.wordpress.com/2014/06/23/kernel-3-15-0-6-exton-3-15-0-stable/)

---

### Post by zika on 2014-07-21
> **craig10x said:**
> Update...using exton's compiled kernel package (3 deb files) i am now running the ubuntu patched version of 3.15.0-6 on my ubuntu 14.04...although instead of using his command to install, i installed each deb using gdebi and it worked perfect!  re-booted and using it now...so, now i have the lower temperatures of the patched ubuntu version (as opposed to the mainline version) and no multimedia stability problem like i was having with 3.13 kernel...

I will be using it right until final release of Utopic and then i will upgrade right into it....In case anyone is interested, they can see it here:  (exton to the rescue....lol) :mrgreen:
[http://extonlinux.wordpress.com/2014/06/23/kernel-3-15-0-6-exton-3-15-0-stable/](http://extonlinux.wordpress.com/2014/06/23/kernel-3-15-0-6-exton-3-15-0-stable/)What is the incentive to use such kernel while there are kernels from mainline PPA (vanilla made for Ubuntu) and from PPA ([http://packages.ubuntu.com/utopic/kernel/](http://packages.ubuntu.com/utopic/kernel/)) that are with all Ubuntu flavours added?
Kernel from the source You've chosen is not (as far as I know) either from one nor from other side of a scale, somewhere in the middle... ;) Yes, 3.15 was not produced for Utopic but mainline has whole its genesis...
To each his own. Choice is Yours. What is also interesting is that 3.13 should have some important traces from subsequent newer kernels as far as I rember decision made some while ago. Bit, I might be wrong, it happened so many times.

---

### Post by craig10x on 2014-07-21
@zika: he simply compiles the ubuntu patched versions of each final kernel release to make them easier for people like me (less technical prowess) to install...:D
Apparently, he knows exactly which packages to grab where as i did not...and no one here was really taking me by the hand and giving me the specific ones i needed to use...;)
I know you tried to help, but you were a bit too technical for me to grasp...

The reason why i needed the ubuntu patched versions that you are getting automatically in Utopic development, as opposed to the mainline versions, is that i found from running mainline that at least on my hardware (an intel i3 laptop) they run CONSIDERABLY hotter then the ubuntu patched versions which run as cool as a cucumber...

Since i installed his this morning, i can see it IS indeed the ubuntu patched release of 3.15.0-6 as the temps run several degrees cooler then mainline and this is running just as well as it did for me when i was on 14.10 development... The reason why i needed it is that a modification was made in the 3.13 kernel after the initial 3.13.24 the final was installed with, which made my multimedia unstable and i needed to get a newer kernel to get away from that problem...this will do it for me and let me "ride out" 14.04 until either it gets the 3.16 kernel next february OR i upgrade to 14.10 in October (have not quite decided yet but there is plenty of time)...

My other option was to keep manually booting into 3.13.24 but that was a bother every day and this is a much better solution overall...so basically exton saved my rear end :mrgreen:

---

### Post by zika on 2014-07-22
> **craig10x said:**
> @zika: he simply compiles the ubuntu patched versions of each final kernel release to make them easier for people like me (less technical prowess) to install...:D
Apparently, he knows exactly which packages to grab where as i did not...and no one here was really taking me by the hand and giving me the specific ones i needed to use...;)
I know you tried to help, but you were a bit too technical for me to grasp...

The reason why i needed the ubuntu patched versions that **you are getting automatically in Utopic development**, as opposed to the mainline versions, is that i found from running mainline that at least on my hardware (an intel i3 laptop) they run CONSIDERABLY hotter then the ubuntu patched versions which run as cool as a cucumber...

Since i installed his this morning, i can see it IS indeed the ubuntu patched release of 3.15.0-6 as the temps run several degrees cooler then mainline and this is running just as well as it did for me when i was on 14.10 development... The reason why i needed it is that a modification was made in the 3.13 kernel after the initial 3.13.24 the final was installed with, which made my multimedia unstable and i needed to get a newer kernel to get away from that problem...this will do it for me and let me "ride out" 14.04 until either it gets the 3.16 kernel next february OR i upgrade to 14.10 in October (have not quite decided yet but there is plenty of time)...

My other option was to keep manually booting into 3.13.24 but that was a bother every day and this is a much better solution overall...so basically exton saved my rear end :mrgreen:I'm not getting it automatically (on this machine for sure since it is not UU)... ;)

---

### Post by craig10x on 2014-07-22
Oh yeah..just noticed that...you are running trusty also...thought you were on development....so of course, you wouldn't be getting those unless you download them yourself...
I really needed that ubuntu patched version like really bad...so exton really saved the day for me ;)

I was a little nervous when i installed (having no previous experience with his work) but it went super smooth and i when i re-booted i was right in it with no problem...sweet :mrgreen:

---

### Post by Cavsfan on 2014-07-22
> **craig10x said:**
> Thanks Cavsfan...Nice Chart you linked to...:D
I was kind of hoping they'd have the utopic kernel for this point release but had a feeling it would not be until 14.04.2

Yeah I think I amazed myself on that one! :lol: I found exactly what you were asking. I was curious about that as well.

---

### Post by Cavsfan on 2014-07-23
Just picked up the 3.16.0-5-generic kernel running fine but still no systemd. I tried it and no bueno. :sad:

---

### Post by DogMatix on 2014-07-24
> **Cavsfan said:**
> Just picked up the 3.16.0-5-generic kernel running fine but still no systemd. I tried it and no bueno. :sad:

The 3.16.0-5 kernel seems to have ironed out my problems. It has booted cleanly twice. No glitchy graphics during boot. I haven't tried systemd yet. But this is the first 3.16 kernel I've got running properly so things are movingin the right direction for me.

EDIT: I can boot to a GUI desktop in systemd. However, networking, wireless or wired, is not working. GUI Shutdown got a Dbus error and trying to shutdown from Terminal got to 'system halt' message then just sat there. I've replicated these problems over a couple of boots so I guess systemd is not an option for me at the moment either.

EDIT +1: Just read your messages on Launchpad about systemd 208. I'll wait it out until that hits utopic updates and see if that helps.

---

### Post by Cavsfan on 2014-07-24
> **DogMatix said:**
> The 3.16.0-5 kernel seems to have ironed out my problems. It has booted cleanly twice. No glitchy graphics during boot. I haven't tried systemd yet. But this is the first 3.16 kernel I've got running properly so things are movingin the right direction for me.

EDIT: I can boot to a GUI desktop in systemd. However, networking, wireless or wired, is not working. GUI Shutdown got a Dbus error and trying to shutdown from Terminal got to 'system halt' message then just sat there. I've replicated these problems over a couple of boots so I guess systemd is not an option for me at the moment either.

EDIT +1: Just read your messages on Launchpad about systemd 208. I'll wait it out until that hits utopic updates and see if that helps.

Glad things are improving for you! I couldn't get very far with systemd. It would go as far as the login screen but it wouldn't allow anything to be entered or clicked on.

I had to either Alt+Tab+F1 to login to CLI and then sudo reboot or press the reset button to reboot.

Opening up Pre-release updates and just getting the systemd updated did the job for me. It should be hitting the main updates soon I would think. 
I went ahead and tried it to test it for them and it worked great. But, I don't blame you for waiting. It will fix the problem when systemd 208 is released.

---


---
title: "Daily Live, Ubiquity Crash"
date: 2012-02-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by arpanaut on 2012-02-10
For the past week or so, since A-2, Ubiquity crashes about half way through the install.
It seems that the target drive gets unmounted and then the installer disappears.
Or maybe the other way around, the live session continues working but the cursor is the spinner.
I can't find any relevant information in any logs.  I might not be looking in the right places?
I didn't find any ubiquity bugs on launchpad that appeared similar to my issues.

Anybody having any luck using the daily live to complete the install?

I'm off to get the alt.iso to see if I have better luck.
Frustrating as I only have one install of PP now and it has been updated from NN.
I really need a fresh install to test with.

Thanks

---

### Post by VMC on 2012-02-10
I haven't had problems with the live installer for a couple of weeks. Maybe your hardware or BIOS is the problem - but if you installed ok in the past, that can't be it unless something changed. I use the AMD64 iso.

Also I write the ISO to a usb stick instead of cd.

---

### Post by jerrylamos on 2012-02-10
I did have a couple ubiquity crashes on pangolin, not with the last .iso I tried from Feb 7 daily build.  I usually use the daily builds and not the ones in the alpha/beta release notes.

Jerry

---

### Post by arpanaut on 2012-02-10
Thanks guys,
i386 here, never really had install issues before, so I'm stumped.
Booting from USB on flash drive and HDD grub boot both fail.
Just weird, Alpha 2 image worked on a different rig, but I wiped the flash drive to test daily,
and zysync wiped the A-2 image. Guess I should keep a copy of a working image as Jerry advises.

Nothing really different on this rig except that I had a power supply failure a few weeks ago.
 but after I replaced the PS everything has been normal. The install issue is fairly new, don't know.

I've got 2 pata HDD, 2 sata Hdd on here, and usually 8-10 different installs, old and new.
Messed up my A-2 install from not paying attention, just want a fresh PP
Meh... I'll figure it out!

Thanks again.

---

### Post by VMC on 2012-02-10
> **arpanaut said:**
> Thanks guys,
i386 here, never really had install issues before, so I'm stumped.
Booting from USB on flash drive and HDD grub boot both fail.
Just weird, Alpha 2 image worked on a different rig, but I wiped the flash drive to test daily,
and zysync wiped the A-2 image. Guess I should keep a copy of a working image as Jerry advises.

Nothing really different on this rig except that I had a power supply failure a few weeks ago.
 but after I replaced the PS everything has been normal. The install issue is fairly new, don't know.

I've got 2 pata HDD, 2 sata Hdd on here, and usually 8-10 different installs, old and new.
Messed up my A-2 install from not paying attention, just want a fresh PP
Meh... I'll figure it out!

Thanks again.
Ther's a log file just for ubiquity when it breaks. Don't reboot and look into /var/logs for some clues.

Also start ubiquity from cli and see what pops up.

---

### Post by jbicha on 2012-02-11
I'd give it another try in a couple days once the new webkit builds. There's also a new ubiquity that was posted tonight; perhaps it fixes some of the brokenness.

---

### Post by arpanaut on 2012-02-11
> Ther's a log file just for ubiquity when it breaks. Don't reboot and look into /var/logs for some clues.

That's what I find strange, I don't find any logs on either the live cd's logs or the "target" logs in the installer/live-session.
Just seems strange there is no evidence of the crash.

> Also start ubiquity from cli and see what pops up.
Yup next option when I'm ambitious to feel failure again. lol
> 
There's also a new ubiquity that was posted tonight; perhaps it fixes some of the brokenness.

Thanks for that!  Hopefully so..  Just wanted to answer some this new call for testing stuff and was thinking
a cleaner install would "prove" better.

Onward and Upward

TYVM

---

### Post by kansasnoob on 2012-02-11
Just now performing a fresh install with the i386 20120211 Ubuntu image and on my first try I booted to the live desktop first, then selected install, and once I got to "preparing to install" I selected to DL updates and install 3rd party software. 

Shortly thereafter everything froze. Well, saying "everything froze" is inaccurate. X did not freeze, I could still move the mouse pointer and Alt + SysReq + K killed X, but the login screen never appeared.

I then repeated but this time chose "install" w/o first going to the live DE, and I left the DL updates and 3rd party software boxes unchecked. Then the installation completed OK.

Now I need to rinse & repeat a couple of times to see whether it's a matter of having booted to the live DE first, or if it had to do with selecting DL updates and/or 3rd party stuff :)

But that may take a while.

---

### Post by kansasnoob on 2012-02-11
> **kansasnoob said:**
> Just now performing a fresh install with the i386 20120211 Ubuntu image and on my first try I booted to the live desktop first, then selected install, and once I got to "preparing to install" I selected to DL updates and install 3rd party software. 

Shortly thereafter everything froze. Well, saying "everything froze" is inaccurate. X did not freeze, I could still move the mouse pointer and Alt + SysReq + K killed X, but the login screen never appeared.

I then repeated but this time chose "install" w/o first going to the live DE, and I left the DL updates and 3rd party software boxes unchecked. Then the installation completed OK.

Now I need to rinse & repeat a couple of times to see whether it's a matter of having booted to the live DE first, or if it had to do with selecting DL updates and/or 3rd party stuff :)

But that may take a while.

******************

OK I narrowed that issue down. There is no crash on my Intel test box if I choose install from the get-go rather than beginning from the live desktop.

ATM I'm not going to submit a bug report on that, rather I'll watch package updates and try again in a few days. I really doubt this is purely a "ubiquity" bug.

I'm much more inclined to think it has to do with graphics rendering, maybe gtk :confused:

With feature freeze coming on the 16th and UI freeze coming on the 23rd we have plenty of time until Beta 1 releases on March 1st ;)

Right now I'm going to give the non-pae mini.iso another spin :guitar:

---

### Post by arpanaut on 2012-02-11
Interesting observations, I'm in the habit of going directly to the live desktop then installing.
It didn't occur to me to try just the installer. My Bad..

Got my fresh install using the alt.iso, been a while since I had used that tool, kinda clunky but effective.
I'd mark this solved but it really isn't. Will continue testing the daily live to see if it gets fixed.
Like you say, we've got time before Beta-1 .

Thanks for the feedback.

---

### Post by kansasnoob on 2012-02-11
I wouldn't mark it solved. Lets wait and see what happens in the next few days :D

---

### Post by donniezazen on 2012-02-20
Ubiquity from Feb 19th is not working. After it crashes, it stops responding to double click. Bug reporting took me to this only report, if my memory serves well (All of this happened in Live CD and I did not take note of it).

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/841807](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/841807)

---

### Post by nm_geo on 2012-02-20
I just did a clean ubiquity install of current daily PP 12.04 i386 32bit pae on my old ThinkCenter MP55.  All went well and she is up to snuff Capitan..

---

### Post by sgage on 2012-02-20
I think the problem has something to do with the partitioning. I always use "something else", and after the partition display comes up, it crashes while I'm trying to set it up, bringing me to the live desktop.

If I fire up gparted from the live session, make sure the partitions are the way I want, and format them the way I want, the subsequent installation runs perfectly.

It's been doing this for weeks now.

---

### Post by nm_geo on 2012-02-20
> **sgage said:**
> I think the problem has something to do with the partitioning. I always use "something else", and after the partition display comes up, it crashes while I'm trying to set it up, bringing me to the live desktop.

If I fire up gparted from the live session, make sure the partitions are the way I want, and format them the way I want, the subsequent installation runs perfectly.

It's been doing this for weeks now.

I did take the do something else option. However, I had a previous partition built from a failed install and I 

reformat it and rewrote it to ext4 using the ubiquity partman.  So, I guess that would be closer to your 

example using Gparted.  It kinda surprised me that it worked as it seems I usually have to use the 

alternate to get a clean install.

---

### Post by donniezazen on 2012-02-20
> **sgage said:**
> I think the problem has something to do with the partitioning. I always use "something else", and after the partition display comes up, it crashes while I'm trying to set it up, bringing me to the live desktop.

If I fire up gparted from the live session, make sure the partitions are the way I want, and format them the way I want, the subsequent installation runs perfectly.

It's been doing this for weeks now.

I think you are right. I have seen that in previous releases. I am gonna give it a try later today.

---

### Post by donniezazen on 2012-02-21
> **donniezazen said:**
> I think you are right. I have seen that in previous releases. I am gonna give it a try later today.

Update:- As long as I wipe my hard drive before running Ubiquity, it runs just fine.

---


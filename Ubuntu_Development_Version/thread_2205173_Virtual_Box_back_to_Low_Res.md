---
title: "Virtual Box back to Low Res"
date: 2014-02-12
forum: Ubuntu Development Version
---

### Post by makitso on 2014-02-12
Todays update borked Virtualbox again (updates to virtualbox-guest-dkms may have been the problem).  Were again at low res

---

### Post by ajgreeny on 2014-02-12
Same here on my Xubuntu 14.04 VM running on the Oracle version of VBox with the VBoxguest additions and the virtualbox-guest-dkms, utils, etc etc packages installed in the guest.

I have even tried a new zsynced daily iso image and that boots fine but utterly refuses to go to a full desktop being stuck at 680x440 or something similar.  I'm not on that machine at the moment so can not check those resolution figures but it is just about unusable.

Great pity, as things had been running brilliantly till yesterday.

---

### Post by pnarciso on 2014-02-13
Same problem here. Even vbox addition iso driver won't work.

---

### Post by Elfy on 2014-02-15
I've managed to get it working in a new install of daily and updated.

```
wget https://www.virtualbox.org/download/testcase/VBoxGuestAdditions_4.3.7-92075.iso
sudo mv VBoxGuestAdditions_4.3.7-92075.iso /usr/share/virtualbox/VBoxGuestAdditions.iso
```

then install guest additions as normal

Not sure how long it will last.

[https://www.virtualbox.org/ticket/12623](https://www.virtualbox.org/ticket/12623)

thanks unit193

---

### Post by ajgreeny on 2014-02-16
OK.
That works for the moment at least with a daily .iso from this morning (Feb 16).  Thanks for the info Elfy !

Incidentally I also have WinXP in a VM in order to update my satnav, and that is also working fine with the 4.3.7 guest additions, though when I updated from the previous version XP gave me many warnings that it could cause problems.  I didn't worry about that as I had an XP snapshot from 2 days ago ready if it was a problem, but it is good.

---

### Post by ajgreeny on 2014-02-22
Now back to a similar problem, unfortunately.

I have the 64 bit xubuntu trusty now installed Feb 19, using that day's daily .iso and although I am able to get a large screen it is impossible to get the correct resolution any more.

I have tried both versions of the VBoxGuestAdditions (4.3.6.and 4.3.7 as noted above in posts 4 & 5) but I can not get 1440x900 res.  Everything else is working fine in xubuntu except this problem, and WinXP is still working fine with the 4.3.7 additions.

---

### Post by ajgreeny on 2014-02-23
UPDATE:
I have managed to get the fullscreen running properly again on my 1440x900 monitor by manually writing an /etc/X11/xorg.conf file just to get the correct resolution with contents.
```
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes       "1440x900" "1024x768"
    EndSubSection
EndSection
```

I still have to use the 4.3.7 VBox GuestAdditions as shown above, as the standard version, 4.3.6, will not give me fullscreen or any other high resolution at all, just 640x480 or similar.

---

### Post by QIII on 2014-02-23
Seems to work for me.  I'd just not bothered for the last couple of weeks.

---

### Post by ajgreeny on 2014-02-24
I presume this is all something to do with new versions of xorg, (if they are new) or virtualbox-guest-dkms, as you suggested, not detecting my monitor properly, as it did work properly for a long time until a week ago when makitso first posted.

I am running on an Intel -i5-3570K cpu with only the on board graphics HD4000, and as I said, I could get a high resolution but just not the correct one.  It will be interesting to see what happens if any further xorg updates come along.

---

### Post by makitso on 2014-02-24
The problem was corrected mid-week.

---

### Post by ajgreeny on 2014-02-24
Which part of the problem?

I can not get fullscreen using the 4.3.6 guest-additions, with or without the virtualbox-guest-dkms package installed in the VM, but with the 4.3.7 guest-additions all is OK whether or not I have the virtualbox-guest-dkms installed, as long as I have that xorg.conf file to get the correct resolution.

PS:  The same situation occurs in all the *ubuntu 14.04 family that I have tried using the most up to date daily .iso images.

EDIT: I have only just noticed that when using the VBoxGuestAdditions 4.3.7 I can not get the bidirectional clipboard to work, nor shared folders in either direction.

---

### Post by Elfy on 2014-02-26
Update to vbox came through here today - better than it was

---

### Post by ajgreeny on 2014-02-26
> **Elfy said:**
> Update to vbox came through here today - better than it was

Whoo-hoo ! !

Great new version of VBox that has got everything working again properly; fullscreen,- tick; shared clipboard,- tick; shared folders,- tick.
I'm now back to proper testing again, though the Lubuntu Trusty i386 version I have as a VM needed build-essentials in order to build the guest additions.  Xubuntu Trusty 64 bit on the same VBox host (on myXubuntu 12.04 64bit) did not seem to need build-essentials, but I installed them just in case tey turn out to be needed later.

---


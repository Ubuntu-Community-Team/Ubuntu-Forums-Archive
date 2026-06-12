---
title: "Virtual Box OSE - Guest Additions Installation"
date: 2011-10-25
forum: Virtualisation
---

### Post by cryptotheslow on 2011-10-25
Hi,

Having a few problems getting guest additions installed and working here. Have tried following various tutorials / instructions scattered around but I'm not sure they are fully up to date.

Anyway the setup:

Host is running 10.04 LTS Desktop 32bit
Virtual Box OSE and Guest Additions installed from the repos
Guest is running 11.10 Desktop 32bit

The Guest Additions ISO shows up as mounted in the guest.

So the question is what order to do things in :confused:

In the guest an Additional Driver is available in jockey-gtk for VM virtualisation.

I have tried installing the additions only - the end of the install script complains about an unrecognised X server and additions don't seem to work.

I have tried "Activating" the Additional Driver first - which appears to go fine and shows as Active...... until I reboot the guest, then jockey-gtk shows it as Inactive again and trying to reactivate ends with errors.

So yeh....
What order to do things in?
Is that Additional Driver in the guest required?
Do the Guest Additions even work on 11.10 yet?

I've completely deleted and re-created the virtual box now and done a fresh install of 11.10 in it as I'm sure my thrashing around between drivers and guest addition install attempts had left a mess. So it's virgin territory again :)

Thanks
crypto :D

---

### Post by CharlesA on 2011-10-25
It could be because of the new DE that 11.10 uses. I'm not sure if the OSE version of VBox has the guest additions for it.

---

### Post by cryptotheslow on 2011-10-25
OK - I'll just not bother with them for now. I've not found anything that's not working in the VB as expected yet so maybe I don't even need them. It's only a scratch box for messing around testing stuff in, so hardly important.

Thanks :)

---

### Post by CharlesA on 2011-10-25
I found a couple threads about the guest additions and 11.10.

[http://ubuntuforums.org/showthread.php?t=1861291](http://ubuntuforums.org/showthread.php?t=1861291)

---

### Post by cryptotheslow on 2011-10-26
Thanks Charles. :)

Now I need to do some reading up on the differences between the Oracle and OSE versions (apart from the clearly open-source nature of the latter).

Just not enough hours in the day to get everything done at the moment so it can wait. Probably find I'm moving to the next LTS before I get round to it knowing me :D

---

### Post by CharlesA on 2011-10-26
As far as I know they are both open source. The only closed source package is the extension pack.

---

### Post by cryptotheslow on 2011-10-26
I definitely need to do some more reading then - as from what I've seen they look and behave identically, so I had presumed the difference just came down to the license. No doubt it will become clear once I get into it.

Thanks again :)

---


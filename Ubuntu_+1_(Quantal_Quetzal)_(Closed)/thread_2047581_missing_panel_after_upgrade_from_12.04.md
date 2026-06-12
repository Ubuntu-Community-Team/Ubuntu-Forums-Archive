---
title: "missing panel after upgrade from 12.04"
date: 2012-08-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by dwellna on 2012-08-25
Hi guys,

I'm having a laptop here from a friend who was doing a dist upgrade from 11.10 to 12.04 which somehow froze (he said so) so he aborted it. I managed to get the system fixed using a rescue system and tried to complete the upgrade by installing all updated packages using the update manager. Somehow the upgrade still was not complete after doing this. So the update manager told me, that I could try a partial upgrade which when started told me that I could not upgrade from my version. The other option was to upgrade to 12.10 which basically worked fine but after finishing this and rebooting, the panel is gone and when I manage to get a window opened (e.g. I opened a folder which is located on the desktop) I can only see the window content, I guess it is not drawn completely.

I'd rather try to fix this than to do a complete new installation. If anyone has some suggestions on what I can do/try I'd be very glad.

Thanks a lot!
David

---

### Post by Curtis6767 on 2012-08-25
Unfortunately, 12.10 is very buggy at the moment and because it's in Alpha 3 right now it shouldn't be used on one's main system. It hasn't worked for me in more than a week.

I would suggest you revert to 12.04 or 12.04.1, which has just come out.

If you continue to have problems installing 12.04 or 12.04.1, then you might want to post your issue on the 'Absolute Beginners' forum and you can probably get some help there.

---

### Post by meanpt on 2012-08-25
I second your problem, but with the daily builds from august 24 and 25  for both the 32 and 64 bit editions: nor the upper panel nor the launcher  are displayed or working, in live mode, not to mention the installer is  unable to format a partition ... this sucks ...

---

### Post by ronacc on 2012-08-25
12.10 is still in alpha , it is meant only for those willing and ready to accept breakage ranging from mildly irritating to very severe , right now it is very sever fo some hardware . please do not install or upgrade to 12.10 until it is released unless you are ready for problems .

---

### Post by kansasnoob on 2012-08-25
Yep, even the live installer is borked ATM:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1041277](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1041277)

---

### Post by dwellna on 2012-08-25
Alright, I see...
So, what would be the best procedure to revert to a previous version? Should I boot from the live cd and do an install into the same partition or could the resulting installation be corrupted that way? Would user specific data preserved that way? When I select to install next to the existing installation, it says that user settings will be kept and I saw that a seperate partition will be created.
Should I do that instead and delete the partition with the old system afterwards?

Thanks,
David

---

### Post by grahammechanical on 2012-08-25
It is a messy situation.

If you choose the Do Something Else option and direct the installer to install into the existing partition then there is a risk that user data will be over written but if you do not mark the partition to be formatted it should only over write the system files.

You have to select the partiton.

Click Change

Select a partiton format such as ext4 (make sure that it is the same partition format as at present - use the Disk utility)

Give the partition a mount point of /

Do NOT tick the Format box

The installer will find the already existing swap partition and use it.

But it is always best to backup any data that your friend does not want to lose. I think that this will work.

Any other suggestions, people?

Regards

---

### Post by dwellna on 2012-08-25
Hi, thanks for the suggestion.
I did exactly that, the system installed but I now got the problem, that wireless, touchpad is not working at all. I cannot mount my USB storage device and the display does not work with its native resolution. All this is working fine when I boot from the live cd from which I also installed. Basically with no network access, what can I do to at first enable my wireless adapter and then get the touchpad and the graphics driver fixed?

Thanks,
David

---

### Post by cariboo on 2012-08-25
You're going to have to give us some hardware details, before we can help you, did you install 12.4.1 or 12.10?

---

### Post by dwellna on 2012-08-26
Hi guys,

everything is working now. I figured out what was wrong with my hardware. The kernel modules did not load because there were no modules present for the kernel 3.5.0.12 which was previously installed with 12.10 but not present in 12.04.1. So the kernel was loaded but modules have been deleted during the installation. I simply removed the kernel files from /boot and manually changed the grub.cfg to load the shipped kernel from 12.04.1 instead and everything was working again.

Thanks again for your help!

David

---


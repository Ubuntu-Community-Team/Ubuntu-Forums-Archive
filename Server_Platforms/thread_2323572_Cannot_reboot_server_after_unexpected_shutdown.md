---
title: "Cannot reboot server after unexpected shutdown"
date: 2016-05-06
forum: Server Platforms
---

### Post by Mahmoud_Ghoneem on 2016-05-06
I`m running zimbra mail server on ubuntu server 14.04 on a vm on hyper-v with 3 processors and 4GB ram . and everything was going well until the server suddnly turned off . from that moment it doesnt boot any more


and it shown grub loader with 2 options 1st load ubuntu in normal mode and it shows only black screen without any response . and 2nd recovery mode which ends up with the folowing error


[http://i.imgur.com/rIxlBlF.jpg](http://i.imgur.com/rIxlBlF.jpg)


and i tried to boot from ubuntu desktop not server live cd and tried boo-repair with that result


[http://paste.ubuntu.com/16242384/](http://paste.ubuntu.com/16242384/)


but i cant boot to my system until now !!!


any help ??


Thanks in advance

---

### Post by QIII on 2016-05-06
Moved to Server Platforms.

Hopefully you will get better advice here.

---

### Post by darkod on 2016-05-06
Hmmm... Complicated... Did you install the OS or it is a VM created from your provider template?

I see you used EFI boot. IMHO things just get complicated with EFI and it is not needed (yet)... Linux is quite happy running on legacy boot. And much easier to fix.

Then, it looks like you have separate /boot partition (the /dev/sda2). And it is only 256MB. One thing I hate about the ubuntu server guided install with LVM is that it creates very small /boot partition. Then in the future you always have to be careful not to run out of disk space on /boot (and it happens a lot if you keep many kernels).

And as much respect as I have for the boot-repair tool, don't run it on production servers when you don't know what outcome it will have... I mean, how do you know it "understood" your setup correctly and the actions it will do are the correct ones and will not mess things up further???

In your place, I would try:
1. Boot with the desktop cd in live mode and activate the LVM.
```
sudo vgchange -ay
```

2. If that works out OK, try running fsck on both the root LV and the /boot partition (do not mount anything!!!):
```
sudo fsck /dev/sda2
sudo fsck /dev/mail-vg/root
```

According to the boot-repair output you VG is named mail-vg and the LV is named root, so if that is correct you can use /dev/mail-vg/root to specify the root LV once you have activated the LVM.

If the fsck shows no errors, that's good but you still have to reinstall the grub boot I think. Actually only the bootloader might have gotten messed up from the sudden shutdown. But I have no experience repairing EFI boot... If it was legacy, it's very easy.

In theory, the same applies, and you can try chroot-ing into your install from live mode and reinstall the grub-efi package. But you'll have to search more for an exact procedure about repairing the EFI boot.

---

### Post by Mahmoud_Ghoneem on 2016-05-07
thanx [COLOR=#DD4814][darkod]("http://ubuntuforums.org/member.php?u=946366") [/COLOR] for your reply

its worked for me but while fsck /dev/mail-vg/root its keeping ask me to remove mail server folders and files . and if i did the system will boot but also will useless !! . any idea ??

---

### Post by darkod on 2016-05-07
Hmmm.... fsck should not ask you to remove whole folders... Can you post the exact message?

---

### Post by Mahmoud_Ghoneem on 2016-05-07
done . but now i can`t login with error message 

unable to setup logging errno 30 read-only file system

---

### Post by darkod on 2016-05-07
I didn't understand what does that 'done' refer to. I just said to post the fsck message. Did you accept fsck to try and repair the root LV?

Can you try the recovery mode entry now in the grub menu? In the menu that shows up select "drop to root shell". Does that load the system?

---

### Post by Mahmoud_Ghoneem on 2016-05-07
yes load the system but not loading ZSC Server ! . and when i try to boot in normal mode it gaves me the above error message (read only filesystem )

---

### Post by Mahmoud_Ghoneem on 2016-05-07
Dear  [COLOR=#DD4814][darkod]("http://ubuntuforums.org/member.php?u=946366")    [/COLOR]

To be clear with you i mean that yes i can login with root from recovery mode . and also from normal boot but when i`m trying to login with root after normal boot it doesn't login with root and ends with error ( filesystem read only )

---

### Post by darkod on 2016-05-07
But did you do any fsck repair on the root LV or you left it like that?

---

### Post by Mahmoud_Ghoneem on 2016-05-07
yes off course thats why the system boots again . thanx again

---

### Post by Mahmoud_Ghoneem on 2016-05-07
yes off course , thats why the system reboots again . thanx sir

---

### Post by darkod on 2016-05-07
But it looks like the repair was not 100% successful. The system boots in read-only mode, which means it still finds some errors.

Try this:
1. Boot again in live mode, activate the LVM as before, and run fsck on the root LV again. Does that report more errors?

2. After that try booting and see if it boots in read-only again. If it does, try:
- press CTRL-ALT-F1 and login in that terminal
- try running
```
sudo mount -o remount,rw /
```
- press CTRL-ALT-F7 and login in there

This time the system should be read-write. But if you try rebooting it it might boot in read-only again. Check that...

---

### Post by Mahmoud_Ghoneem on 2016-05-08
i`v booted from live cd again and now there are no more errors .

but when i`m booting in normal mode its the same problem and also after trying to run the mount command from recovery mode its also the same error (read only file system )

please could you help me to fix this error via team viewer if u can ??? it just a virtual machine and you can easly access it via remote desk top or team viewer

---

### Post by darkod on 2016-05-08
Unfortunately I am also not sure what is wrong... In normal mode can you log in (even if the OS is read only)?

Then take a look in /var/log/dmesg to see if there are any errors reported and clues why it is mounting as read only... Also take a look in /var/log/syslog.

You might find some clues... If you find any post them here and maybe someone will have an idea. Also do a search on google for the specific errors reported to see what you can find...

Usually a sudden shutdown should not create so many issues but it seems like you had some bad luck with this... It might not even be from ubuntu itself, it might be the hyper-v and how it presents the storage (disks) to ubuntu. You should double check if all is good with the hyper-v after the sudden shutdown.

---


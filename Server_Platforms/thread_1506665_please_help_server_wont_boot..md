---
title: "please help server wont boot."
date: 2010-06-10
forum: Server Platforms
---

### Post by terry_gardener on 2010-06-10
i have recently setup server and i shut it down and moved it into the room i am going to keep turned it on and when i turned it on i couldn't connect to it.

i think it might have been because no one was logged on.

so i turned it off by the power button since i hadn't connected a keyboard and monitor and moved it in the other room where i can connect monitor and keyboard i could hopefully setup auto login.

but when it boots it goes to a screen with: 
fsck from util-linux-ng 2.17.2 
/dev/sda1: clean, 59748/14934016 files, 1215549/59729408 blocks 

and nothing seems to be happening. 

how do it get back to the logon screen.

---

### Post by BoneKracker on 2010-06-10
reboot

---

### Post by terry_gardener on 2010-06-10
tried reboot and i get the same screen

---

### Post by BoneKracker on 2010-06-10
Maybe you powered off your machine without shutting down?

You probably ought to boot from a CD and run fsck on your key partitions.

---

### Post by terry_gardener on 2010-06-10
i loaded the rescue system option from the ubuntu server cd and then ran fsck and get result 0.1% non-contiguous but it wont repair the issue.

how do i repair the issue.

---

### Post by terry_gardener on 2010-06-10
thank you bonekracker for the advice. 

i have decided and currently in the process of just reinstalling it and then start again.

thanks anyway

---

### Post by BoneKracker on 2010-06-10
Good luck with your reinstall.

---

### Post by terry_gardener on 2010-06-11
when i reinstalled ubuntu server and setup using the like above again and at the end i rebooted and got the same problem. 
i opened fstab and removed the entry i placed in there for the external usb hdd and then rebooted and it was fixed.
so the problem was the fstab. 

later today i am going to install usbmount to try and automount the usb drive on boot.

---

### Post by BoneKracker on 2010-06-11
I can't imagine how a flawed entry for a non-essential filesystem could prevent the system from booting. (I assume it's a non-essential filesystem.)

You should be able to automount it at boot with an fstab entry.  Does Ubuntu server have udev installed?

Also, usbmount appears to be an un-maintained package.

---

### Post by terry_gardener on 2010-06-11
well it didn't boot when i had the entry in fstab but when i removed it it worked. 

checked the changelog for usbmount and it was last updated in February this year where on the usbmount website it stopped in 2007. 

in the link below it shows the maintainer of ubuntu developers 

[http://packages.ubuntu.com/lucid/usbmount]("http://packages.ubuntu.com/lucid/usbmount")

---

### Post by BoneKracker on 2010-06-11
> **terry_gardener said:**
> well it didn't boot when i had the entry in fstab but when i removed it it worked. 

checked the changelog for usbmount and it was last updated in February this year where on the usbmount website it stopped in 2007. 

in the link below it shows the maintainer of ubuntu developers 

[http://packages.ubuntu.com/lucid/usbmount]("http://packages.ubuntu.com/lucid/usbmount")

That just means somebody from Ubuntu put it in the Ubuntu repository. Look at the top of this page:
[http://usbmount.alioth.debian.org/](http://usbmount.alioth.debian.org/)

Do you still have a copy of your broken fstab file?

---

### Post by terry_gardener on 2010-06-11
> **BoneKracker said:**
> Do you still have a copy of your broken fstab file?

i know what the line was that i added to it.

UUID=71610a3d-c7c2-4d93-b4fc-f54b288e3a31 /media/usb ext3 defaults 0 0

---

### Post by BoneKracker on 2010-06-11
> **terry_gardener said:**
> i know what the line was that i added to it.

UUID=71610a3d-c7c2-4d93-b4fc-f54b288e3a31 /media/usb ext3 defaults 0 0

That looks fine to me.  I don't see how that could have been the problem.

What happens when you try to mount it manually using those parameters?
```
sudo mount -t ext3 -U 71610a3d-c7c2-4d93-b4fc-f54b288e3a31 /media/usb
```

---

### Post by terry_gardener on 2010-06-11
just a question then, when i booted the system both times when i got the error the fstab had this entry but the usb hdd wasn't plugged in would this make any difference

---

### Post by terry_gardener on 2010-06-11
didn't try the parameters you have stated 
sudo mount -t ext3 -U 71610a3d-c7c2-4d93-b4fc-f54b288e3a31 /media/usb

what i used to test it manually mounting.

sudo mount /dev/sdb1 /media/usb 

which worked fine

---

### Post by BoneKracker on 2010-06-11
> **terry_gardener said:**
> didn't try the parameters you have stated 
sudo mount -t ext3 -U 71610a3d-c7c2-4d93-b4fc-f54b288e3a31 /media/usb

what i used to test it manually mounting.

sudo mount /dev/sdb1 /media/usb 

which worked fine

Try it:
```
sudo mount -t ext3 -U 71610a3d-c7c2-4d93-b4fc-f54b288e3a31 /media/usb
```

Also, what's the output of
```
sudo blkid
```

---

### Post by terry_gardener on 2010-06-11
i removed usbmount and reboot then plugged in the drive and did the command 

sudo mount -t ext3 -U 71610a3d-c7c2-4d93-b4fc-f54b288e3a31 /media/usb

and it worked ok 

also i have attached the blkid file

---

### Post by BoneKracker on 2010-06-11
> **terry_gardener said:**
> i removed usbmount and reboot then plugged in the drive and did the command 

sudo mount -t ext3 -U 71610a3d-c7c2-4d93-b4fc-f54b288e3a31 /media/usb

and it worked ok 

also i have attached the blkid file

Well, if it worked for you manually, there is no reason it wouldn't work in the fstab file.  I can't explain the symptoms you are describing (it didn't work before, then you deleted it and it worked), but it should work fine, exactly as you described.

Depending on what's on that partition, you might want some other non-default mount options, though, for security (such as nodev,noexec) and/or performance (noatime).

I hesitate to tell you to try something that wasn't working before, but I bet if you create an entry in there it will work fine.

The only thing I can think of is that maybe you didn't have a mount point created for it in media (i.e. "/media/usb" didn't exist).  Also, the /media directory is really for dynamically-mounted stuff under the management of auto-mounters (e.g. pmount, etc.)  It is my practice (and I believe the correct thing to do) to put manually-created, admin-managed mount points in /mnt.

```
sudo mkdir -m 0700 /mnt/usb
```

And the fstab entry would be something like:

```
UUID=71610a3d-c7c2-4d93-b4fc-f54b288e3a31     /mnt/usb     ext3     noatime,nosuid,nodev     0   0
```

Or you could do

sudo tune2fs -L external /dev/sdb1

and then it would be something like 

```
LABEL=external     /mnt/usb     ext3     noatime,nosuid,nodev     0   0
```

---

### Post by terry_gardener on 2010-06-11
i have now tested it again, i have re entered the entry in fstab as it was before using the defaults option (as i dont know what the other options do) and then rebooted and it worked. 

unplugged the usb hdd and then reboot again and get the original message.

so i plugged it in again and then rebooted and it works again.

so it works fine if the usb hdd is plugged in but if it isn't it wont boot.

---

### Post by BoneKracker on 2010-06-11
> **terry_gardener said:**
> just a question then, when i booted the system both times when i got the error the fstab had this entry but the usb hdd wasn't plugged in would this make any difference

Sorry, I didn't see this before.

Yes, that would make a difference, but it shouldn't prevent the server from booting (you would receive some kind of error message in your logs that it was unable to boot that partition).  That behavior could depend on how Ubuntu has things set up.  If you often boot the system without the drive present, then one option would be to use an entry like this
```

UUID=71610a3d-c7c2-4d93-b4fc-f54b288e3a31     /mnt/usb     ext3     noauto,noatime,nosuid,nodev     0   0
```

Then, (if you're not using udev or somethign else that hotplugs the device when you switch it on or plug it in) when you want to mount the drive later, you just issue the command:
```
sudo mount /mnt/usb
```

Or, if it's all files belonging to your user-level account anyway (in other words, root isn't needed for anything):

```
UUID=71610a3d-c7c2-4d93-b4fc-f54b288e3a31     /mnt/usb     ext3     user,noauto,noatime,nosuid,nodev     0   0
```

Then the command is just
```
mount /mnt/usb
```

If you want to be super-lazy about it, create a symlink at the root of the filesystem:
```
ln -s /usb /mnt/usb
```

Then the command just becomes
```
mount usb
```

---

### Post by BoneKracker on 2010-06-11
> **terry_gardener said:**
> i have now tested it again, i have re entered the entry in fstab as it was before using the defaults option (as i dont know what the other options do) and then rebooted and it worked. 

unplugged the usb hdd and then reboot again and get the original message.

so i plugged it in again and then rebooted and it works again.

so it works fine if the usb hdd is plugged in but if it isn't it wont boot.

I see.  I don't think it should be preventing it from booting.

Try the "nofail" option.

```
UID=71610a3d-c7c2-4d93-b4fc-f54b288e3a31     /mnt/usb     ext3     nofail     0   0
```

If not, try the errors=continue option
```
UID=71610a3d-c7c2-4d93-b4fc-f54b288e3a31     /mnt/usb     ext3     errors=continue     0   0
```

---

### Post by terry_gardener on 2010-06-11
bonekracker i would like to give you a big thank you for all your help on this topic.

the external usb hdd has all the music and video files for the xbmc media center and that is why i wanted a server so that my desktop doesn't have to be on so i could use the xbmc media center.

since i am not upgrading the media center until week after next i can leave the server turned off until it is needed for this propose which will mean the usb hdd will be plugged in constantly, which in turn solve the problem.

---

### Post by BoneKracker on 2010-06-11
> **terry_gardener said:**
> bonekracker i would like to give you a big thank you for all your help on this topic.

the external usb hdd has all the music and video files for the xbmc media center and that is why i wanted a server so that my desktop doesn't have to be on so i could use the xbmc media center.

since i am not upgrading the media center until week after next i can leave the server turned off until it is needed for this propose which will mean the usb hdd will be plugged in constantly, which in turn solve the problem.

You're welcome.

Explore the mount man page for descriptions of those options (noatime, nosuid, nodev, nofail, and errors=continue).

---


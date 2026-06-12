---
title: "Migrating Virtual Guest to Native Host"
date: 2010-11-05
forum: Virtualisation
---

### Post by Glencore on 2010-11-05
Hello,

I have been using ubuntu server and desktop on virtual box for a while now. I have come to enjoy it more than being in Windows. I would like to install it natively. I am wondering. is there any way I can take my virtual machine and apply what I have done there to a new ubuntu install?

I have a ntfs hard disk, will ubuntu resize that for me at install? 

Any good apps for backing up all my my firefox data and then applying that to my firefox in ubuntu?

I need to keep windows for some stuff for work, and for some games I like.

Any help much appreciated, thanks.

---

### Post by JustinR on 2010-11-05
> **Glencore said:**
> Hello,

I have been using ubuntu server and desktop on virtual box for a while now. I have come to enjoy it more than being in Windows. I would like to install it natively. I am wondering. is there any way I can take my virtual machine and apply what I have done there to a new ubuntu install?

I have a ntfs hard disk, will ubuntu resize that for me at install? 

Any good apps for backing up all my my firefox data and then applying that to my firefox in ubuntu?

I need to keep windows for some stuff for work, and for some games I like.

Any help much appreciated, thanks.

Hi,

This is a bit complicated but please bear with me - and if you have any questions - just ask! 

To migrate the VM to actual hardware:

Go to Applications > Accessories > Terminal
```

VBoxManage internalcommands converthd -srcformat VDI -dstformat RAW /PATHTOVDI /PATHTODESTINATIONFILE

```

When that is finished type:
```

dd if=/RAWDISKIMAGE of=/HARDDRIVE bs=4096 conv=notrunc,noerror

```
The RAWDISKIMAGE is the same path used in /PATHTODESTINATIONFILE above.
and /HARDDRIVE is the hard drive device (eg. /dev/sdX)

Both of these codes might take awhile.
**NOTE**: Whatever 'virtual hard drive' size your VDI VM disk is (eg. 100GB) the destination file will be 100GB! Make sure your have enough space!

[COLOR="Red"]**WARNING**[/COLOR] Make sure you use a spare HDD for the DD command - don't run the command your actual hard drive is (eg. /dev/sda or /dev/hda). _**Use a separate, blank drive!**_

And the easiest way to backup firefox stuff is to copy over the '.firefox' folder in your home directory to the home directory on the other Ubuntu installation.

If you want to put the Ubuntu VM on your actual hard drive with Windows on it - let me know! Its easier just to use a separate HDD though.

---


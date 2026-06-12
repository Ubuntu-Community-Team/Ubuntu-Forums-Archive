---
title: "Integrity Errors while running disk check for  Ubuntu 9.04 Server Edition"
date: 2009-06-12
forum: Server Platforms
---

### Post by SimMiles on 2009-06-12
Hello,
Well I am trying to install Ubuntu Server Edition. I know how to do this because I have done it with Ubuntu 8.10 on a diffrent computer. So I am no beginer at installing Ubuntu Server Edition. But I learned that before installing it would help with I check the cd for defects using the " Check CD for Defects" option on the CD (when booted). Well I keep getting integrity errors. and MD5 checksum. I have no clue what those mean so i figured I would post here. I download My ISO using a torrent file (located on Ubuntu website) and downloaded the ISO. I used a CD-RW and did a full erase using (Roxi Creator 8 ) then burned it using Roxi Creator 8. The computer I am trying to install the server edition on is kind of old (its a *Micron* PC) but reliable. I know the cd drive on it can take CD-RW and CD-R but can not take DVD. So when I got those integrity errors I figured I did not burn it correctly. So I went through the process again of erasing and then burning it. I even tried it at a slower speed. Still did not work. So I figured I got a bad ISO file so instead i downloaded from a mirror (not torrent) and I erased and burned the new ISO. Again I still get integrity errors and MD5 Checksum errors. Is there any suggestions or anything I could do to fix this? Is there a possibility of a Minimal CD for Ubuntu Server Edition 9.04. Well I hope someone can help. It will be much appreciated.

Thanks,
**Dillon Brown**

---

### Post by cdenley on 2009-06-12
> **SimMiles said:**
> Hello,
Well I am trying to install Ubuntu Server Edition. I know how to do this because I have done it with Ubuntu 8.10 on a diffrent computer. So I am no beginer at installing Ubuntu Server Edition. But I learned that before installing it would help with I check the cd for defects using the " Check CD for Defects" option on the CD (when booted). Well I keep getting integrity errors. and MD5 checksum. I have no clue what those mean so i figured I would post here. I download My ISO using a torrent file (located on Ubuntu website) and downloaded the ISO. I used a CD-RW and did a full erase using (Roxi Creator 8 ) then burned it using Roxi Creator 8. The computer I am trying to install the server edition on is kind of old (its a *Micron* PC) but reliable. I know the cd drive on it can take CD-RW and CD-R but can not take DVD. So when I got those integrity errors I figured I did not burn it correctly. So I went through the process again of erasing and then burning it. I even tried it at a slower speed. Still did not work. So I figured I got a bad ISO file so instead i downloaded from a mirror (not torrent) and I erased and burned the new ISO. Again I still get integrity errors and MD5 Checksum errors. Is there any suggestions or anything I could do to fix this? Is there a possibility of a Minimal CD for Ubuntu Server Edition 9.04. Well I hope someone can help. It will be much appreciated.

Thanks,
**Dillon Brown**

It could be a bad CD-RW, bad burner, bad CD-ROM drive, bad cable (IDE?), or bad memory. You should test the integrity of the CD on another computer, test the memory of your server, and verify the checksum of the ISO before you burn it.
```

md5sum ubuntu-9.04-server-amd64.iso

```
[http://releases.ubuntu.com/jaunty/MD5SUMS](http://releases.ubuntu.com/jaunty/MD5SUMS)

You can try the [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD"), but I would get to the bottom of this possible hardware error, first. You don't want random errors to corrupt your server.

---

### Post by Therion on 2009-06-12
Ditch the CD-Rewritable media and try a decent brand of straight CD-R instead.  Burn it slow, around 16x or a little slower.

CD-RW's are a known problem when it comes to burning .iso files.  Sometimes you can get away with it, but it's certainly not the ideal media for this particular use.

---

### Post by SimMiles on 2009-06-12
Well Those are some great suggestions. I will try each one. I will get back to you guys on each one too.
Also will the minimal cd do server edition installation?

Thanks,
**Dillon Brown**

---

### Post by cdenley on 2009-06-12
> **SimMiles said:**
> Also will the minimal cd do server edition installation?


I don't think it will install the server packages which are available with the server installer, unless it downloads them during install. It also probably won't install the server-optimized kernel. It is easy to add both of these configurations after install, though. Regardless of the installer you use, it is still the same OS with the same repos.

---


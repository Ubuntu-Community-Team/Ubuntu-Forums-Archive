---
title: "forgot my password and my keyboard doesn't work in recovery mode"
date: 2010-01-21
forum: Security
---

### Post by axima on 2010-01-21
so i forgot my new password. I followed the guide on how to recover the password but in recovery mode my keyboard doesn't work, i have tried a usb and a ps2 keyboard. what is going on? is there a fix? or is there another way to reset my password?

---

### Post by hemimaniac on 2010-01-21
is the keyboard enabled at boot? i know with my bios settings i can disable/enable the kb during bootup

---

### Post by axima on 2010-01-21
i have no idea, i don't care anymore, i did the reset via live cd, god that was a pain in the *** experience

did anyone have the same keyboard problem as me? (just boot into recovery mode and see if your arrow keys work)

---

### Post by FuturePilot on 2010-01-21
> **axima said:**
> i have no idea, i don't care anymore, i did the reset via live cd, god that was a pain in the *** experience

did anyone have the same keyboard problem as me? (just boot into recovery mode and see if your arrow keys work)

It's probably this bug. [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/456806]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/456806")

---

### Post by sisco311 on 2010-01-21
Boot a Live CD, mount your root (/) partition. 

[list=1]
[*]Option1:

Chroot in your installation
```
sudo chroot /media/mount-point
```

replace /media/mount-point with the actual mount point of the root partition.

Change your password:
```
passwd username
```

replace username with your login name.

Exit from the chroot and reboot:
```
exit
sudo reboot
```


[*]Option2
Edit the */media/mount-point*/etc/shadow file.

The line which stores your password should look like this:
```
username:**$6$SALTSALT$encrypted-password**:14630:0:99999:7:::
```

The fields are separated by a colon symbol. The second field(bold) is the encrypted password. Replace it with:
```
username:**$6$lqvrTifX$yf17LLw9hjijR3CyolTYyuolyxMM.ZRP2AUUfyQetlc0LjzKbrturTE/KJDOInmNOMVvoU4ER6U62Ry0.VGAi1**:14630:0:99999:7:::
```
Save the the file and reboot.

Use your login name and the password **password** to log in. Once you are logged in change your password to a secure one.

[/list]

Youtube video: [http://www.youtube.com/watch?v=AkENYv7kEhg&](http://www.youtube.com/watch?v=AkENYv7kEhg&)


EDIT: d'oh, too late. :)

---


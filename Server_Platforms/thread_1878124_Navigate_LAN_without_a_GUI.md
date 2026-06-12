---
title: "Navigate LAN without a GUI"
date: 2011-11-09
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2011-11-09
I have a file containing notes and comments used in setting up a server that would be copied to the desktop from another pc on the LAN.

The file would be opened and snippits from the file would be copied and pasted into the Terminal, conf files, etc.

So, if you setup a server without a GUI, how can you navigate a LAN and open up such a file?

TIA

---

### Post by nothingspecial on 2011-11-09
You would use ssh

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by ChrisRChamberlain on 2011-11-09
nothingspecial

Thanks for that - in that case a simpler alternative would be to have the file on a USB memory stick.

The notes, instructions, etc for setting up ssh are in this file, so it would be easier to setup ssh with the file open.

If so, how would you mount the USB memory stick and open the file?

---

### Post by nothingspecial on 2011-11-09
Assuming the usb stick is formatted fat first create a directory to mount it in eg 
```

sudo mkdir /mnt/stick
```

then identify your usb stick

```
sudo fdisk -l
```

it will be something like

```
/dev/sdb1
```

Then mount it like so
```

sudo mount -t vfat /dev/sd?? /mnt/stick
```

However assuming you have another computer with which to connect to the server, you can copy and paste from the client machine into a ssh session you have open on it.

I would choose to install a ssh server during the installation then you can connect to it as soon as it is installed and do everything from the client.

---

### Post by darkod on 2011-11-09
+1 for the SSH.

Doesn't matter what you are using your server for, and especially if it stuck somewhere without monitor, keyboard, etc, having SSH access is a must. It simplifies everything, now and in future.

---

### Post by ChrisRChamberlain on 2011-11-10
Thanks both for your input.

---


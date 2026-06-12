---
title: "executing mount command at startup/modprobe: FATAL: Error"
date: 2011-03-30
forum: Server Platforms
---

### Post by iconoclast hero on 2011-03-30
What I needed to get this project finished was how to execute 
```
mount -t smbfs -o noserverino,ro,password=windowsxppwd '//192.168.1.2/Shareaza/My Music' /var/lib/mpd/Music

```at start up so that I can use this Ubuntu 10.10 server box for the sole purpose of being an  mpd server next to my stereo and that if power is lost, it will return  to the state of having mpd up and running automatically.

For whatever reason, mpd only seems to work when I use those options for mounting my windows XP share.  I was able to get this to work via the rc.local file, but when I tried to do it with a /etc/fstab modification resulting in the error on boot resulting in hang:
```
modprobe: FATAL: Error inserting padlock_sha  (/lib/modules/2.6.35-22-generic-pae/kernel/driver/crypto/padlock-sha.ko): No such device
```To get around it, I booted from the 10.10 server CD and entered a rescue shell and commented out the line in /etc/fstab that I came up with using [this community guide]("https://help.ubuntu.com/community/MountWindowsSharesPermanently"):

```
//192.168.1.2/Shareaza/My\040Music /var/lib/mpd/Music smbfs iocharset=utf8,uid=1000 0 0
``` when I launch ```
sudo mount -a
```before rebooting, the share is mounted properly (although it is not working with mpd) but hangs on boot.  I did not include any credentials because it isn't necessary when I do the mount -a.

Any suggestions as to why I was unable to mount the share via the fstab at boot but I could using the mount -a?

Thanks

(I posted this because it explains how to mount an XP share at boot so it is compatible with mpd as well as to get around the fatal error.)

---

### Post by Morbius1 on 2011-03-30
Because fstab is being executed before your network is up. Mountall and upstart are the culprits I suspect.

---

### Post by iconoclast hero on 2011-03-30
If it makes any difference, I'm running via wireless WPA2-PSK AES configured by /etc/network/interfaces.

> **Morbius1 said:**
> Because fstab is being executed before your network is up. Mountall and upstart are the culprits I suspect.

---

### Post by Morbius1 on 2011-03-30
There is no fix or solution for this problem that I'm aware of - there are only workarounds.

You already found one using rc.local.

You could "automate" the "mount -a" by creating a script in /etc/network/if-up.d:
```
gksu gedit /etc/network/if-up.d/fstabmount
```Add the following:
```
#!/bin/sh
mount -a
```Make the file executable:
```
sudo chmod +x /etc/network/if-up.d/fstabmount
```Anything in if-up.d will execute only after the network is up.

There's probably a way to do this with your own upstart job but I haven't explored that.

---


---
title: "mount an external HD (with network connection not usb)"
date: 2008-08-16
forum: Server Platforms
---

### Post by pascali70 on 2008-08-16
Hi,

I have an external HD (connected via network, not usb).  
How can I mount this drive to my server (i can do it with the graphical interface from an ubuntu desktop, but I don't know how to do it from a server in text mode :-( )
I already tried mount smb://ip-adress /mountname but that doesn't seem to work.
Can somebody help me ?

thanks in advance,

Pascal.

---

### Post by MJN on 2008-08-16
Hi Pascal,

Assuming it does support SMB (it likely does) then firstly make sure you have smbfs installed then mount it with:

```
sudo mount -t smbfs -o username=<user>,password=<pass> //<device IP>/<sharename> <path to mount point>
```

...replacing the <variables> as appropriate. Note that the <path to mount point> must exist (e.g. /mnt/externalHD)

You can find out the necessary/available <sharenames> using **smbclient -L <device IP> -N**

Mathew

---

### Post by pascali70 on 2008-08-16
:) this works.  thank you very much for you're help.  And thank you also for the command to see the available shares.

---

### Post by MJN on 2008-08-16
You're welcome!

---

### Post by pascali70 on 2008-08-17
I think I did something wrong, it doesn't work anymore, I now get 'mount_data version 1919251317 is not supported'.  I must say i reinstalled the server but i did install smbclient on it.

---

### Post by pascali70 on 2008-08-17
sorry I'm too fast, I fixed it.  smbfs wasn't installed.

---


---
title: "Firewire!"
date: 2008-11-19
forum: Ubuntu Studio
---

### Post by Jdm111 on 2008-11-19
I get this message in kino
 WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394! 
please may you helpsudo chown name-of-your-user /dev/raw1394

---

### Post by mateuszbaranski on 2008-11-20
> **Jdm111 said:**
> I get this message in kino
 WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394! 
please may you helpsudo chown name-of-your-user /dev/raw1394

What version of buntu you use?
I saw it in 7.04. Since 7.10 it was working fine.
It simply means that kino doesn't have enough priviliges to use firewire device. Check if your user is in video group.
```
groups
```

If nothing else work you could start kino as a root:
```
sudo kino
```

---

### Post by Jdm111 on 2008-11-20
> **mateuszbaranski said:**
> What version of buntu you use?
I saw it in 7.04. Since 7.10 it was working fine.
It simply means that kino doesn't have enough priviliges to use firewire device. Check if your user is in video group.
```
groups
```

If nothing else work you could start kino as a root:
```
sudo kino
```

I have tried kino as root still nothing. I got video yesterday but i have rebooted today and nothing. I use Ubuntu 8.10

---

### Post by lisati on 2008-11-20
If memory serves correctly, the [Kino website]("http://www.kinodv.org/") has a tutorial video that you can download that includes a section on setting up FireWire.

---

### Post by Erlander on 2008-11-21
Have a look here:

[https://help.ubuntu.com/community/Firewire]("https://help.ubuntu.com/community/Firewire")

I used Method 2 under Other Methods at the bottom.

If you open Kino with sudo you will find that you don't own the files but that root does.

Rob

---


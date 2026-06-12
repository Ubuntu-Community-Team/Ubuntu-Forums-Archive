---
title: "Get your head round this one...."
date: 2006-06-05
forum: Server Platforms
---

### Post by Ted_Smith on 2006-06-05
Apologies if this is in the wrong forum - it seems the most fitting forum out of all of them for the query.

I understand that there is no registry in Linux like there is in Windows. A good thing I fancy. I've read that the 'equivalent' of it, if you can call it that, is the /etc. 

However, my query is a little bizarre. 

In Windows, when you plug in a USB device, Windows initiliases it and stores various bits of data like the device manufacturer in the registry. So, if you looked at the computer later on without the device plugged in there would be a trace of it's connection to that machine having existed once upon a time. 

However, without a registry in Linux, could the equivalent be done I wonder? When you first plug it in, I notice entries are made in the /var/log/messages file dumped and appended by sysklogd. But it does not dump some of the info I am after like the Serial Number of the device. The data I am after is in fact shown in System --> Administration --> Device Manager when the device is plugged in. But what I want to know is if it's retained anywhere once the device is removed.

Any ideas? 

Cheers

Ted

---

### Post by LordHunter317 on 2006-06-05
GNOME may hide some pieces in gconf (which is a registry-equivalent for GNOME applications) but that's certainly not system-wide or guaranteed.

As far as I know, HAL ultimately persists the data in the form of udev rules in /etc/udev/rules.d.  But I could easily be mistaken.  This data isn't necessarily meant to be persisted (at least all of it), most of it is read from the kernel via /sys when the device is attached.

---

### Post by Ted_Smith on 2006-07-05
Thanks LordHunter

I've done some additional research since. Interestingly, I notice that when you look in Device Manager, there's an entry that looks something like this : 

```

block.storage_device     strlst   /org/freedesktop/Hal/devices/storage_model_someBits&Pieces



```

The /org/frede.... bit looks like a path entry to something. But there is no /org/freedesktop... path on the filesystem. 

Also, when the device is plugged in, an entry is made in dev/disk/by-uuid. For example 1234_56AA. The entry itself looks like an actual file that is subsequently automatically deleted when the device is unmounted. I'm yet to do an undelete test but that's an interesting lead. 

Any help with the /org would be most useful.

Ted

---

### Post by Ted_Smith on 2006-07-06
The entries I made reference to above are only found in file system unallocated  space. I did a search after forensically imaging the disk drive and found several entries like the one above, but all of it was in unallocated space. It isn't recorded in any actual live files. 

I'd love to understand what the entries actually are. Are they output from a kernal process? From a technical point of view, what do those values represent and where are they read from and how? What does 'block.storage_device' mean or relate to?   What does 'strlst' relate to?

---

### Post by mzembe on 2006-07-07
Maybe you were looking in /proc ...

---


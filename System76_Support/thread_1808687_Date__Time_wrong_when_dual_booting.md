---
title: "Date / Time wrong when dual booting"
date: 2011-07-20
forum: System76 Support
---

### Post by holdorph on 2011-07-20
I am dual booting with Windows.  Normally when I install Ubuntu I am given an option on whether the hardware/bios clock is in UTC or in local time.  Using the Ubuntu that came shipped with the System76 machine I did not have that option to configure.

Does anyone know how I tell a system76 installed ubuntu environment that my hardware/bios clock is local time and NOT utc?  I'd prefer to change the Ubuntu side of things because it's how I do it in other dual-boot environments where I've installed both OS'es.

Thanks,


> Solution:  edit /etc/default/rcS and change the line UTC=yes to UTC=no.  Then reset the hardware clock.  Now the time/display should be fixed in both OSes.


---

### Post by jdb on 2011-07-20
> **holdorph said:**
> I am dual booting with Windows.  Normally when I install Ubuntu I am given an option on whether the hardware/bios clock is in UTC or in local time.  Using the Ubuntu that came shipped with the System76 machine I did not have that option to configure.

Does anyone know how I tell a system76 installed ubuntu environment that my hardware/bios clock is local time and NOT utc?  I'd prefer to change the Ubuntu side of things because it's how I do it in other dual-boot environments where I've installed both OS'es.

Thanks,

sudoedit /etc/default/rcS
or use your editor of preference, but you have to have root permissions
change UTC=yes to UTC=no

jdb

---

### Post by holdorph on 2011-07-20
I wish that had worked.  I found that suggestion googling yesterday.  Unfortunately it didn't help.  I'll confirm it again later today when I'm in a spot to boot both OSes, but I know I booted windows last night and then Linux this morning (after changing /etc/default/rcS yesterday) and my time is wrong still/again (depending on how you look at it).

---

### Post by jdb on 2011-07-20
> **holdorph said:**
> I wish that had worked.  I found that suggestion googling yesterday.  Unfortunately it didn't help.  I'll confirm it again later today when I'm in a spot to boot both OSes, but I know I booted windows last night and then Linux this morning (after changing /etc/default/rcS yesterday) and my time is wrong still/again (depending on how you look at it).

The desktop I dual-boot is running Ubuntu Lucid Lynx 10.04 & Windows 7.

I don't remember changing anything other than that one entry.
If I find anything else I changed I'll let you know.

jdb

---

### Post by holdorph on 2011-07-21
Ok, I booted to windows after making that change and it was 'wrong' in windows too.  I updated the clock and the time was right in windows and the next time I booted to Linux it was right in Linux too.  So, I guess that change does work, but it requires fixing your clock one time after making the change.

:popcorn:

---


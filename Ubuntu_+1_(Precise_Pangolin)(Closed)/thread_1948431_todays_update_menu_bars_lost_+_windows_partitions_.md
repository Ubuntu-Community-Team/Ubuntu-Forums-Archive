---
title: "todays update: menu bars lost + windows partitions gone?"
date: 2012-03-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by gja on 2012-03-28
Hi,

did an update of 12.04 this morning, reboot required:

- after reboot the menu bars did not show up.
had to go to console (ctrl-alt-Fx) and do "unity --reset". 
(lucky i have another pc at hand to look it up)

-now after a few reboots I cannot seem to find my windows 7 partitions.
Before the update they were there.
Any idea on how to get them back?

Thanks.

---

### Post by sgage on 2012-03-28
> **gja said:**
> Hi,

did an update of 12.04 this morning, reboot required:

- after reboot the menu bars did not show up.
had to go to console (ctrl-alt-Fx) and do "unity --reset". 
(lucky i have another pc at hand to look it up)

-now after a few reboots I cannot seem to find my windows 7 partitions.
Before the update they were there.
Any idea on how to get them back?

Thanks.

Are the Windows 7 partitions simply not being mounted at boot, or are the partitions really gone?

---

### Post by gja on 2012-03-28
they don't seem to be mounted.
/mnt is empty.

Or do I need to look somewhere else?

edit: to make it more clear: the Win7 installation is still working fine. 
the automount is only broken/gone.

---

### Post by sgage on 2012-03-28
> **gja said:**
> they don't seem to be mounted.
/mnt is empty.

Or do I need to look somewhere else?

By default they mount under /media when you first access them in nautilus, and there is no subdirectory there for the partition until you access it. I take it you're not even seeing them in nautilus at all?

The first thing I do after a fresh install is add a line to fstab so that my Windows partition mounts at boot time. Something like this will do it:

/dev/sda1  /media/windows  ntfs  errors=remount-ro  0  0

You'll have to manually make the /media/windows subdirectory. You can make that directory anywhere you like. And of course change sda1 to whatever partition your windows stuff is on.

---

### Post by gja on 2012-03-28
Until the update this morning, both Win7 partitions showed up automatically in Nautilus.
No need for manual fstab interference.
After the update my /media is empty after booting and no drives in Nautilus.

I guess I'll just wait for another update to see if they show up again.

Thanks.

---

### Post by VMC on 2012-03-28
> **gja said:**
> Until the update this morning, both Win7 partitions showed up automatically in Nautilus.
No need for manual fstab interference.
After the update my /media is empty after booting and no drives in Nautilus.

I guess I'll just wait for another update to see if they show up again.

Thanks.

I'm not sure there's a problem here. My "/media" also is empty, but under Devices in Nautilus all the partitions show up unmounted. I've never had them auto mount brfore.

---

### Post by sgage on 2012-03-28
Before I make the fstab entry, my Windows partitions would show up in nautilus, but with no subdirectory in /media until first accessed, at which point a directory is created. This directory then goes away when the partition is unmounted.

I use the fstab method because I have a few important symlinks into the Windows partition that I want to work before I touch the partition.

If the gja is not seeing the partitions in nautilus at all, that's something new to me. 

Have you tried manually mounting them? It could be that the startup item for automount or mounting assistant or whatever it's called got disabled?

---

### Post by gja on 2012-03-29
I see the partitions in /dev.
I can mount them manually.

However the Windows partitions did automount until yesterday's update.
They showed up as "133 GB drive" and "300 GB drive" in Nautilus.

Now Nautilus shows only the home folder by default.

---

### Post by sgage on 2012-03-29
> **gja said:**
> I see the partitions in /dev.
I can mount them manually.

That's a relief! I've never had nautilus fail to find them, though. I removed my fstab line, and nautilus found my windows partition and mounted it when I accessed it. I then disabled "mount helper" in startup apps, but it still worked fine.

I guess I'm out of ideas for the moment...   :confused:

---

### Post by gja on 2012-03-29
Just noticed something:

Open Firefox and when attaching files to my webmail, I get a file browser window that does show my Windows partitions!

And now they are mounted in /media too?

Mmmm. I'll reboot and see if it's fixed.

edit: reboot
- win partitions not mounted upon boot
- when opening file browser from web mail, they appear!

strange.

---


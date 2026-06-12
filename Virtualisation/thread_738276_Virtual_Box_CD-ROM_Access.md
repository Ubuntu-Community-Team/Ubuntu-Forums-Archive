---
title: "Virtual Box CD-ROM Access"
date: 2008-03-28
forum: Virtualisation
---

### Post by kneewax on 2008-03-28
Just getting to grips with Virtualbox and have figured most things out on my own or using previous posts. 

I am having trouble with though with CD-ROMs.  I have set up the VM to allow the guest OS access to the CDROM drive on my laptop.  This works however if I change CDs the guest OS does not recognise the new CD.  Infact it appears to continue to allow access to the removed disc.

I assume that it caches the disk image when the VM starts - is that right?  Is it possible to get the guest OS (in this case Win XP Pro) to use the Ubuntu mounted  CDROM drive as if it were a native install?

cheers

Kneewax

---

### Post by keplerspeed on 2008-07-24
i have mounted my cd drive, but I get an error in my host OS, windows XP. when i try to open the cd, it says "windows cannot read from this disk. the disk might be corrupted or it could be using a format that is not compatible with windows"

my cdrom drive is mounted as /dev/scd0.

Thanks guys..

---

### Post by keplerspeed on 2008-07-24
ah interesting... ive tried a few different cd's, some work, some dont. the drive cd for my hplaser printer works fine but music cd is no good. ok confirmed, all cd's work appart from music... i can live with that. kneewax, thats weird, when I take eject a cd it can no longer be read.

---


---
title: "LTSP install package"
date: 2008-10-29
forum: Server Platforms
---

### Post by jv13613 on 2008-10-29
Hi,
  I was wondering if I set up a ltsp server and had 2 clients and 2 accounts account1 and account2. If I install a package on account1 then I logout. If I login as account2 will that package still be there. I don't want it to be. And how could I install a package on all the accounts if I wanted to?:confused:

---

### Post by lykwydchykyn on 2008-10-29
With a standard LTSP setup, your clients are working with desktops on the server itself.  So if you install a package, it's there for all clients by default.

If you want to limit who can run a program, you could remove the shortcuts from account2's menu.  If the user is advanced enough to get around that, you can simply create a group and set the file permissions on the executable so that only group members can run the program.

If you need me to, I can elaborate on that.

---

### Post by jv13613 on 2008-10-29
Thanks
 would it be possible to have a seperate file system for each user, or seperate root?

---

### Post by lykwydchykyn on 2008-10-29
I've never tried to do anything like that.  How much power do your clients have, maybe you should look into doing client-side apps instead of having them log back into the server.

---

### Post by yldouright on 2008-10-29
This is an excellent topic. I have an old dual P3-500 with 1GB a Radeon (R100) GPU and a fast U2 array that I wanted to enroll as a home LTSP. Will this box be sufficient to serve three workstations? One of the boxes is a PPC 7100/80 running Yellow Dog Pomona. How would that Mac have to be setup?

---

### Post by lykwydchykyn on 2008-10-29
> **yldouright said:**
> This is an excellent topic. I have an old dual P3-500 with 1GB a Radeon (R100) GPU and a fast U2 array that I wanted to enroll as a home LTSP. Will this box be sufficient to serve three workstations? One of the boxes is a PPC 7100/80 running Yellow Dog Pomona. How would that Mac have to be setup?

That depends entirely on what you expect the clients to be able to do.  You probably want to start your own thread on that question, though.

---

### Post by jv13613 on 2008-10-29
does each user have its own home dictionary? can u install a package in the home dictionary?

---

### Post by yldouright on 2008-10-30
lykwydchykyn
Sorry if this is a threadjack but since you asked, I only need Firefox and OpenOffice served. The Mac has a 4GB drive and the other PC boxes have modern bios later than PC98 and all the boxes have Video boards with at least 4MB of VRAM.

---

### Post by lykwydchykyn on 2008-10-30
> **jv13613 said:**
> does each user have its own home dictionary? can u install a package in the home dictionary?

Home dictionary?

---

### Post by jv13613 on 2008-10-30
Sorry I didn't know how ltsp users work. Now I know. But what is the maximum # users on a machine?

---

### Post by lykwydchykyn on 2008-10-30
Have a read through this:
[http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/ltsp-theory.html](http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/ltsp-theory.html)

There is no hard limit on users, it just comes down to what your hardware can handle.

---

### Post by yldouright on 2008-10-30
lykwydchykyn
Thanks for the link. Very informative. According to the text, I should be able to serve twice as many as I planned. One question reading that tome did not answer was the boot process for a NuBus Mac floppy which lacks the bios calls necessary to call the BootP routines. Will loading the initrd.gz from a local hard drive be a better solution?

---


---
title: "vbox freezes on &quot;grub is loading.&quot;"
date: 2010-01-16
forum: Virtualisation
---

### Post by tuvu on 2010-01-16
I'm using vbox 3.1.2 on windows 7 64-bit. My guest OS is ubuntu 9.0.4. Everything is working fine until this morning.

I didnt turn off the guest OS last night and when I woke up, vbox hanged. I had to force power off the guest OS then, and tried to restart it. Since then, vbox always freezes on "grub is loading" screen. I restarted windows several times but the problem is there. I believe the guest OS is damaged somehow but I have no idea how to fix it.

My main concern is how to access to and save the data I have on the guest OS. I have the .dvi image file (the current state which is damaged).

I was wondering if there is anyway I can access to the data stored in .dvi file, or how I can fix the damaged guest OS?

I'm so frustated now, my whole week data is on there. Any help is highly appreciated. Thanks.

---

### Post by fouadatmeh on 2010-01-16
Hello,
You can use the ubuntu live cd to boot in the guest and get your data back.
as for repair, you can try to run 
> sudo fsck /dev/sda1
where sda1 is your os partition...

---

### Post by tuvu on 2010-01-16
Thanks fouadatmeh, I tried that and it took so long to boot from the CD, which is kind of weird. Once it's booted, the virtual HDD was not there. After that, I believe the .vdi file is logically damaged on the host OS. Then I ran scandisk on windows and everything works like a charm now. :popcorn:

---

### Post by fouadatmeh on 2010-01-16
Great News :)

---


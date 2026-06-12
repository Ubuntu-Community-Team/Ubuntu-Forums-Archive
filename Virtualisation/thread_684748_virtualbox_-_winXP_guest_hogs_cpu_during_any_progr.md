---
title: "virtualbox - winXP guest hogs cpu during any program install"
date: 2008-02-01
forum: Virtualisation
---

### Post by 4ll4N on 2008-02-01
Hi all,

I've searched Ubuntu and Vbox forums to no avail so here's my problem.

I have a guest install of WinXP sp2 running on virtualbox.
vdi file is on a mounted ntfs partition (secondary partition where I keep my files). 
1.70Ghz intel centrino (not core 2 as it's an old vaio vgn-a197vp)
2gb of RAM (1gb for guest OS + 90mb video ram)

Virtual OS boots up within 10secs but whenever I try to install any program, cpu is used 100% and install takes FOREVER.

I realize my cpu is rather slow by today's standards, still it shouldn't be THAT bad!

Any help very welcome! Thanks.


EDIT
It is just plain slow...
I tried the tickless kernel thing. Didn't do a thing.
Tried running as standard pc instead of acpi, still no difference. I'm totally stumped.

---

### Post by kyphi on 2008-02-01
Why is your vdi file on an ntfs partition?  It should be in your Home folder under /.VirtualBox/VDI.

Your processor should be fine for the task.  1GB for base memory is a bit too much - mine is running fine on 371MB with 8MB for video.

Your host system needs some RAM too and I think that you have throttled it by giving too much RAM to your guest system.

Try an adjustment to guest RAM and Video and see if that helps.

---

### Post by 4ll4N on 2008-02-03
Hi. thanks for you reply.

I put it on the ntfs partition because I don't have much space left on my root partition.
The laptop I'm using had WinXP on it before I moved over to Ubuntu and I kept it there because I need to use CS3 now and then. I was planning to do that through VirtualBox and then get rid of the dual boot altogether later.

I've tried lowering the amount of RAM but no improvement. CPU use is 100% when there is any type of activity in WinXP

---

### Post by kyphi on 2008-02-03
Like you, I use my XP installation in VirtualBox to run a graphics manipulation programme - PhotoImpact.

My CPU usage is quite low.

It is most likely that high CPU activity and slowness in operation are caused by having the vdi file on another partition.

To give your Ubuntu installation a bit more room, the only remedy I can suggest is to resize your partitions and put the vdi file where it belongs in your home folder..

Before repartitioning, don't forget to defrag your XP installation.

---

### Post by 4ll4N on 2008-02-03
I'll give that a go. Thanks :)

---

### Post by 4ll4N on 2008-02-10
That solved it! Thanks.

---


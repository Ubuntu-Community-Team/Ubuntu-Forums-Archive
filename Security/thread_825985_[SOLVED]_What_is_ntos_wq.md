---
title: "[SOLVED] What is ntos_wq?"
date: 2008-06-11
forum: Security
---

### Post by wmdiem on 2008-06-11
I'm very new to Linux, so I'm sorry if this is a trivial question, but does anyone know what the process ntos_wq is? I just installed Crunch Bang linux (ubuntu + openbox), and i've noticed that a process called ntos_wq is always near the top of the highest CPU use processes (sometimes going up to 25% of my 1.7gHz processor). 

It is being shown as running as root, using 0 memory. 

When I googled it all i found was that there was a virus called ntos.exe (i have no idea if the two are related, but it's all that came up). 

I am just wondering what this thing is and what it does. 

Thanks for any help.

---

### Post by Private_Ops on 2008-06-11
I wouldn't think its ntos.exe since exe files cannot run natively under linux.

Other wise I'd say its a system process.... though I don't appear to have it running on my system but, then again I'm running gnome not openbox.

Maybe someone else a little more experienced can ping in on this. (sorry if this is no help)

:::EDIT:::

Appearently it's a process that is involved with Ndiswrapper. Do you have anything setup with ndiswrapper?

---

### Post by wmdiem on 2008-06-11
Yup, I used ndiswrapper to use the XP driver for my wifi card. 
Thanks.

---

### Post by Private_Ops on 2008-06-11
> **wmdiem said:**
> Yup, I used ndiswrapper to use the XP driver for my wifi card. 
Thanks.

I'd say that's what it is then.

---

### Post by twothird on 2008-06-12
well, i uninstalled ndiswrapper and removed all three ndiswrapper packages, but the problem with ntos_wq persists.

what happens is, when i start downloading anything, ntos_wq activates and eats up 100% of my CPU
obviously, this happens only when I use my wireless connection.

i see many people have the same problem. I guess changing the driver should help.. i'll give that a try

____

alrite, had some problems changing the driver, as im a noob with linux, but it seems that kernels 2.6.21 and up can use compat wireless drivers. which are just awesome.
anyway, it wanted to install B43 over my the one that I should use - iwl3945. managed to get it right with modprobe.

BUT the thing is, even though it all seems to be right, and i don't get the ntos_wq process eating up all my CPU, it all still DOES SLOW DOWN when I start downloading anything. That was why I started considering this a problem in the first place.
it only happens when I use wifi, and I didn't notice it happening before (maybe i just didn't use it enough)

there was something weird though. I had kdesu running, and when I started downloading something, kdesu went up to 100% cpu usage. i killed it, but it didn't help. it was all still running slow. again, this only happens when i use a wifi connection

---


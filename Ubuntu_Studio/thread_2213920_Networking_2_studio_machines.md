---
title: "Networking 2 studio machines"
date: 2014-03-29
forum: Ubuntu Studio
---

### Post by BrianSwatton on 2014-03-29
I've been using Ubuntu Studio for some years now.  I've just installed it on another machine too, I was hoping to be able to get them accessing each others drives over the network.  All I can see in networks is the XP machine that's also on though.

Is what I'm trying to do possible with Studio (12.04)?   Perhaps someone could point me at some info if so? 

I didn't want to install the general ubuntu 12.04 on the latest install because I wanted to stick with xfce instead of unity, which I really disliked a lot.  Maybe I have to to get network functionality?   The 2nd machine doesn't really need low latency, but I was hoping to use the same GUI.

I've had a bit of terminal experience, but not a huge amount.

Thanks for reading.

---

### Post by jejeman on 2014-03-29
First define exactly what you want to achive. e.g. share folders etc.
Than choose your method: Samba, NFS, SSH.

---

### Post by SeijiSensei on 2014-03-29
For sharing that works with both Linux and Windows, you're probably best off using [Samba]("https://help.ubuntu.com/community/Samba") on each of the Ubuntu machines.  With Samba, your XP machine will be able to see the Ubuntu machines' drives as well.

---

### Post by BrianSwatton on 2014-03-29
Thanks, both.

I'm having a play with Samba now.  I had thought I could get away with only installing Samba on the machine I want to share from, but it seems not.  It shows in the Network page, but the workgroup name is wrong and it fails to retrieve the share list.  More playing to do.

---

### Post by BrianSwatton on 2014-03-31
Not sure what was going on with Samba, but it began working properly after more reboots. 

Networking nicely now thanks.

---


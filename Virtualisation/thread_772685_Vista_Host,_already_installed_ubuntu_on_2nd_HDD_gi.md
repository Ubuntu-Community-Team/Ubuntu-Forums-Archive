---
title: "Vista Host, already installed ubuntu on 2nd HDD give grub error 21 with virtual box"
date: 2008-04-28
forum: Virtualisation
---

### Post by slater22 on 2008-04-28
I am currently on my vista partition and I would like to see if anyone can help me with my problem.  I have 2 separate hard drives.  One has Vista Ultimate, one has ubuntu.  I would like to make Vista the host and ubuntu the guest.  I made an image of the physical drive, but when I run virtualbox (as an administrator) IT shows up with Grub loading... Error 21.  I have read around on what the error is, but I was wondering if anyone knew how to fix this?

Thanks.

---

### Post by samexner on 2008-04-28
Boot into your VirtualBox VM with the ubuntu livecd, and run these commands:
```
    sudo grub

    > root (hd0,0)

    > setup (hd0)

    > exit

```

Your boot menu should be back after doing this.

---

### Post by slater22 on 2008-04-28
Thank you for the reply.  When I do this is says Error 17: Cannot mount partition.  Is there a reason for this? have I created the image wrong or something like that? thanks for the help.

---

### Post by samexner on 2008-04-28
> **slater22 said:**
> Thank you for the reply.  When I do this is says Error 17: Cannot mount partition.  Is there a reason for this? have I created the image wrong or something like that? thanks for the help.
When you boot into the LiveCD, can it find your ubuntu partition?

---

### Post by slater22 on 2008-04-28
That is the one thing it cannot do.  I am currently on my ubuntu partition trying to figure out a way to make this work properly, if possible.  Any tips on things to do here, I was pretty sure I set it up to be able to see my ubuntu partition but the LiveCD didn't see it.

---


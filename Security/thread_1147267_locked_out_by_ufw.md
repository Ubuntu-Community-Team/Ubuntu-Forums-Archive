---
title: "locked out by ufw"
date: 2009-05-03
forum: Security
---

### Post by oldgarol on 2009-05-03
Just installed ufw and enabled default deny then idiot I am I enabled ufw without making any allows, so of course I am now unable to get in....any help please. I am using Ubuntu 8.04 hardy Heron on a vps hosting (unmanaged)

---

### Post by bodhi.zazen on 2009-05-03
Probably nothing you can do except call your VPS hosting co and see if they can access the guest.

Depending on the platform and configuration you can VNC into the guest (KVM) or direct access from the command line (OpenVZ / Parallels).

Once you have access, disable ufw and you will have access.

---

### Post by iponeverything on 2009-05-03
On the bright side, it's a mistake you are only likely to make once.

---

### Post by oldgarol on 2009-05-03
Many thanks to iponeverything and bodhi.zazen for your replies. I did manage to get in through hosting control panel and disable ufw.

---


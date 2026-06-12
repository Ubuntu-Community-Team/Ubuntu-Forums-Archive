---
title: "VPS Ubuntu backup - SSH, How?"
date: 2014-03-11
forum: Virtualisation
---

### Post by dado023 on 2014-03-11
[COLOR=#283A5E][FONT=verdana]hi everyone,[/FONT][/COLOR]

[COLOR=#283A5E][FONT=verdana]i haev a small VPS, KVM, installed Ubuntu LTS 12.04 64bit[/FONT][/COLOR]
[COLOR=#283A5E][FONT=verdana]I have SSH using Putty.[/FONT][/COLOR]

[COLOR=#283A5E][FONT=verdana]Now, how do i do backup?[/FONT][/COLOR]

[COLOR=#283A5E][FONT=verdana]this is what comes out when i type [I]sudo lvdisplay

[/I][/FONT][/COLOR]--- Logical volume ---
  LV Name                /dev/mojvps/root
  VG Name                mojvps
  LV UUID                NtdyEr-3hqu-NznF-Fbun-1kbQ-2h2m-vVdxE0
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                10.82 GiB
  Current LE             2771
  Segments               3
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0

  --- Logical volume ---
  LV Name                /dev/mojvps/swap_1
  VG Name                mojvps
  LV UUID                kupJ5c-3Xfp-tGA9-s3Wm-K7qY-snr6-wHDYnq
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                956.00 MiB
  Current LE             239
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

[FONT=verdana, geneva, lucida, lucida grande, arial, helvetica, sans-serif][COLOR=#283a5e]So, how do i do this, because when i googled, i found all scenarios with additional extra drive for backup purpose, but i don't have that on VPS, so, how do i create backup of my system into one compressed file which i can download to my windows PC?[/COLOR][/FONT]

---

### Post by CharlesA on 2014-03-11
Do you have another Linux machine you can use to store the backups?

I run rsync over ssh all the time to backup my VPS.

---

### Post by dado023 on 2014-03-12
gosh, your post made me dizzy, everything is upside-down ](*,)

No, but i do have windows 7 on my own PC, can i "rsync" to it? and how?

---

### Post by CharlesA on 2014-03-12
I guess you could try using WinSCP and use their scripting functionality, but it won't be nearly as powerful as rsync.
[http://winscp.net/eng/docs/scripting](http://winscp.net/eng/docs/scripting)

There is also rsync for Windows, but I've never used it.
[https://www.itefix.no/i2/cwrsync](https://www.itefix.no/i2/cwrsync)

---

### Post by dado023 on 2014-03-12
thanks for this, i am pretty much clueless here, i will try winscp and see how it goes

---


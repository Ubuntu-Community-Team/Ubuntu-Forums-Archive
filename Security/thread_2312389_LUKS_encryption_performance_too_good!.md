---
title: "LUKS encryption performance too good?!"
date: 2016-02-04
forum: Security
---

### Post by DB4711 on 2016-02-04
Hello,

I just tried LUKS out. I encrypted in 15.10 with a right click in file explorer my USB 3 3,5" 3TB HDD. Then I made a performance test with and w/o LUKS. I noticed that there's nearly no difference in performance. I can't believe it. With encryption 180/190 Mbit/sec without 160 Mbit/sec.

In the past I used many different encryptions and had always about 50 - 80 % performance loss.

I read that Ubuntu uses AES-256 to encrypt the disk volume. For security reason it should be OK.

My Hardware: notebook ist good, old, but good. There's a SSD, an i7-2630QM and a GT 550m.

Are your performance losses also minimal like this?

---

### Post by sudodus on 2016-02-04
If you want encryption, I suggest that you install Ubuntu or an Ubuntu flavour (Kubuntu, ... Xubuntu) with 'encrypted disk' alias 'LVM with encryption'.

See this link (yes, I know it is made for testing, but it works well as an instruction for a regular installation too)

But you should install versions 14.04.1 LTS, 14.04.2, 14.04.3 or 15.10, while Xenial Xerus is still developed (to become 16.04 LTS).

[Install (entire disk with lvm and encryption) in Ubuntu GNOME Desktop amd64 in Xenial Daily](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/111723/testcases/1451/results)

> 
...
6. Check 'Encrypt the new Ubuntu Installation for security' and 'Use LVM with the new Ubuntu Installation'
    'Encrypt the new Ubuntu Installation for security' and 'Use LVM with the new Ubuntu Installation' is checked
...


---


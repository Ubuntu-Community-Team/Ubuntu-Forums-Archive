---
title: "Strange key in DB"
date: 2021-05-07
forum: Security
---

### Post by georgesgiralt on 2021-05-07
Hello 
On my very old laptop (Lenovo E540) I had to put a new mainboard in because the previous one has failed. 
Secure boot was enabled so at first boot of Ubuntu, a process ran to install the Canonical Secure Boot key. It failed and ran for hours using 100% of one thread. I installed the /var/lib/shim-signed/mok/MOK.der by hand (as I knew from a previous attempt *).
And all was fine. 
Today, wanting to document my work in my notes, I've found that I have a key in the DB which is somewhat strange. All I've got is :
```

# mokutil --db
[key 1]
  [SHA-256]
  14e62a4905e19189e7082898XXXXXXXXXX0a331XXXXXXXXXX2b0e818a827f436  (key edited obviously...)

[key 2]
........well known key from Redmond....

```
I do not know were this key comes from and if it was present before installing the Mobo or not. Bur I can't export it to a .der file in order to remove it nor manipulate it. 
So I've got a couple of questions : 
1) what is this key and were did it comes from ? 
2) is it safe to remove and if yes how ? 
Many many thanks in advance for your help and answer. 
Have a nice and bright day ! 
* : The Lenovo BIOS and ACPI is somewhat flawed on this machine.  I've a bunch of ACPI errors during boot (not solved by BIOS update nor Linux Kernel updates) and even Grub is unable to display it's menu if I use the unicode.pf2 font... So I'm not surprised that the automatic installation of the Canonical Secure Boot key is not working as it is on a lot of other machines I've worked with...

---


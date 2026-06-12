---
title: "Installation of lucid lynx hangs"
date: 2010-06-01
forum: Ubuntu Studio
---

### Post by shinjan on 2010-06-01
i have downloaded ubuntu studio 10.04 from torrent file available in ubuntu studio site.

1.Now I tried to install it directly from the iso as described [here]("https://help.ubuntu.com/community/Installation/FromWindows"). It showed an error 'Can't mount the cd-rom' that is it couldn't mount the iso automatically.

2.Creating startup disk on my Seagate external hard disk (NTFS) didn't work out as 'Make startup disk' was greyed out.

3.Then I tried to install the OS from a pen drive. It proceeds fine until it hangs at 45% scanning disks in setting up the partitioner. I have waited for about 15 mins, but nothing happened.

So how to solve these 3 issues?
Pls help

---

### Post by mango42 on 2010-06-01
Did you check that the .iso was okay, first?

Checked the md5sum against [http://cdimage.ubuntu.com/ubuntustudio/releases/10.04/release/MD5SUMS](http://cdimage.ubuntu.com/ubuntustudio/releases/10.04/release/MD5SUMS) after download?

I've never attempted to install from Windows so don't know the pitfalls. If you're comfortable with disk partitioning, you could carve some free space first and install UbuntuStudio straight from the DVD.

---

### Post by shinjan on 2010-06-01
I have created free space...
will it not work from pen drive?
and what about the 2nd issue mentioned above?
Btw how to check the md5?there are so many md5s in the md5sum.txt inside the iso....

---

### Post by lisati on 2010-06-01
1) Don't use the md5sums on the CD, use the one from the web site relevant to the ISO you downloaded.
2) How did you burn the CD? Did you remember to use the "Burn as disk image" (or equivalent) with your disk burning software?

---

### Post by shinjan on 2010-06-01
yes md5sum is checked...it's ok...
i didn't burn it in a cd. As i mentioned earlier I made a bootable pen drive out of the iso using startup disk creator available in ubuntu by default.

---

### Post by sgx on 2010-06-02
> **shinjan said:**
> I have created free space...
will it not work from pen drive?
and what about the 2nd issue mentioned above?
Btw how to check the md5?there are so many md5s in the md5sum.txt inside the iso....

Hi, use the simple command with the name of your .iso

md5sum linuxmint-9-gnome-cd-i386.iso

The sum must match the one from the download page. The size
of 2 downloads of the same file may be identical, and still
one might fail the checksum, and prevent a perfect install

Cheers

---

### Post by shinjan on 2010-06-02
I have checked the md5sum...they are matching...
now what should be my steps?

---


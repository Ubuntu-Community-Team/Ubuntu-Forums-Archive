---
title: "messed up my install."
date: 2012-03-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nutpants on 2012-03-02
Just installed 12.04 beta dual booting with windows 7 but I made an error some where but I have no idea how to fix it and only have my phone for net access.

Partitions
1 primary 50 GB windows 7
2 extended partition
2.1 logical 5GB /boot
2.2 lvm encrypted 99 GB /
2.3 150 GB ntfs logical
2.4 250GB ntfs logical
2.5 whatever was left ntfs logical

I manually set up the lvm correctly I think.

With way the install seems to have gone fine but when all was said and done

My computer just boots windows

Sooooo grub must be installed to  /boot. 
(I expected it to go to the MBR)
How can I boot into it?
I have a 12.04 alt install on USB
Windows 7 install disk and
Ubuntu 11.o4 install disk to work with.

And a phone to surf the web with and down load limited small stuff.

Thank you for any info.

---

### Post by Double.J on 2012-03-02
Hi there, if the install has all gone well as you say, and you've just installed grub in the wrong place, then all you need do is boot up the installer media and select the "try" live mode and repair grub from there. Two main ways of doing it - 

Firstly, the newer, downloadble tool recommended by Ubuntu - info [here]("https://help.ubuntu.com/community/Boot-Repair")

You could also install [easy bcd]("http://neosmart.net/EasyBCD/") inside windows and point it at the boot partition (the older versions on the right are the free ones)

Or you could do the old fashioned method through the terminal:

```

sudo mkdir /fix
sudo mount /dev/sda[COLOR="Red"]X[/COLOR] /fix [COLOR="red"]Where X is your ubuntu home partition[/COLOR]
sudo mount --bind /dev /fix/dev
sudo mount --bind /proc /fix/proc
sudo mount --bind /sys /fix/sys
sudo chroot /fix
sudo grub-install /dev/sda
sudo update-grub
```

Hope it helps!

---

### Post by nutpants on 2012-03-02
thank you that should work one way or another..

---

### Post by nutpants on 2012-03-02
Maybe it's a beta install disk bug
I tried everything I could with bcd and after having no luck getting grub to boot (or finding grub really)
 
I just deleted the Ubuntu partitions and tried reinstalling 5 times with the altx64 beta 12.04 install disk 5 different ways and still not Grubb any where..
Just booting windows every time...

(and I'm just not going to let Ubuntu have the whole disk the only option left)
Maybe I'll wait a week and get a daily build and try again..

If anyone can point this thread to the people in beta for testing, my thanks.

---

### Post by sffvba[e0rt on 2012-03-02
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*


404

---


---
title: "Just found a handy command:"
date: 2011-01-02
forum: The Cafe
---

### Post by Timmer1240 on 2011-01-02
To remove all the unused Linux Kernel headers, images and modules, simply run this command:  dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

---

### Post by CharlesA on 2011-01-02
Nice one. That's a bit easier then the way I was doing it. :)

---

### Post by Timmer1240 on 2011-01-02
Lot of useful things here! [http://www.webupd8.org/](http://www.webupd8.org/)

---

### Post by cariboo on 2011-01-02
If you are running Natty, and are a synaptic user, it marks older kernels as obsolete the next time you run it after installing a new kernel and rebooting.

---

### Post by CharlesA on 2011-01-02
> **cariboo907 said:**
> If you are running Natty, and are a synaptic user, it marks older kernels as obsolete the next time you run it after installing a new kernel and rebooting.
Does that affect the way dpkg sees them?

Just curious, as I haven't checked out Natty yet.

---

### Post by Timmer1240 on 2011-01-02
I just might have to upgrade someday I guess Im still using and loving Karmic 9.10 but support is going to end soon. Im not sure if I like the new unity desktop I just love gnome and how easy and intuitive it is but will upgrade sooner or later maybe in April.

---

### Post by wojox on 2011-01-02
All but the current and second most run from the command line:

```
OLD=$(ls -tr /boot/vmlinuz-* | head -n -2 | cut -d- -f2- | \
    awk '"'"'{print "linux-image-" $0}'"'"' )
if [ -n "$OLD" ]; then
    apt-get -qy remove --purge $OLD
fi
apt-get -qy autoremove --purge

```

---

### Post by ki4jgt on 2011-01-03
Awesome. I just lost 395 megs :-)

---

### Post by theraje on 2011-01-03
That is handy! In fact, I think I'll commit it to memory.

...

As if. :P

---

### Post by earthpigg on 2011-01-03
> **Timmer1240 said:**
>  dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

is there a website that explains all the *s/\(.*\)-\(* stuff? 

i see it a lot and it is clearly powerful, flexible, and robust as hell, but i don't even know what it is called, so have no idea how to google it.

---

### Post by mkendall on 2011-01-03
Try a search for "sed tutorial"

---

### Post by oldos2er on 2011-01-03
> **cariboo907 said:**
> If you are running Natty, and are a synaptic user, it marks older kernels as obsolete the next time you run it after installing a new kernel and rebooting.

Wow. I hope this behavior is configurable (i.e., can be disabled).

---

### Post by cariboo on 2011-01-03
> **CharlesA said:**
> Does that affect the way dpkg sees them?

Just curious, as I haven't checked out Natty yet. 

Dpkg was updated to 1.15.8.7ubuntu1, but I don't see anything in the change logs about changing the way it looks at packages.

---

### Post by CharlesA on 2011-01-03
> **cariboo907 said:**
> Dpkg was updated to 1.15.8.7ubuntu1, but I don't see anything in the change logs about changing the way it looks at packages.
Thanks. :)

---

### Post by ceramicm on 2011-01-03
[QUOTE=earthpigg]is there a website that explains all the s/\(.*\)-\( stuff?

i see it a lot and it is clearly powerful, flexible, and robust as hell, but i don't even know what it is called, so have no idea how to google it.[/QUOTE]

[_This_]("http://sed.sourceforge.net/sed1line.txt") is a pretty handy guide to [_sed_]("http://en.wikipedia.org/wiki/Sed").

---

### Post by CharlesA on 2011-01-03
> **ceramicm said:**
> [_This_]("http://sed.sourceforge.net/sed1line.txt") is a pretty handy guide to [_sed_]("http://en.wikipedia.org/wiki/Sed").

I have that one bookmarked, it's very handy indeed. :)

---

### Post by wojox on 2011-01-03
> **ceramicm said:**
> [_This_]("http://sed.sourceforge.net/sed1line.txt") is a pretty handy guide to [_sed_]("http://en.wikipedia.org/wiki/Sed").

That is a nice cheatsheet. :p

---

### Post by earthpigg on 2011-01-03
> **ceramicm said:**
> [_This_]("http://sed.sourceforge.net/sed1line.txt") is a pretty handy guide to [_sed_]("http://en.wikipedia.org/wiki/Sed").

thank you, sir.

---

### Post by chriswyatt on 2011-01-03
That's saved me over a gigabyte of hard drive space.  Nice :)

---

### Post by sdowney717 on 2011-01-03
oh wow, that took forever to run and left a possible error??
just posting what was left of terminal but there was so much more!

free space before 201.2
free space after  203.3

```
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.32-20-generic
Found initrd image: /boot/initrd.img-2.6.32-20-generic
Found linux image: /boot/vmlinuz-2.6.32-19-generic
Found initrd image: /boot/initrd.img-2.6.32-19-generic
Found linux image: /boot/vmlinuz-2.6.32-18-generic
Found initrd image: /boot/initrd.img-2.6.32-18-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
dpkg: warning: while removing linux-image-2.6.32-17-generic, directory '/lib/modules/2.6.32-17-generic' not empty so not removed.
Removing linux-image-2.6.32-18-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 2.6.32-18-generic /boot/vmlinuz-2.6.32-18-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-18-generic /boot/vmlinuz-2.6.32-18-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-18-generic /boot/vmlinuz-2.6.32-18-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.32-20-generic
Found initrd image: /boot/initrd.img-2.6.32-20-generic
Found linux image: /boot/vmlinuz-2.6.32-19-generic
Found initrd image: /boot/initrd.img-2.6.32-19-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
Purging configuration files for linux-image-2.6.32-18-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-18-generic /boot/vmlinuz-2.6.32-18-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-18-generic /boot/vmlinuz-2.6.32-18-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.32-20-generic
Found initrd image: /boot/initrd.img-2.6.32-20-generic
Found linux image: /boot/vmlinuz-2.6.32-19-generic
Found initrd image: /boot/initrd.img-2.6.32-19-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
dpkg: warning: while removing linux-image-2.6.32-18-generic, directory '/lib/modules/2.6.32-18-generic' not empty so not removed.
Removing linux-image-2.6.32-19-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 2.6.32-19-generic /boot/vmlinuz-2.6.32-19-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-19-generic /boot/vmlinuz-2.6.32-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-19-generic /boot/vmlinuz-2.6.32-19-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.32-20-generic
Found initrd image: /boot/initrd.img-2.6.32-20-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
Purging configuration files for linux-image-2.6.32-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-19-generic /boot/vmlinuz-2.6.32-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-19-generic /boot/vmlinuz-2.6.32-19-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.32-20-generic
Found initrd image: /boot/initrd.img-2.6.32-20-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
dpkg: warning: while removing linux-image-2.6.32-19-generic, directory '/lib/modules/2.6.32-19-generic' not empty so not removed.
Removing linux-image-2.6.32-20-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 2.6.32-20-generic /boot/vmlinuz-2.6.32-20-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-20-generic /boot/vmlinuz-2.6.32-20-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-20-generic /boot/vmlinuz-2.6.32-20-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
Purging configuration files for linux-image-2.6.32-20-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-20-generic /boot/vmlinuz-2.6.32-20-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-20-generic /boot/vmlinuz-2.6.32-20-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
dpkg: warning: while removing linux-image-2.6.32-20-generic, directory '/lib/modules/2.6.32-20-generic' not empty so not removed.
Removing linux-image-2.6.32-21-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 2.6.32-21-generic /boot/vmlinuz-2.6.32-21-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-21-generic /boot/vmlinuz-2.6.32-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-21-generic /boot/vmlinuz-2.6.32-21-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
Purging configuration files for linux-image-2.6.32-21-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-21-generic /boot/vmlinuz-2.6.32-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-21-generic /boot/vmlinuz-2.6.32-21-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
dpkg: warning: while removing linux-image-2.6.32-21-generic, directory '/lib/modules/2.6.32-21-generic' not empty so not removed.
Removing linux-image-2.6.32-22-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
Purging configuration files for linux-image-2.6.32-22-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-22-generic /boot/vmlinuz-2.6.32-22-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
dpkg: warning: while removing linux-image-2.6.32-22-generic, directory '/lib/modules/2.6.32-22-generic' not empty so not removed.
Removing linux-image-2.6.32-23-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
Purging configuration files for linux-image-2.6.32-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
dpkg: warning: while removing linux-image-2.6.32-23-generic, directory '/lib/modules/2.6.32-23-generic' not empty so not removed.
Removing linux-image-2.6.32-24-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
Purging configuration files for linux-image-2.6.32-24-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
dpkg: warning: while removing linux-image-2.6.32-24-generic, directory '/lib/modules/2.6.32-24-generic' not empty so not removed.
Removing linux-image-2.6.35-22-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
Purging configuration files for linux-image-2.6.35-22-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
Removing linux-image-2.6.35-23-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.35-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic

```

---

### Post by infestor on 2011-01-03
> **Timmer1240 said:**
> To remove all the unused Linux Kernel headers, images and modules, simply run this command:  dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

regexp wins again :D

---

### Post by bodhi.zazen on 2011-01-03
> **earthpigg said:**
> is there a website that explains all the *s/\(.*\)-\(* stuff? 

i see it a lot and it is clearly powerful, flexible, and robust as hell, but i don't even know what it is called, so have no idea how to google it.

It is IMO helpful to learn "regular expressions"

[http://linuxreviews.org/beginner/tao_of_regular_expressions/](http://linuxreviews.org/beginner/tao_of_regular_expressions/)

[http://www.zytrax.com/tech/web/regex.htm](http://www.zytrax.com/tech/web/regex.htm)

[http://www.linuxjournal.com/article/6324](http://www.linuxjournal.com/article/6324)

Used by sed, grep, awd, nginx, perl, the list goes on ...

---

### Post by phrostbyte on 2011-01-03
> **earthpigg said:**
> is there a website that explains all the *s/\(.*\)-\(* stuff? 

i see it a lot and it is clearly powerful, flexible, and robust as hell, but i don't even know what it is called, so have no idea how to google it.

"regular expressions"

---

### Post by phrostbyte on 2011-01-03
Wow, and I thought I was being so clever. I swear this thread was still on page one in my view. 

:lolflag: 8-[ 8-[ 8-[ 8-[

---

### Post by earthpigg on 2011-01-04
> **phrostbyte said:**
> "regular expressions"

really?

and ***two*** people said this?

who the hell named this?

---

### Post by CharlesA on 2011-01-04
> **earthpigg said:**
> 
who the hell named this?

That's just the name for it, not sure who named it, but the idea is that it does pattern matching.

Always makes me think of this:

[img]http://imgs.xkcd.com/comics/regular_expressions.png[/img]

---

### Post by inobe on 2011-01-04
very nice, saved me some work


edit: any more of the good stuff ?

---

### Post by inobe on 2011-01-05
does anyone know how to put that command together and explain what it does ?

---

### Post by mlnease on 2011-07-21
> **Timmer1240 said:**
> To remove all the unused Linux Kernel headers, images and modules, simply run this command:  dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
Thanks!  This helped me to get rid of one old kernel but not a couple others (please see attached)--any further advice?

Thanks in Advance,

mike

---

### Post by CharlesA on 2011-07-22
> **inobe said:**
> does anyone know how to put that command together and explain what it does ?

It uses sed to do pattern matching of the output of dpkg -l, other then that, I can't really explain much.

> **mlnease said:**
> Thanks!  This helped me to get rid of one old kernel but not a couple others (please see attached)--any further advice?

Thanks in Advance,

mike

You could try using the one I got working - modified from the one the OP posted.

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1 | xargs apt-get purge --assume-yes
```

---

### Post by mlnease on 2011-07-22
> **CharlesA said:**
> It uses sed to do pattern matching of the output of dpkg -l, other then that, I can't really explain much.



You could try using the one I got working - modified from the one the OP posted.

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1 | xargs apt-get purge --assume-yes
```

Thanks!  Got an interesting result.  ```
First, mn@mn-desktop:~$ sudo dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1 | xargs apt-get purge --assume-yes
[sudo] password for mn: 
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mn@mn-desktop:~$
```So I opened a gksudo nautilus and tried changing the permissions on /var/lib[FONT=monospace]/dpkg/lock[/FONT] and received this:  ```
mn@mn-desktop:~$ gksudo nautilus
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
mn@mn-desktop:~$
```Any clue?

---

### Post by CharlesA on 2011-07-22
Do you have another package manager open?

Have you already rebooted?

---

### Post by mlnease on 2011-07-22
> **CharlesA said:**
> Do you have another package manager open?

Have you already rebooted?

First, thanks again for your time an interest.  Yes, I've run update-grub and update-grub2 and rebooted--the grub screen remains the same and no, I had no other package manager open.  I find now that I'm able to access var/lib/dpkg via gksudo nautilus (your code returns the same error message as above); but I'm a bit nervous about tampering with the permissions without knowing what I'm doing.  Any suggestions?

---

### Post by halj32 on 2011-07-22
I think that you may need to add sudo to the line to run as root

---

### Post by CharlesA on 2011-07-22
Ah. I got the same error before I tried adding **sudo** before apt-get:

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1 | xargs sudo apt-get purge --assume-yes
```

---

### Post by cariboo on 2011-07-22
If you are using a recent version of Ubuntu, you have to run:

```
sudo update-grub
```

to remove the unsued kernel entries

---

### Post by mlnease on 2011-07-22
> **CharlesA said:**
> Ah. I got the same error before I tried adding **sudo** before apt-get:

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1 | xargs sudo apt-get purge --assume-yes
```
Bravo, yes, that made it run--but the entries are still there, even after running sudo update-grub and rebooting.

But I hate to take any more of your time on this--thanks a million just the same.

---

### Post by mlnease on 2011-07-22
Thanks, yes, I've run 'sudo update-grub' and 'sudo update-grub2' repeatedly, to no effect.  By the way, if I enter 2.6.38-8 or 2.6.38-10 in the Synaptic search window, nothing comes up.  Odd, no?

---

### Post by mlnease on 2011-07-22
By the way, I've just been copying and pasting your code--should I be replacing any characters, such as '( uname'?  Sorry but the code is all Greek to me...

---

### Post by CharlesA on 2011-07-22
Nah it can be run as is.

Strange that it's not updating the grub menu.

What is the output when you run update-grub?

Here's what mind looks like:
```
charles@Thor:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-33-server
Found initrd image: /boot/initrd.img-2.6.32-33-server
Found linux image: /boot/vmlinuz-2.6.32-32-server
Found initrd image: /boot/initrd.img-2.6.32-32-server
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by mlnease on 2011-07-22
> **CharlesA said:**
> Strange.

What is the output when you run update-grub?

```
mn@mn-desktop:~$ sudo update-grub
[sudo] password for mn: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.04 (11.04) on /dev/sda1
done
mn@mn-desktop:~$
```

---

### Post by CharlesA on 2011-07-22
That looks normal. Does the grub menu still have the extra entries?

Also are you dual booting?

---

### Post by mlnease on 2011-07-22
> **CharlesA said:**
> That looks normal. Does the grub menu still have the extra entries?

Also are you dual booting?

Yes, attached is a shot of the grub screen from a minute ago; and yes, I'm dual-booting with Lucid and Natty.

---

### Post by Bandit on 2011-07-22
> **earthpigg said:**
> is there a website that explains all the *s/\(.*\)-\(* stuff? 

i see it a lot and it is clearly powerful, flexible, and robust as hell, but i don't even know what it is called, so have no idea how to google it.

Dont know about websites, but its defined in the Linux+ study guide by Sybex.  Have to learn those types of CLI info to pass the exam.. Pray for me.. :(

---

### Post by CharlesA on 2011-07-22
> **mlnease said:**
> Yes, attached is a shot of the grub screen from a minute ago; and yes, I'm dual-booting with Lucid and Natty.

Try booting into Natty and seeing which kernels are installed there.

---

### Post by cariboo on 2011-07-22
As CharlesA said boot into your other installation, the command won't work on an installation that isn't running.

---

### Post by mlnease on 2011-07-22
Thanks, both--I've tried that with the same result.  I'm in Natty now but am downloading a lot of package files over a very slow connection--soon as I'm able, I'll run update-grub again, restart and post my results.

Thanks for your continued attention.

---

### Post by mlnease on 2011-07-22
OK, back in Natty--ran the code in #35 again, ran update-grub and restarted--same results.

Guys, it isn't like this is a major problem, just a graphic annoyance (I *think*)--I *really* appreciate all the help but maybe it's time to just live with it.

Thanks again for all your time.

---

### Post by CharlesA on 2011-07-22
Curious - what happens if you pick one of the other kernels?

---

### Post by vrhahaha on 2011-07-22
hi mlnease,

I've had the same situation before

sudo grub-mkconfig -o /boot/grub/grub.cfg

then proceed to update-grub solved mine

I hope that can help you

---

### Post by mlnease on 2011-07-23
Good question--why didn't I think of that?  I get a black screen with 'Error-file not found' for both 2.6.38-8 and 2.6.38-10.

---

### Post by mlnease on 2011-07-23
Thanks, vhrahaha--I tried it but the grub screen remains unchanged.

---

### Post by CharlesA on 2011-07-23
> **mlnease said:**
> Good question--why didn't I think of that?  I get a black screen with 'Error-file not found' for both 2.6.38-8 and 2.6.38-10.
I wonder where it's pulling the Grub menu from.

```
locate menu.lst
```

You could also post what the contents of /boot/grub/grub.cfg are.

---

### Post by zer010 on 2011-07-23
I've found this thread quite interesting and informative. Thanks to all who posted. Currently, I'm running Xubuntu 11.04 and even after some kernel upgrades, I don't get the older kernels listed in GRUB2. 

I'm also interested in where mlnease's grub is getting it's listing from.  I've never had an issue like that before..

---

### Post by mlnease on 2011-07-23
> **CharlesA said:**
> I wonder where it's pulling the Grub menu from.

```
locate menu.lst
```You could also post what the contents of /boot/grub/grub.cfg are.

```
mn@mn-OptiPlex-745:~$ locate menu.lst
/usr/share/doc/memtest86+/examples/grub-menu.lst
``````
mn@mn-OptiPlex-745:~$ sudo /boot/grub/grub.cfg
[sudo] password for mn: 
sudo: /boot/grub/grub.cfg: command not found
mn@mn-OptiPlex-745:~$
```

---

### Post by CharlesA on 2011-07-23
Ah, good no menu.lst.

Run this:

```
gedit /etc/grub/grub.cfg
```

---

### Post by mlnease on 2011-07-23
Here's /user/share/doc/memtest86+/examples/grub-menu.lst:
# sample /boot/grub/menu.lst entry for memtest86
#
# This example assumes the contents of /boot is on the root partition.
# If your /boot is on its own partition, remove /boot from the 'kernel' line.

title  memtest86+
root   (hd0,0)
kernel /boot/memtest86+.bin

title  memtest86+ (serial console 115200)
root   (hd0,0)
kernel /boot/memtest86+.bin console=ttyS0,115200n8

---

### Post by mlnease on 2011-07-23
> **CharlesA said:**
> Ah, good no menu.lst.

Run this:

```
gedit /etc/grub/grub.cfg
```

Done--it's blank.

---

### Post by CharlesA on 2011-07-23
Whoops, it should have been /boot/grub/grub.cfg.

Shouldn't multitask when posting.

---

### Post by Lucid As A Lynx on 2012-06-01
My boot drive was so full ubuntu couldn't install updates.
This command got me 2.5Gb back and now all is well :-)

---

### Post by sffvba[e0rt on 2012-06-01
*Thread **closed**.*


404

---


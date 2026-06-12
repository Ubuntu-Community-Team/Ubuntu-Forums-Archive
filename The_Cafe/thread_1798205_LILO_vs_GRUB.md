---
title: "LILO vs GRUB"
date: 2011-07-06
forum: The Cafe
---

### Post by createdcreature on 2011-07-06
Which do you think is better?

---

### Post by jtarin on 2011-07-06
Well I used Lilo for well over 12 years when running Slackware in a dual-boot situation and I found it quite comfortable to use. I never did like Grub back in those days as it was extremely unreliable.The only problem with Lilo back then it had limitations when installed to the MBR it sometimes had problems finding Linux if it was beyond the 1024 cyl. Those were the days. To over come that I always installed Lilo to the / of the partition where Linux lived and then dd'ed the first 512 block size and copied to my C:\ drive and used boot.ini to boot it. Never had a problem. Used to update Lilo and copy it to C:\ worked like a charm....very easy to configure and edit.

---

### Post by aeiah on 2011-07-06
the standard now is grub2. its a boot manager - if it works, just use it.

---

### Post by jtarin on 2011-07-06
> **aeiah said:**
> the standard now is grub2. its a boot manager - if it works, just use it.Great observation, but that wasn't the question.:p

---

### Post by aeiah on 2011-07-06
> **jtarin said:**
> Great observation, but that wasn't the question.:p

ok:

grub2 is better in my opinion, because it is the standard, and accomplishes its basic task of booting operating systems in a reliable manner.

---

### Post by wildmanne39 on 2011-07-06
Hi, I also like grub2 and it is included on the livecd, but I have not used lilo, so I am not going to say grub2 is better, but I have not had any problems with it.

---

### Post by createdcreature on 2011-07-06
In 2004, GRUB was unstable, and not a contender. However, LILO is best at booting Linux, not Windows, and now GRUB is stable, so it is better now. LILO developers I think fell out.

---

### Post by jtarin on 2011-07-06
> **Robert Moyse said:**
> In 2004, GRUB was unstable, and not a contender. However, LILO is best at booting Linux, not Windows, and now GRUB is stable, so it is better now. LILO developers I think fell out.
Lilo development picked up last year....I think after the problem your talking of.

---

### Post by Perkins on 2011-07-06
They both have their advantages.  LILO is smaller and simpler.  I have a couple of old machines with old drives, and LILO is the only bootloader that functions with them.  GRUB tends to be more powerful with more options.  I carry a USB stick with GRUB and a whole pile of floppy images that do various diagnostics, along with an Ubuntu install.  A simple update-grub is enough to find all the operating systems on whatever machine it's attached to and be able to start them.

---


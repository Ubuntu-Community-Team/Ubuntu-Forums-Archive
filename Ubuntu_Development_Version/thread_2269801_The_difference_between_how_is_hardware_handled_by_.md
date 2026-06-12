---
title: "The difference between how is hardware handled by Ubuntu and Manjaro"
date: 2015-03-18
forum: Ubuntu Development Version
---

### Post by aljosa2 on 2015-03-18
Hi all,
today I have finally managed to try the working (20150318/18-Mar-2015) daily build image of Ubuntu 15.04 (Vivid Vervet) on my Asus N750JV-T4069H Notebook, in order to see if this operating system and my Asus N750JV-T4069H Notebook are now more in love then the year before. 
Curious to see if there are some variations between how is hardware handled by different operating systems, I have also tried the new Manjaro XFCE 0.9.0-pre4 edition.

Congratulations to developers :) although using bootable live system without installing anything, both Ubuntu and Manjaro are amazingly fast.
Both system ship with X.org server 1.17.1, kernel 1.19.1 and systemd.

Unfortunately, on both systems my screen brightness function keys are not working. Other things seems ok.

I'm not an expert, and still don't understand fully what are all this Ubuntu dmesg lines related to "mtrr_gran_size/mtrr_chunk_size"

```
[    0.000000] DMI: ASUSTeK COMPUTER INC. N750JV/N750JV, BIOS N750JV.210 04/11/2014
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x42f200 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7C00000000 write-back
[    0.000000]   1 base 0400000000 mask 7FE0000000 write-back
[    0.000000]   2 base 0420000000 mask 7FF8000000 write-back
[    0.000000]   3 base 0428000000 mask 7FFC000000 write-back
[    0.000000]   4 base 042C000000 mask 7FFE000000 write-back
[    0.000000]   5 base 042E000000 mask 7FFF000000 write-back
[    0.000000]   6 base 042F000000 mask 7FFFE00000 write-back
[    0.000000]   7 base 00C0000000 mask 7FC0000000 uncachable
[    0.000000]   8 base 00BFC00000 mask 7FFFC00000 uncachable
[    0.000000]   9 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 512MB, type WB
[    0.000000] reg 2, base: 16896MB, range: 128MB, type WB
[    0.000000] reg 3, base: 17024MB, range: 64MB, type WB
[    0.000000] reg 4, base: 17088MB, range: 32MB, type WB
[    0.000000] reg 5, base: 17120MB, range: 16MB, type WB
[    0.000000] reg 6, base: 17136MB, range: 2MB, type WB
[    0.000000] reg 7, base: 3GB, range: 1GB, type UC
[    0.000000] reg 8, base: 3068MB, range: 4MB, type UC
[    0.000000] total RAM covered: 16110M
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 64K     chunk_size: 128K     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 64K     chunk_size: 256K     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 64K     chunk_size: 512K     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 64K     chunk_size: 1M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 64K     chunk_size: 8M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 64K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 128K     chunk_size: 128K     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 128K     chunk_size: 256K     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 128K     chunk_size: 512K     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 128K     chunk_size: 1M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 128K     chunk_size: 2M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 128K     chunk_size: 4M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 128K     chunk_size: 8M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 128K     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 128K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 256K     chunk_size: 256K     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 256K     chunk_size: 512K     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 256K     chunk_size: 1M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 256K     chunk_size: 2M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 256K     chunk_size: 4M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 256K     chunk_size: 8M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 256K     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 256K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 512K     chunk_size: 512K     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 512K     chunk_size: 1M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 512K     chunk_size: 2M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 512K     chunk_size: 4M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 512K     chunk_size: 8M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 512K     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 512K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 1M     chunk_size: 1M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 1M     chunk_size: 2M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 1M     chunk_size: 4M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 1M     chunk_size: 8M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 1M     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 1M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 2M     chunk_size: 2M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 2M     chunk_size: 4M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 2M     chunk_size: 8M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 2M     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 2M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 4M     chunk_size: 4M     num_reg: 10      lose cover RAM: 8946M
[    0.000000]  gran_size: 4M     chunk_size: 8M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 16M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 32M     num_reg: 8      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 64M     num_reg: 8      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 128M     num_reg: 8      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 256M     num_reg: 8      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 512M     num_reg: 8      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 1G     num_reg: 8      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 2G     num_reg: 9      lose cover RAM: 2M
[    0.000000]  gran_size: 8M     chunk_size: 8M     num_reg: 10      lose cover RAM: 758M
[    0.000000]  gran_size: 8M     chunk_size: 16M     num_reg: 10      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 32M     num_reg: 8      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 64M     num_reg: 8      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 128M     num_reg: 8      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 256M     num_reg: 8      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 512M     num_reg: 8      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 1G     num_reg: 8      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 2G     num_reg: 9      lose cover RAM: 6M
[    0.000000]  gran_size: 16M     chunk_size: 16M     num_reg: 10      lose cover RAM: 254M
[    0.000000]  gran_size: 16M     chunk_size: 32M     num_reg: 8      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 64M     num_reg: 8      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 128M     num_reg: 8      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 256M     num_reg: 8      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 512M     num_reg: 8      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 1G     num_reg: 8      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 2G     num_reg: 9      lose cover RAM: 14M
[    0.000000]  gran_size: 32M     chunk_size: 32M     num_reg: 10      lose cover RAM: 142M
[    0.000000]  gran_size: 32M     chunk_size: 64M     num_reg: 8      lose cover RAM: 46M
[    0.000000]  gran_size: 32M     chunk_size: 128M     num_reg: 8      lose cover RAM: 46M
[    0.000000]  gran_size: 32M     chunk_size: 256M     num_reg: 8      lose cover RAM: 46M
[    0.000000]  gran_size: 32M     chunk_size: 512M     num_reg: 8      lose cover RAM: 46M
[    0.000000]  gran_size: 32M     chunk_size: 1G     num_reg: 8      lose cover RAM: 46M
[    0.000000]  gran_size: 32M     chunk_size: 2G     num_reg: 9      lose cover RAM: 46M
[    0.000000]  gran_size: 64M     chunk_size: 64M     num_reg: 10      lose cover RAM: 110M
[    0.000000]  gran_size: 64M     chunk_size: 128M     num_reg: 8      lose cover RAM: 110M
[    0.000000]  gran_size: 64M     chunk_size: 256M     num_reg: 8      lose cover RAM: 110M
[    0.000000]  gran_size: 64M     chunk_size: 512M     num_reg: 8      lose cover RAM: 110M
[    0.000000]  gran_size: 64M     chunk_size: 1G     num_reg: 8      lose cover RAM: 110M
[    0.000000]  gran_size: 64M     chunk_size: 2G     num_reg: 9      lose cover RAM: 110M
[    0.000000]  gran_size: 128M     chunk_size: 128M     num_reg: 8      lose cover RAM: 238M
[    0.000000]  gran_size: 128M     chunk_size: 256M     num_reg: 8      lose cover RAM: 238M
[    0.000000]  gran_size: 128M     chunk_size: 512M     num_reg: 8      lose cover RAM: 238M
[    0.000000]  gran_size: 128M     chunk_size: 1G     num_reg: 8      lose cover RAM: 238M
[    0.000000]  gran_size: 128M     chunk_size: 2G     num_reg: 9      lose cover RAM: 238M
[    0.000000]  gran_size: 256M     chunk_size: 256M     num_reg: 6      lose cover RAM: 494M
[    0.000000]  gran_size: 256M     chunk_size: 512M     num_reg: 6      lose cover RAM: 494M
[    0.000000]  gran_size: 256M     chunk_size: 1G     num_reg: 7      lose cover RAM: 494M
[    0.000000]  gran_size: 256M     chunk_size: 2G     num_reg: 8      lose cover RAM: 494M
[    0.000000]  gran_size: 512M     chunk_size: 512M     num_reg: 5      lose cover RAM: 750M
[    0.000000]  gran_size: 512M     chunk_size: 1G     num_reg: 7      lose cover RAM: 750M
[    0.000000]  gran_size: 512M     chunk_size: 2G     num_reg: 8      lose cover RAM: 750M
[    0.000000]  gran_size: 1G     chunk_size: 1G     num_reg: 3      lose cover RAM: 1774M
[    0.000000]  gran_size: 1G     chunk_size: 2G     num_reg: 3      lose cover RAM: 1774M
[    0.000000]  gran_size: 2G     chunk_size: 2G     num_reg: 3      lose cover RAM: 1774M
[    0.000000] mtrr_cleanup: can not find optimal value
[    0.000000] please specify mtrr_gran_size/mtrr_chunk_size
[    0.000000] e820: update [mem 0xbfc00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbf000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
```

but hey, the Manjaro dmesg seems to me much better:

```
[0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: ASUSTeK COMPUTER INC. N750JV/N750JV, BIOS N750JV.210 04/11/2014
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x42f200 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7C00000000 write-back
[    0.000000]   1 base 0400000000 mask 7FE0000000 write-back
[    0.000000]   2 base 0420000000 mask 7FF8000000 write-back
[    0.000000]   3 base 0428000000 mask 7FFC000000 write-back
[    0.000000]   4 base 042C000000 mask 7FFE000000 write-back
[    0.000000]   5 base 042E000000 mask 7FFF000000 write-back
[    0.000000]   6 base 042F000000 mask 7FFFE00000 write-back
[    0.000000]   7 base 00C0000000 mask 7FC0000000 uncachable
[    0.000000]   8 base 00BFC00000 mask 7FFFC00000 uncachable
[    0.000000]   9 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC 
[    0.000000] e820: update [mem 0xbfc00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbf000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
```

I've made the same experiment on my wife's notebook Asus X750JN-TY027H. 

The good news is that the option to install the Nvidia driver (346.47) for the graphics card (GeForce GT 840M) is now present in additional drivers.
Also, no problem here with the "mtrr_gran_size/mtrr_chunk_size" stuff.
On both Ubuntu and Manjaro everything ok with screen brightness function keys.

Unfortunately, [**Elantech touchpad is completely dead**]("https://bugzilla.kernel.org/show_bug.cgi?id=94981") on both systems. The only difference is that on Ubuntu even cursor is missing, while on Manjaro at least cursor is visible.

---

### Post by grahammechanical on 2015-03-18
You might be interested in this person project by this developers. He is collecting information brightness, etc., on different hardware because he thinks that Linux is not uniform in how it deals with the back light 

[http://www.zygoon.pl/2015/03/analyzing-lantern-submissions.html](http://www.zygoon.pl/2015/03/analyzing-lantern-submissions.html)

Regards.

---

### Post by aljosa2 on 2015-03-20
Thanks for your suggestion :)

So, yesterday I've made an experiment and installed both Manjaro and Ubuntu on my Asus N750JV-T4069H optimus notebook.

During the installation process, which is pretty slow, Manjaro asked me if I want to use free or proprietary drivers. I have opted for proprietary drivers. New Manjaro is a very fast distro. Dmesg output seems ok to me. Personally, I much more prefer Ubuntu nvidia-prime solution over Manjaro bumblebee, but bumblebee in Manjaro works perfect.

During the installation process of Ubuntu, which is pretty fast, Ubuntu didn't ask me for keyboard input language. This is a very big problem because I have italian keyboard, and by creating strong password with various symbols, once installation is finished I am not able to login into Ubuntu.
New Ubuntu is a very fast distro, too.
Unfortunately, there is still something very wrong with the installation of Nvidia 346.47 driver.
In order to fix the not so nice dmesg output related to many "mtrr_gran_size/mtrr_chunk_size" bad lines, I needed to add the "enable_mtrr_cleanup mtrr_spare_reg_nr=1 mtrr_gran_size=64K mtrr_chunk_size=256M" kernel boot parameter inside grub.
Although screen brightness function keys still doesn't work, the very good news is that the screen brightness settings are not any more reset to maximux after every reboot.

Another great news:
The root cause of the Elantech touchpad problem in Asus X750JN-TY027H optimus notebook has finally been correctly identi&#64257;ed :)

[https://bugzilla.kernel.org/show_bug.cgi?id=90841#c6](https://bugzilla.kernel.org/show_bug.cgi?id=90841#c6)

---

### Post by aljosa2 on 2015-03-28
hi, can anyone please tell me one thing about "mtrr_gran_size/mtrr_chunk_size" mess:

as much as i can understand, kernel consists of some parts written for debian based systems, and of some parts written specifically for arch based systems.
since there is a big difference between how manjaro and ubuntu manages mtrr, the problem that i have is caused by kernel, or by ubuntu?

thanks in advance for any explanation

---

### Post by dino99 on 2015-03-28
> **aljosa2 said:**
> hi, can anyone please tell me one thing about "mtrr_gran_size/mtrr_chunk_size" mess:

 the problem that i have is caused by kernel, or by ubuntu?

thanks in advance for any explanation

well it is as simple as comparing ubuntu kernel & vanilla kernel

---

### Post by aljosa2 on 2015-03-28
hi 9d9,
thanks for your reply, plese let me understand better:

take for example kernel 3.19.3
there is one "generic" version here
[https://lkml.org](https://lkml.org)
and another one ubuntu specific here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19.3-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19.3-vivid/)

who's to "blame" for mtrr bug?

---

### Post by dino99 on 2015-03-28
i've never pay attention to mtrr, so i cant elaborate much; but you have catched the idea
at first glance i would say that the ubuntu custom packaging introduce much more issues than benefits; cant know without testing ;)

---

### Post by aljosa2 on 2015-03-28
if kernel would be one and the same for everyone, then "culprit" would obviously be the ubuntu team.
as i know that some parts of the "generic" kernel are written specifically for arch, i'm not sure if bug is inside the "generic" kernel - inside the part written for non-arch

---

### Post by aljosa2 on 2015-04-19
Here's what's new:
Solution for Elantech touchpad problem will become part of kernel 4.1, and most probably will not be backported to 3.19.

---

### Post by tokyobadger on 2015-04-19
There's an explanation of MTRR and the relevant kernel config options you'd need to adjust at this [blog](http://my-fuzzy-logic.de/blog/index.php?/archives/41-Solving-linux-MTRR-problems.html)
It looks like the Ubuntu kernel has some options switched off(?) - you'd need to compile your own - [Ubuntu instructions here](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

---

### Post by aljosa2 on 2015-04-19
> **tokyobadger said:**
> There's an explanation of MTRR and the relevant kernel config options you'd need to adjust at this [blog]("http://my-fuzzy-logic.de/blog/index.php?/archives/41-Solving-linux-MTRR-problems.html")
It looks like the Ubuntu kernel has some options switched off(?) - you'd need to compile your own - [Ubuntu instructions here]("https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel")

Let me express my point of view:

When I was twenty years old, they used to call me "doctor". Because then, long time ago, I was a real expert (auto mechanic) for cars - without exaggeration. 
I was just a "kid" when I disassembled the whole automobile into the smallest pieces, and cut in half all of them using grinder in order to understand how they work. 
It is from those times that I'm sick with one particular disease: Instead of alleviating the consequences, I always tend to eliminate the cause.
That said, it doesn't mean that I am generally against fast applied temporary solutions. On the contrary, they're welcomed, but only for a short time period after which things need to be fixed in the right way.

During the latest twenty years, I have become an expert in politics/money too. 
I was working on one Internet-based alternative currency system, so I needed to learn a lot about computer world.
Certainly, I'm very far away of being an expert in this sector, but there are also many things that I can comprehend without difficulties. 

In my modest opinion, Linux is already irreversibly contaminated by "evil" because of whom this operating system exist as an alternative to Windows at the first place.
According to Forbes, with his 80 billion dollars Bill Gates is a richest person on Earth. That simply is not true. There are some people wealthier than him, including me: 

<snip>

And that's exactly the reason why I'm seriously considering to make some huge donation as soon as I meet an idea capable to become independent system, better of both Windows and Linux.

Back to the "mtrr" question, in my case it's a problem now already 3 years old.
Thanks to the help of one expert, I can medicate this issue by adding the following kernel boot parameter: "enable_mtrr_cleanup mtrr_spare_reg_nr=1 mtrr_gran_size=64K mtrr_chunk_size=256M".
But that's not the point. 
Since no "mtrr" issue exist in Manjaro these days, maybe it could be that this problem does not exist any more neither in Ubuntu. I wouldn't be at all surprised if maybe Ubuntu developers have simply forgotten to switch the "damn" thing on?

---

### Post by Elfy on 2015-04-19
try [https://www.linuxfoundation.org/participate/linux-donate](https://www.linuxfoundation.org/participate/linux-donate) 

and with that I'll close this thread. 

There is no chance of this getting fixed in Ubuntu in the next 5 days - if it is an issue and this forum will be for 15.10 issues thereafter.

---


---
title: "Thinkpad T60p with Ubuntu 11.04 &amp; dual boot."
date: 2012-02-25
forum: Testimonials &amp; Experiences
---

### Post by wangmf8877 on 2012-02-25
While my Winxp is a little old, I installed Ubuntu 11.04 to give it a try at the beginning of 2011. My disk was already partition into C:\Winxp and D:\data.

I didn't install 10.04LTS, because I wanted to keep the ThinkVantage key to resume Winxp back into factory status sometime. I only found this installation option in 11.04, which allowed me to install GRUB on second disk. I installed Ubuntu 11.04 at the end partition of my hard disk, just besides the hidden partition of Winxp restore system. So the Ubuntu boot loader was located at /dev/sdaN (N=some number depends on your system, for mine, it's sda5).

After installation, Winxp booted up directly, because I installed GRUB on second disk, and didn't touch the MBR of Winxp (so to keep ThinkVantage function). In order to get Ubuntu, I booted with a Ubuntu live usb, and used "sudo dd if=/dev/sda5 of=sda5.bak bs=512 count=1" to get my GRUB boot loader. Then in Winxp I added [c:\sda5.bak="Ubuntu11.04"] into C:\boot.ini, and copied sda5.bak to C:\. So I could use Winxp boot loader "C:\boot.ini" to get dual OS options.

After about 1 year usage in Ubuntu classical interface, I fully transferred to Ubuntu, and only went back to Winxp once in a month. Ubuntu is much more stable, faster, and with better interface than Winxp. Eventually I changed C:\boot.ini, with [default=c:\sda5.bak] :)

Thank you very much! Ubuntu developers. You did a great job and deserve a grateful salute.

---


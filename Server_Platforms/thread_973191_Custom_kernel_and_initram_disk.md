---
title: "Custom kernel and initram disk"
date: 2008-11-06
forum: Server Platforms
---

### Post by psilikon on 2008-11-06
So I am trying to build and Asterisk server with 8.10 server. There are a couple of options that must be changed in the kernel for Asterisk to be happy so I need to build a custom kernel. I followed this guide [http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/) . Everything seems to be right but I am confused when it comes to an initial ram disk... Do I *need* one if I build the modules for my harddisk controller and filesystem type into the kernel. I made sure to include the -initrd when I did a make-kpkg but an initrd was not created.  I also tried to use the original 2.6.27-7 initrd in my /boot dir.  Could someone please let me know what I'm doing wrong or perhaps refer me to another howto?

Thanks!

---

### Post by kerry_s on 2008-11-06
you always need a ramdisk or you won't have a boot.
the how to looks right, you should be able to just copy and paste it right down.

i grabbed mine from kernel source:
[http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.27.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.27.4.tar.bz2)

here are my notes, from when i did mine:

sudo su
apt-get update
apt-get install kernel-package libncurses5-dev build-essential
mv *.tar.bz2 /usr/src
cd /usr/src
tar xvjf *.tar.bz2
ln -s linux-2.6.27.4 linux
cd /usr/src/linux
make clean && make mrproper
cp /boot/config-`uname -r` ./.config
make menuconfig
make-kpkg clean
make-kpkg --initrd --append-to-version=-custom kernel_image
#with headers# make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
##stop reboot and switch to the stock kernel & remove old custom kernel
sudo su
cd /usr/src
dpkg -i *.deb
reboot

i start where i downloaded the kernel to ~/Desktop and just copied and pasted my way down. i know it works i've done it 11 times. :lolflag:

---

### Post by psilikon on 2008-11-06
Nice! Lovin' the quick response. Maybe I forgot the make clean and make mrproper. 

Question here:

make-kpkg --initrd --append-to-version=-custom kernel_image
#with headers# make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

The first line makes the actual kernel image and the second does what??


Thanks.

---

### Post by kerry_s on 2008-11-06
> **psilikon said:**
> Nice! Lovin' the quick response. Maybe I forgot the make clean and make mrproper. 

Question here:

make-kpkg --initrd --append-to-version=-custom kernel_image
#with headers# make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

The first line makes the actual kernel image and the second does what??


Thanks.

i use this 1 if i only want the image:
make-kpkg --initrd --append-to-version=-custom kernel_image

the other line:
make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

does both image and headers.
 
i don't need the headers so i use the first line and i just left that there just in case i need it down the road. my laptops old 450mhz 256mb ram it takes about 6 hours to compile the image and headers, but only 4 hours for just the image.
you really only need the image, unless your doing some compiling that needs the kernel headers.
anytime you see a line with "#" are usually comments. 
#with headers# is to tell me to use that 1 if i want headers.
sorry if it confused you.

---

### Post by psilikon on 2008-11-07
Ok thanks... got it.  I think I'll compile headers in case I need to compile kernel module in the future... the box is a quad core w/ 4 GB of 1066 ram.

Thanks again.

---

### Post by icanfly0307 on 2008-12-17
Its gonna compile real fast on that computer!! :)

---


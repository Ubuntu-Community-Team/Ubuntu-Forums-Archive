---
title: "Server won't boot new Kernel after Hardy upgrade"
date: 2008-06-20
forum: Server Platforms
---

### Post by lodp on 2008-06-20
Hi,

I finally upgraded my server from Gutsy to Hardy yesterday. Everything seems to be working fine, but even after a re-boot it still appears to be running the old kernel:
> 
$uname -r
2.6.22-14-server
How do I make it boot the new kernel? It's a remote server, and I just noticed that there's no GRUB installed..

Here's the content of /boot:

> abi-2.6.22-14-server
abi-2.6.24-19-server
boot.0800
coffee.bmp
config-2.6.22-14-server
config-2.6.24-19-server
debian.bmp
debianlilo.bmp
initrd.img-2.6.22-14-server
initrd.img-2.6.22-14-server.bak
initrd.img-2.6.24-19-server
initrd.img-2.6.24-19-server.bak
map
sarge.bmp
sid.bmp
System.map-2.6.22-14-server
System.map-2.6.24-19-server
vmlinuz-2.6.22-14-server
vmlinuz-2.6.24-19-server


---

### Post by doogy2004 on 2008-06-21
> **lodp said:**
> Hi,

I finally upgraded my server from Gutsy to Hardy yesterday. Everything seems to be working fine, but even after a re-boot it still appears to be running the old kernel:

How do I make it boot the new kernel? It's a remote server, and I just noticed that there's no GRUB installed..

Here's the content of /boot:

what is the contents of your /boot/grub/menu.lst ?

---

### Post by lodp on 2008-06-21
that's the thing -- there's no /boot/grub folder at all! So it doesn't seem like grub is installed..

---

### Post by doogy2004 on 2008-06-21
> **lodp said:**
> that's the thing -- there's no /boot/grub folder at all! So it doesn't seem like grub is installed..

My bad, maybe lilo is installed a quick google search found that the config for lilo is located at /etc/lilo.conf . Give that a try.

---

### Post by lodp on 2008-06-22
That was it, thanks!

Here's what lilo.conf looks like:

> boot=/dev/sda
root=/dev/sda2
timeout=40
prompt
default=Linux

image=/boot/vmlinuz-2.6.22-14-server
  label=Linux
  read-only
  initrd=/boot/initrd.img-2.6.22-14-server


So I just replaced the filenames with the newer ones (*2.6.24-19-server), and ran /sbin/lilo. That gave me a warning:

> 
sudo /sbin/lilo
Warning: LBA32 addressing assumed
Added Linux *
One warning was issued.


I googled the error and added the "lba32" option, now I don't get that error anymore. Anyway, I'm a bit scared of hitting reboot now, because since this is a remote server I'll be boned if it hangs in the process somewhere. Can somebody tell me everything's gonna be alright?

This is what my /etc/lilo.conf looks like now. Changes to previous (working) version emphasized:

> boot=/dev/sda
root=/dev/sda2
timeout=40
prompt
**lba32**
default=Linux

image=/boot/vmlinuz-2.6.**24-19**-server
  label=Linux
  read-only
  initrd=/boot/initrd.img-2.6.**24-19**-server


---

### Post by lodp on 2008-06-25
*bump*

I still haven't dared to re-boot the server (since it's remote and I'd have to pay sombody to fix it in case it doesn't boot). Can somebody tell me whether the way I fixed up lilo above for the new kernel seems right?

BTW, why isn't this handled by the distribution upgrade tool? I remember it working fine with grub when upgrading my desktop installation every time so far since dapper. Is lilo just too old?

---

### Post by doogy2004 on 2008-06-26
Sorry, I didn't want to reply because I've never really used lilo.  I would imagine that it isn't handled because the tool that is called after the kernel is upgraded is (from my understanding) designed to reconfigure the Grub menu.lst with the updated kernel.

About the restart, like I said I've never used lilo, but I would imagine that if you aren't getting any errors from the tools in lilo you should be just fine.  This is just speculation on my part, but everything looks good.

---


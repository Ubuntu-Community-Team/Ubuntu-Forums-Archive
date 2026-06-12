---
title: "Preboot authentication failure attemp Ubuntu drops to shell"
date: 2013-07-10
forum: Security
---

### Post by Traxster on 2013-07-10
Hello everyone,


         Just recently installed Ubuntu 13.04 (x64) on a new laptop  (Acer s3). Basically, I bought this machine brand new, and installed  Ubuntu over Windows 8 with the Live CD. I did not wipe the hard drive  before the new install, I just mearly used Ubuntu's quick format method,  and did not do any custom partitioning. I set up preboot authentication  with LUKS (whole disk encryption) since it gave me the option to do so  during installation. I also seperately encrypted the HOME directory.This  morning, while half asleep, I had 3 consecutive preboot authentication  failures attempts  and I was dropped into a shell. Is this normal? 

 I did read a little about initramfs. This does not appear to be a big gaping security hole? However, **I am concerned about the alert.**  (/dev/mapper/ubuntu--vg-root does not exist.) Also want to mention that  when I reboot the system, as long as I don't fail preboot  authentication 3 times, it will let me boot right into the system.    normally. Below is the message (retyped) displayed by Ubuntu.


Gave up waiting or root device.  Common Problems
- Boot args (cat /prIoc/cmdline)
- check rootdelay = '(did the system wait long enough?)
-missing modules (cat /proc modules; is /dev)
Alert! /dev/mapper/ubuntu--vg-root does not exist. Dropping to a shell


BusyBox v1.20.2 (Ubuntu 1:1.20.0 - 8ubuntu1)
built in shell (ash)
enter 'help' for a list of built in commands
(initramfs)_


Any insight would be greatly appreciated. 

traxster

---

### Post by Cheesehead on 2013-07-11
The system drops to the busybox prompt only under a few circumstances. It means that the bootloader works, the kernel loads, and initramfs (the initial read-only) system loads. Then, the system unmounts the boot disk (which is read-only) and fails to remount it read-write.

The most common reasons for dropping to busybox are:
Grub misconfiguration (not your problem - it would drop to busybox every time)
Hardware misconfiguration (UEFI, for example - see [http://askubuntu.com/questions/293768/cant-get-ubuntu-13-04-64bit-to-boot-after-upgrading-mobo-cpu-and-memory](http://askubuntu.com/questions/293768/cant-get-ubuntu-13-04-64bit-to-boot-after-upgrading-mobo-cpu-and-memory))
Hardware failure - flaky HDD controller, or motherboard issue.

Since it's intermittent on a new laptop, you might have a warranty hardware issue.


> **Traxster said:**
> I did read a little about initramfs. This does not appear to be a big gaping security hole?
In what way? Your data is encrypted. Go ahead, try to decrypt it.

---

### Post by Traxster on 2013-07-12
> **Cheesehead said:**
> In what way? Your data is encrypted. Go ahead, try to decrypt it.

I encrypted the entire hard drive during the installation process. I think it is 256-AES-CBC

---

### Post by Delphos on 2013-08-12
Traxster, I suppouse Cheeseahead's question was rethorical :-)
You simply can't to decrypt your data without the key. If you lose it, you're in troubles ;-)
LUKS is a great choice.

---

### Post by Traxster on 2013-08-12
> **Traxster said:**
> I encrypted the entire hard drive during the installation process. I think it is 256-AES-CBC


I guess you were asking me in what way it is a security hole? is it possible for someone to get dumped to initramfs prompt, and say maybe load a program into it, that logs pw for luks? I can't imagine so, but check out [this]("http://www.debian.org/doc/manuals/securing-debian-howto/ch4.en.html#s-lilo-passwd") . scroll down to section 4.5. That is what got me worried. 


traxster

---


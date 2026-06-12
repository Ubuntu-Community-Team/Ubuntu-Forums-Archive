---
title: "GRUB stops at menu after power cut"
date: 2012-03-23
forum: Server Platforms
---

### Post by jordang on 2012-03-23
Dear All,

I'm not very experienced with Linux, just user for desktop and server for 12 years now.
I've recently replaced my home server to a an atom based motherboard with just a hdd. This board has _no battery_, so as power is cut, it forgets the time until it is syncronised again.

I had several issues, but now it is nailed down to one problem : if power is lost, regardless if I shut it down correctly or just cut, it would not boot. It stops at the grub menu.
This case, I have to plug a keyboard in and hit an [enter], than it boots fine.
I have also noticed, this case there is no countdown. I have tried to set "0" at timeout, but it does not matter. 

Thanks for any advise.

It is Ubuntu server 11.10

This is my config file :


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

JG

---

### Post by sudodus on 2012-03-23
Welcome to the Ubuntu Forums, jordang,

Have you tried to have the keyboard attached to the computer at boot? Maybe the computer looks for a keyboard, and maybe you can unset that in the bios menu system.

By the way, what version and flavour are you running, Ubuntu Server 11.10 or something else?

---

### Post by jordang on 2012-03-23
Hello,
Thanks for your reply!

Yes, it is ubuntu server (64bit) 11.10. 
Yes, I have tried to boot with the keyboard, it is the same.

Regards,
JG

---

### Post by jordang on 2012-03-23
I think it is important to highlight, that if I just reboot, it boots fine. If I shut down and unplug power than plug back, it stops at the grub menu. 

JG

---

### Post by sudodus on 2012-03-23
You also wrote that there is no battery. I guess you mean that there is no motherboard battery. Is there a battery holder? Then maybe it would work after power shut-off, if you insert a battery. 

An other idea is to let the computer wait longer before trying to boot (to let it 'accept' that the clock is bad), so instead increase the timeout to for example

GRUB_TIMEOUT=30

Or is there some other place, earlier in the boot process, where it could be kept waiting for a longer time? Check in the bios menu, if there is such a setting.

---

### Post by jordang on 2012-03-23
Correct, there is no RTC battery on the motherboard. there is no place for it. It is a minimalist atom board.
I have tried longer timeout, but no matter what I set for timeout, it does not count after power cycle.
I have another look at the bios menu.

I had a tip before, that grub knows somehow what was the last choice in the menu and if error occured. I believe it thinks that error occured, and waits for choosing the boot, but I could not find how to switch off this function.

Regards,
JG

---

### Post by dharmavir on 2012-03-24
I am new to linux and ubuntu world but I think you should try updating grub again, if you haven't tried that yet.

$ sudo update-grub

---

### Post by jordang on 2012-03-24
yes, I did.
In the first 10 case sometimes I forgot, but now I always do update. It is in the header of the config file, that is how I know it is needed. I was playing with the settings for about half a day :-(
Regards,
JG

---

### Post by jordang on 2012-03-24
A friend found a solution.

in grub.cfg
****
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1 
****
-1 should be 0 .

It works.

Now the only problem is that in case of kernel update, it will execute update-grub I think, which will overwrite this change. It is not that big problem.

Regards,
JG

---

### Post by sudodus on 2012-03-24
Thank you for sharing the solution :KS

And please mark this this thread as SOLVED clicking on [COLOR="Red"]**Thread Tools**[/COLOR] at the top of this page

---

### Post by snkkid on 2012-03-26
Hi,

I know this is a little late but I think it is better to make your recordfail modification in :
```
/etc/grub.d/00_header
```and after do a 
```
sudo update-grub
```because the /boot/grub/grub.cfg will be crushed by future update-grub command you can do.

Sorry for my english
snkkid

---

### Post by supremedalek on 2012-09-06
So, what does the recordfail test do?

I ask because I did apply the suggested change and noticed the grub menu is no longer being shown.

---

### Post by Aberanta on 2013-01-09
Thanks Jordang for the solution!!

And to complete it and preserve the changes after updates i've fount an alternative to the solution proposed by snkkid that i think is better because if you upgrade the grub package, the file "/etc/grub.d/00_header" can be overwritten.

Just edit the file "/etc/default/grub" and add a line like "GRUB_RECORDFAIL_TIMEOUT=10" (anything greater than 0), upgrading grub does not modify nothing and the problem is solved for ever :)

sorry for my english and happy new year :)

---

### Post by Lele83 on 2013-05-28
Or you can add  ```
GRUB_RECORDFAIL_TIMEOUT=1 
```
into ```
/etc/default/grub
``` and then regenerate the grub.cfg with 

```
sudo grub-mkconfig
```

Bye

> **jordang said:**
> A friend found a solution.

in grub.cfg
****
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1 
****
-1 should be 0 .

It works.

Now the only problem is that in case of kernel update, it will execute update-grub I think, which will overwrite this change. It is not that big problem.

Regards,
JG

---


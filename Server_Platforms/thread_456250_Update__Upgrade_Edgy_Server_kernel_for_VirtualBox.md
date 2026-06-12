---
title: "Update / Upgrade Edgy Server kernel for VirtualBox"
date: 2007-05-27
forum: Server Platforms
---

### Post by atwright on 2007-05-27
Hi,

I have just installed an Edgy Server guest in VirtualBox on a WinXP host OS. Upon booting the new system I get the error:```
"Unknown interrupt or fault at EIP 000000060 c0100295 00000294"
```
I searched Google and found this in the VirtualBox KB:```
http://www.virtualbox.org/ticket/110
```To summarise, it says this is a bug in Edgy and I need to upgrade / update the kernel to 2.6.19 or newer.

Given that I cannot get the system to boot, how would I change the kernel (I have the ISO to boot from but the recovery option seems to want me to reinstall the system).

All help gratefully received :)


Andy

---

### Post by atwright on 2007-05-27
Update:

I stopped being an idiot and followed through the rescue mode wizard. Got to the end, chose the first HDD (hd0?). Got to the terminal and typed:```
aptitude install linux-386
```

It has just finished installing and it fixed the problem!

So, for anyone trying to install Edgy (6.10) server in VirtualBox who receives the error:```
"Unknown interrupt or fault at EIP 000000060 c0100295 00000294"
```
[LIST=1]
[*]Boot from the CD
[*]Choose "Rescue broken system" (run through the wizard)
[*]When you reach the terminal type: ```
aptitude install linux-386
```
[*]Restart (I couldn't figure out how to do this as "sudo shutdown -r now" and "sudo halt now" didn't work...
[/LIST]

Source of this solution: [http://ubuntuforums.org/showthread.php?t=294712]("http://ubuntuforums.org/showthread.php?t=294712")

---


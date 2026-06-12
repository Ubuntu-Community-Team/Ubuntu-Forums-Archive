---
title: "Simultaneous OS boot by virtualization"
date: 2013-11-11
forum: Virtualisation
---

### Post by wolfgentleman on 2013-11-11
I have 2 hard drives: one with Linux, the other with Windows. I also  have 2 monitors. I want to use both of the OSes at the same time,  however that's not possible without 2 of everything or virtualization. I  had a thought but I do not know how to go about it. I thought that  maybe I could use a bare minimum Linux install with nothing but  something like VirtualBox and it's dependencies, and set it up to load  on the drives on the monitors as soon as it boots up. All that would be  needed would be a custom program that controlled the 2 instances,  handled the start up, shutdown, and reboot, and the resources the OSes  where allowed to use. I don't know how to do this though, so I was  wondering if there was an OS that has already been made for this and if  it was even probable on 4 gigs of RAM and 4 CPU cores without lag. I  wanted to do this so I didn't have to reboot 2 or more times per day  just to play my game for an hour and when I need to do something that is  only available through Windows then go back to Linux. If everything  that I do worked on Linux whether it be through wine or otherwise I  would never look back on Windows, but unfortunately I can't. Any and all  solutions and suggestions are welcome and appreciated.

---

### Post by TheFu on 2013-11-12
Whatever OS has the gaming needs to be your "hostOS" for virtualization. Usually that is Windows. This assumes that "games" need lots of direct hardware access to the GPU. If you are running chess or word games, then your hostOS can be anything you like. FPS games and you probably want the actual OS.

Then install whatever VM tool you like - virtualbox, vmware-player, vmware-workstation, etc .... and load Ubuntu into a virtual machine (ClientOS) running under the "hostOS."  

High-end graphics does not work well on virtualized installations. Inside the virtual machine, only virtual devices are provided ... these have little to do with the actual hardware inside the PC case. Your video card DO NOT MATTER to the clientOS.

WINE does not support every Windows program though it might support all the programs that you care able. This is highly unlikely, however. Check over at winehq.com .

You do not want to run 3 OSes just to have access to 2 OSes.
```
HW
|____Windows (runs on the real hardware)
|    |____Ubuntu
|    |____Banking VM (TinyCore)
|    |____20-other-client-OSes
```
Ask if this is not clear.

---

### Post by wolfgentleman on 2013-11-19
Well, the whole reason I was trying to get this working is because A) Tera Online does not work in Wine, I tried using PlayOnLinux and one of the admins said it was "broken" and he has no plans to fix it. and B) I have an old Lexmark printer, pre-Linux driver support, that I use for scanning and everything I have found on the model says there is no way to use it. So I was hoping that this would work...... I guess I continue to reboot to play my game and scan... I had to get rid of the other monitor anyway because I got a new snake and it was going out, so I would have eventually had to go back to doing it this way. Thanks for the explanation....

---

### Post by TheFu on 2013-11-20
So, I would run Windows directly on the hardware and use Virtualbox (or similar) to run Ubuntu and 20 other ClientOSes inside virtual machines.  No need to reboot to scan or play a game.

Not sure what a snake has to do with this at all.

---


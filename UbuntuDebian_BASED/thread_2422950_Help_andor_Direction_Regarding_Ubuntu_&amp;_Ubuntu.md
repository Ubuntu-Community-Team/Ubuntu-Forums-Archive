---
title: "Help and/or Direction Regarding Ubuntu &amp; Ubuntu-based Install"
date: 2019-07-15
forum: Ubuntu/Debian BASED
---

### Post by tf4545 on 2019-07-15
[COLOR=#1A1A1B][FONT=&amp]Hey Folks,
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Due to unforeseen circumstances, I just bought a new HP machine from a local store and rather than booting into Windows 10 I wanted to just install POP!_OS from System76 right from the first power-up rather than run Win 10. Don't like it, don't need it!
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]After shutting off Secure Boot and booting from my newly burnt USB drive into POP!_OS 19.04 I saw that I had no wireless. As in no wireless recognized at all. Wireless is not even an option in the the Setting panel. I figured I could just use a wired connection, do the install then take care of what driver issue(s) were the culprit but alas, plugging in my rarely used network cable, I still didn't have a connection via the plugged in connection. I could see the wired connection in Settings but it said it was only 1000mbs which is way low for what my service gives me and couldn't connect to anything using Firefox[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]
So, after re-installing Win 10, last night I posted my woes on the POP Reddit hoping to get some direction. No answers there thus far so I thought I would give the Ubuntu Forums a try as I also tried Ubuntu 19.04 with the same results. 

Here is some info regarding the machine:
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]HP 15-dw00[/FONT][/COLOR][COLOR=#1A1A1B]34n[/COLOR][COLOR=#1A1A1B][FONT=&amp]r 15.6" Laptop[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Wireless Card - RTL8821CE[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Ethernet Card - Listed as PCIe GbE Family Controller
Intel 8th Gen i7-8565U
8GB DDR4-2400 RAM
256GB Solid State Drive
Intel 620 Graphics
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Wireless and wired connections run flawlessly on Win 10.
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]So, am I correct in thinking that this is a driver and/or kernel issue? Is there anything I can do to get Linux running on my machine?
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Also, in trying to install Linux, I tried Ubuntu 19.04, Linux Mint 19.1 Cinnamon, Manjaro 18.0.4 Gnome, as well as elementary OS and all had the same results across all five distros.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Lastly, I also noticed that the screen brightness functions keys did not work but that isn't a deal-breaker and I've remedied such annoyances in the past.
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Many thanks in advance for any and all help and/or direction![/FONT][/COLOR]

---

### Post by oldfred on 2019-07-15
Moved to otherOS since not Ubuntu.
Do not know details of what [COLOR=#1A1A1B][FONT=&amp]POP!_OS has changed.

HP also has some issues.
Have you updated UEFI. Some of issues are resolved with UEFI update.
If SSD have you updated firmware?

[/FONT][/COLOR]        HP Pavilion Gaming Laptop 15 -cx0049nr Disable Optane memory
[https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved](https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved) 
            HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work
[https://ubuntuforums.org/showthread.php?t=2390309](https://ubuntuforums.org/showthread.php?t=2390309) 
            See last post for many boot parameters, still using UEFI, not Legacy
[https://ubuntuforums.org/showthread.php?t=2407615](https://ubuntuforums.org/showthread.php?t=2407615)&
[https://ubuntuforums.org/showthread.php?t=2406993](https://ubuntuforums.org/showthread.php?t=2406993) 
    
[COLOR=#1A1A1B][FONT=&amp][/FONT][/COLOR]

---

### Post by TheFu on 2019-07-15
1000mbs probably **is**  1000 Mbps - which is GigE.  Network and disk speeds are always stated in Mbps in the commercial world.  Some software shows "MBps", which would be 8x smaller for the same speed - 125 MBps.

I know nothing about PopOS and know nothing about 19.04.  Sorry.

You can use this command to post data about the network hardware and drivers being automatically setup. That would help people to help you.
**sudo lshw -C network**

---

### Post by tf4545 on 2019-07-15
Problem solved! After a fair amount of research into the cause of the networking issues when trying to install POP!_OS (this is also an issue with Ubuntu 19.04 and 18.04), I took the 18 hour old HP machine back to the retailer, got a full refund, and bought a Dell machine which accepted POP after turning off Secure Boot and switching the drive settings from RAID to AHCI.

So, a change in machines was the ticket for me!

Thanks for the help/direction!

---


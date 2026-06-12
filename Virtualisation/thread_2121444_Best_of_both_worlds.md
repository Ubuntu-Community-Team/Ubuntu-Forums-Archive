---
title: "Best of both worlds?"
date: 2013-03-01
forum: Virtualisation
---

### Post by EricG1793 on 2013-03-01
I installed Windows 8 and later Windows 7 on VirtualBox with Ubuntu 12.10 as the host.

I'm pleased with VirtualBox because Guest Additions makes it easy to get Windows Aero working. I also think it's more aesthetically pleasing, there are most options to configure the machine, and it seems to run better in general. However, most annoyingly, I couldn't get USB devices to connect  to the VM; with the device connected, if I went to add a filter, there were no devices detected. Copying between host and guest wouldn't work. I am continually annoyed switching between host and guest because I click minimize for the VM, it minimizes for an instant then comes back, then I have to click minize again, and it stays down. However, the Launcher disappears (as well as the "taskbar" at the top of the screen, not sure what Ubuntu calls it), so I have to click over there to get it to reappear. When I restore the VM, the display is blacked out, and I have to run my mouse over the entire surface to "wipe off" the VM (or open a program full-screen). Kinda like erasing everything in Paint. (I thought only having 3 GB physically on the host system was the issue and now have 8 GB, no difference.) Then, last week, my Windows 8 started losing its network connection (it always used NAT). I switched to Bridged, thinking that that would solve some of the issues I'd been having with the VM not having its own IP address at the same time. This worked at home, and at another house, but not at work. It stopped working at home after a couple days.

Fed up, I installed a fresh installation of Windows 7 today. Same issues. However, bridged adapter won't work at home, either! Only NAT.

Even more fed up, I installed VMware Player. I was pleased at first. I still have to click minimize twice to make it minimize, however, the Launcher doesn't disappear, and there is no "wiping off" the VM upon maximizing it. My flash drive easily connects to it. However, bridged adapter still won't work, but NAT does. Also, now, I am unable to get Aero working, even though the WDDM(?) driver is installed (as confirmed in Device Manager)! I cannot tell it to just use Aero in the personalization menu, or the performance options System.

It seems like VMware would be easier to get working correctly -- any ideas are appreciated! Or tips for another program that will just work....

---

### Post by TheFu on 2013-03-02
Use 12.04, not 12.10.

---

### Post by EricG1793 on 2013-03-02
Which of these issues will that solve?

---

### Post by TheFu on 2013-03-02
> **EricG1793 said:**
> Which of these issues will that solve?

I don't know, but I do know that 12.10 seems to have more issues than any LTS release because they are concentrating on complex new features that might not quite be completely ready.  That is the nature of non-LTS releases.

I also know that virtualbox on 12.04 works and works well for desktop-on-desktop VMs, provided to follow the standard rules for VMs. These are not always the defaults, sadly.
[http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) explains more.

---

### Post by EricG1793 on 2013-03-04
Did a clean install of 12.04 and the VM with Virtualbox. I had read about the vboxusers thing when it came to USB. I finally stumbled across an article that actually explained how the heck to do that, and how USB works. No more double-minimizing. I think the black screen upon returning to VM might be OK, too. However, no bidirectional clipboard, and same problem bridging adapter. NAT works.

---


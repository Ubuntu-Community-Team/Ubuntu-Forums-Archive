---
title: "VirtualBox problems (mouse clicks stop working sometimes), considering alternative"
date: 2018-07-09
forum: Virtualisation
---

### Post by mikeymikec on 2018-07-09
I'm running 18.04 LTS, and while I have many smatterings of Linux experience over the years, I think I'm still a newbie.  I migrated from Win7 about a month ago.

While using a virtual machine, sometimes both mouse buttons stop working.  The pointer can move around the screen, but clicking does nothing.  It affects the host as well as the VM, and the only solution I've found to mostly work is to switch to a console (ctrl+alt+F1), then steadily switch consoles back to X.  However, on occasion this solution doesn't work and I'm left with a flashing cursor in the top-left corner and not being able to switch to a console.  Lubuntu installed the Linux AMD GPU driver.  System is set up with UEFI but with secure boot disabled.

I considered changing to another piece of virtual machine software, but my attempts to install VMware failed after the initial installation of the software when it wanted to run first-time configuration and was failing to install a monitor driver.  I researched solutions for that but they mostly revolved around 'disable secure boot' even though Win10 already says that secure boot is disabled (I relegated Windows to the role of gaming OS, dual-booting with Lubuntu as the primary).

The virtualbox issue isn't VM specific, I'm pretty sure I've had it with both my XP VM and a Lubuntu VM that I was using for testing.  Both VMs pre-date the Lubuntu installation as my primary OS (I told virtualbox to export the VMs then re-imported them under Lubuntu).

So I guess I'm either asking for a recommendation for virtual machine software to replace virtualbox or ideas for how to fix the virtualbox issue please!

---

### Post by TheFu on 2018-07-09
Only have 1 hypervisor installed on a physical machine at a time.  If you uninstall 1 and reinstall another, be certain to reboot between to clean up kernel modules.  It is possible to make these work on the same system, but manual steps are necessary.

I've been using KVM + libvirt + virt-manager since 2010.  Switched away from VMware ESXi and Virtualbox.  Never regretted the decision. virt-manager works locally and remotely over a built-in ssh tunnel. No VM solution works well with GPU-heavy DEs, so use XFCE, LXDE, or Mate as the DE. Avoid Unity, KDE, or Gnome3.  The heavier DEs might work on a local-only setup. I've never tried that.  Basically, I always use remote connections.

I never install guest OSes with UEFI.  Always use legacy BIOS.

I have never installed 18.04 on any physical machine.  Maybe next year, after it has some time to prove is it a great OS.  My primary VM server runs 14.04 and 2 others are running 16.04.

"New" is the enemy of "stable."

---

### Post by mikeymikec on 2018-07-20
For the record, with regard to the Virtualbox problem I've found that pressing the 'escape' key (default being Right-Ctrl) a few times is enough to get the mouse buttons working again.

---

### Post by mrsmith31012 on 2018-11-07
Just if anyone still has this problem:

I have installed lubuntu 18.04.1 as host with virtualbox version 5.2.10_Ubuntu r121806

I experience the same problem as [COLOR=#000000]mikeymikec which means that if I start my Windows 10 guest OR Ubuntu 18.04.1 guest I lose mouse control within a random time between 5 to 15 minutes.
The cursor is still moving but both buttons stop working. The buttons are also not working at the host side which makes this bug really annoying.

In order to solve this problem I searched through a bunch of forums and sites bot did not found a really good solution. Until now.

Here is a listing of workarounds which do work at my machine:

1. Switch to a terminal and kill virtualbox -> obviously not what we want.
2. Press your Host Key (which is right ctrl if not changed) + f --> this will switch the VM into fullscreen. Press the combo again and your mouse clicks should work. (just pressing the Host Key as mentioned by [/COLOR][COLOR=#000000]mikeymikec did not do the trick for me)[/COLOR]
[COLOR=#000000]This works pretty good but is super annoying to switch between fullscreen and windowed VM every ~10 minutes just to be able to control your machine again.
3. Everytime you boot your VM click "Input -> Mouse Integration" at the menu bar. This will disable mouse integration for this VM. It solves the problem, but now you have to press your Host Key to exit the controls of your VM.
Works every-time but is not really a "solution"

4. And currently the best solution in my opinion: Go into the preferences of your VirtualBox Manager. Click on "Input" and make sure that "Auto Capture Keyboard" is not selected for "VirtualBox Manager" and "Virtual Machine". Click on OK -> finish
This was the only solution which really solved the problem for me. I'm not quite sure what "Auto Capture Keyboard" really does because if I move my mouse into the VM window my keyboard is hooked to the VM anyways. Maybe I don't understand this feature.

I hope I could help anyone who has this kind of problem in the future.
Cheers ;)[/COLOR]

---

### Post by heiko_s on 2018-11-07
> **mikeymikec said:**
> I'm running 18.04 LTS,... I considered changing to another piece of virtual machine software, but my attempts to install VMware failed...
So I guess I'm either asking for a recommendation for virtual machine software to replace virtualbox or ideas for how to fix the virtualbox issue please!

I can't help with VirtualBox, but perhaps "another virtual machine software".

As TheFu pointed out earlier, you might want to use kvm as hypervisor and run your Windows machine on kvm (Kernel Virtual Machine). This is right now the best option in terms of hardware compatibility and performance.

However, your hardware (CPU and motherboard) must support IOMMU, which in Intel terminology is VT-d and AMD calls it AMD-v or so. It also needs to be enabled in the BIOS of your motherboard (by default, most m/b manufacturers disable it). It is also helpful to own a modern GPU with UEFI graphics card BIOS that you can pass through to Windows.

Using kvm and a dedicated GPU, you can actually create a Windows VM that performs like Windows installed on bare metal. This is perfect for gaming, video and photo editing (i.e. GPU and/or CPU heavy stuff).

My Windows 10 VM performs to within 96-100% of the performance I can get when Windows is installed directly on my hardware. I'm doing this for the last 6 years and have never ever thought of returning to dual-boot. There are lots of tutorials on the web. I prefer a bash script to start the VM, and have written tutorials on that. See [https://ubuntuforums.org/showthread.php?t=2405522]("https://ubuntuforums.org/showthread.php?t=2405522").

---

### Post by heiko_s on 2018-11-07
> **TheFu said:**
> ...I've been using KVM + libvirt + virt-manager since 2010.  Switched away from VMware ESXi and Virtualbox.  Never regretted the decision. virt-manager works locally and remotely over a built-in ssh tunnel. No VM solution works well with GPU-heavy DEs, so use XFCE, LXDE, or Mate as the DE. Avoid Unity, KDE, or Gnome3.  The heavier DEs might work on a local-only setup. I've never tried that.  Basically, I always use remote connections.

I never install guest OSes with UEFI.  Always use legacy BIOS.

I have never installed 18.04 on any physical machine.  Maybe next year, after it has some time to prove is it a great OS.  My primary VM server runs 14.04 and 2 others are running 16.04.

"New" is the enemy of "stable."

When you use KVM, it is actually better to use UEFI for the VM if your graphics card supports it - see [Intel IGD and arbitration bug]("https://heiko-sieger.info/running-windows-10-on-linux-using-kvm-with-vga-passthrough/#Intel_IGD_and_arbitration_bug") (my summary).

I've tried virt-manager several times and regretted it every time. The last time (August 2018) I spent a week installing and re-installing a Windows 10 VM to get the performance I am used to. Mind you, it wasn't such a problem to get the Windows VM up and running, but performance kinda sucked. Eventually I got it working more or less, but the hassle of using a GUI and then having to edit the resulting xml config file using some antiquated editor (vim or so) really put me off.

@TheFu: I assume you are a moderator? Perhaps you could update the sticky "The Virtualization Mega-Thread" - it is kind of ancient. There is more up-to-date information on the web (see also my website, which has plenty of links to other sources too). I'd be glad to help out if needed.

Edit: I would usually subscribe to your "New" is the enemy of "stable" phrase, but Ubuntu 18.04 and the newer qemu 2.11 does bring some improvements. Let alone virt-manager, which greatly improved despite my bashing it once again.

---

### Post by kukat on 2018-11-08
Can you type "top" on a console when you have this problem, and share with us a snapshot?

---

### Post by dvdtree on 2019-02-23
Hi, 				 				 					 						 	[**[COLOR=#000000]mrsmith31012,[/COLOR]**]("https://ubuntuforums.org/member.php?u=2111243") I have the exact same problem here (VBox 5.2.1_Ubuntu r123745 on lubuntu 18.04, Win10 guest).
Thanks for the workarounds I'll try to use them.
Until now, as a workaround, I used to add the USB key of another wireless mouse (doesn't matter if the extra mouse is on or off). This operation immediately un-freezes the mouse buttons.
Regards,
David

---

### Post by lammert-nijhof on 2019-03-05
Download the lastest Virtualbox version 6.04 from the Virtualbox web site and your problem will very probably be solved. Ubuntu provides you with a really old version of Virtualbox with 5.2.10. The latest 5;2 version is 5.2.26 and they have an even newer version with 6.04 that I use without problems.
Don't try QEMU/KVM since Microsoft will often block the activation of Windows. In Virtualbox you can activate Windows in the VM, if your VM runs on the original machine with e.g. the Microsoft activation code sticker.

---

### Post by mcba on 2019-04-21
I've found that pressing the Windows logo key ("winkey") on the keyboard restores the mouse clicking for me. This seems to have the same effect as pressing Gnome's "Activities" button (although without a working mouse click, you can't do that directly).

The issue only started for me with Ubuntu 18.04LTS running in Virtualbox under Windows 10. Earlier versions of Ubuntu worked fine. Upgrading to Virtualbox 5.2.26 didn't help.

---

### Post by onlinecoderwtf on 2019-07-14
> **mrsmith31012 said:**
> Just if anyone still has this problem:

I have installed lubuntu 18.04.1 as host with virtualbox version 5.2.10_Ubuntu r121806

I experience the same problem as [COLOR=#000000]mikeymikec which means that if I start my Windows 10 guest OR Ubuntu 18.04.1 guest I lose mouse control within a random time between 5 to 15 minutes.
The cursor is still moving but both buttons stop working. The buttons are also not working at the host side which makes this bug really annoying.

In order to solve this problem I searched through a bunch of forums and sites bot did not found a really good solution. Until now.

Here is a listing of workarounds which do work at my machine:

1. Switch to a terminal and kill virtualbox -> obviously not what we want.
2. Press your Host Key (which is right ctrl if not changed) + f --> this will switch the VM into fullscreen. Press the combo again and your mouse clicks should work. (just pressing the Host Key as mentioned by [/COLOR][COLOR=#000000]mikeymikec did not do the trick for me)[/COLOR]
[COLOR=#000000]This works pretty good but is super annoying to switch between fullscreen and windowed VM every ~10 minutes just to be able to control your machine again.
3. Everytime you boot your VM click "Input -> Mouse Integration" at the menu bar. This will disable mouse integration for this VM. It solves the problem, but now you have to press your Host Key to exit the controls of your VM.
Works every-time but is not really a "solution"

4. And currently the best solution in my opinion: Go into the preferences of your VirtualBox Manager. Click on "Input" and make sure that "Auto Capture Keyboard" is not selected for "VirtualBox Manager" and "Virtual Machine". Click on OK -> finish
This was the only solution which really solved the problem for me. I'm not quite sure what "Auto Capture Keyboard" really does because if I move my mouse into the VM window my keyboard is hooked to the VM anyways. Maybe I don't understand this feature.

I hope I could help anyone who has this kind of problem in the future.
Cheers ;)[/COLOR]

My case:
1. Ubuntu 18.04 with all updates.
2. Oracle Virtual Box 6.0.8 r130520
3. VirtualBox Extension Pack
4. Lenovo 520-IKB
5. Windows 10 guest.
6. Guest Additions installed
Still having trouble with mouse lock. 
1. After disabling [COLOR=#000000]"Auto Capture Keyboard" everything is fine!
Thank you! :)[/COLOR]

---


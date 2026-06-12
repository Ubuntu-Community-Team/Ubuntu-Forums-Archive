---
title: "VirtualBox guest OS (Windows XP) does not recognise USB"
date: 2011-06-19
forum: Virtualisation
---

### Post by Paddy Landau on 2011-06-19
I have gone through these forums to solve my problem, with no success.

I have the latest version of PUEL VirtualBox (4.0.8 downloaded directly from the [VirtualBox website]("http://www.virtualbox.org/")) with guest extensions, running on Ubuntu 10.04 64-bit. My user is a member of vboxusers.

The guest OS is Windows XP SP3 with all updates (except .NET Framework 1.1 SP1, which fails to install for reasons unknown). Guest Additions are installed (I know this because the mouse integration and full-screen both work, and the Oracle Guest Additions icon shows in the Windows task bar).

In the USB settings, I have enabled the USB controller and the USB 2.0 (EHCI) controller, and added a filter to accept any USB device.

[LIST=1]
[*]I start the guest machine (Windows XP).
[*]I select (tick) the USB device -- a simple USB stick formatted as FAT32 -- from the Devices menu.
[*]The USB stick automatically unmounts from Ubuntu.
[*]However, Windows does not see the USB stick; it does not show the expected "installing new device" pop-up that Windows does with new USB devices; it does not show up on the list of drives.
[*]If I untick the USB stick from the Devices menu, it automatically remounts in Ubuntu.
[/LIST]
I have tried this with two different sticks in case one of the sticks was at fault, but I get the same results. I know at least one of the sticks works with Windows, because I use it to transfer files to another Windows XP computer.

I am completely stumped as to how to solve this. Please help.

Thank you.

---

### Post by Paddy Landau on 2011-06-22
I've asked [this question on AskUbuntu]("http://askubuntu.com/questions/50022/guest-os-cannot-see-usb-even-after-selecting-it-in-virtualbox"). I hope someone can give me a solution.

---

### Post by BrandonC19 on 2011-06-22
I had the same problem, and here's how I fixed it. 
1>Go to System>Administration>Users and Groups
2>Click "Manage Groups"
3>Scroll down to find the group "vboxusers"
4>Click the checkmark beside your username.
5>Logout or reboot. 
You can now access the flash drive by clicking the USB icon at the bottom of the VM window and selecting your USB stick.
Hope this helps!:)

---

### Post by Paddy Landau on 2011-06-22
> **BrandonC19 said:**
> I had the same problem, and here's how I fixed it...
Thanks, Brandon, but:
> **Paddy Landau said:**
> My user is a member of vboxusers.
I've already done this. :(

---

### Post by Paddy Landau on 2011-06-24
I found the problem. Windows did not have the drivers installed for the USB.

The solution was simple. In the Windows guest OS, go to Control Panel > System > Hardware. The USB is shown with a yellow question mark. Right-click and install drivers (you need an Internet connection).

---

### Post by Gotit on 2011-07-23
> **Paddy Landau said:**
> I found the problem. Windows did not have the drivers installed for the USB.

The solution was simple. In the Windows guest OS, go to Control Panel > System > Hardware. The USB is shown with a yellow question mark. Right-click and install drivers (you need an Internet connection).

Yep, that was my problem too.  Thanks, Paddy!!

---


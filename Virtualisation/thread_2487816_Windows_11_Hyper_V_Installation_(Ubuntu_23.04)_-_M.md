---
title: "Windows 11 Hyper V Installation (Ubuntu 23.04) - Mouse Not Captured"
date: 2023-06-15
forum: Virtualisation
---

### Post by ckrafcky on 2023-06-15
Recently installed Ubuntu v 23.04 via Hyper V on Windows 11 64bit. The installation goes smoothly, and the guest is restarted.  Once restarted, I am able to login.  Once logged in, the mouse stops working.  Looking at the lower right hand corner of the 'RDP' window, I noticed it says 'Mouse Not Captured'.  Doing my research, I have seen people disable 'Enhanced Session Mode' - Didn't work, Run sudo apt upgrade - After all upgrades completed, mouse still doesn't work, Open VMConnect with the attempt to save my settings in the 'Options' area - Options are not available, so this doesn't work, Attempting to update the kernel via the text area - Appears to work, but the mouse is still not being captured.  I use a Logitech MX Master 3S wireless mouse connected via Bolt receiver (No firmware updates are available).

---

### Post by MAFoElffen on 2023-06-15
<< This should be moved to the Virtualization Section >>

Let me boot as Windows > Hyper-V and look at this... Be right back.

---

### Post by MAFoElffen on 2023-06-16
It is not an Ubuntu 23.04 thing, it's actually a Hyper-V / RDP thing...

Yes. On some VM's in Hyper-V, when viewing the VM with RDP, which the Hyper-V VM viewer uses that protocol when on a Windows OS, it sometimes get an error where it pops up a dialog box saying that it couldn't capture the mouse... This is a problem with Hyper-V's RDP enchanced session and what used to be referred to as their VM Guest integration services.

Basically, you either disable the enhanced session for the VM, or if you need to use the enhanced abilities given by the 'enhanced session', you physically pass-through the USB mouse as a shared, local (remote to the VM Guest) device in the RDP Session...

Do you need instructions to do either of those?

---

### Post by ckrafcky on 2023-06-18
Hi - 

I ended up removing version 23.04 and installing version 22.02 LTS instead.  This seems to have fixed my mouse issue.  Just a side note, before I rolled back, I tried to get the mouse to work with disabling Enhanced Session as well as enabling Enhanced Session.  Both times I still experienced the same issue.

---

### Post by klaus-burgundia on 2023-08-06
I found [this]("https://c-nergy.be/blog/?p=18902") page which shows how a 23.04 server can easily be turned into a "desktop" version. I just tried it on Windows Server 2019 HyperV, and I can confirm that it is working.

```
sudo apt -y install ubuntu-desktop

sudo apt -y install gnome-panel gnome-settings-daemon metacity nautilus gnome-terminal
```

I say "desktop" as it's not 100% identical to the real desktop version - but at least it's running.

---


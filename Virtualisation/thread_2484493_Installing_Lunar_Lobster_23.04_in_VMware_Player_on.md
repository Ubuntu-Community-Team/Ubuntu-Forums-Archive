---
title: "Installing Lunar Lobster 23.04 in VMware Player on Ubuntu 22.04"
date: 2023-02-28
forum: Virtualisation
---

### Post by brendan7707 on 2023-02-28
My BaseOS is Ubuntu 22.04 with VMware Player 17.0.1 installed.  I've installed many Linux variants over the years (and Windows) as VMs.  So, I'm familiar with the installation sequence of Ubuntu booting as a VM and then having the Ubuntu GUI install asking: Select keyboard, Download updates, Installation type (erase disk), Time Zone, User/pass, etc.  Even with an SSD it takes a few (5?) minutes.  Fine.

I've downloaded the Lunar Lobster 23.04 daily build, 2023-2-16.  VMware detects the ISO as 23.04.  Then VMware (not the Ubuntu GUI) asks me for the user/pass.  The Ubuntu boots but there is no guided install GUI.  The GUI login screen pops up quicker that with the 22.04 install for comparison.  The user/pass I entered don't work.  I pulled up a terminal and the login fails there too.

In searching with Google, I've not come across much.  I did see that with VirtualBox, there was a suggestion to use 'changeme' as the password.  Pretty thin info out there for VMware.

Any help?  And, TY.

---

### Post by slickymaster on 2023-02-28
Thread moved to **Virtualisation** for a better fit

---

### Post by MAFoElffen on 2023-02-28
If the Lock Screen comes up (during a timeout in the Live Session), the Live Session Lock Screen dialog says "Live Session User"... There is no password set for this user. Just press the <Enter> key.

Note that the installer for the daily is broken right now. ([https://ubuntuforums.org/showthread.php?t=2484409](https://ubuntuforums.org/showthread.php?t=2484409)) It goes in an infinite loop. So use an earlier "daily" build.  

I don't know when they updated the UI, but the initial Try / Install screen used to be too large (and the buttons where almost off the screen), where you had to get rid of that first screen, then restart the installer for the graphics to work right. That has since been changed / updated...

---

### Post by ActionParsnip on 2023-03-03
Are there any bugs reported for this?

---

### Post by MAFoElffen on 2023-03-03
Update: Just tested Lunar Desktop Daily Build ISO 220230303. Working great.

---

### Post by ActionParsnip on 2023-03-03
Pretty standard. Prereleases are not for production or casual users. They are for people who want to submit bug reports to help get the release ready. If you need an OS that works then I suggest you use the latest LTS. You'll have a better experience. Jammy (the current latest LTS) is also supported long after Lunar is end of life (EOL)

---

### Post by guiverc on 2023-03-03
You've not said what Ubuntu *lunar* (23.04) ISO you were using; only gave a date (20230216)

A quick look at what's available [http://iso.qa.ubuntu.com/qatracker/milestones/441/builds](http://iso.qa.ubuntu.com/qatracker/milestones/441/builds) & I see no desktop ISO that old (*and there are two desktop ISOs with different installers*), but I see a number of 0216 dated Server ISOs using the `subiquity` installer (*five are listed* *with that date*).

Given the date of that ISO (Feb 16) why try and use it?  Sorry I'm a desktop user (*almost exclusively*) and thus don't even try and keep up with server issues on *dailies*, but the date to me is a huge clue (*contrast the dates of ISOs with other builds on the iso tracker link I provided!*).

I suggest being specific as to build/architecture etc.

---

### Post by mlharmon on 2023-04-20
> **brendan7707 said:**
> My BaseOS is Ubuntu 22.04 with VMware Player 17.0.1 installed.  I've installed many Linux variants over the years (and Windows) as VMs.  So, I'm familiar with the installation sequence of Ubuntu booting as a VM and then having the Ubuntu GUI install asking: Select keyboard, Download updates, Installation type (erase disk), Time Zone, User/pass, etc.  Even with an SSD it takes a few (5?) minutes.  Fine.

I've downloaded the Lunar Lobster 23.04 daily build, 2023-2-16.  VMware detects the ISO as 23.04.  Then VMware (not the Ubuntu GUI) asks me for the user/pass.  The Ubuntu boots but there is no guided install GUI.  The GUI login screen pops up quicker that with the 22.04 install for comparison.  The user/pass I entered don't work.  I pulled up a terminal and the login fails there too.

In searching with Google, I've not come across much.  I did see that with VirtualBox, there was a suggestion to use 'changeme' as the password.  Pretty thin info out there for VMware.

Any help?  And, TY.

I experienced this issue myself just now and I resolved it by not allowing VMWare Player to use "Easy Install" and instead chose "I'll install the OS Later" prompt.  I went into the VM settings then and chose/verified the options and started the VM.  I was able to then choose the "Try/Install" option and the install completed successfully.

Mark

---

### Post by jlynde on 2023-04-24
> **MAFoElffen said:**
> If the Lock Screen comes up (during a timeout in the Live Session), the Live Session Lock Screen dialog says "Live Session User"... There is no password set for this user. Just press the <Enter> key.

Note that the installer for the daily is broken right now. ([https://ubuntuforums.org/showthread.php?t=2484409](https://ubuntuforums.org/showthread.php?t=2484409)) It goes in an infinite loop. So use an earlier "daily" build.  

I don't know when they updated the UI, but the initial Try / Install screen used to be too large (and the buttons where almost off the screen), where you had to get rid of that first screen, then restart the installer for the graphics to work right. That has since been changed / updated...

I downloaded the Live ISO image last night.  Right now I am at the login prompt (it timed out) and I tried just hitting enter but it says: "Unlocking failed".  Has something changed?  Is there a password now?  Oh, I just realized that this is a VMWare virtualization thread.  I just used a USB Thumb drive.  But if you know the answer, please reply.

---


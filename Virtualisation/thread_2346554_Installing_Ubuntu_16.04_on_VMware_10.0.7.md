---
title: "Installing Ubuntu 16.04 on VMware 10.0.7"
date: 2016-12-16
forum: Virtualisation
---

### Post by troubadoor on 2016-12-16
Hello!
I am trying to install Ubuntu 16.04.1 on VMware workstation 10.0.7, but I am having a problem with screen resolution. I've been installing Ubuntu on VMware the same way since 10.04 and it always went smooth. If I use 16.04's mini.iso, also everything goes OK (it's not a graphic mode installation). But with the official 16.04.1 desktop CD the following happens:
- when it comes to question "Where are you?", I click continue
- it then asks for Keyboard layout, which I change to English (US)/English (US)
The problem starts here: the Ubuntu's screen is suddenly extended to the right and not shown entirely in the default 640x480 VMware's window. I cannot see the buttons on the right lower part of the Ubuntu's screen, only the part of the first button is visible (without button label). If I click (blindly) this first (unknown) button, the whole process returns to question "Where are you?". From there on I cannot click anything else - Ubuntu's screen remain extended and buttons are inaccessible somewhere on the right.

Why would installation change internal screen resolution in the middle of installation if nothing else changed? What can I do to convince installation the screen resolution is still the one it started with (in this case VMware's default VGA 640x480)?

PS: I just tried the same installation on the latest version of VMware Workstation (12.5.2) and it behaves the same.

---

### Post by howefield on 2016-12-16
Thread moved to the "*Virtualisation*" forum.

---

### Post by efflandt on 2017-01-12
Something is just strange about 16.04.1 and I have not been able to figure out what. I could not install it directly on my desktop PC because when rebooting (warm or cold) it would totally blank out my legacy BIOS splash screen, grub menu, and plymouth (screen totally black until gui login). It ran fine, just major blank screen boot issue.

32-bit 16.04.1 worked fine in virtualbox in 64-bit 14.04 host. But because I had troubles with 16.04, I am now running 64-bit 16.10. In that when I try to install 32-bit 16.04.1 into virtualbox (whether from repos or Oracle) it goes to an odd size window and the graphics get all scrambled (subject for a separate post). But 32-bit 14.04 works fine in vbox in 64-bit 16.10 host. So I am in the process of downloading 32-bit 16.10 to see how that works. The only thing I need 32-bit for is 32-bit only Linux WebEx which needs 32-bit Java and browser.

Good luck.

PS: I discovered that the scrambled graphics for 16.04 live/install in VirtualBox can be fixed by using Host+F1 (to go to text console) then Host+F7 to go back to X. Then after rebooting the new system install VirtualBox guest extensions. In vbox the **Host** key is **right-Ctrl**. I don't know what the Host key is in VMware or whether switching to text console and back will also help you. In vbox it changed it from something like a 1184x400 window with scrambled graphics to a large enough 4:3 window to get at the buttons during install. Although, I successfully used an old computer that reverted to 640x480 VGA graphics to do a regular (not virtual) install on a drive that I was going to use on another computer, by dragging the install window over enough to get at the buttons.

---


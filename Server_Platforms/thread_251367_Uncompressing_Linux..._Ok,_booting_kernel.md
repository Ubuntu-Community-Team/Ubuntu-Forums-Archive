---
title: "Uncompressing Linux... Ok, booting kernel"
date: 2006-09-05
forum: Server Platforms
---

### Post by phyberoptix on 2006-09-05
Hi and thank you for reading this.

I have just finished a fresh install of 6.06 server on a Dell D600 laptop, and on boot the system appears to stop at

[FONT="Courier New"]Uncompressing Linux... Ok, booting the kernel.[/FONT]

Can anyone give me a little guidance here?](*,) 

Thank you

---

### Post by alecjw on 2006-09-05
I get that on edgy testing. In the grub menu (just press esc when it prompts you), there should be 2 of the one which you usually select. Choose the second one.
Never quite understood what it meant by that message. Think it must be something like "Uncomprssing linux. OK then, I'll stop speaking geek: Loading the kernel"

---

### Post by phyberoptix on 2006-09-05
Tried that too (recovery mode) and it stops in the exact same spot...

---

### Post by Argyle on 2006-09-12
Is there still no resolution to this?

---

### Post by icyisamu on 2006-09-13
Are you using the Server cd?

The following is taken from Vmware forums, but it should work nonetheless.

1. Leave ur partition untouched and boot the Server cd. At the selection, choose "Rescue a broken system."

2. Follow the instructions. You will eventually reach a section with a couple of items. 

Choose "execute a shell in /dev/discs/disco/part1" . It may look different on your system.

3. You will be given shell access.

4. Type "sudo apt-get install linux-686". You need an internet connection to do this.

5. Let it install.

6. Once installation is successful, type exit and press enter. Now choose to reboot the system. At grub or lilo, it should use the new 686 kernel.

NOTES:
I had to install the kernel twice before it worked - it installed an earlier version of kernel for the first time. So verify the version of the kernel before installing. Maybe do a "sudo apt-get update" first.

---


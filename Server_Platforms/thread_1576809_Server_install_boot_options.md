---
title: "Server install boot options"
date: 2010-09-17
forum: Server Platforms
---

### Post by memilanuk on 2010-09-17
Hello,

I'm curious about the boot options during the server install immediately following selecting the language.  The ones labeled 'F1, F2,...F6' at the bottom of the screen.  I can't seem to find any usable information in the official documentation, and what I can find in the community docs seems to apply to the desktop live cd version, as the options are different from what I'm seeing when booting from the server install cd.

Specifically, the option 'F4 Modes' used to be for selecting graphics modes, but now contains options 'Normal', 'OEM Install', 'Install minimal system', and 'Install minimal virtual machine'.  And 'F6 Boot Options' used to contain various parameters for booting with funky hardware... it still does, but has two other options 'Expert' and 'Free Software Only' which are similarly unexplained as to what exactly they do.

Where can I find some documentation that covers what those options actually do, etc.?  Seems like some important options to be left completely out of the official documents...

Thanks,

Monte

---

### Post by memilanuk on 2010-09-18
Btt

---

### Post by CharlesA on 2010-09-18
I'm guessing that the "mininal virtual machine" only installs the minimal needed for the OS to install and run inside a VM.

I just did an install using that option and it only used about 600MB of space for the base OS. (Normal server install uses about 800MB) That minimal install uses about 50MB of RAM, while the regular install uses around 150MB. Not an insanely huge difference, but if you are in a VM with limited memory, it's a good thing.

Thanks for bringing it up, I've been doing full installs on my VMs.

Check out this [link]("http://blogbuildingu.com/articles/ubuntu-installation-guide") for some more info. It's for 8.10, but should mean the same for 10.04.

Check [here]("https://help.ubuntu.com/community/JeOSVMBuilder") too.

---

### Post by memilanuk on 2010-09-18
Charles,

Thanks for the links.  The Community Docs link on JeOS is interesting... I'm kind of interested in something along those lines.

Is it just me, or should something like that maybe be covered in the official docs?  What would be a good way of bringing it up to the right folks?

Monte

---

### Post by CharlesA on 2010-09-18
I would think so, but I've not really gone over the server install docs in a whole lot of depth.

---


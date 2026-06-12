---
title: "virtual box in fullscreen"
date: 2010-03-25
forum: Virtualisation
---

### Post by Linux Lover II on 2010-03-25
Hi everyone!

I got the following problem: I installed Win7 with Virtual Box inside Ubuntu, but the virtual machine gives only a small window, and [ATTACH]151456[/ATTACH]won't go fullscreen: I included a screenshot to explain my problem more properly:

can anyone help to get a larger screen in virtual box?


Thanks in advance!

---

### Post by mkvnmtr on 2010-03-25
You will need to install guest additions. Do this by clicking install guest additions under device on the window of virtual box. Then it needs to be run in the guest os. It might runn automaticaly or you might need to find it and runn it yourself. 
If it is like xp you also might want to set your resolution on the windows os.

---

### Post by Linux Lover II on 2010-03-25
Thanks, I figured it out :) and it works great!

A pity it doesn't share its C-drive with ubuntu...

---

### Post by new_tolinux on 2010-03-25
You can just setup samba on Ubuntu or share some folders in Windows if the virtual machine is "wired to the network".

After that you can either connect from Windows to Linux and map a network drive (or from Linux to Windows, just your choice).
Although I actually prefer sharing in Windows because there are more options to set rights to a specific folder/file. Ubuntu is unfortunately restricted to "User", "Group" and "World" rights.

---

### Post by Linux Lover II on 2010-03-25
Thanks!

---

### Post by d3v1150m471c on 2010-03-25
> **Linux Lover II said:**
> Thanks!

Windows automatically networks itself to the host OS. Utilize the shared folders with virtualbox.

---


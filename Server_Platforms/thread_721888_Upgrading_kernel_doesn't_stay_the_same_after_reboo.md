---
title: "Upgrading kernel doesn't stay the same after reboot"
date: 2008-03-11
forum: Server Platforms
---

### Post by Sir Jake on 2008-03-11
I downloaded the rt-kernel for ubuntu 7.10 server
Just everytime my server gets restarted it goes back to the old kernel.
And the programs I run drop from 330fps down to 49 when I restart because it uses the old kernel.
I need to know how I can make the real time kernel always startup. It would not be so bad but this server is going to a colocation and I would hate this to happen when it's there.
I'm also still new with linux so sorry if I ask or forgot anything.
Thanks Jake.

---

### Post by lloyd_b on 2008-03-12
> **Sir Jake said:**
> I downloaded the rt-kernel for ubuntu 7.10 server
Just everytime my server gets restarted it goes back to the old kernel.
And the programs I run drop from 330fps down to 49 when I restart because it uses the old kernel.
I need to know how I can make the real time kernel always startup. It would not be so bad but this server is going to a colocation and I would hate this to happen when it's there.
I'm also still new with linux so sorry if I ask or forgot anything.
Thanks Jake.

Which kernel is started by default is controlled by the file "/boot/grub/menu.lst".  Look for a line that says "default    0" (or whatever number).

Then scroll down to where the kernels are defined.  The first kernel is "0", the second kernel is "1", etc.  Change the value on that "default" line so that the default is your rt kernel.

Note that you'll need a "sudo" or "gksudo" in front of the editor comand ("sudo nano /boot/grub/menu.lst", "gksudo gedit /boot/grub/menu.lst").

Lloyd B.

---

### Post by Sir Jake on 2008-03-12
Thank you very much, I thought it was something like that. Just never wanted to play with it. :) 
Nothing worse then screwing up my server just befor I send it away.
Once again thanks.

---


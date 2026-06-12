---
title: "Problems in installing GUI for Ubuntu Server 12.04"
date: 2014-09-08
forum: Server Platforms
---

### Post by hdry on 2014-09-08
Hey, so I just started industrial training yesterday, and one task I was given was to install Ubuntu Server in VirtualBox. I have to admit that my prior knowledge in Linux was basically restricted to home use, and I'm kind of unused to using a command line interface for the majority of the time, and I looked around and tried to install a GUI.

So far, whenever I try to install it using apt-get, I would usually get this error:

[IMG]http://i.imgur.com/KB1MDEy.jpg[/IMG]

I've tried other GUIs such as Unity and Gnome core but the problem remains. Does anyone have any suggestions on how to fix this?

---

### Post by hdry on 2014-09-09
I've edited the  /etc/apt/sources.list file in vim, saw that the Universe and Multiverse repos were enabled, and I even enabled these:

[IMG]http://i.imgur.com/u80fz9z.jpg[/IMG]

After saving it, I ran apt-get update again, and tried re-installing it a GUI, but I got this:

[IMG]http://i.imgur.com/MzHzWUL.jpg[/IMG]

---

### Post by ibjsb4 on 2014-09-09
Its acting like it never updated.  When you did the original update, did it update any packages or just say 0 packages to update.  Not behind a proxy are you?

---

### Post by nerdtron on 2014-09-09
Does this machine is even connected to the internet?
What does "sudo apt-get update" output?

And I'm curious why do you need a GUI for? Are you going to run a GUI program?
When you remotely connect to the server using ssh you are limited to a command line after all so why?

---

### Post by lukeiamyourfather on 2014-09-10
Linux servers typically don't have a GUI because it's unnecessary, uses more resources, can make the system less secure, and often the GUI takes longer to do something than the command line. Under the network settings for the virtual machine you can setup port forwarding (since it's NAT by default on VirtualBox). I usually use something like 2222 instead of the default 22 for SSH. Then you can connect to the virtual machine via SSH (ssh -p 2222 user@localhost) so you can do things like copy and paste using a GUI on the host.

---


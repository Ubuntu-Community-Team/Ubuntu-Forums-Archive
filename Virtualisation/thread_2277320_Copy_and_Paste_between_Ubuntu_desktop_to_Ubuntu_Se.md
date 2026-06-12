---
title: "Copy and Paste between Ubuntu desktop to Ubuntu Server running on VirtualBox"
date: 2015-05-08
forum: Virtualisation
---

### Post by robertzito on 2015-05-08
I set the clipboard to bidirectional in my VM settings running Ubuntu Server 14.04. I know you can use Ctrl + Shift + V to paste and copy is just right click on the command I want and copy. But when I try copying the command I want from my desktop Ctrl + Shift + V does not work.

Is there something I am missing or this is not something that can be done?

---

### Post by bapoumba on 2015-05-08
*Thread moved to **Virtualisation**.*

---

### Post by v3.xx on 2015-05-08
? gpm ?

[http://manpages.ubuntu.com/manpages/trusty/man8/gpm.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/gpm.8.html)

[https://answers.launchpad.net/ubuntu/+source/gnome-desktop/+question/212118](https://answers.launchpad.net/ubuntu/+source/gnome-desktop/+question/212118)

---

### Post by etescartz on 2015-05-08
If you're running a Server in a VM , then why don't you just ssh into the VM and use the terminal?

Think about it. It's a server with no graphical interface.

If you only had the sever version installed on a actual computer instead of the VM would you have been able to copy paste into it's command line prompt? You have no multitasking available in the same TTY unless you use some multimplexer like "screen" or "tmux" or a software such as "gpm" as **v3.xx** suggested.

---

### Post by TheFu on 2015-05-11
Yeah.
I ssh into my servers. 
Avoid using the "console" like the plague. Consoles are to be used whenever something REALLY bad has happened, not for daily use.
Plus, with most terminals, you can use select/paste with the mouse alone - no need for that pesky keyboard stuff - too many extra steps.

---


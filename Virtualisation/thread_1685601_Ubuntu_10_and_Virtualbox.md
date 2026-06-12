---
title: "Ubuntu 10 and Virtualbox"
date: 2011-02-10
forum: Virtualisation
---

### Post by rustydusty1717 on 2011-02-10
Hello all, just got a few questions for any Ubuntu geeks out there.
 
Last night I installed virtualbox as I want to run a few virtual servers to play with. Mostly XP Pro and Windows Home Server and possibly a Mac server later on.
 
Now my main question is if there is any way to get the original Ubuntu and Gnome to use a lot less resources. With nothing running, it uses roughly 250-300Mb of ram. Anyway to get that a little lower, or even turn gnome off and use some of a remote application to manage virtualbox? I originally was just running Ubuntu 10 server and loved it, however needed Gnone for virtual box. I'd just love to get the main resources down to around 100-150 for Ubuntu alone while still running virtualbox. Any suggestions are greatly appreciated, thanks!

---

### Post by CharlesA on 2011-02-11
You don't really need Gnome for virtualbox. You can run it headless (like I do).

I mostly use [phpvirtualbox]("http://code.google.com/p/phpvirtualbox/") to manage it. I also forward the GUI over SSH by using X11 forwarding, as well.

I think my server uses around 300MB of RAM with everything running - minus the VMs, of course.

---

### Post by rustydusty1717 on 2011-02-11
Okay, so with phpvirtualbox I could remotely manage virtualbox from any other computer and also turn Gnome off on the host machine, correct? At work we run ESX-i and use VMware Vsphere to remotely manage the virtual machines. Is that what phpvirtualbox is? I'd love to be able to get rid of Gnome again and have a program I can launch and connect to, and control virtualbox remotely, from anywhere.

---

### Post by CharlesA on 2011-02-11
It's just a web interface for VBox.

By default it has no authentication, and isn't using a secured connection, but you can set it to do both of those.

---


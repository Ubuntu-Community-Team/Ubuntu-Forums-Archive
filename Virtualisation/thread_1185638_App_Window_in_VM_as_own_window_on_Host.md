---
title: "App Window in VM as own window on Host?"
date: 2009-06-12
forum: Virtualisation
---

### Post by Pnuts on 2009-06-12
I was reading an article on Win7 about a built in feature that allows you to run a VM of Windows XP and have the windows appear as normal windows in Win7 as if you launched them there. Its mainly for compatability of older aplications, but this is a remarkable feature.

Is there any type of VM software available currently that would let me do this? Say a FF3 window from a Ubuntu VM in XP, or an IE window from windows in Ubuntu? Doesnt have to be a web browser application, just used them as examples.

-Pnuts

---

### Post by Cheesemill on 2009-06-12
Check out seamless mode in VirtualBox.

Cheesemill

---

### Post by Pnuts on 2009-06-13
Thank you, this looks like it will do what I described. I did some testing and the VM seemed to freeze once it entered seemless mode. I will continue to play around with this though as it is what I wanted.

Thanks again,

Pnuts

---

### Post by Cheesemill on 2009-06-13
You could also check out [SeamlessRDP]("http://www.cendio.com/seamlessrdp/") with VMware if you're having problems with VirtualBox.
I don't use it myself because it doesn't work when your XP machine is connected to a domain.

---

### Post by f1r3br4nd on 2009-07-02
No, SeamlessRDP does not work as advertised with the latest version of VirtualBox. From all my Googling, I have *not* been able to find a single working set of instructions for getting truly seamless RDP with VirtualBox.

With newer versions of VirtualBox, there is RDP built in, and you can use it kind of seamlessly by making the desktop invisible (with the menu bar still visible and a ton more memory getting used than if you could run it in VBoxHeadless or VBoxRDP mode). In fact, SeamlessRDPshell.exe won't even run because it recognizes VBox's instance already running.

But what I'm talking about is connecting through rdesktop and seeing the program you want to run and only that program.

Rdesktop does connect (remember to use localhost as your IP if you're running it locally) just fine but shows the whole desktop and completely ignores any commands you try to put in the -s argument. So you get a remote desktop, but as far as anything I've been able to find online about VirtualBox goes, it's not truly seamless yet.

---


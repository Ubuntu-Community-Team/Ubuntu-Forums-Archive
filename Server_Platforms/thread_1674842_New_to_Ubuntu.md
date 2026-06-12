---
title: "New to Ubuntu"
date: 2011-01-24
forum: Server Platforms
---

### Post by slikka on 2011-01-24
[FONT=Calibri][SIZE=3]Hi all, I’m totally new to Ubuntu/Linux, but found it fascinating and would like to learn more.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I have installed Ubuntu server 10.04 converted my XP desktop to a .vmdk file using VMware converter. Want to run my XP desktop on my Ubuntu server and use VNC viewer to do a remote connection to my xp box, please help.[/SIZE][/FONT]

---

### Post by Claus7 on 2011-01-24
Hello and welcome to the forums!

I will try to answer your question, yet I should say that I did not understand it very much. So my contribution would be:

install in the ubuntu box the package: xtightvncviewer that you will find from synaptic package manager (From System->Administration->Synaptic Package Manager).

Then open a terminal (From Applications->Accessories->Terminal) and type something like:
```
vncviewer *address of your xp box*
```

Hope it helps,
Regards!

---

### Post by slikka on 2011-01-24
hi, thanks for the reply...ok I want Ubuntu server 10.04 ,my windows xp as a guest. I would than remote desktop to the xp desktop from say another windows pc or ubuntu desktop...

---

### Post by slikka on 2011-01-24
So i must ran this? qemu-img convert windowsxp.vmdk -O raw windowsxp.img
 
than how to I start my XP?

---

### Post by Claus7 on 2011-01-27
Hello,

how about this:
[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

did not understand the qemu thing in the first place. Are you sure that this option is the only option you get?

Regards!

---


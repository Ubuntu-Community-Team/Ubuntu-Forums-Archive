---
title: "[SOLVED] Blue Screen of Death..."
date: 2008-02-09
forum: Virtualisation
---

### Post by dwally89 on 2008-02-09
Hi,

I recently upgraded my RAM from 1GB (2x512MB) to 2GB (2x1GB) in order that I could run Vista Ultimate using VirtualBox whilst running other applications at the same time.

I have allocated 1GB to the virtual PC.

However...

When I try to run Visual Basic Express 2008 on it, it works fine, until I load my project, upon which I get the blue screen.

Does anyone know why it's doing this, and how it can be solved?

Thanks

---

### Post by p_quarles on 2008-02-09
(moved to Virtualization)

Have you installed the VirtualBox guest extras for Vista? These are mainly meant to add extra functionality to the VM, but in my experience they add a good level of stability as well.

---

### Post by dwally89 on 2008-02-09
Yeah I've installed them.

---

### Post by fjgaude on 2008-02-09
You know from my little experience with Vista it takes nearly a gig just to start up, and with big apps loaded it likely will wish it had 2 gigs.

I got rid of my copy of Vista and am back to WinXP SP2 waiting for SP3.

---

### Post by dwally89 on 2008-02-09
But as for the actual cause of the problem?

---

### Post by fjgaude on 2008-02-09
> **dwally89 said:**
> But as for the actual cause of the problem?

Did you go into swap because of lack of real RAM? Could you tell the machine was slow before you loaded the last app, your project?

There can be any number of other things that might have caused the blue screen. Like, some bad memory chip, hard drive having errors, no allocating enough disk space for the type of apps you plan on running, etc.

---

### Post by dwally89 on 2008-02-10
Nope, it didn't go into swap (I always run the system monitor when running the virtual PC, to check how much RAM is being used.) The machine runs slowish with other apps, but still works (lets me sync my iPod etc).

So any ideas of how to solve this problem?

---

### Post by dwally89 on 2008-02-10
Ok, so the VB.net project I was trying to open was not located on the virtual hard drive, so I copy & pasted it to the virtual hard drive, and tada, no blue screen.

---

### Post by fjgaude on 2008-02-10
Very good... and it is so rewarding that VMware can copy and paste as it does between the host and guest.

You can use other means to access your data on the host, through Samba shares and going the other way, through shares in Windows using file managers.

---


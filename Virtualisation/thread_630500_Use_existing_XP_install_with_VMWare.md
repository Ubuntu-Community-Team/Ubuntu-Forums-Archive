---
title: "Use existing XP install with VMWare?"
date: 2007-12-03
forum: Virtualisation
---

### Post by allspiritseve on 2007-12-03
I have XP and Kubuntu 7.10 dual-booted on my laptop. I just installed VMWare Server 1.04. How can I make it run my existing XP install from within kubuntu?

Thanks,

Cory

---

### Post by cogadh on 2007-12-03
You might be able to, but you really shouldn't. When you run an existing XP installation through a VM using raw disk access, it changes the hardware and invalidates your Windows activation. If you try to boot back into Windows, it will likely not boot. You might be able to get around it by creating a seperate hardware profile in Windows and making the VM use that profile, but you will likely still have problems.

---

### Post by allspiritseve on 2007-12-03
OK, so basically there's no way to still keep the option of booting into windows natively?

Cory

---

### Post by Tteddo on 2007-12-03
> **allspiritseve said:**
> OK, so basically there's no way to still keep the option of booting into windows natively?

Cory

No, if you convert it to a VM it will have to be re-activated, and if you boot it natively again all the hardware will be the VM's so it will want to be activated again. I think you only get 3 or 4 times, and you will have to call each time because more than 2 items will have changed.

What you could do is run the File and Settings Transfer Wizard in XP and use that to backup your real install, then restore in the VM. It's under Start>>All Programs>>Accessories>>System Tools.

---

### Post by McMonarch on 2007-12-03
I've tried the same thing. Only one of my windows installations can be activated at a certain time. I want to use both copies but I can't. If anyone knows any tips about this I would love to get them.

---

### Post by McMonarch on 2007-12-04
Thanks for those links Gumbi. You're right that the last article could be illegal but it is a good solution. Its much better than getting an illegal product key though. :)

---

### Post by Victory on 2007-12-04
The two methods of virtualizing Windows in Ubuntu linked to be gumbi are good but they're for people using SCSI drives. If you've got an IDE drive instead, I recommend using this guide.

[http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu/](http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu/)

Many people who have IDE drives and use the SCSI set of instructions end up having BSODs.

---

### Post by gumbi18 on 2007-12-04
Yes it is much better than getting an illegal CD key, but unfortunately it's questionable as to whether its legal. :confused: And thanks for the link Victory, I'll test that method when I get home from work tonight. And hopefully all goes well.:)

Once running windows in VMware there is some pretty interesting things that can be done such as integrating the windows start menu onto the GNOME desktop.The link is:
[http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/]("http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/")

It's very handy but a bit of a resource hog.

---

### Post by McMonarch on 2007-12-04
I used that tutorial that you posted Victory on my VMWare and it works great... except for the activation part of course. 

By The Way, does anybody know how to speed up the virtual machine besides giving it more RAM? I've already cut down the visual effects and it still runs pretty slow.

---

### Post by Victory on 2007-12-06
If you use Gumbi's link to the activation workaround [http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/](http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/) you can fix that.

---

### Post by jakornblum on 2008-04-04
That link only works if you are running Windows XP PRO, if you are running XP HOME, use the following guide:
[http://ubuntuforums.org/showthread.php?p=4644845](http://ubuntuforums.org/showthread.php?p=4644845)

---


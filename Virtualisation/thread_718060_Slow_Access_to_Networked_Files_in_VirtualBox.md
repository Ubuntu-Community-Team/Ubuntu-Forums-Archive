---
title: "Slow Access to Networked Files in VirtualBox"
date: 2008-03-07
forum: Virtualisation
---

### Post by eagledrc on 2008-03-07
Hey,

So I have a sweet setup.  VirtualBox XP Pro SP2 on Ubuntu 7.10 Gutsy.  I have Adobe CS3 installed on there with 2000 MB of RAM dedicated to the virtual machine, and it works great.  Its a tad bit slow when switching and starting programs, but if I am just using one program, it works great.  I have my network configured to access the files on my Ubuntu HD, and it works, but it is very slow.  In Windows Explorer, it takes several minutes after clicking on the networked folder to open it.  Once opened, it is slow, but a speed acceptable considering the setup.  Is there a way that I can access the folders with decent speed?

---

### Post by fjgaude on 2008-03-07
Use only one core if you have more.

You are accessing your Ubuntu files through Samba, thorugh a LAN, or directly on the same computer?

---

### Post by eagledrc on 2008-03-07
How do I use only one core?  I have an AMD 64 X2 Dual Core 5000+ processor.  
I'm not sure how I'm acessing them.  Probably LAN.  What I did was install the VirtualBox Addons, then added a network place in XP which was one of the shared folders that I chose.  Would Samba work better?  Or directly?

---

### Post by fjgaude on 2008-03-08
In the VBox window, one of the options in the setup should show the cores. Use one and not two.

I haven't used VBox for a year now so I forget the menu items to click.

---

### Post by eagledrc on 2008-03-10
I couldn't find them in the VBox settings...I don't know where to change that.

---

### Post by fjgaude on 2008-03-10
Hopefully, someone else who is presently using VBox can help.

Sorry.

---

### Post by eagledrc on 2008-04-22
Problem fixed...[http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux)
sharing desktops, i put a file on one desktop, access it on another.  it works great

---


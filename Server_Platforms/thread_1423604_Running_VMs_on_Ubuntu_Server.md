---
title: "Running VMs on Ubuntu Server"
date: 2010-03-06
forum: Server Platforms
---

### Post by CharlesA on 2010-03-06
Is it possible to run them without a GUI? I'm guessing it isn't.

Also, what would be the best way to go about it? I know I could VNC into the machine, but would I need to leave the VNC server running so that it doesn't screw up something?

Thanks.

---

### Post by dasunsrule32 on 2010-03-06
Use xen, it is all CLI. ;)

---

### Post by nerr on 2010-03-06
I've had a lot of luck using Virtualbox for my VM needs.  It also ships with a VRDP server, allowing you to use Remote Desktop (RDP) to access the VMs hosted on a command-line only machine.  It works quite well in my experience.

EDIT: I should also note that the package you want is virtualbox-3.1, as it is the one that comes with the VRDP server and VBoxHeadless commands.

---

### Post by CharlesA on 2010-03-06
Oh awesome. Thanks!

---

### Post by koenn on 2010-03-07
> **CharlesA said:**
> Is it possible to run them without a GUI? I'm guessing it isn't.

Also, what would be the best way to go about it? I know I could VNC into the machine, but would I need to leave the VNC server running so that it doesn't screw up something?

Thanks.
Depends what VMs you're talkin about.
VMware server has a large set of commands.
It also has a web interface so you can run it on a sever without X

---

### Post by CharlesA on 2010-03-07
> **koenn said:**
> Depends what VMs you're talkin about.
VMware server has a large set of commands.
It also has a web interface so you can run it on a sever without X

Thanks. I was thinking about VirtualBox since I have the most experience with it. VMWare is what we use at work, and a web interface sounds great. 

I think I'll give it a shot.

---

### Post by CharlesA on 2010-03-08
> **nerr said:**
> I've had a lot of luck using Virtualbox for my VM needs.  It also ships with a VRDP server, allowing you to use Remote Desktop (RDP) to access the VMs hosted on a command-line only machine.  It works quite well in my experience.

EDIT: I should also note that the package you want is virtualbox-3.1, as it is the one that comes with the VRDP server and VBoxHeadless commands.

Thank you. I installed VBox on my server and it seems to work perfectly.

VBoxHeadless + VRDP is awesome.

---

### Post by dasunsrule32 on 2010-04-08
I never liked using VBOX headless, because it pulls in so many packages that don't need to be installed, all the GTK packages, etc.

---


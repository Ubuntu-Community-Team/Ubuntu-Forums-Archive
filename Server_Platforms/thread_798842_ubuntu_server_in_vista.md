---
title: "ubuntu server in vista"
date: 2008-05-18
forum: Server Platforms
---

### Post by hugohh on 2008-05-18
I am not a very tech savvy person. I have vista, which I use for everyday work. 

Wanted to know how can I simultaneously run vista (originally booted) and ubuntu server (as a home server) in it. I know that I could do that with vista, but I want to keep everything organized.
 Everywhere it says virtual box, wmware... I get totally mixed up.

Also, does ubuntu server have some GUI or is it purely based on a command-line interface? 

Finally, is there that much difference between the desktop and sever editions or is the server edition simply a stripped down version of the desktop one? Therefore if my server will not handle enormous amounts of requests, is it okay the desktop edition because of the simpler GUI?

Thanks for the help!

---

### Post by damis648 on 2008-05-18
I would not recommend running a virtualized server, if that is even possible. The server edition btw has absolutely no GUI, unless you install it, which can be done.

---

### Post by tamoneya on 2008-05-18
First we will start with the desktop and server editions.  Server is like you said a stripped down version of desktop.  There are however a couple of extra things added like it will help you get standard servers up and running during the install process.  for someone like you who prefers the GUI just go with the standard Ubuntu Desktop.  

As for running the server simultaneously with vista you will need to set up a virtual machine.  This is done with a program like VMWare or virtual box.  VMWare requires a lisences and other stuff so it is probably easiest if you just go with virtual box.  Download it here: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads).  Select Binaries all platforms and then set the platform to Windows x86 and language to multilanguage.

---

### Post by prshah on 2008-05-18
> **tamoneya said:**
> 
As for running the server simultaneously with vista you will need to set up a virtual machine.  This is done with a program like VMWare or virtual box.  VMWare requires a lisences and other stuff so it is probably easiest if you just go with virtual box.  Download it here: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads).  Select Binaries all platforms and then set the platform to Windows x86 and language to multilanguage.

[s]Caveat: ubuntu server will _not_ run out-of-box virtualised in virtual-box; that's because ubuntu server kernel has PAE support enabled by default, which vbox does not support.[/s]

[s]So, if you can afford a license, VMWare is the way to go.[/s]

Edit: As corrected below, vbox does support (experimental) PAE from 1.60.

And yes, for "lighter" loads, you can go the desktop edition, but installing and configuring the various components for a webserver may be difficult to do individually; in ubuntu-server, there are a number of pre-built and ready-configured options you can choose, to setup your server practically instantly.

---

### Post by Lapp-Same on 2008-05-18
> **hugohh said:**
> 

Finally, is there that much difference between the desktop and sever editions or is the server edition simply a stripped down version of the desktop one? Therefore if my server will not handle enormous amounts of requests, is it okay the desktop edition because of the simpler GUI?

Desktop and Server Kernel is diffrent.... Server kernel is not a stripped Desktop edition....is a diffrent kernel... Who runs more stable on heavy tasks, and to dedicated programs...

---

### Post by Popcorned on 2008-05-18
> Caveat: ubuntu server will _not_ run out-of-box virtualised in virtual-box; that's because ubuntu server kernel has PAE support enabled by default, which vbox does not support.

Virtual Box Now Supports PAE

> This version is a major update. The following major new features were added:

[LIST]
[*]Solaris and Mac OS X host support
[*]Seamless windowing for Linux and Solaris guests
[*]Guest Additions for Solaris
[*]A webservice API
[*]SATA hard disk (AHCI) controller
[*]Experimental Physical Address Extension (PAE) support
[/LIST]

Although it mentions experimental, it does infact work with Hardy. You have to enable PAE on a per image basis in the settings window.

- Mathew

---

### Post by hugohh on 2008-05-19
Thanks for your help, but I decided it is simpler to stick with apache in vista

---

### Post by windependence on 2008-05-19
> **Lapp-Same said:**
> Desktop and Server Kernel is diffrent.... Server kernel is not a stripped Desktop edition....is a diffrent kernel... Who runs more stable on heavy tasks, and to dedicated programs...

You are quite correct on that, and not just that but the kernel is optimised for virtualization as well.

What's wrong with a virtualized server, damis648? I run several of these in a production environment on Ubuntu server and they run just fine.

PAE works but is more of a hack than a real solution. VMware will run the VM paravirtualized which is fine in most situations.

-Tim

---


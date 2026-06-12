---
title: "VMWare Server - rumour or reality"
date: 2009-09-01
forum: Virtualisation
---

### Post by Warthaug on 2009-09-01
Over the past few years I've switched 90% of my work computing to ubuntu.  Unfortunately, there are a small number of programs I must use, or which lack a good linux equivalent, which don't run under wine.

Notably, I'm talking about powerpoint (forget open office; its got a long ways to go to match powerpoint), a statistics & graphing package called prism, as well as some various molecular biology apps that despite my best efforts won't run in wine.

As such I am planning on setting up a visualized winXP to run those programs through, using VMWare Server.

While talking to a friend about this, he mentioned that the newest VMWare version operated through your web browser, rather than through a dedicated program.  He also thought that full-screen was limited to the "full screen" mode of the browser, meaning in firefox you'd still have an address bar up top.

My question is simple - are the above two rumours true, and in the case of the full-screen rumour, is there a way around that (if true).

Thanx

Bryan

---

### Post by bodhi.zazen on 2009-09-01
Yes it is trus. server 2.0.x is buggy, stay with version 1 if you can.

To work around this, VNC into the windows box.

---

### Post by HermanAB on 2009-09-01
Yup, VMware server 2.x is best avoided...

---

### Post by JKyleOKC on 2009-09-02
> **Warthaug said:**
> My question is simple - are the above two rumours true, and in the case of the full-screen rumour, is there a way around that (if true)?It's partially true. For full control of the virtual machine you have to go in through the browser, but by adding three lines to the VMX file you can activate VMWare Server's built-in VNC server and then access the VM through VNC (Remote Desktop is the way it shows up on my Xubuntu system) and do almost anything that you would do at the actual console, in true full-screen mode with no title bar at the top. The only things I cannot do by this approach involve certain hotkeys that are trapped out by the VNC client and thus never make it to the VM itself. However I cannot connect USB ports via VNC, and must use the browser interface to set them up when I need to. Using Firefox 3, the Web Access goes to full screen with no title bar once I hit the "maximize" button of the title bar. I used it that way for several months before learning about the VNC feature.

As for VMWare Server 2 being buggy, I've been using it ever since it was released and once I found out about the built-in VNC server have had no problems. Before that, I was unable to access the VM through browsers across my LAN, only from the one system that hosted VMWare. The Web Access routines would time out for no known reason. Now with VNC I can use the VM from anywhere on the LAN, and can even have it up on several screens at the same time although I have no need to do so.

---

### Post by Bachstelze on 2009-09-02
> **bodhi.zazen said:**
> Yes it is trus. server 2.0.x is buggy, stay with version 1 if you can.

No problem with 2.x here. You can't download 1.x anymore, anyway.

---

### Post by bear24rw on 2009-09-02
you can also try virtual box, both me and a friend run win xp in vbox and it runs pretty well. its also in the repos :)

---

### Post by bodhi.zazen on 2009-09-03
> **HymnToLife said:**
> No problem with 2.x here. You can't download 1.x anymore, anyway.

No problem meaning what exactly ? Does it install on Ubuntu without any modification or patch ? Have the fixed the problems with the web interface (last time I looked it was slow and buggy) ? What about the features ? Last time I looked there were a number of features from 1.x simply not available in 2.x, the one that comes to mind is the ability to boot / install on physical partitions .

---

### Post by stefangr1 on 2009-09-03
> **Warthaug said:**
> 
While talking to a friend about this, he mentioned that the newest VMWare version operated through your web browser, rather than through a dedicated program.

This is true, you can access the vm's using an add-on for mozilla-firefox. Configuration of the machines goes trough the browser, while the screen can be opened in a separate window. Because of that the performance is relatively low, you can no longer play games on a virtual machine, though for everything else performance is very well on the local network.

> **Warthaug said:**
> 
He also thought that full-screen was limited to the "full screen" mode of the browser, meaning in firefox you'd still have an address bar up top.

This is false, you can resize the window with the vm-screen on it as you like, or make it full screen.


I don't agree with the posters above stating that vmware-server-2 should not be used. Even though performance of the virtual machines was much better in vmware-server-1, and there are some minor issues (like not being able to enter the vm-bios because it takes more time to open the interface than to pass the virtual bios), stability of the vm's is very good (I have never had a VM crash). The advantage of the web interface should be that you don't need to install anything, but in reality you still need to install the add-on, and performance of the vm's when upload speeds are below say 300kb/s is too low to be usable anyway.

EDIT: I added a sreenshot.

---

### Post by crownedzero on 2009-09-03
I just ran across this thread and was hoping for input/help. I'm taking an introduction to linux in school atm and we're running with openSuSE. Initially I tried installing SUSE on a partition but none of my hardware was found and/or supported. =( Ever tried to troubleshoot one PC without the Internets! OMG it sucked. 

Fresh copy of 64 bit Ubuntu brewing at home as we speak, just asking for input Virtualbox or VMware. Any similar cases? Which worked best for you?

---

### Post by TJet1.8 on 2009-09-03
> **stefangr1 said:**
> This is true, you can access the vm's using an add-on for mozilla-firefox. Configuration of the machines goes trough the browser, while the screen can be opened in a separate window. Because of that the performance is relatively low, you can no longer play games on a virtual machine, though for everything else performance is very well on the local network.



This is false, you can resize the window with the vm-screen on it as you like, or make it full screen.


I don't agree with the posters above stating that vmware-server-2 should not be used. Even though performance of the virtual machines was much better in vmware-server-1, and there are some minor issues (like not being able to enter the vm-bios because it takes more time to open the interface than to pass the virtual bios), stability of the vm's is very good (I have never had a VM crash). The advantage of the web interface should be that you don't need to install anything, but in reality you still need to install the add-on, and performance of the vm's when upload speeds are below say 300kb/s is too low to be usable anyway.

EDIT: I added a sreenshot.

Well...actually, the "add-on" for Mozzila or IE "is" a separate program very similar to VMware Player. You access the VMware Server console via a browser, but when you open a VM...it is opened in a "VMware Remote Console" plugin/app.
The "VMware Remote Console" is automatically installed the first time you open a VM console.

You can also generate a shortcut link to your VM through VMware Server 2 that allows you to access specific VM's by double-clicking on the generated shortcut. This opens the VMware Server Web console with your specific VM in focus. You then click anywhere in the console screen and it will open the VMware Remote Console plugin/app. 

You can also access the VMware Server Console using the ESX Virtual Infrastructure Client or newer vSphere client.
In the "IP Address / Server Name" box, you just enter your VMware Server URL ( i.e. - [https://servername:8333](https://servername:8333) ), user name, password, and the VI client replaces your VMware Server Web Console interface. The VI client also provides more functionality than the Web console.
From there, you just right-click on VM and select "Open Console".
This opens your VM console using the VI Client's console app.

As for performance/functionality between VirtualBox and VMware Server 2....they both perform equally well. VMware products provide a little more functionality, but use a little more resources.
If you have more than 3 or 4 GB of RAM in your system...I would choose VMware.

---

### Post by batfastad on 2009-09-05
Having recently started messing around with VMware Server 2 to virtualise some Linux servers, I was surprised about the web management of VMware Server too.
The web management interface is pretty clunky (I get intermittent AJAX errors) but to control the actual VMs it's not bad.
To control the VMs all you have to do is login to the web management, go to the VM you want to control and it opens a firefox/IE plugin which opens a slimmed-down version of VMware Player to fully control the VM, and that console window is no longer tied to your browser once its open (on windows at least). Also once you're in the web management interface, you can download a desktop shortcut for a particular VM to fire it straight up so you don't need to go in to the web management first!

I find the performance decent enough for server admin across the internet. So performance on a local VM should be very good.

Here's a document on the different options available to control a VM in VMware Server 2
[http://communities.vmware.com/docs/DOC-8840](http://communities.vmware.com/docs/DOC-8840)
With the latest version of Server 2 there is no longer a seperate management console app provided so the web admin is where it all kicks off. But there's plenty of different options for the actual controlling of the VMs themselves

HTH

Cheers, B

---


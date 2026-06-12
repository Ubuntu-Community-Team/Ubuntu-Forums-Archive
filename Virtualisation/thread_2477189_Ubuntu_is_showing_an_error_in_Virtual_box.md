---
title: "Ubuntu is showing an error in Virtual box"
date: 2022-07-17
forum: Virtualisation
---

### Post by allhddcom on 2022-07-17
Hi I am trying to use Ubuntu in a virtual box but it is showing an error that you don't have enough memory. I have 4 GB Memory ([[COLOR=#000000][FONT=Arial]HP 647903-B21[/FONT][/COLOR]]("https://www.allhdd.com/memory-ram/pc3-10600/32gb/hp-new-sealed-hpe-647903-b21/"))in my Laptop. I am not sure why [Virtualbox]("https://www.virtualbox.org/")6.1 is showing me this error. Is there any reason Why I am getting this error?

---

### Post by ajgreeny on 2022-07-17
You have 4gb ram but how much memory have you given to the VM?

---

### Post by SeijiSensei on 2022-07-17
What is the host OS? If it's Windows, I recommend setting the maximum memory size for the Ubuntu virtual machine to 1.5 GB, leaving 2.5 GB for the more greedy Windows. 

4GB of memory is pretty much the minimum if you want to run virtual machines. I'd consider investing in an upgrade to 8 GB. You probably have an empty slot into which you could insert another 4 GB memory.

---

### Post by TheFu on 2022-07-17
> **allhddcom said:**
> Hi I am trying to use Ubuntu in a virtual box but it is showing an error that you don't have enough memory. I have 4 GB Memory ([[COLOR=#000000][FONT=Arial]HP 647903-B21[/FONT][/COLOR]]("https://www.allhdd.com/memory-ram/pc3-10600/32gb/hp-new-sealed-hpe-647903-b21/"))in my Laptop. I am not sure why [Virtualbox]("https://www.virtualbox.org/")6.1 is showing me this error. Is there any reason Why I am getting this error?

4G is the minimal for any hypervisor host.
You'll want to use a light Ubuntu DE, probably LXQt / Lubuntu, not the normal Ubuntu with Gnome. Also, you'll want to allocate 2G or less and 1 vCPU to the VM.  If it runs a desktop, use 128MB for the video RAM, but uncheck the 2D and 3D acceleration settings inside the VM settings.  Running VMs is all about sharing resources that are limited.  We have to be smart about our choices on limited systems.

If you run 
```
$ inxi -Fbz
```
inside the VM, we'll be able to see other issues that you can probably correct too.  inxi will need to be installed. It isn't there by default.
```
sudo apt update
sudo apt install inxi
```
are the commands for that.

---


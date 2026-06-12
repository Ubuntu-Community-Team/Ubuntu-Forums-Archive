---
title: "VMware won't recognize wireless card"
date: 2008-04-07
forum: Virtualisation
---

### Post by DeviantFeatures on 2008-04-07
i'm a total n00b when it comes to linux and Ubuntu. I was able to successfully install VMware and get windows XP pro to work. The problem I have is that it won't recognize my wireless internet card. The house in on a wireless network. Is it absolutely necessary to connect via my ethernet port? Also, I have tons of my windows software on my external harddrive. VMware won't recognize this hard drive. How can I install all my stuff into the virtual machine? I'm desperate here! I need to edit footage.

---

### Post by Gerlads Mod on 2008-04-08
I'm having the same problem with the wireless card not working in VMware.

I'm running a Dell Inspirion E1505 notebook.

I don't really use VMware that much anyway. I only use it for when I need to print.

---

### Post by fjgaude on 2008-04-08
One suggestion, power off the VM, then go to VM tab menu, Settings at it bottom, then at the bottom click on Add. Then Hardware, ethernet. See if you can do something with that finding your wireless card or whatever it takes.

Since I don't do wireless under vmware I can't say what you'll find. NAT and then see.

---

### Post by DeviantFeatures on 2008-04-09
I'll try it and see what happens. Thank you so much. The only reason I even installed VMware is because audio and video production apps on Linux suck bawls. I need to use my sony, native instruments, and adobe apps. Thanks for the help again.

---

### Post by Ptero-4 on 2008-04-09
Just set your VM to use NAT (go to the "ethernet" section). It will make a virtual ethernet card which picks up your hosts internet connection (you don't need to have your PC connected through ethernet, it just need to be connected to the internet and it works).

---

### Post by vcarbon on 2008-04-09
when you install vmware, make sure you set up 2 bridged internet connection, ex. eth0 and eth1. assuming eth1 is your wireless It will ask you if you want to set bridged networking in the installer and give you the default options of eth0 which is your wired conection...say yes. The it will ask if you want to set up another bridged connection and give you the default as no, but type yes and it will automatically configure you eth1. that should do it. I usually dont install nat or the other network when it asks. Make sure you have the bridge network connection in you configuration tab under vmware and you should be good.

once the virtual machine is running you dont have direct access to you wireless like you would under a native install therefore you have to connect to the internet thought the bridged network connection.

good luck :guitar:

---

### Post by DeviantFeatures on 2008-04-17
so, as of right now...i'm fucked? i have to re-install vmware to make those changes? that kind of sucks. but, if it's what I have to do then cool. also, there's the issue of my external hard drive. that has all my program files. so, how do i get that to show up in the vm?

---


---
title: "how can I access Windows files from Ubuntu through VirtualBox?"
date: 2011-01-27
forum: Server Platforms
---

### Post by nick24 on 2011-01-27
I am running Ubuntu 10.10 through VirtualBox on Windows 7 machine, is there a way I can access my Windows files remotely in my Ubuntu machine? Ideally I want a server running on my Windows and a client in my Ubuntu machine and be able to access/transfer files between the two computers. Any ideas? I was told it can be done with Samba and Putty but I need more clarification on that or any other other method for that matter. Thanks a lot :P

---

### Post by gordintoronto on 2011-01-27
This is all on one computer? When you open Places/Home, is there an item on the left side that says 139 GB Filesystem, or something along those lines? If so, it's your Windows hard drive; one click and you're there.

Samba is for accessing files across a network.

---

### Post by Zimmer on 2011-01-27
More clarity, please Nick24.

If your aim is use of a single physical machine with Ubuntu in a VirtualBox then  you need to use specific shared folders between the Win7 install and the Ubuntu Virtual machine set up via VirtualBox.

If your eventual aim is to run Win7 and Ubuntu on separate physical machines then you will need to investigate SAMBA and network shares etc..

---

### Post by nick24 on 2011-01-28
> **Zimmer said:**
> More clarity, please Nick24.

If your aim is use of a single physical machine with Ubuntu in a VirtualBox then  you need to use specific shared folders between the Win7 install and the Ubuntu Virtual machine set up via VirtualBox.

If your eventual aim is to run Win7 and Ubuntu on separate physical machines then you will need to investigate SAMBA and network shares etc..



Thank you for the reply guys. Zimmer yes Ubuntu is running on the same machine alongside Windows using VirtualBox. I will look in to the shared folder option to see what I can set up. Thanks again

---

### Post by nick24 on 2011-01-28
> **gordintoronto said:**
> This is all on one computer? When you open Places/Home, is there an item on the left side that says 139 GB Filesystem, or something along those lines? If so, it's your Windows hard drive; one click and you're there.

Samba is for accessing files across a network.


grindtoronto, on a dual boot/live cd system yes you can access your windows files from Ubuntu, but I am running it Virtually so technically they are completely two separate computers, hence I can't access any files between the two...........yet......Thanks for your reply

---

### Post by Zimmer on 2011-01-29
You will need to install the guest additions in the Virtual machine to use shared folders...  :)

---

### Post by nick24 on 2011-01-29
> **Zimmer said:**
> You will need to install the guest additions in the Virtual machine to use shared folders...  :)

Yup my guest additions are installed and I am able to access my music from my lovely Ubuntu.......sweet. Thanks for the help everybody

---


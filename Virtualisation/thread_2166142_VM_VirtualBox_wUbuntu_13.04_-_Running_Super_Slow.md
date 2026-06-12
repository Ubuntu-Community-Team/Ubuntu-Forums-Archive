---
title: "VM VirtualBox w/Ubuntu 13.04 - Running Super Slow"
date: 2013-08-07
forum: Virtualisation
---

### Post by MrManican on 2013-08-07
So this is my first adventure into virtualizing Ubuntu. I've set aside 100GB and 4GB of RAM. It seems my Windows 7 runs fine but when I work in Ubuntu, it is laggy. I know I need to provide more information, just not sure what you will need to help me out.

Thanks in advance for any suggestions/ideas/fixes!

---

### Post by TheFu on 2013-08-08
[http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) explains how to get the best performance for VirtualBox. It isn't specific to 13.04, but should work if you follow the instructions.

---

### Post by james25 on 2013-08-08
2D graphics acceleration gives a big performance boost when using Virtualbox but it can only be enabled on virtual Windows. So, I can't help you much but that is probably the source of your problem. Apart from that, make sure it has plenty of memory (at least 512 MB) and as much video memory as possible.

---

### Post by MrManican on 2013-08-08
Thanks for the information. I am resetting up my environment now as per the specs outlined in the aforementioned article. I'll definitely post on how this turns out!

---

### Post by MrManican on 2013-08-08
So I've resetup the virtual environment and I am still experiencing severe slowness. I've setup all specks to match those of [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox). Where windows has the task manager and I can monitor the resources used, does Ubuntu have anything like this?

---

### Post by TheFu on 2013-08-09
top or htop

But I have doubts that you got everything in that article correct. Was there any part that you aren't 100% positive about?  Did you disable Unity? Did you increase the video RAM to the guest? Did you preallocate the storage? Dud you disable 2d and 3d graphics for the clientOS?  Did you get the guest additions installed?

What are the specifications for the host computer?  CPU, RAM, disk, network card and connection?

---

### Post by markbl on 2013-08-09
Enable 3D acceleration in the VB guest settings.

---

### Post by MrManican on 2013-08-09
You are right TheFu, I didn't get rid of Unity. Didn't know what it was really and I suppose I just expected that it wouldn't be installed.

So it seems I would have been better off using 12.04 as per the article but I'm going the hard way about this and removing Unity, which is far from easy. That had to be found in a thread of it's own: [http://ubuntuforums.org/showthread.php?t=2137021](http://ubuntuforums.org/showthread.php?t=2137021)

And as for enabling 3D acceleration, that didn't seem to improve performance. I appreciate the suggestion though.

---

### Post by MrManican on 2013-08-09
My host box specs:
OS: Win 7 Ultimate
RAM: 8GB
Sys Type: 64-bit OS
Processor: AMD Athlon 64 X2 Dual Core Processor 5000+ 2.60 GHz

Virtual Environment:
OS: Ubuntu 13.04
RAM: 4GB
Sys Type: 64-bit OS
Processor: 1 CPU / Enabled PAE/NX
Acceleration: Enabled VT-x/AMD-V / Enabled Nested Paging
Enabled IO APIC / Disabled EFI
Enabled Hardware clock in UTC time
Enabled absolute pointing device
HD: 100 GB fixed size storage
Network is a attached to a Bridged Adapter and I have a Realtek PCIe GBE Family Controller

---

### Post by MrManican on 2013-08-09
Downgraded to 12.04 and now it runs like a champ as per your instructions. If you find a way to make 13.04 run smooth, I can always upgrade later!

Thanks TheFu!

---

### Post by markbl on 2013-08-11
> **MrManican said:**
> Downgraded to 12.04 and now it runs like a champ ...
If this is the case then I suspect you are not running the current version of VirtualBox (4.2.16)?  You haven't stated the version anywhere here.

---

### Post by himagain on 2013-08-16
Hi there,
OK - Why run on LTS?
Cheers!

---

### Post by novo2809 on 2013-11-27
Having very slow perform when running Ubuntu 12.10 and 13.04 in virtualbox? It’s because Ubuntu can’t use graphics card for acceleration, ubuntu uses CPU for rendering graphics trough LLVMpipe. It makes running ubuntu in virualbox really slow. [http://namhuy.net/951/how-to-fix-slow-performance-ubuntu-13-04-running-in-virtualbox.html](http://namhuy.net/951/how-to-fix-slow-performance-ubuntu-13-04-running-in-virtualbox.html)

To check if your Ubuntu 12.10 or 13.04 guest is using 3D acceleration
```
/usr/lib/nux/unity_support_test -p
```

You should see something like this
```
Not software rendered: no
Not blacklisted: yes
GLX fbconfig: yes
GLX texture from pixmap: yes
GL npot or rect textures: yes
GL vertex program: yes
GL fragment program: yes
GL vertex buffer object: yes
GL framebuffer object: yes
GL version is 1.4+: yes
Unity 3D supported: no
```

If you see “Not software rendered” and “Unity 3D supported” both say no. This means Unity is using slow LLVMpipe.

To enable 3D supported, fist you will need to update linux-headers
```
uname -r
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get autoremove
sudo apt-get install build-essential
```

Now insert vitualbox guest iso from devices and to install manually
```
cd /media
ls
cd username
ls
cd VBOX*
ls
sudo ./VBoxLinuxAdditions.run
```

Insert vboxvideo to /etc/modules
```
sudo nano /etc/modules
```

Add “vboxvideo” at the end of the file
```
loop
lp
vboxvideo
```

Reboot the machine
```
sudo reboot
```

---


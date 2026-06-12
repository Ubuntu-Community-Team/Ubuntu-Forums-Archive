---
title: "Virtualbox Ubuntu Guest is randomly extremely slow"
date: 2013-03-27
forum: Virtualisation
---

### Post by Diadem82 on 2013-03-27
Machine: HP Laptop with intel i5 cpu
Virtualization Software: Virtualbox 4.2.10
Host OS: Windows 7
Guest OS: Ubuntu 12.04 (64 bit)
Virtual machine parameters: 8 GB fixed size hd, 2 GB memory, 128 GB video memory. 3D acceleration enabled, all other settings default.


Installing Ubuntu works fine. No problems during install, and it works flawlessly afterwards. Internet worked fine, I could apt-get without issues, etc. It took me a while to get the guest additions up and running, but that also worked. I was busy trying to mount my shared folder and then ... things just slowed down. When typing on the console it suddenly took up to a minute for the text to appear. Everything else is slow as molasses as well. There doesn't seem to be a reason for this, I have plenty of memory and my cpu is sitting at 12% usage.

I've played around with different settings in virtualbox. I've reinstalled ubuntu several times with different parameters (64 bits or not, IO APIC enabled or not), but the pattern is always the same: It works nice for a few minutes after installing and then slows the hell down.

Perhaps it's some package that breaks the system, but I certainly don't know enough about linux to figure out exactly which one. So I'm hoping someone here recognizes this problem and can help fix it. I did some googling, and I don't seem to be the only one having trouble with a slow ubuntu in virtualbox, but I couldn't really find any solutions. I did install the guest editions each time, but I don't think those cause the problem, since it worked fine for a while with those enabled. Also, not using them is not really an option, since I do need their functionality.

---

### Post by SeijiSensei on 2013-03-27
One possibility is that the physical machine is starved for memory and needs to put things into swap while the VM is running.  I've had that happen on Windows 7 machines with 2 GB of memory.  During the period when the swapping is taking place, the whole machine slows to a crawl.  One obvious symptom of this problem is that the disk activity light will start flashing for a while while the swapping occurs.

I wouldn't allocate more than 768 MB for the Ubuntu guest on a Win7 box with only 2 GB of physical memory.

---

### Post by marks_linux on 2013-03-30
Just to add youre not alone. Though 12.04 ran better than 12.10 for me. I transferred and fired up a mint Nadia VM I had and it runs much smoother. When I get chance I'll try out 13.04

---

### Post by stabby on 2013-05-15
I have the same problem with 13.04. It's not starved for resources - I'm running on intel i7 cpu and 16GB of ram, Windows 7 64 host. Assigned for the vbox 2GB memory and 256MB for video, and enabled 3D support. Increasing and decreasing those doesn't seem to make any difference. Still it's very choppy and has occasional couple-seconds-long complete freezes. That didn't happen with 12.04 or 12.10.

Edit: Reinstalled unity-guest-utils, updated virtualbox to 4.2.12, enabled IO-APCI and increased number of cpu's to 2. Runs much better now. Still not as smooth as native installation, but as long as I don't get those freezes anymore I can live with it.

---

### Post by yeswetran on 2013-05-19
Anyone try Tor or anything like that? VMs, in my opinion. run like Tor. You're basically layering up the insides of your computer, so what I'd do is connect your VM to a wired internet connection alongside a wireless one to boost the download speeds of the iso boots, and try cleaning up Ubuntu once you use it. This guy called Jason Graham wrote a few articles about making this stuff faster:
[http://techod.com/how-to-make-ubuntu-faster/](http://techod.com/how-to-make-ubuntu-faster/)

---

### Post by novo2809 on 2013-11-27
Having very slow perform when running Ubuntu 12.10 and 13.04 in virtualbox? It’s because Ubuntu can’t use graphics card for acceleration, ubuntu uses CPU for rendering graphics trough LLVMpipe. It makes running ubuntu in virualbox really slow.

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

source: [http://namhuy.net/951/how-to-fix-slow-performance-ubuntu-13-04-running-in-virtualbox.html](http://namhuy.net/951/how-to-fix-slow-performance-ubuntu-13-04-running-in-virtualbox.html)

---

### Post by electrohandyman501 on 2013-11-27
I have 5 different VM's that I use for evaluations. I am using VMWare player for my environment.
I've not had any issues with them being excessively slow. Granted they are a LITTLE slower than if they were on the physical hardware as I would expect.
I setup each "machine" with 20Gb single drive, 2 processor cores, 1G ram, auto video settings with NO 3D acceleration(3D caused problems).
I have both 32bit and 64bit guests. My host is Win7 64bit, 4core i3, 4G ram.

Other than my VMWare setup, I am dual booted with 12.10 32bit.

---

### Post by TheFu on 2013-12-20
If the LLVM stuff doesn't solve the slow performance, here's [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) a detailed virtualbox setup for performance article that has worked well for many, many people.

---

### Post by beetee2 on 2013-12-24
> **TheFu said:**
> If the LLVM stuff doesn't solve the slow performance, here's [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) a detailed virtualbox setup for performance article that has worked well for many, many people.

I tried that link, and it did absolutely nothing for me. Now I'm trying the LLVMPipe stuff.

FWIW my host is a Win7 x64 16GB Ram, 120GB SSD, 1 TB HDD in Raid, Radeon 7970, i7 2500k. It's no slouch.

If 13.10 guest won't work, my next step is to try 12.04.

---


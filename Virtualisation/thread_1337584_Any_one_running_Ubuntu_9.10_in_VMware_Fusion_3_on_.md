---
title: "Any one running Ubuntu 9.10 in VMware Fusion 3 on MBP"
date: 2009-11-25
forum: Virtualisation
---

### Post by jeyaganesh on 2009-11-25
Hi,
I am interested in installing Ubuntu 9.10 on MBP in VMware Fusion 3. Does any one run Ubuntu like this? I saw a youtube video that showing a person running Ubuntu Remix 9.10 in VMware Fusion.:D

---

### Post by VSack on 2009-11-26
jeyaganesh,

Yes, I am running Ubuntu 9.10 Karmic on several machines, including as a VM on my MacBook Pro 5,3.

I've tried Fusion 3, VirtualBox, and Parallels 5 and feel that Fusion 3 has the best performance and features for daily usage (I'm in my VMs ALOT).  Parallels bogged down and had issues, VirtualBox used up a lot of additional resources, and Fusion at least "just works"

The only thing I don't like is that I can't figure out how to Compiz to work.  VMWare doesn't support it, and this means no desktop effects, AWN, etc. :(

I'm including my directions on how to install Tools as well.  Hopefully this helps someone someday :)


```

How to install VMWare Tools on Ubuntu in VMWare Fusion 3 (Difficulty: Easy):

In OSX Host: Click Virtual Machine
Click Install VMWare Tools

In Ubuntu Guest: Copy VMwareTools-8.2.3-204229.tar.gz to your desktop
Extract Contents of .gz
Click Applications > Accessories > Terminal
Type: cd Desktop/vmware-tools-distrib OR cd /home/*YOUR USERNAME*/Desktop/vmware-tools-distrib
Type sudo ./vmware-install.pl
Enter your password

Now you'll see a bunch of prompts.  Unless you are particular or REALLY know what you are doing you can basically bypass all the options by hitting enter every time you are prompted.  VMTools will install itself where it needs to, build the linux headers it needs to, and the rest.  I counted 13 "prompts" I entered through to finish the install.

As per the final instructions of the tools type the following:
sudo /etc/init.d/networking stop
sudo rmmod pcnet32
sudo rmmod vmxnet
sudo modprobe vmxnet
sudo /etc/init.d/networking start

Reboot your VM
Enjoy proper VM drivers, Desktop resizing, clock synchronization, etc.!


```

---

### Post by jeyaganesh on 2009-11-27
VSack, thanks for your nice reply with installation instruction. I think compiz may need more graphic power. I like compiz very much in ubuntu. I will try this soon.

---

### Post by tnsmart on 2009-11-28
So I tried to install VMware tools following those steps but in Terminal, after typing 'cd/Desktop/vmware-tools-ditrib' I get: 'bash: cd/Desktop/vmware-tools-ditrib: No such file or directory'.  What could I be doing wrong?  Thanks.

---

### Post by fjgaude on 2009-11-28
Make sure you are using the right command line protocol. Make sure you know the path to the tools:

```
cd /home/<yourIDname>/vmware-tools-distrib
```

Something like that.

---

### Post by tnsmart on 2009-11-28
> **fjgaude said:**
> Make sure you are using the right command line protocol. Make sure you know the path to the tools:

```
cd /home/<yourIDname>/vmware-tools-distrib
```

Something like that.

Thanks!  I guess I had the wrong path.

---

### Post by VSack on 2009-11-28
> **tnsmart said:**
> Thanks!  I guess I had the wrong path.

My fault, I had just copied and pasted my notes and they were a bit off. 

I fixed them in the original post.

---

### Post by jeyaganesh on 2009-11-29
VSack, Have you tried to activate 'compiz' with 'High performance' graphics instead of 'Better battery life'?

---

### Post by VSack on 2009-11-29
Affirmative.  

I've tried a number of different hacks to attempt to get it to work, but it seems like fundamentally, Ubuntu and VMWare are just not cooperating with one another.

VMWare's Fusion OpenGL compatibility only works with Windows, and more than likely VMWare Tools just isn't even broadcasting to the OS that it can handle 3D graphics.

That being said, I have been testing Fusion vs. Parallels over the weekend because I was tired of being limited by VMWare's lack of attention to Linux.  Apparently, its good enough for them to use Linux for THEIR products, just don't ask them to actually support it when we want to.

Anyway, so far as I have been able to tell, Parallels has much better graphic support but VMWare manages has faster memory processing and less overhead on the host system.

All of my experiences with VirtualBox have ended in tears.  Its always higher in resource usage than the other two running two different VMs at the same time.

Both support forums have people crying for help, but its falling on deaf ears.  

Finally, I need to also clarify:  On Parallels Desktop, I am forced to use 9.04 Jaunty.  9.10 Karmic does not install their tools properly still.  Both VMs seem to have problems with the audio changes in Karmic.

Reverting to 9.04 in VMWare doesn't help, since you still can't get Compiz.

---

### Post by jeyaganesh on 2009-11-30
I am installing Ubuntu on VMware fusion 3 now. But it is stuck at VMware tools easy installation. It says 'VMware Tools is currently being installed on your system. ... please wait for the graphical environment to launch.' 

But nothing happened for 10 mins. I got the VMware fusion by digital download.

Now, how can I enter the graphical environment?

---

### Post by jeyaganesh on 2009-11-30
Success!
I reboot Ubuntu and installed manually using VSack's guidance above. After installation, the CD got unmounted itself. 

Can I delete the 'vmware-tools-distrib' folder in the desktop?

Now I am going to change screen settings according to my MBP screen.:D

Thanks for your help.

---

### Post by jeyaganesh on 2009-12-02
Hi, I got a strange problem now.
Whenever I start the ubuntu, it comes to the desktop and goes back to the black screen of VMware tools installation. I already installed the vmware tools manually.

Anyone know how to stop this? During the startup, the screen resizes itself from small to big and back to small. 

Yesterday I quit the vmware and opened it again. Today I randomly pressed 'ctrl + F' buttons when it is in vmware tools installation. It suddenly came to the desktop and works stable. 

It is sad that vmware fusion only provide basic graphic support to linux.
I have installed Ubuntu in a 4gb USB stick. It works fantastically in a ~4 years old computer. Even compiz fusion works great on it. 

It is pity it doesnt work on MBP. 

Anyhow, please give me suggestion to avoid that vmware tools installation problem.

Thanks in advance!

---


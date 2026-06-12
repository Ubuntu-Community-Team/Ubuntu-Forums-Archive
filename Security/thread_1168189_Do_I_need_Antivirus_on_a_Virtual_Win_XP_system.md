---
title: "Do I need Antivirus on a Virtual Win XP system??"
date: 2009-05-23
forum: Security
---

### Post by N9TA on 2009-05-23
Ok...I admit, I am completely ignorant on this....
I'm running a virtual Windows XP Media Center Edition via VirtualBox on my Ubuntu 9.04 64 bit machine. Do I need a "Anti Virus" program for my virtual Windows XP/MCE system??

           Fred

---

### Post by HermanAB on 2009-05-23
Yes, you need ClamWin and Spybot Search and Destroy as usual.

---

### Post by cariboo on 2009-05-24
It depends on what you are using your XP vm for. I have XP Pro, Vista, Win 7 and Jaunty running in vms. I have not yet felt the need to install antivirus software on the Windows vm's.

---

### Post by N9TA on 2009-05-24
> **cariboo907 said:**
> It depends on what you are using your XP vm for. I have XP Pro, Vista, Win 7 and Jaunty running in vms. I have not yet felt the need to install antivirus software on the Windows vm's.

I'm using the XP MCE virtual machine to sync my Ipod Touch with Itunes, log ham radio contacts with my windows based logger, make house plans with "3D Home", run Quicken, and other misc stuff. Most of the stuff I run is "network aware" at the least....and in some cases (Itunes) network dependent.

I have installed F-Secure Client Security on the VM and have had no problems. If there was a Linux based Itunes....or something that could talk to my Ipod......and a descent ham radio logger, I could SHREAD MS products.......but there is not.

I have learned a lot with Ubuntu....and had some fun, along with some frustrations. However, I'll probably never be able to switch totally to Linux. I've tried it many times over the years....man, like maybe 15 years....and Ubuntu is the closest I've seen yet. 

Most of the time I boot to my primary hard drive which contains Vista.....and will soon have Windows 7.

---

### Post by whoop on 2009-05-24
> **N9TA said:**
> Ok...I admit, I am completely ignorant on this....
I'm running a virtual Windows XP Media Center Edition via VirtualBox on my Ubuntu 9.04 64 bit machine. Do I need a "Anti Virus" program for my virtual Windows XP/MCE system??

           Fred
If you keep files on this virtual machine that you value then you should.

---

### Post by estamand on 2009-05-24
Whether it is installed on a computer or in a virtual machine you still have to protect your installation.

Same goes for linux.  People say it is not 'prone to virus' but there are rootkits/DOS attacks out there that you need to have some sort of firewall as protection as well.

---

### Post by arcane14 on 2009-05-24
if you use the virtual machine to test software of your own, might not be a problem. as someone else said previously, if you keep files on it, you want to protect them. i run xp in virtualbox for itunes and for testing random proggies i'm interested in. but i have a drop box account and i've mapped my home folder, so any files i want to use on the virtual machine i access/write/save outside of it, so no worries if the virtual system comes crashing down.

like @estamand said, it's always good practice to rock a firewall, like the Uncomplicated Firewall frontend for iptables [[ufw]("https://wiki.ubuntu.com/UbuntuFirewall")]

PS Since I'm not too worried about losing my virtual machine, I'm trying out Panda's [[Cloud Antivirus]("http://www.cloudantivirus.com/")]

---

### Post by terrrorr on 2009-05-25
Hi arcane14,

How virtual machine is different than any others stand alone machine. Of course, there is virtual hosts which provide NAT and firewall protection, but that does not give you full secure. Use your common sense.

- I do not want to share any files or folders to machine which is not fully protected
- I do not want to create any kind of connection to Internet if my machine (virtual or not) is not behind firewall.

- Terrrorr

---

### Post by Keithhed on 2009-05-25
> **whoop said:**
> if you keep files on this virtual machine that you value then you should.

+1

---

### Post by bodhi.zazen on 2009-05-26
You should treat virtual machines the same a physical machines.

so whatever you would do to harden Windows on a physical machine, do the same with your virtual machines.

Of course the advantage we have with a VM - snapshots.

---

### Post by arcane14 on 2009-05-26
> **terrrorr said:**
> Hi arcane14,

How virtual machine is different than any others stand alone machine. Of course, there is virtual hosts which provide NAT and firewall protection, but that does not give you full secure. Use your common sense.

- I do not want to share any files or folders to machine which is not fully protected
- I do not want to create any kind of connection to Internet if my machine (virtual or not) is not behind firewall.

- Terrrorr

Agreed. But, for me, the way they are different is that I don't use the vm to do much on the web, if anything. Sine the vm only has read capabilities to the host, it's a one-way street.

To clarify my previous post, I'm always running a firewall on both boxes host and vm. When I'm in the vm testing, like I said, I'm running Panda. However, I'm rarely connected to the net in the vm anyway, which is probably why I'm not as concerned.

---

### Post by bmullan on 2009-05-26
> **N9TA said:**
> I'm using the XP MCE virtual machine to sync my Ipod Touch with Itunes, log ham radio contacts with my windows based logger, make house plans with "3D Home", run Quicken, and other misc stuff. Most of the stuff I run is "network aware" at the least....and in some cases (Itunes) network dependent.

I have installed F-Secure Client Security on the VM and have had no problems. If there was a Linux based Itunes....or something that could talk to my Ipod......and a descent ham radio logger, I could SHREAD MS products.......but there is not.

I have learned a lot with Ubuntu....and had some fun, along with some frustrations. However, I'll probably never be able to switch totally to Linux. I've tried it many times over the years....man, like maybe 15 years....and Ubuntu is the closest I've seen yet. 

Most of the time I boot to my primary hard drive which contains Vista.....and will soon have Windows 7.
maybe you already know about this I saw you mention your HAM radio interest so thought I'd pass on ... 
[https://wiki.ubuntu.com/AmateurRadio]("https://wiki.ubuntu.com/AmateurRadio")

---


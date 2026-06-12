---
title: "How to virtualize windows under 12.04.-precise-64-minimal?"
date: 2013-11-03
forum: Virtualisation
---

### Post by d-hoeller on 2013-11-03
Hello,

I rented a dedicated server and to get windows server os i would need to pay an extra € 25/month which i really want to avioid.

So i am looking for a way to virtualize windows xp or 7 as a guest system under this server.

Please note that i don't want any dicussion on why i want to do that, but i just want it like that.

Can someone help me to get that run?

Kind regards
David

---

### Post by TheFu on 2013-11-03
Do you want remote access to the server and desktop?
Does the server have a GUI or is it 100% CLI?
Do you have ssh-key access to the main server?
Are you certain the server is real hardware and not just a VPS?  Does it support VT-x at the CPU?

Regardless, you have a bunch of software to install. Which to install really depends on the answers above.

Have you tried to do this locally? Which software did you use?  Running a desktop-on-a-desktop is relatively easy, but it becomes harder (only from an understanding and expectations perspective) when ZERO physical access is available.

BTW, I run lots of Linux and Windows in remote servers, so this is definitely possible. Accessing Windows remotely adds additional security considerations that I elected to solve by only allowing a nearby Linux access and using Linux remote access to get to the Windows machine through a secure method.

I look forward to your responses.

---

### Post by d-hoeller on 2013-11-03
Hey,

First of all thank you for the responce.

1. Yes, i want remote access to the server and desktop.

2. The server now has a gui because i installed one, but for the purpose i wanted to use it, it still does not work (need windows). Still i would prefer to install it CLI based as atm i dont get it any virtualization running when i try to install it gui based. So i also would reset the server in the 1st place if someone shows me a way to get everything needed installed CLI based. (So far I installed ubuntu-desktop + tightvncserver and also have gui based access)

3. I have ssh access.

4. it is a real hardware and no vps. The cpu is an Intel Core i7-3770 so i guess yes.

@ 2: i am totally not into Linux, but i got it run somehow after tons of research. still it seems the installtion is somehow not complete cause when i try to run splashtop, teamviewer or virtualbox i allways get error messages like 'failed to recv data from socket' or 'connection as been gracefully closed'.


Ah and yes, i got totally no physical access to the server.

---

### Post by TheFu on 2013-11-03
> **d-hoeller said:**
> Hey,
First of all thank you for the responce.
Happy to help. This is fun for me too! ;)

> **d-hoeller said:**
> 1. Yes, i want remote access to the server and desktop.
To the server, I would use ssh. No GUI.  Create ssh keys on your current client (usually ssh-keygen), then use ssh-copy-id to the server. That should be it. You will never be asked for a password again.  If non-standard ports are used, setup a ~/.ssh/config file with the name you like, userid, port and real, approved IP or hostname.  It makes a nice record.  Sorry - if you your client machine is MS-Windows, I havent a clue how to make it this easy. Putty is great for what it does, but I got frustrated and loaded Linux to get a full X/Windows environment years ago. Managing Linux from Windows sorta ... sucks.  Mainly I missed the select/paste facilities built-into X/Windows across every terminal, every program, every where. That added step - -copy- sucked to me. ;)

> **d-hoeller said:**
> 
2. The server now has a gui because i installed one, but for the purpose i wanted to use it, it still does not work (need windows). Still i would prefer to install it CLI based as atm i dont get it any virtualization running when i try to install it gui based. So i also would reset the server in the 1st place if someone shows me a way to get everything needed installed CLI based. (So far I installed ubuntu-desktop + tightvncserver and also have gui based access)
VNC is not secure and slow for desktop productivity stuff.  I prefer running FreeNX on the server and NoMachines v3.5.x nxclient remotely. It works GREAT from Windows too. Best of all, a secure ssh tunnel is part of the NX protocol, so you dont need to add anything more. Turn down the Ubuntu Desktop _cheese_ ... use LXDE, remove Unity. You have already seen how poor the GUI performance is over the internet.  NX is 2-3x more efficient compared to all the RDP and VNC solutions.  I use it for my daily-use desktop in a private cloud.   The newly released NoMachine v4.x clients suck, IMHO, plus never got one of them to connect to a FreeNX server.  Google -freenx ubuntu- for setup instructions. Should be about 20 minutes if you follow those closely. There are 2 main manual steps - generating new server-side keys and taking the key to your client.
[http://blog.jdpfu.com/2012/10/23/remote-desktops-rock](http://blog.jdpfu.com/2012/10/23/remote-desktops-rock) explains a little about where we are headed.

It is possible to do everything with a CLI interface, but if you are new to Linux, it is unrealistic for you to learn that much quickly. Linux is like learning a new language - 6 months min _immersion_ is needed to begin to get a handle.

Then you want to install KVM and virt-manager.   **sudo apt-get install kvm virt-manager**
That will get you everything you need for virtualization, I believe.

Which desktop do you have at home? If Linux, life will be easier because you can run virt-manager directly and it will use an ssh tunnel (and your ~/.ssh/config file settings) to connect directly to the remote VM host. From there, you setup the KVM VM for Windows. It is much like VMware player, vSphere, VirtualBox, .... .  Nice GUI.  

Before you setup any VM, read this: [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) to avoid making poor choices on the settings that will make your Windows VM slow. Highlights are:
* do not use sparse HDD allocations - use RAW storage, fully preallocated storage (not qcow2, not VMDK, not VDI).
* As with a smart Windows install - 2 partitions - -a- for OS/Apps and -b- for data. (sorry, Im experimenting with a different remote desktop and the single-double-quote keys dont work) ;)
* use the SATA driver
* disable disk caching for the VM - the hostOS will do that.
* use ICH-based chipsets wherever possible - not P4iii
* use the Intel Pro/1000 ethernet driver
* enable both ACPI and APIC
* use Cirrus video - there are issues with all the others unless you really know what you are doing.
* Allocate the amount of CPU and RAM needed for the clientOS workload, not more. For Linux desktops, that is usually 1G of RAM and 1 vCPU.  For Windows media center, 1.5G of RAM and 1 or 2 vCPUs.
Anyway, there are subtle settings in that link - learn the ideas and apply them to KVM VM settings.  Someday I will write a KVM settings how-to.

Before you setup the Windows VM, come back - we need to create a bridge on the Linux side. The automatic bridge is not as stable as a manually created bridge.  However, if you screw this up, you will loose remote access.  How many IPs do you have?

> **d-hoeller said:**
> 3. I have ssh access.
Excellent. We want to use this for everything possible, including Windows. Setup key-based access - NOT passwords.

> **d-hoeller said:**
> 4. it is a real hardware and no vps. The cpu is an Intel Core i7-3770 so i guess yes.
Nice.  You probably have 6G-32G of RAM?

> **d-hoeller said:**
> @ 2: i am totally not into Linux, but i got it run somehow after tons of research. still it seems the installtion is somehow not complete cause when i try to run splashtop, teamviewer or virtualbox i allways get error messages like 'failed to recv data from socket' or 'connection as been gracefully closed'.

Remove all those programs.  Virtualbox will get in the way of KVM.  Virtualbox is great for desktop-on-desktop use, but not for remote servers.  Use **sudo apt-get purge** ... you want to remove every part of those things to limit the danger of interference with KVM.

I hope this was clear. If not, ask.  BTW, who installed Linux on the remote machine?  Is LVM2 available?  It would really make your hostOS storage faster and much more flexible for the VMs.  **sudo parted -l** output would be helpful ... since it is unlikely that your default install set things up good for a VM host.

Update - See [http://blog.jdpfu.com/2013/11/03/setup-kvm-virtualization](http://blog.jdpfu.com/2013/11/03/setup-kvm-virtualization) for a diagram of how using KVM works.  I will steal some of the text from above for the article.

---


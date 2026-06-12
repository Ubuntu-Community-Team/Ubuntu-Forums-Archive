---
title: "Virtualbox XP guest slow networking"
date: 2013-12-08
forum: Virtualisation
---

### Post by migs73 on 2013-12-08
Hi folks

I am running the latest virtualbox (from the Oracle website) on a 13.10 host with XP pro Guest. I have guest additions installed, and it seems to work fine except for the network speed. Downloading anything on the internet is very slow.
Googling this problem returns the advice to change the virtual network card to another type. Tried this but to no avail, but it also has some issues on any of the Intel type virtual cards, as my XP says it does not have the drivers for them. I thought this was one of the things included in the guest additions?

I have read bridged may also help but as this has DHCP issues (?) which may be a bit beyond my current expertise (or lack of it!!).

Any help/how to's much appreciated.

Mike

---

### Post by bashiergui on 2013-12-09
> I have read bridged may also help but as this has DHCP issues (?) which may be a bit beyond my current expertise (or lack of it!!).Are you saying you had DHCP issues when you tried bridged? Or you're worried about issues? If you have a router then there should not be any DHCP issues. How do you connect to the internet?

Bridged means that your router will see the Windows XP VM as another separate computer on the network. XP will get an IP address and so will your computer. Bridged mode might improve the speed.

---

### Post by codenine75a on 2013-12-09
I would check your network throughput using the task manager.  Network lag is the worst.  It could come from almost anything under the sun.

---

### Post by migs73 on 2013-12-10
> **bashiergui said:**
> Are you saying you had DHCP issues when you tried bridged? Or you're worried about issues? If you have a router then there should not be any DHCP issues. How do you connect to the internet?

Bridged means that your router will see the Windows XP VM as another separate computer on the network. XP will get an IP address and so will your computer. Bridged mode might improve the speed.

No I hadn't tried it because I saw how to's talking about having to set up DHCP for the VM, didn't realise that you r existing DHCP server could do it! That is good news, I'll give it a try.

If that doesn't work I'll take a look at my network speed.

Anybody any ideas why my virtual Intel cards ask for a driver disc even although I have guest additions installed? Do I maybe just have to point the driver install tool to the virtual guest additions CD?

Thanks

---

### Post by bashiergui on 2013-12-10
I've run hundreds of vms in VB and the one constant thing has been I've never had a driver issue. It just gets handled automagically. My method to troubleshoot the driver thing would be build a new VM with the same .iso, but I would give it more disk space. That seems to have fixed many of my oddball issues in the past.

---

### Post by DuckHook on 2013-12-11
I've had the same issues as migs73 and my XP Pro VM installs do not work on Intel Pro NICs without installing Intel drivers. The only virtual NICs that work out of the box for me are the PCnet series, which are awful. The Intel Pro desktop NIC works with every Linux-based guest, but some distros will be obscenely slow while other distros work at almost bare metal speed. Oddball guests like Minix and Hurd are especially touchy and I've learned that you have to really fiddle with the settings to get optimal results. With the right settings, the speed-up can be amazing though.

@migs73

For XP you may wish to try the VirtIO driver. It has to be downloaded from the Fedora site [here]("http://alt.fedoraproject.org/pub/alt/virtio-win/latest/images/") (yes, it's Fedora, but it works on most any distro host). Unlike the other virtual NICs that are fully virtualized (and so carry all of the attendant overhead), the VirtIO NIC is paravirtualized which means that you are running your network at least partially on bare metal. The speedup for Windows is significant.

You can try switching between NAT and bridged to see which gives you better performance. There are no rules here. There are so many factors in play that you can only establish the best combination through personal experimentation.

---

### Post by TheFu on 2013-12-19
Sorry to be late. Been on travel for awhile and behind nasty country-wide filters that blocked much of my access....  anyway.

You probably already know this, but WinXP support ends in a few months, so I hope this is just a test system. Regardless, this article [http://blog.jdpfu.com/2010/06/22/virtualbox-performance-improved](http://blog.jdpfu.com/2010/06/22/virtualbox-performance-improved) that I wrote in 2010 describes how to get about 50% better disk and network performance for WinXP under virtualbox.
The best, quick, answer is to download the WinXP Intel PRO/1000 drivers from the intel.com website and install those inside your VM, then select that card to be provided inside the VM-settings (virtualbox) for that WinXP VM.  It doesn't matter what your actual, physical, network card is to the VM. Only the virtual hardware will be known.

We are assuming that you have enough CPU and RAM to make this worthwhile.  Very little can be done to make centrino or sempron-based systems perform with virtualization well.  A Core2Duo or better CPU is really needed to be happy.

To bridge or not to bridge.  You can setup a private, DHCP network that is only used for VMs inside VirtualBox **OR** you can select "bridged networking" which will make the VM a fully functional client on the network - just like every other network client.  I use bridged networking exclusively here.

After you get the new NIC driver loaded, you might want to tune the rest of the VM settings following [this guide]("http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox"). Many people have found this helps get nearly native performance for guests.  Desktops with GUIs are hard to get good performance, so be certain to turn down all the graphics stuff - go for the Win95 interface.

Good luck and please post back if you have issues or success!

---

### Post by migs73 on 2013-12-22
Thanks Guys, lots of things to try!

FYI this VM was on a AMD sempron single core Laptop, but (as suggested by The Fu) this was just to slow and was killing the battery very quickly.
It is now on a Centrino Core Duo with both OS's getting a Core each and it runs a lot faster and it has two batteries so lasts longer. The network speed is still slower than I would expect, so I'll still give some of your suggestions a try.
Also I know XP support finishes soon, this system is to run some old software I need for my job, some of which doesn't like newer versions of windows (mind you I don't like the newer versions either!).

I'll report back and let you know how I got on,

Thanks

Mike

---

### Post by bashiergui on 2013-12-22
> Also I know XP support finishes soon, this system is to run some old software I need for my job, some of which doesn't like newer versions of windows (mind you I don't like the newer versions either!). If that software runs locally (not on the internet) and you don't use email or browsers in XP, there's no reason not to run it after support ends. Create the files in XP, then email/upload them using Ubuntu.

---

### Post by TheFu on 2013-12-22
> **bashiergui said:**
> If that software runs locally (not on the internet) and you don't use email or browsers in XP, there's no reason not to run it after support ends. Create the files in XP, then email/upload them using Ubuntu.

Is the networking going faster?  We really want to help.

As to running an unpatched OS on a network - **air-gap** is the key-word of the day.

---

### Post by migs73 on 2013-12-23
Hi there,

Tried to install the VirtIO drivers but XP sees the driver as corrupt (I will maybe try again later).
Tried the Intel drivers and these installed fine and seem to have improved performance greatly, I was even able to stream video (although I'll never need to do this!).
I also tried some of the other performance enhancing ideas, and there seems to be a marked improvement.

So thanks again, 

Thread solved

:D

Mike

---


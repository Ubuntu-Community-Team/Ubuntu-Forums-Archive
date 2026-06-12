---
title: "Virtualbox on a Flash Drive"
date: 2013-02-26
forum: Virtualisation
---

### Post by daniell59 on 2013-02-26
I just installed Virtualbox on a flash drive. My initial observatiion is- very slow, like watching paint dry.

---

### Post by meteorrock on 2013-02-26
What are the hardware specs on your comp? My hypervisor is near native, no lags here. Could try Xen if you are on a lower end hardware computer. 

Those hypervisors are more for workstations, performance on laptops and lower grade computer towers do have some performance issues.

Make sure you have memory swapping enabled along with your BIOS  Intel-vt or AMD-v/rvi virtualization enabled for a speed boost.

---

### Post by squakie on 2013-02-26
What is the host OS, and what OS did you install in the guest (the VM)?

---

### Post by DuckHook on 2013-02-27
The problem is:> flash driveA VM is resource killing in the best of circumstances. Running from a flash drive is like expecting a hive of bumblebees to lift a jetliner. I run a CLI Ubuntu minimal install from a flash drive. The results are okay. I've also tried Lubuntu. Let's just say, molasses flows faster. A VM on top of that? I'm surprised it doesn't just give up the ghost.

Your biggest blockages will be disk I/O, especially if your guest OS resorts to swap. If you can shoehorn the whole VM into RAM, then aside from a slow load, things are better, but still huge slowdown whenever the OS goes to cache, writes to temp or loads any large library. And the gods help you if your Windows guest schedules a disk scan during your session.

It's an interesting experiment, though...

---

### Post by Bucky Ball on 2013-02-27
*Thread moved to **Virtualisation**.*

Not sure why you posted in ***Absolute Beginners*** when you have 575 beans ...

It will *not* improve your chances of help, just the opposite. Posting in the correct section will improve your chances of more specific help. ;)

---

### Post by mastablasta on 2013-02-27
> **daniell59 said:**
> I just installed Virtualbox on a flash drive. My initial observatiion is- very slow, like watching paint dry.
 
did you install portable virtualbox and then boot live? it works relatively fast for me (2GB ram, USB 2.0, windows starter, AMD E450 1.6Ghz, Lubutnu or AntiX is the OS)

---

### Post by squakie on 2013-02-27
I just wondered if it's also a Windows 8 host and a 12.xx vm.  If so, there are posts on the forum and on the net for things you have to do to try to get it to run faster.  I finally got 3d acceleration enabled so it does run faster, but I've still got problems where it just really doesn't run right - not Ubuntu's fault.  I know it I tried booting from the Cd to load the VM, and it was WAY WAY slower in previous version of Ubuntu AND an older version of Windows and VirtualBox.   So, it's not Ubuntu, but it my case at least it's having a Windows 8 host, virtualbox and Ubuntu 12.xx.  So, besides just the difference in speed by running from a Live media (particularly if a USB flash drive), if it's a Windows 8 host it may be slowing you down.  
 
Just my 2 cents worth based on my trying Ubuntu 12.xx in virtualbox with Windows 8 as the host (this is also on a Dell laptop).  Don't know if it will help you or not.

---

### Post by daniell59 on 2013-02-27
I just realized that my post has been moved. I should have posted here.
My host is Ubuntu 12.04 64. I want to create a windows machine in which I can run Quick Books. So far everything is working, but very slowly. I am not sure whether I can use another Flash drive and have VB recognise it so that I can upload data.

---

### Post by DuckHook on 2013-02-27
> **daniell59 said:**
> I want to create a windows machine in which I can run Quick Books.

Why does it need to be on a flash drive? Why not your HDD? Even if you manage to get it running quickly, having a mission-critical app like Quickbooks running inside a VM on top of Ubuntu on a flash drive strikes me as living rather dangerously, don't you think?

If you want the Quickbooks data to reside on the flash drive, that can easily be arranged without running a whole VM from the stick.

You are creating a very fragile architecture.

---

### Post by daniell59 on 2013-02-27
> **DuckHook said:**
> Why does it need to be on a flash drive? Why not your HDD? Even if you manage to get it running quickly, having a mission-critical app like Quickbooks running inside a VM on top of Ubuntu on a flash drive strikes me as living rather dangerously, don't you think?

If you want the Quickbooks data to reside on the flash drive, that can easily be arranged without running a whole VM from the stick.

You are creating a very fragile architecture.

I want it for portabilty. For instance, I take a trip somewhere. I will be able to access from any computer.

---

### Post by DuckHook on 2013-02-27
> **daniell59 said:**
> I want it for portabilty. For instance, I take a trip somewhere. I will be able to access from any computer.

I see. And if you back up to the cloud, I suppose that this will safeguard your data too. So long as you are aware of how brittle your computing model is, then it is a workable solution for you.

To increase speed, you may wish to use an external USB HDD instead. I also understand that flash drives come in many different I/O speeds, though I've never been able to figure out the designations on sticks. You would benefit from the fastest stick you can find.

Your system considerations will be similar to people who use SDDs so you may wish to read [this]("http://ubuntuforums.org/showthread.php?t=2081873") thread, especially post #8 from @oldfred.

---

### Post by C.S.Cameron on 2013-02-27
USB3 flash drives are getting cheap.

---

### Post by pixiq on 2013-02-28
It might work better with a USB3 pendrive, because many standard pendrives have very slow flash, slower than USB2. But you cannot expect it to be really fast unless the computer has a USB3 port.

---

### Post by daniell59 on 2013-02-28
> **pixiq said:**
> It might work better with a USB3 pendrive, because many standard pendrives have very slow flash, slower than USB2. But you cannot expect it to be really fast unless the computer has a USB3 port.

I only have USB 2.0.  That wont change anytime soon.

---

### Post by pixiq on 2013-02-28
If you have only USB2 on the computer, you will still get an improvement with a USB3 pendrive because the flash hardware will not limit the speed. But the improvement is not at all as big as if you get USB3 on your computer too.

---

### Post by daniell59 on 2013-03-01
> **pixiq said:**
> If you have only USB2 on the computer, you will still get an improvement with a USB3 pendrive because the flash hardware will not limit the speed. But the improvement is not at all as big as if you get USB3 on your computer too.

I man consider adding a USB 3.0 card.

---

### Post by pixiq on 2013-03-01
> **daniell59 said:**
> I man consider adding a USB 3.0 card.
I suggest that you ask (maybe in a new thread with a good title) if someone can recommend a USB 3 card, that can be used to boot USB 3 pendrives. There used to be problems with some old types of cards.

---

### Post by daniell59 on 2013-03-01
> **pixiq said:**
> I suggest that you ask (maybe in a new thread with a good title) if someone can recommend a USB 3 card, that can be used to boot USB 3 pendrives. There used to be problems with some old types of cards.

Thanks, that is a good idea.

---

### Post by daniell59 on 2013-03-03
I formatted the Flash Drive then reinstalled everything with a later version of Virtualbox. For some reason everything is much faster. Not bad at all. If I can only get it to recognize the second Flash Drive so that I can install data.

This is what I get. Virtualbox is not currently allowed to access USB devices. You can change this by adding your User to the Vbox group. I could not figure out how to do this.

Any insight into this problem will be appreciated.

---

### Post by pixiq on 2013-03-05
I think you do it in the host system like this:

Edit the file ```
/etc/group
``` to contain a line with

```
vboxusers:x:119:daniell
```

- where the number (119) might be another one. Don't edit that!

- and the user name (daniell) should be the one in your host system for the user running Virtualbox (you). Edit this if necessary!

---

### Post by squakie on 2013-03-05
Be sure you have installed the virtualbox addons as well.  They give you USB support.  As far as preserving data across boots, a lot of apps and their data sometimes as well get installed in the file system starting at /.  Having a 2nd USB flash drive may not be the solution you hope for.  I would get the largest USB flash drive I could (say around 32gigs), then use unetbootin to install to the USB drive and ask for persistence and give it about 20gig or so for that, then try it and see.

---

### Post by daniell59 on 2013-03-06
I tried the first code that you gave me. It said permission denied. I am getting to think that this is not a practical solution. Everything has slowed down to a crawl. I tried to put data in with a CD. I was not successful.

---

### Post by TheFu on 2013-03-06
> **daniell59 said:**
> I tried the first code that you gave me. It said permission denied. I am getting to think that this is not a practical solution. Everything has slowed down to a crawl. I tried to put data in with a CD. I was not successful.

Trying to run any full OS off a USB2 drive is crazy IMHO.  I only do it long enough to install an OS to a real disk or SSD.  I will run Puppy or TinyCore from USB, but those Linuxen will load 100% into RAM.  Hoping to run Windows off a USB2 drive* ... crazy,* IMHO.
I have USB3 drives too (spinning and flash). These are faster, but there are queuing issues that make USB terrible for OSes. They are fantastic for data.

Ok, on to the performance tuning stuff for VirtualBox. I have a blog article just about that here: 
[http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)

**Highlights**
* preallocate the virtual disk
* use virtIO for disk and network drivers
* if you can't use virtIO, use SATA and Intel PRO/1000 drivers (Microsoft)
* set video RAM appropriately for your needs
* disable 2D/3D GPU acceleration until after install
* install the guest additions for desktops and if you want hostOS/clientOS disk sharing

Lots of other important settings in that article too that I can't recall now.

Would you consider using a remote desktop instead?  I think you would be happier, if you have broadband connectivity.  I do this myself - even for my daily use desktop.  The window I'm typing this reply into is a VM running on a different system in a private cloud.  I've used it from 6-14K miles overseas multiple times and found it very acceptable.  I'm using a FreeNX server and NoMachine's nxclient (Windows/Linux).  For desktop productivity, it is more than sufficient and 2x-3x more network efficient than VNC or RDP methods.

I'm not the only person doing this "thin client" computing.
[http://yieldthought.com/post/31857050698/ipad-linode-1-year-later](http://yieldthought.com/post/31857050698/ipad-linode-1-year-later)
[http://blog.jdpfu.com/2012/10/23/remote-desktops-rock](http://blog.jdpfu.com/2012/10/23/remote-desktops-rock) explains more. Check out the comments.

---


---
title: "VBox vs. vmware 7"
date: 2012-04-07
forum: Virtualisation
---

### Post by terrykiwi83 on 2012-04-07
Is VMware as good as VirtualBox? I have never used VMware, only Virtualbox. Would be interesting to see what people think of them?

---

### Post by uRock on 2012-04-07
Moved to its own thread. Please do not hijack other people's threads.

---

### Post by Dedoimedo on 2012-04-08
What do you mean by good?
Stability, ease of maintenance, performances, features, price?
Did you mean Workstation 7, which costs some 189 dollars?
Dedoimedo

---

### Post by haqking on 2012-04-08
> **terrykiwi83 said:**
> Is VMware as good as VirtualBox? I have never used VMware, only Virtualbox. Would be interesting to see what people think of them?

what is good ?

They both do the same in my experience from a desktop point of view, if you are talking enterprise level then obviously Vmware wins.

I personally use Virtualbox extensively at home

---

### Post by devinwhite717 on 2012-04-10
VMware is better than Vbox with great feautures you can download the latest version  here:

[http://www.vmware.com/](http://www.vmware.com/)

---

### Post by lincoln32 on 2012-04-10
I like virtualbox since it will work on older computers that do not support virtul machines in hardware. (old desktops ect) VMware is good on servers
but our AZ server team has just started using PROXMOX both on desktops and servers with great success [http://www.proxmox.com/](http://www.proxmox.com/)  and might be another direction to look at. also KVM is another good solution for a server.

---

### Post by 1clue on 2012-04-10
VMware is enterprise-level software.  They have free-to-use products and they have contributed to Open Source, and they're pretty much bullet proof.  I use it professionally at work, but the licenses for their "really good stuff" is way beyond what a regular home user could afford.  The good news on that front is that most of the features available on the "really good stuff" are for managing dozens of VMs which all need to remain operational all of the time.  If you're using these features in more than an academic way often enough to make them helpful then you're not a home user.

I haven't tried their desktop/small server stuff for quite awhile, so I can't comment on that but back when I bought a license for their desktop setup it was the best thing going for a desktop vm.


Speaking to other solutions, if you just want to turn on a VM every now and then and only need to use it when you're logged in, then try virtual box.  It seemed pretty good when I played with it.

KVM seems to be the free solution people use for serious work.  It's a lot more work to get working IMO than VMware but as far as I can tell it does what it needs to do.  I never tried anything fancy and I never used it in any professional capacity.

If you're using only free software you can stop reading here.

<soapbox>

There seems to be a lot of fear, uncertainty and doubt regarding commercial software on VMs.  There is nothing to worry about, even if it's a Linux-based virtualization solution.  If you call the company in question to find out about licenses for virtual machines, they're just happy you're trying to be legitimate rather than using stolen software.

Virtualization is here to stay on Enterprise software.  Every large software company supports virtualization to some degree, and most of them support it in ways most people haven't thought of yet.  Lots of small businesses use virtualization.  Most medium sized ones do, and I'm betting there's not a single fortune 500 that doesn't make heavy use of virtualization.

License-wise on the guests all these things are identical:  Every virtual machine needs to have licensed software on it.  This includes Open Source licenses, which have requirements even if you never bothered to read the agreement.  Installing Windows on a VM needs a Windows license.  Copying that VM to two new places and then running them all at the same time requires 3 Windows licenses.  Running Microsoft Office on them requires an Office license for each VM, same as if it were hardware.

Speaking to Microsoft and licenses:  There are lots of combinations available.  They're all easy to read and understand, and if you're confused you can call the Microsoft guys and tell them what you're trying to do, and they'll direct you to the cheapest and best fit for your situation.  They'll help you get up and running right away, and then you have x number of days before the trial licenses expire.  There are some licenses that are not advertised and may have options that fit you nicely.

If you wind up talking to the Microsoft guys -- and I usually do -- just be honest with them.  Tell them for-profit or education or small business or just a home user screwing around.  Tell them if it's for production or for testing.  Tell them if you're going to install it once and leave it, or if you'll scrape it off every now and then and install it again.  They have licenses that take all that into account, and it helps the guy figure out where you're coming from.

Another thing that might ease your conscience is that the people who answer the questions about which license aren't the guys who provide the license.  They'll tell you which one works best for your situation and then you go buy it somewhere else.  There's no gestapo coming around to break your kneecaps just because you asked questions.

</soapbox>

Hope that helps.

---

### Post by ajmc on 2012-04-10
I would go for the VBox since it's free and have not not experience a problem with.  I created VMs on company operations and never failed me.

---

### Post by FatFrog on 2012-04-10
If you have the spare hardware, VMware ESXi is free. 
You can install it as the host OS on a dedicated box and then using the vSphere client (also free) you can build VM's fairly easily.

Plus, its an excellent way to get a grasp on enterprise level VM management...

However, there isn't a client for vSphere that runs on linux. so you'll probably still have to run a VirtualBox Windows guest locally to get vSphere to work. 

I have also seen some instructions on running a headless VirtualBox server on Ubuntu, but I haven't tried that

---

### Post by 1clue on 2012-04-10
One of these days I'm going to do a serious KVM installation.  Right now I don't have the extra hardware.  KVM looks to be a serious approach worthy of attention, I just haven't had the opportunity to try it out.

There's a lot of Open Source software out there that is worth using.  There's quite a bit that's as good as the commercial competition.  There are a few that are so outstanding as to be a whole lot better than the commercial competition in every way that matters, to the point that even the Windows Masses notice.  Apache's httpd comes to mind, as does mysql.  KVM looks to be one of these in a couple years IMO, at least for a medium sized installation.

---

### Post by forrestcupp on 2012-04-11
Performance aside, if you're just setting up some VMs on your personal computer, VirtualBox is a heck of a lot easier to use and set up than to do the same in the free versions of VMware. If you don't believe me, compare installing an OS in VirtualBox with Guest Additions with installing an OS in VMware player with VMware Tools.

VirtualBox makes everything as easy as can be. And from what I've heard, the performance is pretty close.

---

### Post by dcstar on 2012-04-12
> **forrestcupp said:**
> 
.........
If you don't believe me, compare installing an OS in VirtualBox with Guest Additions with installing an OS in VMware player with VMware Tools.


Yep, very tough to select the "Install VMware Tools" menu item in the guest VM using VMware Player - it almost wore my mouse out doing it.

Seriously, even installing VMware Tools on a Linux system is trivial.

---

### Post by forrestcupp on 2012-04-12
> **dcstar said:**
> Yep, very tough to select the "Install VMware Tools" menu item in the guest VM using VMware Player - it almost wore my mouse out doing it.

Seriously, even installing VMware Tools on a Linux system is trivial.

They must have changed things then. You used to have to download the VMware Workstation trial and extract Tools from it to be able to install them in Player. They must have made things easier.

---

### Post by DWade on 2012-04-12
So KVM is only on a Linux machine?

With Virtual box I have the same version on both Linux and Windows with my virtual setup to be used on either host.

You can't do that with VMware Unless you buy both Linux and Windows versions.

---

### Post by haqking on 2012-04-12
> **DWade said:**
> So KVM is only on a Linux machine?

With Virtual box I have the same version on both Linux and Windows with my virtual setup to be used on either host.

**You can't do that with VMware Unless you buy both Linux and Windows versions**.

not sure if im reading you wrong there.

However you can use a VM from vmware on virtualbox and a VM from virtualbox on vmware, you can also use a VM built on Linux on windows or one that is built on linux in windows.

OVF is platform independant also if you dont want to reconfigure your vdmk

---

### Post by DWade on 2012-04-12
Sorry, what I meant was;

I have a windows partition, 2 linux partitions, and a extended partition with large data partion and a swap partition.

The data partition has 2 XP viturals a windows 7 virtual and a windows 8 consumer preview testing virtual, wereby I can be in windows and use the virtuals or in Ubuntu 11.10 or Ubuntu 10.04.

So all parameters are the same in each 3 hosts for the guests.

---

### Post by CharlesA on 2012-04-12
> **DWade said:**
> So KVM is only on a Linux machine?

Correct.

> With Virtual box I have the same version on both Linux and Windows with my virtual setup to be used on either host.

You can't do that with VMware Unless you buy both Linux and Windows versions.

You can move images between Vmware and Vbox.

The only hitch I have run into is that I have to convert any VMs I have running on ESXi to VMplayer before Vbox would read the disks. I'm guessing that is due to how ESXi does snapshots or deltas or whatever.

---

### Post by DWade on 2012-04-13
Yes, you can move images, but I was talking about one computer with three boot partitions, using the same virtual disk.

For instance I am in windows and open a windows xp virtual with a graphic's programs. and begin designing a brochure. I stop save everything and reboot and go into Ubuntu and load up the same virtual XP and finish the brochure.

You can't do that very easily with VMware. and If you purchase VMWare you have to buy both Windows and Linux Versions. You can download trials of VMware for 30 days and test, but... That thirty days is from the date you sign up and download the file and get the serial key.  I know I tried using one at a later date it wouldn't work.

---

### Post by CharlesA on 2012-04-13
That's only for VMware workstation.

You can use VMware player, but it doesn't have the ability to take snapshots iirc.

---

### Post by DWade on 2012-04-13
I just went to VMware.  I guess I will be doing some more testing.  Things have changed since I last tested VMware. There are all kinds of Products there, although more geared for commercial office infrastructure, but sure has changed.

Although Virtualbox is getting better with every release.

---

### Post by 1clue on 2012-04-13
KVM runs on linux only, but that's the host, meaning the OS running on the bare metal.

I understand it runs a windows guest just fine, although I have never tried.

---

### Post by DWade on 2012-04-13
2 items.  In Virtual Box you can edit the HD UUID, the Machine UUID and the Hardware UUID, using Libre office.  Making the Hardware UUID the same as the Machine UUID.  

Can you do the same in VMware.  

Because when you make the virtual disk, edit it set it up then you can go to another partition using a different Distro and set it up the same with the same machine, hardware, and harddisk UUID's. in the system parameters.  This will stop if you load windows 7 or Vista from asking you reactivate. 

Otherwise if you don't edit and set it up for the existing disk it will run and then ask to be reactivated. I know cause it happened to me several times before I got it right.  then its a hour with microsoft getting a new activation code.

If I run the VMware player can I use the Virtualbox virtual hard drive and setup the parameter the same and UUID so it won't ask to be reactivated?

---

### Post by DWade on 2012-04-14
> **CharlesA said:**
> 
You can move images between Vmware and Vbox.

The only hitch I have run into is that I have to convert any VMs I have running on ESXi to VMplayer before Vbox would read the disks. I'm guessing that is due to how ESXi does snapshots or deltas or whatever.

I downloaded and installed VMPlayer in Ubuntu 11.10. Player is simular to VBox, but you do not know what your hardware is. and it only recognizes vmdk images, or vmx, ovf. or ova.

Wereas Vbox recognizes all of them and will create either one.  I thought I would make a vhd file to see if I could run windows 8 in the Windows 7 Virtual PC after I installed it in Virtualbox, but it requires 128 megs of video ram or it won't work.  I now wish I'd made it a vmdk file.

You can convert with VBoxmanage to any format.

Next I tried to get to the bios settings but everytime it booted, it by passed settings no matter how many times I hit F2 or CTRL+G [capture keyboard] and the F2.  That must be a workstation only function

The USB transfer rate is about the same as virtualbox.  The new player is a big improvement over the last one I used some time ago...

---

### Post by DAB4970 on 2012-04-15
I have used VMware Player recently in an academic setting on their Windows network with XP as the host.  For some reason they couldn't keep their software up to date.  It seemed the version they were using had some stability issues, and they really needed to upgrade their workstation hardware.

I have tried both VMware and VBox on my Ubuntu host and the same stability issues with VMware seems to arise.  Then I tried VBox.  And I really haven't had a single issue with using VBox.  I haven't tried KVM or any other solution at this time.  But for right now, I stick with VBOX!  I enjoy using it without issues/hassles!

---

### Post by sixstringssteve on 2012-04-17
Like many of these guys have said, it depends what you are doing.  If you are playing at home using VMware Player is fine, as is VirtualBox.  Once I really got into VM's I ditched VBox, just too slow.  With ESXi being free and all, just go with the platform you are going to be able to use in an enterprise environment.  Ubuntu loves VMware, unlike the hiccups with Hyper-V.  Vbox is a great tool for learning, but other than that it is not really cut out for high demand situations.  I reccomend picking up a cheap multi core box with a bit a RAM ($400 at Tiger) and build you an ESXi 5 box and dive in, Virtualization is an exciting area to be in nowadays.
 
Good Luck
 
Steve Melcher
CCNA, SSCP, MCTS

---

### Post by DWade on 2012-04-17
> **sixstringssteve said:**
> Like many of these guys have said, it depends what you are doing.  If you are playing at home using VMware Player is fine, as is VirtualBox.  Once I really got into VM's I ditched VBox, just too slow.  

Which version of Virtual box is too slow?

VM Ware Player runs to fast on the boot, it too me about 50 boots before I could see, F2 Setup  and the middle still haven't gotten.  end F12 Network boot.

You have to have mouse ready to strike and F key ready to depress.
and to Uninstall VMWare of any kind is [sudo vmware-installer -u PRODUCT   e.g. vmware-player Workstation 8.02 etc.]  took me awhile to find that.

---

### Post by dzponce11 on 2012-04-19
VirtualBox is much better. I learned the hard way how difficult it is to get internet in a VMware vm.

~~~~dzponce11

---


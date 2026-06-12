---
title: "Physical to Virtual:Vbox"
date: 2010-04-04
forum: Virtualisation
---

### Post by Jazusa03 on 2010-04-04
Im using a 10.04 beta 2 install of ubuntu on a dual boot system with windows XP. what I'm wanting to do is be able to run Windows XP under virtualbox while in Ubuntu. the problem: I dont have an installation CD of Windows XP, and my Recovery disk will remove all partitions if i use it not just restore windows. I'm fairly new to virtualization so do try to be specific if possible.

right now i have a 200gig HD with 100gigs set to Ubuntu and 100gigs set to WinXP. I'm hoping to reduce the WinXP partition size, and convert it into a .vdi. I only have 1 copy of WinXP with 1 license. So I either have to figure out how to pull WinXP out of my restore CD so it doesnt erase everything or move my exhisting installation of XP to Vbox.
](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by HermanAB on 2010-04-04
Howdy,

Yes, it can be done, but after going to a whole lot of trouble to set it all up, you are still likely to find that it is unsatisfactory to do the switcheroo.

The problems with switching between dual booting and a virtual system mainly concern the switching over of the video driver between the real one and the virtual one and the MS registration nonsense.

So, to use a car analogy: Pick a gear and drive in it.
;)

---

### Post by Jazusa03 on 2010-04-04
> **Jazusa03 said:**
> Im using a 10.04 beta 2 install of ubuntu on a dual boot system with windows XP. what I'm wanting to do is be able to run Windows XP under virtualbox while in Ubuntu. the problem: I dont have an installation CD of Windows XP, and my Recovery disk will remove all partitions if i use it not just restore windows. I'm fairly new to virtualization so do try to be specific if possible.

right now i have a 200gig HD with 100gigs set to Ubuntu and 100gigs set to WinXP. I'm hoping to reduce the WinXP partition size, and convert it into a .vdi. I only have 1 copy of WinXP with 1 license. So I either have to figure out how to pull WinXP out of my restore CD so it doesnt erase everything or move my exhisting installation of XP to Vbox.
](*,)](*,)](*,)](*,)](*,)](*,)

I Also Failed to mention that my copy of XP does not have an I386 file in the "C:/" drive only in the "C:/Windows/I386" which is useless if your making a CD.

---

### Post by TJet1.8 on 2010-04-06
If you want to convert a physical machine to virtual, I would suggest downloading VMware's vCenter Converter Standalone:

[http://downloads.vmware.com/d/info/datacenter_downloads/vmware_vcenter_converter_standalone/4_0](http://downloads.vmware.com/d/info/datacenter_downloads/vmware_vcenter_converter_standalone/4_0)

It is a free download and will convert any physical Windows/Linux machine to a Virtual Machine. In the conversion process, it automatically strips out any hardware specific drivers and leaves you with either a pretty plain generic driver set...or with the VMware Tools driver set if you wish. It will also allow you specify the amount of RAM, Processors, etc...you want in the vm and can take any hard drives and shrink the Virtual Hard Drive down to whatever size you want...based on the amount of data you have on your drive.
It is an EXTREMELY handy tool.

There are some caveats though...but not a big deal:

1.) The resulting image will be in VMware's format. This means that the virtual hard disk will be in .vmdk format. This is not a problem as the VBoxManage command line can convert the .vmdk file to a .vdi file for you.

2.) You need to install the vCenter Converter in your Windows XP, and start the conversion with the vm files being saved on another computer somewhere on your network. You cannot create the vm and save the files on the same physical computer you are converting.

Good luck....:p

---

### Post by BuRbUzZi on 2011-03-28
You can also try Paragon Go Virtual (don't remember the exact name of it, you can Google it). It's small and can convert Physical Windows machine to virtual in desired format (I used VirtualBOX).

---


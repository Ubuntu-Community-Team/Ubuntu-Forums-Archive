---
title: "Best way to put XP on Ubuntu?"
date: 2007-11-07
forum: Virtualisation
---

### Post by Apex-jb on 2007-11-07
I want to run XP in 7.10 but Ive never used any virtualization software. What is the best, free, way to run XP in Ubuntu? I've looked at VMware but I dont have a key and I havent been able to find a guide on how to install VMware Player.

---

### Post by Scunizi on 2007-11-07
I use VMWare Server (free).  When you go to vmware.com and click the server page there is a link for getting keys.  That shouldn't be an issue.  Once you download VMWare, right mouse click and uncompress.  It will create a new folder.  Now from a terminal type 'sudo apt-get install build-essential' .  It will install a bunch of stuff you need to get VMWare working.  Mostly compiler stuff.  Now still in the terminal navigate to the new uncompressed folder.  Like 'cd /home/<username>/Desktop/<vmfolder>.  

Once inside the folder there will be a file end with .pl or .sh (I can't remember).  Type sudo ./<filename_exactly>' then hit enter.  It should install and will ask you many questions.  Just keep the defaults.  You should have an item show up under the Applications/System Tool portion of the menu to start VMware.

Remember when in the terminal syntax, caps, small characters etc can make a huge difference.  If you don't type thing right, nothing will happen.

---

### Post by viking777 on 2007-11-08
FWIW  I have just put xp pro onto virtualbox and it worked like a dream. The only problem I ran into was usb support and that was solved when I was told on this forum that if you want usb you cant use the version of virtualbox that is on the ubuntu servers (the ose version) you have to go to the virtualbox website and download the 'puel' version. Then it all works.

And BTW I have never used virtualisation before so it was all a complete stab in the dark for me, but unusually it worked!

---

### Post by Humph on 2007-11-08
I've just installed XP Pro on VirtualBox 1.5.2 r25433 and, much to my considerable surprise, it's running faster than it did when it was not virtualised! I now have a < 10 second boot time!

Edit: Oh, and this is my first time with virtualisation too!

---

### Post by Calash on 2007-11-08
Virtualbox is a newer product, but they have been advancing a lot and the current release with Gutsy has improved the stability to the point that I use it exclusively now.  Virtualbox can play sound, something that VMWare Server lacks.  Networking is a bit more difficult in VB if you need a direct connection.  There are some nice guides on how to 'Bridge" your connection to vB

The "Seamless" mode is nice, still buggy but a good first step.

---

### Post by Apex-jb on 2007-11-08
So I downloaded Virtualbox and installed it. I added ```
deb http://www.virtualbox.org/debian gutsy non-free
``` to my sources.list but I dont really now what this means,
    > * The innotek public key for apt-secure can be downloaded here. You can add this key with
```

      apt-key add innotek.asc
```

    The key fingerprint is

   ```
 6947 BD50 026A E8C8 9AC4  09FD 390E C3FF 927C CC73
    innotek GmbH (archive signing key) <info@innotek.de>
```

And I dont know the commands for these. 
  >  You will need to install some additional libraries on your Linux system in order to run VirtualBox - in particular, you will need libxalan-c, libxerces-c and version 5 of libstdc++. How to install these will depend on the Linux distribution you are using.

---

### Post by voided3 on 2007-11-09
> Virtualbox can play sound, something that VMWare Server lacks.

I have sound working fine with both Vista and XP on VMware Server, you just have to add an audio adapter in the virtual hardware settings. I use XP on Vmware for listening to radio on iTunes all the time.

---

### Post by serfcx on 2007-11-09
> **Apex-jb said:**
> So I downloaded Virtualbox and installed it. I added ```
deb http://www.virtualbox.org/debian gutsy non-free
``` to my sources.list but I dont really now what this means,
    

And I dont know the commands for these.

If you use synaptic to install software then open it up, search for "VirtualBox" and it should come up. When you ask synaptic to install it will take care of these dependancies for you. Dont worry about not adding the key it will just give you an error message when updating synaptic.

You will get a message about adding yourself to the vboxusers group during installation. This can be done by going to "administration --> users and groups" and manage groups and then click on vboxusers, click properties and put a tick against your name. Make a note of the group ID as you will need it to get usb working.

To get usb working you will need to add the following line to your /etc/fstab file

none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0

Replace the 1001 with your group ID number obtained from above.

You may also need to add the following to the end of your kernel line in /boot/grub/menu.lst file

nmi_watchdog=0

I had to with both Gutsy and Studio to get it working.

To fully get the benefits of XP working well in Vbox get hold of 
VBoxGuestAdditions_1.5.2.iso - there is a link in their forums someplace but I cant remember where. Lots of other good info there as well.

Good luck

---

### Post by TheExplorer on 2007-11-09
2 Apex-jb:
Just download the key file, cd to that directory and type:
```
 sudo apt-key add innotek.asc
```
It will be added.

2 serfcx:
Thanx for the usb code. Didn't even tested usb under Virtbox + XP. Will try in the evening :)

---

### Post by Apex-jb on 2007-11-10
How can I store the hard disk file for a virutal machine on another partition? I can only set it to store it on ubuntus partition which is not big enough to hold both systems.

---

### Post by serfcx on 2007-11-10
> **Apex-jb said:**
> How can I store the hard disk file for a virutal machine on another partition? I can only set it to store it on ubuntus partition which is not big enough to hold both systems.

If you want to create aseperate partition for your virtual guest then you will have to use something like Gparted to resize one of your existing partitions.

What are your current partitions and sizes ?
Are you dual booting with XP ?

Give more info and maybe we can help. Partitioning can lead to unforeseen problems with existing data so you will have to have somewhere to backup.

---

### Post by Apex-jb on 2007-11-11
> **serfcx said:**
> If you want to create aseperate partition for your virtual guest then you will have to use something like Gparted to resize one of your existing partitions.

What are your current partitions and sizes ?
Are you dual booting with XP ?

Give more info and maybe we can help. Partitioning can lead to unforeseen problems with existing data so you will have to have somewhere to backup.I currently have 3 partitions set up. Two 5Gig, one has Ubuntu, the other has XP, and the third is just extra space where I store all my files.

---

### Post by serfcx on 2007-11-11
> **Apex-jb said:**
> I currently have 3 partitions set up. Two 5Gig, one has Ubuntu, the other has XP, and the third is just extra space where I store all my files.

What is the total size of your disc drive as the comment above does not give the size of the space you use where you store your files

Does your ubuntu partition contain your /home partition or is this part of the 3rd partition ?

If you all ready have XP as a dual boot will you still keep it after getting the VM setup ? 

You can always create an extra partition in your 3rd partition using Gparted Live CD, about 5 gb should be good, format to ext3 and mount as /storage. Then you can use this partition to mount your VM. If this existing partition is fat32 or ntfs for windows access (you didn't mention the format) then you will have to defrag several times to try and minimise data loss.

Reading between the lines you dont seem to have much space at all to try and do what you are wanting to do un less you can liberate the 5Gb you currently have for Windows.

Just make sure you backup any vital stuff :wink:

---

### Post by Apex-jb on 2007-11-11
My extra partition has about 30 gigs. My Ubuntu partition does conatin /home, I didnt know you could put it somewhere else. Im not sure If im going to keep XP on dual boot after I get it working as a VM. It depends if I can get my wireless working on campus under Ubuntu.  And completley repartitioning the entire hard drive is no problem. I have plenty of external hard drive space to save any files I need to, which isnt many. Im thinking I may just reformat my ubuntu partition to 10 gigs and use half of it for the VM. Although you said if I make a partition and mount it as /storage I will be able to access it under Virtualbox and use it? Exactly how would I do that? I have a Knoppix 5.1 live CD that I use to partition my hard drive with.

---

### Post by serfcx on 2007-11-12
Hi Apex,
During the creation of your VM you will be asked where to install, you can then choose where - the default is in your /home partition but you can change this to /storage

---

### Post by viking777 on 2007-11-12
> **serfcx said:**
> If you use synaptic to install software then open it up, search for "VirtualBox" and it should come up. When you ask synaptic to install it will take care of these dependancies for you. Dont worry about not adding the key it will just give you an error message when updating synaptic.

You will get a message about adding yourself to the vboxusers group during installation. This can be done by going to "administration --> users and groups" and manage groups and then click on vboxusers, click properties and put a tick against your name. Make a note of the group ID as you will need it to get usb working.

To get usb working you will need to add the following line to your /etc/fstab file

none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0

Replace the 1001 with your group ID number obtained from above.

You may also need to add the following to the end of your kernel line in /boot/grub/menu.lst file

nmi_watchdog=0

I had to with both Gutsy and Studio to get it working.

To fully get the benefits of XP working well in Vbox get hold of 
VBoxGuestAdditions_1.5.2.iso - there is a link in their forums someplace but I cant remember where. Lots of other good info there as well.

Good luck

Sorry to disagree here but the version on the repositories (ose version) does not have any usb options in it. I spent a whole day messing with it to try to get usb to work and it doesn't. To get usb options you need the 'puel' version from the Innotek web site. The 'ose' version doesn't even have a usb entry in the settings menu.

---

### Post by ColdFusionEESG on 2007-11-12
> **Calash said:**
> Virtualbox is a newer product, but they have been advancing a lot and the current release with Gutsy has improved the stability to the point that I use it exclusively now.  Virtualbox can play sound, something that VMWare Server lacks.  Networking is a bit more difficult in VB if you need a direct connection.  There are some nice guides on how to 'Bridge" your connection to vB

The "Seamless" mode is nice, still buggy but a good first step.

Hey Calash,

Well you seem to know your VB and more importanantly the networking options.  So hopefully you can explain a few things to me ;-)

First I should say I'm a web app programmer and data guy...so I'm not afraid of any tech.  That said, my Linux knowledge is pretty lean and my networking is mediocre.

My Setup:
Ubuntu Gutsy 7.10
VirtualBox 1.5.2 running XP Pro fully patched
wired NIC (the office)
wireless NIC (home network..Linksys WRK54G..Atheros card)

My Situation:
Networking over NAT in VB at the office works perfect

Networking over NAT in VB at home (wireless) is VERY odd!!  McAfee VirusScan can update itself, Windows Auto-Updates work (but not if I go to Windows Update in a browser...page not found), and 2 websites can be browsed (my company site and a site we built for a client).

So that's the weird bit...2 websites are accessible (were already in history list, but not cached views...performed searches on the sites...so 100% sure I'm connected).  Any other site I try won't be found!!

So there is some sort of limited connectivity, but I'll be dammed if I can figure out what's going on.

I like VirtBox, but find the network setup SUPER vague....used to Virtual PC where you actually map to your physical hardware (thus knowing which adapter is which).  In VB you just enable adapters and I assume it picks the functioning connection.

Anyways....and help would be much appreciated.

If I get this last bit working it's bye-bye Windows except for games!!

Cheers

---

### Post by Apex-jb on 2007-11-12
Anyone know whats this means, I got this error when I started to install XP under vitrualbox,

```
STOP:  c0000221 Unknown Hard Error
\SystemRoot\System32\ntdll.dll
```

---

### Post by Runamok on 2007-11-12
Same problem with spotty wireless internet connection through NAT on a virtualbox Windows...    No suggestions?

---

### Post by Runamok on 2007-12-04
ColdFusion,

My spotty wireless has been attributed to the DNS information not being passed onto the guest OS, only at home (linksys WRT54G).  This was solved by manually entering in the DNS settings in the TCP/IP settings while at home, and obtianing automatically while on the road.

---


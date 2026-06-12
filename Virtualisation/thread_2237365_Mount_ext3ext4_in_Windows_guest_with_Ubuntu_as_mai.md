---
title: "Mount ext3/ext4 in Windows guest with Ubuntu as main system"
date: 2014-08-01
forum: Virtualisation
---

### Post by johnyjj2 on 2014-08-01
Hi,

I have just installed Ubuntu as main system and Windows 7 as host (on Virtual Box). I would like to mount ext3/ext4 disc in Windows guest system. I have installed Ext2Fsd on Windows (it launched Ext2 Volume Manager) as it says it is "Open source ext3/4 file system driver for Windows (2K/XP/VISTA/WIN7)". I have mounted my drive in Windows through Virtual Box settings Devices -> Shared Folders Settings. Unfortunately, it does appear neither in My Computer nor in Ext2Fsd application. What should I do to enable this share?

Thanks in advance for help :-)

---

### Post by TheFu on 2014-08-01
Storage should only be mounted by 1 OS at a time.  The normal method for a guestOS to access the hostOS storage in virtualbox is through sharing folders setup inside the VM settings.  It is pretty easy, but has some security risks.  There are many, many, many how-tos here and on the internet for setting this up "virtualbox shared" is the search.  [https://www.virtualbox.org/manual/ch04.html](https://www.virtualbox.org/manual/ch04.html) explains.

Other options are to use any of the network-based file sharing methods and treat the 2 systems just like any other systems on the network.  sftp, ssh, scp, CIFS, are all options for Windows.

---

### Post by johnyjj2 on 2014-08-10
Hi, thanks for reply! I have tried two different apps - one is VMWare and the other Virtual Box. Unfortunately neither of those can support features I require out of the box.

VMWare can defragment virtual machine (this is useful as my disc is slow) and I can simply use "Shared Folders", "Mount as system drive" and I can access data on my main OS (Linux Ubuntu). But it works very slowly and crashes from time to time (it was not available in Ubuntu Software Centre so I guess it is not fully and officially supported). With Shared Folders I can use my Linux data in both places (Ubuntu and Win virtual machine). So perhaps it's not true (at least for VMWare) that "storage should only be mounted by 1 OS at a time".

In Virtual Box virtual machine with Windows 7 x64 works much faster (that's why I use Virtual Box right now) but mounting in Shared Folders does not cause that anything new appears in My Computer (and, less importantly, I cannot find anywhere defragmenting virtual machine). I am still unsuccessful on mounting Linux data on Windows virtual machine with Virtual Box (in VMWare it was very easy) - by what you call normal method in machine settings.

PS Finally I was able to access it with [COLOR=#000000][FONT=Verdana]"My Networking Places" -> "Entire Network" -> "VirtualBox Shared Folders". Is there any way to limit "home network connection" only to VirtualBox Shared Folders and not any other devices or machines in local network?[/FONT][/COLOR]

---

### Post by Morbius1 on 2014-08-10
Did you install the "Guest Additions" in the Windows guest. Then your VBox shared folders in the Linux host will automatically appear as a "drive" in Windows.

---

### Post by JKyleOKC on 2014-08-10
> **johnyjj2 said:**
> In Virtual Box virtual machine with Windows 7 x64 works much faster (that's why I use Virtual Box right now) but mounting in Shared Folders does not cause that anything new appears in My Computer (and, less importantly, I cannot find anywhere defragmenting virtual machine). I am still unsuccessful on mounting Linux data on Windows virtual machine with Virtual Box (in VMWare it was very easy) - by what you call normal method in machine settings.

PS Finally I was able to access it with [COLOR=#000000][FONT=Verdana]"My Networking Places" -> "Entire Network" -> "VirtualBox Shared Folders". Is there any way to limit "home network connection" only to VirtualBox Shared Folders and not any other devices or machines in local network?[/FONT][/COLOR]I run a number of Windows VMs using VBox in an Xubuntu host system and have configured each of them to use the VBox shared folders. Since I'm the only user on my little home-office LAN I've not been concerned with blocking other LAN accresses, but since the "network place" in each Windows VM points **only** to the VBox shared folder server, not to the entire LAN, I think the access restriction you want is already in place automagically.

As for defragging the Windows VMs, I use the Auslogics defragger in each VM itself rather than try to do anything via the virtualization program. The "pro" version of this defragger does an excellent job for me and it's relatively inexpensive; there's a free version as well that you can use to try out, but its capability is rather limited and it cannot consolidate the free space as does the pro version.

I tried "defraggler" once, and it destroyed the content of the drive I was defragging, so I've been reluctant to try it again. Auslogics, however, has been quite solid for me over the past couple of years.

Hope this helps a bit...

---

### Post by SeijiSensei on 2014-08-10
I'm pretty sure the shared folder feature in VirtualBox uses CIFS.  It treats the folder on the host or guest as if it were a network file share.  

Remember that the guest cannot see any of the host's resources except in specific cases like USB.  The guest is confined to the image file you created when you set up the VM.

---

### Post by Morbius1 on 2014-08-10
It certainly looks and feels like cifs except it's zero config since VBox does the mounting all by itself but I don't think it's cifs or samba.

I have a Windows VBox guest on a Xubuntu host and I can disable samba on the host:

sudo service smbd stop
sudo service nmbd stop

And the shared folder is still accessible on the Windows guest - in my case as Drive D.

---

### Post by SeijiSensei on 2014-08-10
I know it doesn't rely on using CIFS on either the guest or host.  I thought it was built into the VB software itself, but I haven't really looked into this in detail.

---

### Post by Morbius1 on 2014-08-10
You know, now that I'm in the Windows guest I may have a possible explanation for the original post:
>   [COLOR=#0000cd]I have mounted my drive _in Windows_ through[/COLOR] [COLOR=#0000cd]Virtual Box settings _Devices  -> Shared Folders_ Settings.[/COLOR] Unfortunately, it does appear neither in  My Computer nor in Ext2Fsd application. What should I do to enable this  share?

You are creating the shared folder while the Windows guest is running. It won't show up as a Drive letter that way until you logoff and reboot the guest again and only if you selected Auto-Mount and Make-Permanent.

I usually create these shared folder within the VBox application itself on the host for that guest and then launch the guest.

Either way you have to install guest additions on the guest for all this to work.

---

### Post by JKyleOKC on 2014-08-10
Hi, Morbius and Seiji! Glad you've jumped in on this; it's getting quite interesting.

As I said, I run a batch of Windows guest VMs under VBox, but normally only one of them is active at a time and the rest are lingering in saved state. I habitually set my host's home directory as a shared folder when creating the VM, and normally do NOT check the auto-open box when creating it. Instead, after firing up the guest and installing Guest Additions on it, I then use "My Network Places" to create a network connection to it, and place a shortcut on the Windows desktop to the resulting network place. I usually give the shortcut the simple name "host."

I then use the host's home directory, or some subdirectory of it, as a transfer point for taking things from one VM to another. I find that the data transfers between guest and host are near-instant, much quicker than using FTP or such. It also allows me to use either the VM or the host tools, as necessary, for the task at hand. All in all, quite convenient.

Now to my point after all this explanation. I did, for one VM, check the auto-mount box when creating the shared folder initially, and found to my amazement that it did, in fact, show up as the next available Windows drive letter when I first fired up the VM. Since I had connected two virtual drives to this VM, the result was that I had C: and E: as virtual drives, D: assigned to the CD/DVD interface, and F: as the host's home directory!

That worked exactly as one would expect were it an external USB drive formatted as ntfs; all file system translation took place automatically and I could both read and write anything in $HOME or below so long as it had appropriate *nix permissions. From the host, all is still ext4. From the guest, it's ntfs. No need at all for ANY external translation program.

I can only conclude that all of this is done by either the VirtualBox program itself, or more likely, the Guest Additions.

Hope this helps one and all...

---

### Post by TheFu on 2014-08-13
Is this solved?

---


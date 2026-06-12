---
title: "Virtual webserver suddenly down and LVM LV gives me i/o errors"
date: 2016-01-06
forum: Virtualisation
---

### Post by hierstehtnormaleinname on 2016-01-06
Hello,
I run a Ubuntu 14.4.03 LTS server as host machine for a virtual webserver. 
[B]
Summary of my system setup[/B]
Physical machine runs two SSDs with 250 GB and two HDDs from Western Digital (RED NAS Edition) with 3 TB.
The two SSDs run in software raid1 and the two HDDs also. On both raid  arrays is a LVM installed, in sum two VGs SYSTEM and DATA.
While the local system (Ubuntu 14.4.03 LTS) is installed on the SSDs  raid, the HDDs raid is used for file storage and also as LVM Group to  store my virtual machines images.
The machine owns two network interfaces, one for the host and the other one isolated for the clients [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

[B]Software in use

Host[/B]
On the host (Ubuntu server 14.4.03 LTS) runs stuff like Samba, Netatalk  and Ufw &#8211; file sharing for the LAN side. And I installed lib-virt  package with the virt-manager to set up my virtual clients.

[B](Virtual) Client
[/B]Runs a Ubuntu server minimal virtual headers (+ virtual extras)  as system. Installed is Apache2 with modules like Php + stuff and also  mod security. Also a CIFS-Client package to mount the file storage  folder directly from the host. Well and several extra packages needed  for our Php installations like image magicks, gdm, xml... and so on. Now  on the virtual server within the Apache server are only two Php  installations (web services): 1. OwnCloud and the 2. ResourceSpace, both  based on PHP, MySql, HTML an CSS.

[B]Additionally 
[/B]For security reasons the virtual client has got his own  isolated network interface right to the DMZ interface of my firewall and  only port 80 and 445 are open.
The second interface is for the host to serve our internal network with  samba and Apples **** Netatalk &#8230; also the host has a folder on the HDD  where all company data and also all data from OwnCloud and Resourcespace  get stored in one place. (only the data our services collect from the  users, not the Php scripts itself, what get stored inside the virtual  machine) &#8211; it's out of the reasons, that OwnCloud shares the same data  externally (WAN) while we already share it in our internal network (LAN)  with Samba &#8230;; therefore I created an direct network link using KVMs  virtual bridge in the isolated mode hardened by firewall rules in the  hosts UFW. So virtual clients can connect to the host over the Samba  port only [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

[B]Problem
[/B]Now this set up ran very good for over a few weeks now. But  today and without any reasons the web server started to stuck. Nothing  seems to help, so I performed a restart and recognised the main problem.

The web server is like already explained a virtual installation of  Ubuntu server within the KVM system. Therefore it needs a place to store  his data (images): This could be files like .raw or .qcow2 or as many  tutorials recommend a LVM logical group where KVM automatically creates a  logical volume within this volume than the data (virtual machine) gets  stored in the raw format. Should give me better performance and you can  use snapshots to backup a running machine [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]


So far that sounds very difficult and so much info [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]  but now let's bring it to the point. I have a logical volume  /dev/DATA/WEBSERVER on my hard disk and it is part of the volume group  DATA. The logical volume worked very well the last weeks and now if I  try lvscan or a similar operation I will get no access any more:

```

:/dev/DATA# lvscan
  /dev/DATA/WEBSERVER1: read failed after 0 of 4096 at 52428734464: Eingabe-/Ausgabefehler
  /dev/DATA/WEBSERVER1: read failed after 0 of 4096 at 52428791808: Eingabe-/Ausgabefehler
  /dev/DATA/WEBSERVER1: read failed after 0 of 4096 at 0: Eingabe-/Ausgabefehler
  /dev/DATA/WEBSERVER1: read failed after 0 of 4096 at 4096: Eingabe-/Ausgabefehler
  ACTIVE            '/dev/DATA/storage1' [2,44 TiB] inherit
  inactive Snapshot '/dev/DATA/WEBSERVER1' [19,53 GiB] inherit
  ACTIVE            '/dev/DATA/WEBSERVER1-bak_final_cloud_resspace' [48,83 GiB] inherit
  ACTIVE            '/dev/UBUNTU/system' [102,45 GiB] inherit
  ACTIVE            '/dev/UBUNTU/swap' [8,80 GiB] inherit
```

Eingabe-/Ausgabefehler is German and means Input/output error

As you see I'm not able to enter this logical volume WEBSERVER1 while  all  other logical volumes in the same volume group are still sane and  run without problems.
I also checked the Raid with mdadm &#8211;> everything perfect.
Than I checked the smart status of all disk -> no errors, everything perfect.


So I only know that just on friend was using the Owncloud web service  for some uploads yesterday (same thing as in the days before). All  uploads get stored in the storage directory (/dev/DATA/storage1) outside  of the virtual machine. But suddenly, he said, the server did no longer  load our Owncloud website and that was the minute my LVMs logical  volume got inaccessible. By the way, he has no system user privileges or  even entrance so no way, nobody did anything to cause this directly.

Before I load a two week old backup now I would like to find out what  has happened with my volume because I would like to avoid the same  situation in a few weeks again [IMG]http://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG][IMG]http://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG][IMG]http://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]

I have no clue what may has happened or caused this. Just one suspicion:  KVM got a set up to reserve 50 GiB for the webserver1 within the volume  group as logical volume if needed but it should only increase the  storage if the data increases over 20 GiB, because I just allocated 20  GiB fix for the beginning what normally should be enough aside this is a  normal function of KVM and other visualisation systems too. ?P
Might this be a reasons for breaking my volume. Also I do not understand  why there are existing some snapshot entries relating to webserver1  within the volume groups config file what nobody has created before for  webserver1 and what also are not existing on the disk?

Any Ideas how I could fix this issue or how I could avoid such failure  in the future. Is it save to use LVM for virtualisation or should I  switch back to regular files like qcow2?

thank you very much

---

### Post by MAFoElffen on 2016-01-07
Just getting clarity--

You are running similar to my 2 main servers, which also just happen to be my KVM virtual host servers. It just so happens that those two servers are my DNS primary and secondary, DHCP primary and Secondary, then my other services running from virtual guest servers. Another server is my storage controller. (I slimmed down from iron, where I had 14 servers). So of my 2 mains... Mine are Ubuntu Server, which run DNS, DHCP, and KVM as native services on those hosts. They are both setup on LVM. So similar to yours? (Only difference is that I do not do Apache.)

You said that:
> 
So I only know that just on friend was using the Owncloud web service for some uploads yesterday (same thing as in the days before). All uploads get stored in the storage directory (/dev/DATA/storage1) outside of the virtual machine. But suddenly, he said, the server did no longer load our Owncloud website and that was the minute my LVMs logical volume got inaccessible. By the way, he has no system user privileges or even entrance so no way, nobody did anything to cause this directly.

...and I'm trying to visualize what you said... Was he on the virtual host or on the virtual guest doing an upload? Is the virtual guest setup on it's own LVM? You said the uploads from the guest go to storage on the virtual host outside the virtual guest? So was there a write error on the virtual host? What was the disk usage at that time? Do you have any kinds of disk usage warnings implemented? I'm trying to figure out your structure... for instance I sometime will setup a virtual guest as being mdadm RAID, LVM, or both... with multiple virtual disks... for test environments... but others I point to my shared storage pool.

I know I have filled my disks in the past before I realized that beforehand, that they were full. Easy to do when you have others adding to storage... Now I have a scheduled scripts that check and warn me if I am getting close, so I can add PV extents.

Other than that... I am also curious to what happened to yours, as my system is very similar to yours.

---

### Post by hierstehtnormaleinname on 2016-01-07
MAFoElffen,
thank you for replying to my question. 

> **MAFoElffen said:**
> Just getting clarity--
You are running similar to my 2 main servers, which also just happen to be my KVM virtual host servers. It just so happens that those two servers are my DNS primary and secondary, DHCP primary and Secondary, then my other services running from virtual guest servers. Another server is my storage controller. (I slimmed down from iron, where I had 14 servers). So of my 2 mains... Mine are Ubuntu Server, which run DNS, DHCP, and KVM as native services on those hosts. They are both setup on LVM. So similar to yours? (Only difference is that I do not do Apache.)


Well,  let me try to explain my set up a little better so you are able to  visualize it. Its similar to your installation but not totally equal.


[LIST=1]
[*]A physical server with two Ethernet cards and four disks is my basic hardware.
This server runs Ubuntu 14.4.03 LTS.
I used the software raid tool of the Ubuntu server installation to get both SSDs into Raid1 and both HHDs into another Raid 1 array (so mdadm is used by default)
The Ubuntu server is installed on my SSD raid. The SSDs are only used for the main system and its software packages.
The "Volume Group" name is "SYSTEM"
- 
[*]The second Raid 1 set up is including the two hard disk drives with 3TByte for each drive (Just because SSDs are to expensive with storage space over 500 MB)
This disks use the "Volume Group " named -> "DATA", because there main purpose is storing data (from users, company, and so on)
Within this VG (Volume Group) is on logical volume (LV) called storage1. All network shares or web services use this volume to store there data.
This logical volume takes in about 2,5 TByte of my 3 TByte total storage of the disk (disks in raid).
- 
[*]On the normal server installation samba (and netatalk for apple) serve the network shares within the LAN.
I do not run those services in a virtual machine because I think its save within my own network to have this services up and running directly on the host system.
The network shares are located within the VG DATA as regular folders within the LV storage1.
- 
[*]I use KVM (lib-virt) to enable virtual machines. Because the host server (as mentioned above) is not available from the WAN side for security reasons.
Now I just ran one webserver as virtual machine. This virtual machine was (is) a Ubuntu 14.4.03 LTS (as the host system) with one difference. I used virtual headers to get a smaller kernel optimized for the usage as virtual machine. This virtual machine uses Apache2 as web server and also the second Ethernet card over macvtap (isolated).
So far there is no direct connection from the virtual machine to my host server. Virtual machine uses the DMZ and the host uses the green LAN side.
- 
[*]Now there is no DNS server on the virtual machine because I use an external DNS server. It runs Apache2 with needed packages only. 
The image(s) of the virtual machine(machines if you count my backups) by itself &#8211; and that's the point where it gets a little tricky :) &#8211; was not stored on the SSDs because they are to small.
Therefore I kept free the rest of my 3TByte drive (You may remember, storage1 has 2,5 TByte only and the rest minus partition table was not allocated).
Now in the virt-manager I defined the Volume Group DATA as storage pool. So whenever I create a new virtual machine, virt-manager will create a new logical volume in the mentioned free space.
That's why there are the logical volumes "storage1", "WEBSERVER1", "WEBSERVER1-backup", "WEBSERVER1-bak_final_cloud_resspace". While WEBSERVER1-backup meanwhile got removed, WEBSERVER1-bak &#8230; is a two week old backup (Clone) of WEBSERVER1. So effectively only WEBSERVER1 was up and running as virtual machine.
- 
[*]So all virtual machine(s) use(used) LVM as storage pool instate of a file. But as I created the virtual machine WEBSERVER1 weeks ago I selected to allocate 20 GByte (19,..) immediately with the option to grow my virtual disk up to 50 GByte (48,...) if needed. Well as far as I know lib-virt is than creating a logical volume with the full space but zero filled. But I do not totally understand the way this features works within LVM storage pools. It's totally clear with regular files as storage pools but I'm not sure how this will help with logical volumes except the possibility, that it may creates a LV with lower space and expands it later if needed but simulates the whole 50 GByte for the virutal machines partition within this group &#8211; well as I said, I did not understood this feature so far on LVM pools.
- 
[*]So now basically the virtual machine image(s) are stored on the HDD and also the data storage is located on the hdd raid but all of them in diffrent logical volumes of the same Volume Group.
Well now I faced one problem. Within the web server of the virtual machine I installed OwnCloud (Something similar to DropBox) what should share all the data the users already stored over the Samba/Netatalk shares what are running on my host machine. But the virtual machines did not have any connection to the host (for security reasons) so I needed to find a way to mount this shares. I tried p9 file drivers first what are absolutley bad with permissions between host and guest, in short, that sh.. is not working right. So I fall back to CIFS (Samba) and installed a internal network link from the host to the guest mounting the Samba shares within fstab of my virtual machine. So please do not get confused now. This CIFS shares use the VG DATA with the logical volume storage1  and work like charm also they to not have any relation to the storage volume of the virtual disks! So OwnClouds (a Php package) php, html, css, js files are located within the virtual machine, also the needed MySql database was stored within the virtual machine but any files uploaded by OwnCloud users where stored witin the network storage on the LV storage1.
- 
[*]In summary nothing within the virtual machine could take much space except of the MySql database (but to be hones 20 GByte of database storage are not realistic at all :P but who knows) because all other uploads got passed directly thorugh the virtual machine right into the network storage outside of the virtual machine.
- 
[*]That's now the very confusing point. Its not the logical volume storage1 what causes troubles. Is the logical volume WEBSERVER1. But all this volume did was storing the virtual disk of my virtual web server and containing a database while reciving uploads over a web site and storing them into the network storage outside the virtual machine.
-
 

I hope you are now in able to visualize my set up a little bit better otherwise I can create a sketch for you? :) 
[/LIST]

 
> **MAFoElffen said:**
> 
...and I'm trying to visualize what you said... Was he on the virtual host or on the virtual guest doing an upload? Is the virtual guest setup on it's own LVM? You said the uploads from the guest go to storage on the virtual host outside the virtual guest? So was there a write error on the virtual host? What was the disk usage at that time? Do you have any kinds of disk usage warnings implemented? I'm trying to figure out your structure... for instance I sometime will setup a virtual guest as being mdadm RAID, LVM, or both... with multiple virtual disks... for test environments... but others I point to my shared storage pool

I know I have filled my disks in the past before I realized that beforehand, that they were full. Easy to do when you have others adding to storage... Now I have a scheduled scripts that check and warn me if I am getting close, so I can add PV extents.

Other than that... I am also curious to what happened to yours, as my system is very similar to yours.

Well he just had access to owncloud what ran as Php package on the virtual machine (web server). Whenever he performed an upload the files where passed right trought the virtual machine into the network sotrage outside of the virtual machine. Only the database (MySql) was stored right in the virtual machine. But it is possible that if somebody may uploaded big files (7GByte or more) that they might got stored in the tmp or swap of the virtual machine until the got moved to the network storage. Therefore I'm not sure about how Owncloud was programmed in detail. So is possible that it performs upload by stream or socket in chunks right through the final location or may upload it totally to a temporare location first before the final storing gets processed. But in both cases the virtual machine has in mimium 20 GB - 900 MB free space so even if he has uploaded a 10 GByte file it should not take all available space until it will be moved to the network storage.

Is the virtual guest setup on it's own LVM? No, it uses the same Volume Group "Data" as the logical volume "storage1" does. But each virtual machine get's a own logical volume within the storage pool DATA (LVM group).

I'm not sure about the disk usage of the virtual machine. I had 4 logical volumes within the volume group DATA. storage1 with plenty of free space. WEBSERVER1 what was active and running with a maximum of 50 GB and a start amount of 20 GB. Also two inactive virtual clones (copys of the logical volume as backup with maximum reserved space of 50 GB but only 900 MB in use).
 I should install some kind of monitoring tool or does lib-virt include such a feature?


But what would happen if the LV what contains the virtual disk has no space left? Will this cause in a major failure or just behave as any other system with no more space left?

---

### Post by MAFoElffen on 2016-01-07
I think we are even closer than we thought... My storage controller for my storage pool has Samba on it, but on a physically separate box.

I remember when we thought 10MB drives were so large that we would never fill them up... I am not a fan of 3TB drives.
[IMG]http://i.kinja-img.com/gawker-media/image/upload/s--105xKdQP--/1088211918398259014.jpg[/IMG]
This is a quote from a big data study that Oracle did on 3TB Enterprise drives:
> 
 In fact, one RAID6 group with 3 TB SATA drives will have 60 times lower data integrity than the RAID6 group with 146 GB FC drives. That&#8217;s 6000 percent! And that&#8217;s just one RAID group of drives.

I was a fan of hardware RAID. I am a major fan of mdadm Linux RAID, and I am the project manager for mdadm-gui. I can tell you that is on hold while I'm in school. I am a fan of RAID1 of system drives (SDD). Think of the concept that SDD of the size you have in Mirror as being pretty reliable. Now think a mirror of a large drive, with not so good a track record. So a mirror of a drive that has problems, if left long enough will affect the mirror's image.

So in that case, if you stripe, instead of mirror (on a large drive) you lose less storage and end up with more chances of success. That has been my experience so far with large drives. But I am paranoid with those. Enterprise drives 2TB and above, I prep first. I do low level formats > verify the disk, to write to very sector as a test, and  to mark out any bad sectors... partition > filesystem > test filesystem ... before I use them. I can tell you it takes time. But I think it is well worth it. Like I said, I may be paranoid... But I've been bitten in the past and learned from that.

Next is on LVM. I used to partitions all > add to PV > extend LV's > extend filesystems ... I quit doing "all" at one time. It I deal out smaller chunks at a time, it's faster... and reserving space as I go gives me some slack to play with if I need it. Such as temp storage for LVM Snapshots and same temp storage for VM backups, before moving over to the storage pool. It's not a matter of net load, as I do fiber channel between those 2 servers and my storage pool. It just seems to work better that way to store temp files in it's own temp LV...

When dynamic sized Virtual disks came out, I was excited ... but the new has worn off them. I went back to allocating fixed sized virtual disks. I'd be interested in what others think, but I went back for dependability and management issues. I could not get past allocating an upper limit that I had to choose anyways (that was always defaulting to max size of my free space) and having it start at a lower space... that and mdadm and LVM is going to do what it wants with those anyways. It sometimes just seemed to get weird'ed out sometimes ... Like it got confused. So I went back and didn't have any of those issues anymore. I seem to be able to grow a VM on a fixed virtual disk with less troubles than having a VM on a dynamic virtual disk. I can't put my finger on that. Maybe that will change later down the road, but... Just how it has worked.

---

### Post by heiko_s on 2016-01-10
I didn't even know that you can assign LVM space dynamically.

In order to eliminate one potential source of trouble, I would disable this dynamic feature and use a fixed 50GB size, the maximum you had set.

So on the host you create a 50GB LV in VG DATA, unformated. Then create the guest or restore. Within the VM, just make sure you grow the file system to reach 50GB in case you restored from backup.

The only downside I see in this is that your backup might take longer, depending on how you backup. Even that can be optimized.

I gave up on libvirt and virt-manager as - in my opinion - they add complexity instead of reducing it - but then I'm not really familiar with it.

The way I see it:

If you create an LV inside the host with dynamic size, min 20GB, max 50GB, how on earth should the guest VM know about this?

Regarding KVM, the only dynamic partition size I know of is when using qcow or qcow2, which creates a file that can grow. I tried that with a Windows 10 guest a week ago using qemu-img to create the something.img file - the guest wouldn't even install. Next I created a fixed 50GB file using fallocate -l 50G /media/user/win.img and now the guest would install.

The only thing in your explanation that isn't clear to me is how you were able to dynamically allocate LV disk space to your guest? Can you post the section of the config file or command? My suspicion is that this is also the cause for trouble.

EDIT: One more thought - is there any chance that the WEBSERVER1 LV was mounted on the host in read/write while the guest was running? That could cause havoc on the file system but shouldn't actually wipe out the LV. But if above theory doesn't hold, this is something to look into. And then it could be a bad disk, of course.

---

### Post by hierstehtnormaleinname on 2016-01-13
MaFoelffen and heiko_s, thank you for your help.

MaFoelffen I understand your points and must admit it would have been a better solution to buy multiple small ssds and stripe the system than two large disk in Raid1. But my company was not willing to spend much money and now I can not change it for the moment. But I will consider that on any further setup. At least I used a fixed size for my LVM now but I'm still not sure if it was previously dynamic or if the radio button of virt-manager just set nothing.

heiko_s I used a older backup meanwhile since repairs (if ever successful) are too time consuming. This time I created the LV within sytem-config-lvm and not with the virt-manager. There where and is definitively no mount point KVM handles it on its own.

 Now I still have no real explanation what has happened. Maybe the PHP tmp folder grew very big since massiv upload of very large files (bigger than 7GB), but PHP was configured to allow 500 MB maximum per file so normally the tmp should be clean after each timeout. 

Well I still do not know why there was a Snapshot in the VG-config file for WEBSERVER1.

Now I just run the new installation with external tmp folder and much more disk space. I will run daily backups an monitor the system for a while to see if it stay in stable state.
By the way, all disks are still healthy I checked it in detail. So maybe a mess with the raid or whatever.

I will respond if anything similar happens again.

Thank you so far ;)

---


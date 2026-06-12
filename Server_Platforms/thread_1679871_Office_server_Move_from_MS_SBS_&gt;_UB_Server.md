---
title: "Office server: Move from MS SBS &gt; UB Server"
date: 2011-02-01
forum: Server Platforms
---

### Post by garethsimpsonuk on 2011-02-01
Hi,

We currently run Mirosoft small business server in our office but it isnt working very well and we dont even use half of the features that come with it. We have decided to make the move to a linux server and I have come up with the below spec. Can you guys have a look and tell me what you think and if you have any suggestions.
 
Base System
	• Ubuntu Server 64 bit with Raid and LVM (8/12GB RAM)
	• Vmware workstation
	• USB + Offsite backups (how can this be achieved?)
	• Remote access
                 (we have remote file access in a webbrowser with windows server, can this be achieved)
	• GUI (ubuntu-desktop installs a lot of bloat is there an alternative command)
	• Webmin
	• Samba setup and configured (worried about this as I always run into issues with permissions!)
	• FTP Server
	• ClamAV
	• Media streaming (suggestions please)
	• VPN (we use pptp at the moment which is great because it requires minimal configuration on the client side
	 
MDADM RAID 5 Array
3x1.5TB 

= 3072 GB

/various  critical smb shares

Do we create raid 5 partitions for the swap or is it better to have 3 independent swap partitions? I think the latter..?

LVM Array
4x 1.5TB
1x 1TB
 
= 10TB

/various non -critical smb shares

I don't really understand LVM but it seems to allow you to combine multiple disks into 1 volume similar to raid 0. The advantage over RAID0 is that if a drive fails you don't lose the whole VM.

VMs
	1. Web development server (internal)
	2. Web development server (internal)
	3. Nagios
	4. Backuppc
	5. Client Portal
	6. Windows VM for windows apps

1 problem I have is that the disks for the raid will be brand new but the disks for the lvm volume all have data on them in ntfs. I (with the help of a linux guru friend) will create the base system on the raid volume and then start copying the data off the ntfs disks one at a time, adding to the lvm array as we go. Is this possible and any tips to help the process..?

Any help would be appreciated. Thanks

---

### Post by spynappels on 2011-02-01
All very doable.

The sharing files through a web browser sounds a lot like WebDav to me.

Are you wedded to VMware for the virtual machines? Ubuntu natively supports KVM virtualisation.

Webmin also can replace the GUI, and it would be better resources wise if it did.

I'll post back tomorrow with some specific help on some specific items you mentioned, it's been a long day.

---

### Post by garethsimpsonuk on 2011-02-01
Excellent thanks very much.

Yes web dav is one option but I was thinking more a web based login where you can access the files and download, a bit like remote web workplace on MS SBS: [http://farm4.static.flickr.com/3516/3965809314_30046d0baf_o.png](http://farm4.static.flickr.com/3516/3965809314_30046d0baf_o.png)

We are tied into vmware as all our VMs are running on vmware and we really like the product and features. I didn't know Ubuntu supported virtualisation natively though, interesting.

I look forward to hearing from you :)

Thanks

---

### Post by spynappels on 2011-02-02
Ok, I've had a think about this and what you are looking for may actually be slightly different to what you first thought.

I am basing this on several assumptions, so if I am wrong go ahead and correct me.

I'd be tempted to get a NAS box which supports iSCSI and use the server as an ESXi host, it is free for standalone servers/hosts.

Use the NAS box for your SMB shares and for the Storage for your ESXi host. Run the various services you need as separate VMs on the ESXi host and also port the existing VMs to the ESXi host.

For backup, most NAS boxes (or NAS distros like FreeNAS) allow you to use rsync for backing up to a remote server. Most should also allow you to plug in a USB HDD and backup to that.

You can do almost the whole thing on top of Ubuntu, but I'm not sure about whether VMware Player allows USB passthrough, or whether it can run and be controlled on a headless box.

---

### Post by garethsimpsonuk on 2011-02-02
Thank you Spynappels for your thoughts and input.

I have tested esxi and it is great but as you know it doesnt support software raid which is why we've gone for ubuntu. Your recomended setup sounds great but we can't afford to buy a nas and may a bit over sophisticated for our needs. 

Also, the main ubuntu OS is the primary OS to be used. The other VMs are low traffic, low priority so the VM performance hit wont be an issue.

Why would you need USB passthrough (although I think it is supported)? We can backup the smb shares over the network to another box or using usb. The VMs might be abit more tricky, we would ideally like to backup the whole vmdks but think the VM would have to be shutdown first.

For VMware workstation we will install gnome.

Many thanks for your comments, they are appreciated :)

-

---

### Post by kgatan on 2011-02-02
• USB + Offsite backups (how can this be achieved?)

Rsync Server on Main Ubuntu and a second machine offsite with Ubuntu and Rsnapshots.
Works well with NAS boxes as well, atleast our QNAP, both sides.

This give you the ability to backup encrypted over the internet using ssh and a snapshot backup so you can restore from diffrent points in time.

You can set it up to store any number of hourly/daily and monthly backups and it only takes up the storage of the changed files.

Its also quite easy to configure.


I use a USB-disk backup at home together with Webmin.

It has some backup options that allow pre and after backup scripts so you can mount and umount the disk before and after backup.
Good if you want to store the USB offsite etc.

---

### Post by kgatan on 2011-02-02
• Remote access
                 (we have remote file access in a webbrowser with windows server, can this be achieved)

Ajaxplorer is a nice looking file explorer for the web built on Ajax. Im not sure how ever if you can tie in the users with it or if you need to maintain double sets of credentials.

No idee regarding how secure it is though.

---

### Post by spynappels on 2011-02-03
Ok, well, as kgatan said, rsync for remote backup will do what you need it to. For backing up the VMDKs, you could put them on their own LVM volume and snapshot that volume, that would not require them to be shutdown.

I presume you have a chassis which will take all the drives you are hoping to shove in there?

Also, if you are putting Gnome on there for the VMware Workstation, you are better off sticking an extra 2 GB of RAM in and installing the desktop on top of Ubuntu Server. That will give you some more flexibility, but I'd still recommend you do not auto-run it. Use the CLI for everything and only fire up the desktop when you really need it, and kill it again afterwards. (Not sure if VMware Workstation likes this....)

I mentioned USB passthrough from the point of view of attaching a USB drive to individual VMs and backing them up that way, but that would not be the most efficient way of doing it anyway.

---

### Post by garethsimpsonuk on 2011-02-03
Yes rsync seems like a good option for backup for the main files and webmin backup also seems good option.

Ajaxplorer seems great! This is just what I was looking for as webmin is too advanced for the everyday user. Hopefully I can it up to allow access to the smb shares only and have finer grained access control. Hopefully we can get the user accounts to sync but if not, we will manage.

Snapshotting the volume sounds good but can this not be done on a raid volume? I'd prefer to keep the VMs on there.

Yes, I usually install the server version and then do apt-get install ubuntu-desktop so that I get the server optimised kernel. Plus, the installer allows me to setup the lamp server etc.

Yes we will be re-using our old server as it is which has 8 GB ram at present. 

I will be upgrading the sata controller to something like this:
[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=260717072440&ssPageName=STRK:MEWAX:IT](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=260717072440&ssPageName=STRK:MEWAX:IT)

I will be buying 3 new drives for the raid array and re-using the old drives for the LVM. This presents a problem in that all of the drives have data on them (NTFS). I'm going to have to do some juggling to move it over:

1. setup base system + raid array
2. copy ntfs1 to raid array temporarily
3. format ntfs1 and create lvm array
4.copy data from raid on to lvm
5. copy ntfs2 to raid
6. format ntfs2 and add to lvm
7. copy data from raid back on to lvm
8. copy ntfs3..and so on...

Is this the best way of doing it? We don't have any spare disks to store the data temporarily. This is around 6TB of data.

Thanks for all the input guys, much appreciated.

---

### Post by spynappels on 2011-02-03
I would have though it should be possible to create LVM volumes on top of a RAID array, but am open to correction on that....

You will have to do the juggling you have described in order to get the data from the existing disks, but the good news is that adding disks to a LVM setup is easy to do and should not give much difficulty, apart from the time it will take.

You seem to have a good grasp of what you want to do, I hope it all goes well for you.

Shout if we can help in any other way.

---

### Post by HugoSerrano on 2011-02-03
Hi!

You only need the Desktop environment to run Vmware right? Servers should stay without Desktop Environment. 
If you got some time to test, install ubuntu server with virtualization support. Then install virt-manager in a pc with Ubuntu Desktop, and you can manage the virtual machines from there.

You can also try vmware-server, don't need X to run. But I think vmware is dropping this... last release was in 10/2009.

Regards!

---

### Post by garethsimpsonuk on 2011-02-06
@spynappels thanks if it wasnt for this forum I would be nowhere!

Yeah you can create LVM on top of RAID so that might be an idea.

@HugoSerrano all of our VMs are in Vmware server for windows so migrating to vmware for linux seems logical. As you say, vmware server is going to be dropped while vmware workstation is actively developed still. We are running a GUI on the server anyway as it isn't a high traffic webserver, it's our own internal fileserver and it will help us to have one (the server has plenty of power to run one)

Thanks for all the help and advice, I have purchased the new drives and sata card and they will be here thursday. I'm sure I'll have some more questions before then :)

---


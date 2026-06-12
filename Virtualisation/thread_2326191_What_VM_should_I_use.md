---
title: "What VM should I use"
date: 2016-05-29
forum: Virtualisation
---

### Post by Alvin_Fletcher on 2016-05-29
Hi there.
My name is Alvin and this is my first post:).
I recently acquired a IBM system: x3250 M2, and am looking at running a few things on it.
[LIST=1]
[*]ClearOS
[*]Teamspeak Server
[*]Possibly more depending on server capability.
[/LIST]
Currently I have it running Ubuntu server as command line and it runs great.
What I would like to do is create a VM so that I have two OS running on the system but I would like to keep overhead to a min hence I currently have Ubuntu server instead of the normal OS.
I would like to have ClearOS as one VM and Teamspeak on a separate VM (most likely using ubuntu).

So if anyone could help me in knowing what VM I should use to obtain this goal that would be awesome, if anyone is willing to help me in a bit of a step by step I would be even happier as my Command line skills are not that great at the moment. :D

Here is the link to my Server that I got:
[http://www.trademe.co.nz/Browse/Listing.aspx?id=1087617848](http://www.trademe.co.nz/Browse/Listing.aspx?id=1087617848)

Regards
Alvin

---

### Post by Alvin_Fletcher on 2016-05-30
Hi there.
If anyone could give me a reason why no one wants to help that would be great?
eg To long/to complicated....

---

### Post by Bill Vincenti on 2016-05-30
> **Alvin_Fletcher said:**
> Hi there.
If anyone could give me a reason why no one wants to help that would be great?
eg To long/to complicated....
Sometimes it takes more than a day for others to find this, and this being a particularly complex request, someone with experience willing to help. There are several different VM's out there and it's always best to research them which can take a lot of time to know which one may suit your need the best - then you may be able to present the question with more information pro's/con's from what you've researched and get other's with such experience to help. 
What have you researched so far?
Being you set up an Ubuntu server via CLI shows you have significant Linux skill. So look at VMware, VirtualBox, QEMU, and there are others.

---

### Post by houstonbofh on 2016-05-30
Holiday weekend? :)

I am just going to mention Free (as in beer) systems that can install bare metal, or very close too it.  (So no Virtual Box)  All have goods and bads...

VMware - Yes, they have a free version, and it is actually quite good.  It is also the standard, and everyone supports it.  You can at any time buy a support contract as well if you get stuck, or hire a certified VMware expert.  But...  There really is no way to install and set it up without at least one Windows Desktop for the think client.  This is a hard dependency.  Also, you occasionally will hear about a cool feature, but it is only in the paid version. Doh!

XenServer - This is kind of a messy space.  The Commercial Xen is open source.  But you have commercial Xen [https://www.citrix.com/products/xenserver/](https://www.citrix.com/products/xenserver/) the FOSS version of same [http://xenserver.org/](http://xenserver.org/) the open project [http://www.xenproject.org/](http://www.xenproject.org/) and the Red Hat / Centos add on that also works on Ubuntu.  The Commercial and the [http://xenserver.org](http://xenserver.org) one are the same, and keep version parity.  The XenProject one is interesting, but different from a lot of the public documentation.  The Red Hat addon is quite good, and can be used with Virt-Manager, but is only supported on Red Hat.  And the Xen versions set up drives their way, by God and damned be what you want! And the images them selvs are not in the "filesystem" but must be extracted with a tool.  If you have a second drive you want to use for backups, do not connect it until after the install. (And you will need to use the tool for backups)

KVM - My choice, so I may be biased.  You can run this on a desktop, or on a JEOS install with networking.  Since it is on top of Linux, you can do anything with it you can do on Linux.  The direct access to VM images sure is nice.  (rsync anyone)  It is also very fast when tuned right.  And Virt-Manager works natively with it, and the one running right now on my desktop is connected to 5 VM servers currently.  Best of all, you can buy support from Canonical if you need it at any time!  (and it is the most common choice for OpenStack)  Documentation is at [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) and yes, my name is on some of it.  (I just cleaned up a lot of bridging documentation)

---

### Post by CharlesA on 2016-05-30
Giving my +1 to KVM mainly cuz you can run it natively on Ubuntu.

With that said, I've used with VMWare (ESXi), Hyper-V, and VirtualBox and so far dealing with KVM has been working fine for me.

I manage it via [Proxmox]("http://www.proxmox.com/en/"), rather than the command line, though.

---

### Post by Alvin_Fletcher on 2016-05-30
> **Bill Vincenti said:**
> Sometimes it takes more than a day for others to find this. Thanks for the reply, and noted, I am just a bit excited to get learning.
What have you researched so far? - Yes
So look at VMware, VirtualBox, QEMU, and there are  others
> **houstonbofh said:**
> KVM - My choice, so I may be biased.You may be biased but the internet has many great reviews of that
> **CharlesA said:**
> Giving my +1 to KVM Thanks for that feed back

So here is some more information.
I have spent tones of time on google looking at many different types but there is so much information that I cant figure what I want, I was first looking at LxC/LxD, But am finding it might not do what I want.
Particularly that I want the Ubuntu server to preferably remain CLI if possible to reduce overhead, so will any VM work where the host is CLI but they have a gui.
After more research from trying LxC/D I then started looking into OpenVZ and KVM

The Base Idea of what I wanted to Ubuntu Server running in CLI using "x" to then host a virtual ClearOS and a Virtual Ubuntu OS.
So I guess my first question would be, can you have a have a GUI OS running in a CLI OS?
If not what could I install a temp GUI system (eg mate) then remove it later once those systems are operating virtually?
I do apologizes if im not explaining myself well as im still learning the system.
Thanks

---

### Post by CharlesA on 2016-05-30
You can have a GUI installed, but it isn't usually recommended for servers.

You can administer kvm via virt-manager being forwarded over SSH, but you can also just install a basic GUI and go from there.

See here: [https://help.ubuntu.com/community/KVM/VirtManager](https://help.ubuntu.com/community/KVM/VirtManager)

My server does not have a GUI installed, but I use Proxmox almost entirely to deal with KVM configuration and console access to the VMs. I do not use LXC, which is something Proxmox supports.

---

### Post by Alvin_Fletcher on 2016-05-30
Thank you for that.
I ll have a look at get back to you if I choose to go this root :P:D

> **CharlesA said:**
> You can have a GUI installed, but it isn't usually recommended for servers.

You can administer kvm via virt-manager being forwarded over SSH, but you can also just install a basic GUI and go from there.

See here: [https://help.ubuntu.com/community/KVM/VirtManager](https://help.ubuntu.com/community/KVM/VirtManager)

My server does not have a GUI installed, but I use Proxmox almost entirely to deal with KVM configuration and console access to the VMs. I do not use LXC, which is something Proxmox supports.

So Would you say that Proxmox would offer better functionality over Virt? they both do look like good chooses.

---

### Post by CharlesA on 2016-05-30
> **Alvin_Fletcher said:**
> So Would you say that Proxmox would offer better functionality over Virt? they both do look like good chooses.

I haven't really used virt-manager myself, but it should offer the same functionality. The difference is likely GUI program vs Web-interface.

---

### Post by Alvin_Fletcher on 2016-05-30
> **CharlesA said:**
> I haven't really used virt-manager myself, but it should offer the same functionality. The difference is likely GUI program vs Web-interface.
Thanks for that info.
Im guessing the One you use is the GUI Program (Based on there site), Just confirming. :-)

---

### Post by Bill Vincenti on 2016-05-31
> [COLOR=#000000]If not what could I install a temp GUI system (eg mate) then remove it later once those systems are operating virtually?[/COLOR]
If you choose to install a GUI, you might want to go with something much lighter than Mate, maybe Xfce? there are others much lighter than Xfce too, Gnome stuff tends to install a lot of things you might not want down the road and might have difficulty removing.

---

### Post by Alvin_Fletcher on 2016-05-31
> **Bill Vincenti said:**
> If you choose to install a GUI, you might want to go with something much lighter than Mate, maybe Xfce? there are others much lighter than Xfce too, Gnome stuff tends to install a lot of things you might not want down the road and might have difficulty removing.
Thanks for that info, I will keep my options open.

---

### Post by houstonbofh on 2016-05-31
On my primary KVM server at home, not only does it not have a GUI, it does not have a video card!  And it is running a few Ubuntu desktops, and several Windows desktops and servers!  I use virt-manager to manage it (LOVE IT!) and it can connect to the GUI desktops via VNC or Spice, and the user selects it.  Note that with spice, you will want to set up ssh keys, or you have to log in several times for each device...

---

### Post by Alvin_Fletcher on 2016-05-31
> **houstonbofh said:**
> On my primary KVM server at home, not only does it not have a GUI, it does not have a video card!  And it is running a few Ubuntu desktops, and several Windows desktops and servers!  I use virt-manager to manage it (LOVE IT!) and it can connect to the GUI desktops via VNC or Spice, and the user selects it.  Note that with spice, you will want to set up ssh keys, or you have to log in several times for each device...
Thanks for the feed back. Haven't heard of VNC or spice so will have a look. Thanks :-)

---

### Post by houstonbofh on 2016-05-31
No need...  You install KVM on the server and install the virtmanager client on your desktop.  Connect to the server and open the VMs.  It just works, transparently.

---

### Post by Alvin_Fletcher on 2016-05-31
> **houstonbofh said:**
> No need...  You install KVM on the server and install the virtmanager client on your desktop.  Connect to the server and open the VMs.  It just works, transparently.
Hi there.
What would you say that Virr-Manager has over the other recommended software (primarily: [COLOR=#000000] [/COLOR][Proxmox]("http://www.proxmox.com/en/"))?

---

### Post by MAFoElffen on 2016-06-01
One note, that server model came with differing CPU "choices." Some of those CPU's where not vt-x capable. You may want to confirm that it is.
```

egrep -wo 'vmx|lm|aes' /proc/cpuinfo  | sort | uniq | sed -e 's/aes/Hardware encryption=Yes (&)/g' -e 's/lm/64 bit cpu=Yes (&)/g' -e 's/vmx/Intel hardware virtualization=Yes (&)/g'

```
Next, that server only had 4 RAM slots requiring DDR2 ECC Ram, with an 8GB maximum (4x2GB). That might be tight for what you are talking about, especially if you go GUI on the Host's OS (on your IBM XServer). (Hypervisor host's OS + ClearOS Guest + Teamspeak Server + Possibly more guests).

What is your processor and RAM?

---

### Post by Alvin_Fletcher on 2016-06-01
> **MAFoElffen said:**
> One note, that server model came with differing CPU "choices." Some of those CPU's where not vt-x capable. You may want to confirm that it is.
```

egrep -wo 'vmx|lm|aes' /proc/cpuinfo  | sort | uniq | sed -e 's/aes/Hardware encryption=Yes (&)/g' -e 's/lm/64 bit cpu=Yes (&)/g' -e 's/vmx/Intel hardware virtualization=Yes (&)/g'

```
Next, that server only had 4 RAM slots requiring DDR2 ECC Ram, with an 8GB maximum (4x2GB). That might be tight for what you are talking about, especially if you go GUI on the Host's OS (on your IBM XServer). (Hypervisor host's OS + ClearOS Guest + Teamspeak Server + Possibly more guests).

What is your processor and RAM?
Hi there, for details check out [here]("http://www.trademe.co.nz/Browse/Listing.aspx?id=1087617848").
I do plan on getting more ram, am looking at upgrading it to either 1gig or 2gig sticks depending on what I can find.
Ill run that code most likely tomorrow night, unless I get a chance tonight. I know another test they get you to type in for LxC/D was approved (I think VMX).
I am not going to go GUI on the hosting, only GUI will be ClearOS web interface and the server hosting TS.
If you have any recommendation on a server that is as slim as possible to host TS let me know :-), I made another thread for that but no one sad replied.
Thanks for taking an interest MAFoElffen.
oh also in terms of more guests I know the server int that powerful so I would run no more than one additional guest, possible to operate with dynu if ClearOS doesn't support that.

####EDIT#####
@MAFoElffen: Quick question, would [THIS]("http://www.trademe.co.nz/computers/servers/server-components/auction-1095745699.htm") ram be ok? I can look at getting a few sticks of that.

---

### Post by MAFoElffen on 2016-06-01
Your CPU is okay... but 1GB Total RAM and 500GB of SATA... is going to be tight for a VM Host. My recommends would be t o start out with 16.04 server and KVM. Install with both disks in LVM so you can swap out the drives to bigger. i feel that 1 gb is more than just going to be tight!!! You may have problems starting all but a minimal VM guest on top of a mimimal system. But it is a start.

From experience (I have a rackmount IBM XServer that I keep around for testing), look to see what IBM recommends for DDR2 ECC RRAM cards and stick to those brands/models. XServer are a bit touchy on that.  ECC registered memory is not cheap (but yours is not registered nor not-buffered), but save up for 2GB sticks and try to stay with the same brand/model throughout. Less interleave problems. Again, your top limit on RAM for that server is 8GB. I recommend to paid customers, to use a recommended minimum Sys Req's for Virtual Hosts at 16GB. You figure a rule of thumb of 1/2 your memory for VM Guests. But we did it in the past and survived. Just spoiled at what we have now. The max draw is usually during their start up.

Next may be to check to see which model HDD it has. Circa around that time, there was a 2TB limit on HDD's, where it would not recognise drives as anything bigger. IBM only says 1.5TB between 2 drives on that server, but that was while that server came out, and with their own drives... You opny have 2 drive bays, so you may be limited to 2x2TB = 4TB total.

EDIT-- Memory spec's for your server: DDR2 PC2-6400, CL=5, Unbuffered, ECC, DDR2-800, 1.8 volt, EUDIMM. Comparable to Crucial's CT2840349.
What you linked to will not work, Those are FB-Dimm's or "fully buffered" ... besides being the wrong speed...

---

### Post by Alvin_Fletcher on 2016-06-01
Thanks for that MAFoElffen.
1 thing I think you got wrong is that the server currently has 2 gigs of ram.
I may have looked at the wrong ram as I am trying for a few machines. Ill get back to you on that one.
Currently the server has 2x 250gig HDD, they are in a form of raid as I only have that space available.
For the time being that HD space is enough as I will be using another "Beefy" proliant server to do things requiring more space or ram.
Currently I already have Ubuntu Server 16.xx installed and after everything people have said will be going KVM, I have set Ubuntu server using the disk/disks as LVM
Any recommendations on ram? - I will aim to get 8Gb but do not have a lot $$$ wise, hence I got that for under $20 NZD :-).

Again Thanks alot for the help MAF, this has been really usefull.

[COLOR=#C61919][B]MAFoElffen

[/B][/COLOR]**Update: **I an only seem to find non ECC and CL6 ram on most common NZ pc shops Please have a look here and let me know what you think.
[http://www.pbtech.co.nz/index.php?z=c&p=memory&fs=81197](http://www.pbtech.co.nz/index.php?z=c&p=memory&fs=81197)
Otherwise all I can do is wait till I get a response from a few emails
Again thanks

---

### Post by MAFoElffen on 2016-06-01
> 
[COLOR=#333333][FONT=Helvetica Neue]4x 512MB DDR2[/FONT][/COLOR]

My mistake misreading the above from your link... 

On your RAID 1... With RAID1 and ext4, with 2x250's, you are probably looking at 220 GB to 230 GB as, after your overhead. You could also setup those disks as either jbod or as RAID0 members consisting of 2 logical memebrs of 1 disk each (2x RAID0 disks of 1 each) and do LVM or ZFS pools for more room... That would put you at around 470 GB ... 

The problem I have with with my IBM RAID controllers is personal. I dislike it that they require you to boot from their recovery disks to configure and recover your RAID members. (Instead of HBA based utilities) I originally used the IBM online Raid util's that were for Red Hat rhel, and repackaged them into .deb packages sop I could install and run them in Ubuntu to manage the controller and it's RAID members... But then I got into mdadm (Linux Software RAID) with was more flexible. For a while I was doing LVM on mdadm. After learning LVM and having a good recoevry plan... I now mostly use just LVM.

My main Virtual servers are on Enterprise class Dell Poweredge Servers. One, I use as a storage manager for shared pools (network shared storage). Since you are limited with storage, you might want to keep that thought open.

---

### Post by Alvin_Fletcher on 2016-06-01
Awesome, any recommended links for using and setting up LVM?
Also dont know if you saw the edited in link on last post?

---

### Post by MAFoElffen on 2016-06-02
The company you linked to does not carry any kind of ECC memory... So that would be a no for them.

I do dev testing and on the Ubuntu Srrver Team so, at about 5-10 installs a day... I know the install iso routines fairly well by now. (lol)

In the controller, look for Raid type "jbod". Some controllers do not have that option. If so choose RAID0, but only choose a single disk, thwn create the other disk as same. Then the disks will show througth the RAID controller as 2 disks.

Boot the server install iso. When it starts the partitioner, choose similar to "Let it choose LVM defaults" after the partitioner finshes, choose go back and add the second disk to the LVM. If using the install iso, it is faster to let it do the work for you! Also when just learnign the LVM commands... I do check to make sure the partitoner see's all the disks through the controller.

Basically it creates a small (500MB) ext2 parttiion to use as a boot partition, then your LVM type partition. Within the LVM type partition, it creates a hierarchical tree structure of PG (Physical Volumes) >  VGs (Volume Groups) > LVs (logical volumes) > filesystem.

I do it from scratch. I do this because the biggest complaint is that after a while , people run out of room in their boot partitions. I usually set mine to 1GB, instead of the default 500MB. If you keep up with your  autoremove's after updates, you are safe, but... and I usually add my second extent after my install manually.

On a automated LVM install, it fills the whole extents to the max size. I do this only to how much I think I will need and leave room to grow (unreserved). That way if I need room to temporarily declare space for a backup or a snapshot, it is there... You can grow or shrink on the fly. The same with changing out disks. One limit is that you have to change out a root drive while offline (but is still possible to change to larger root disk offline.

Links?
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)
[http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/)
[https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/4/html/Cluster_Logical_Volume_Manager/LVM_CLI.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/4/html/Cluster_Logical_Volume_Manager/LVM_CLI.html)

tecmint.com has some really good LVM tutorials in 6 parts:
[http://www.tecmint.com/create-lvm-storage-in-linux/](http://www.tecmint.com/create-lvm-storage-in-linux/)
[http://www.tecmint.com/extend-and-reduce-lvms-in-linux/](http://www.tecmint.com/extend-and-reduce-lvms-in-linux/)
[http://www.tecmint.com/take-snapshot-of-logical-volume-and-restore-in-lvm/](http://www.tecmint.com/take-snapshot-of-logical-volume-and-restore-in-lvm/)
[http://www.tecmint.com/setup-thin-provisioning-volumes-in-lvm/](http://www.tecmint.com/setup-thin-provisioning-volumes-in-lvm/)
[http://www.tecmint.com/manage-multiple-lvm-disks-using-striping-io/](http://www.tecmint.com/manage-multiple-lvm-disks-using-striping-io/)
[http://www.tecmint.com/lvm-storage-migration/](http://www.tecmint.com/lvm-storage-migration/)

Just remember to look at your device names and adapt your commands to what you find on your hardware and Linux Flavor. And have fun playing until you feel comfortable with it.

---

### Post by Alvin_Fletcher on 2016-06-02
Cheers for that info, in regards to ram, I seem to have found on trademe ram that seems to match.
One question though, If I cant find C5 will C6 be compatible, I tried researching about C# and got a lot of information over my head.
Last attempt at finding ram for today via trademe:[http://www.trademe.co.nz/computers/components/memory-ram/1-gb-or-more/auction-1097161832.htm](http://www.trademe.co.nz/computers/components/memory-ram/1-gb-or-more/auction-1097161832.htm)

---

### Post by MAFoElffen on 2016-06-02
Yes. IBM says DDR2 of pc2-5300 or pc2-6400, 800mHz and CL5 or CL6... unbuffered, non-registered, ECC, UDIMM.

---

### Post by Alvin_Fletcher on 2016-06-05
Hi there MAFoElffen.
I have the server running and I seem to have SSH set up, But when trying to use virt-manager on my main pc I am unable to connect to the server.
I am using windows and am using a Oracle VM Virtualbox to run ubuntu so I can use Virt-manager.
Know any reason why this wouldnt be working.
Everything seems to be correct.
I know that my server is able to ping to google aswell so it is connected to the network just fine.

---

### Post by houstonbofh on 2016-06-06
Can you ssh from the Ubuntu VM to the kvm server?  Do you get any key warnings?  If not, you will need to look at your routing.

---

### Post by MAFoElffen on 2016-06-07
> **Alvin_Fletcher said:**
> Hi there MAFoElffen.
I have the server running and I seem to have SSH set up, But when trying to use virt-manager on my main pc I am unable to connect to the server.
I am using [COLOR=#b22222]windows[/COLOR] and am using a Oracle VM Virtualbox to run ubuntu so I can use **[COLOR=#b22222]Virt-manager[/COLOR]**.
Know any reason why this wouldnt be working.
Everything seems to be correct.
I know that my server is able to ping to google aswell so it is connected to the network just fine.
Virt-manager works on a remote Ubuntu or Windows Desktop to connect to VM Guests running on a Linux VM Server host, running either KVM, Xen, LXC or QEMU as the Virtualzation hypervisor. 

When you set up a connection, you configure the daemon type (QEMU, KVM, XEN, LXC) it will connect to, pointed to the host's IP address.

*** It does not connect to anything running in VirtualBox.

Any running Linux VM guest, if openssh server is installed, VNC server, Spice server, then you would be able to connect to it with a corresponding client. Ubuntu Desktop does have defualt installed VNC as a service. It would still need to be configured. Also static IP addresses would help to connect to a known target.

---

### Post by Alvin_Fletcher on 2016-06-07
> **MAFoElffen said:**
> Virt-manager works on a remote Ubuntu or Windows Desktop to connect to VM Guests running on a Linux VM Server host, running either KVM, Xen, LXC or QEMU as the Virtualzation hypervisor. 

When you set up a connection, you configure the daemon type (QEMU, KVM, XEN, LXC) it will connect to, pointed to the host's IP address.

*** It does not connect to anything running in VirtualBox.

Any running Linux VM guest, if openssh server is installed, VNC server, Spice server, then you would be able to connect to it with a corresponding client. Ubuntu Desktop does have defualt installed VNC as a service. It would still need to be configured. Also static IP addresses would help to connect to a known target.

Hi there. I think you may have gotten my post confused.
The server is running Ubuntu server with SSH enabled and KvM, I followed all the settings and have in set to the internal ip of xxx.xxx.1.220, I then have a Virtual Ubuntu Home on my Main pc to run Virt manager, when trying to connect to the server it times out.

########UPDATE########
I have confirmed using Putty on my PC and Virtual PC that I can connect to my server and control it remotely :-).
This makes me very happy :-).

Will next work on getting KVM to work via Virt manager

---

### Post by MAFoElffen on 2016-06-10
On Virt-manager connection problems... if you can ping your server (can can ssh to it so that confirms past that), then:
> 
Verify that:
 - The 'libvirt-bin' package is installed
 - The 'libvirtd' daemon has been started
 - You are member of the 'libvirtd' group

Another problem that I've seen occasionally is that sometimes the ~/.ssh/ directory has an owneship issue where it it taken over by root... and can't right the new key to the known hosts file...But (again) if you already ssh'ed to that host, it is not that.

---

### Post by Alvin_Fletcher on 2016-06-11
> **MAFoElffen said:**
> On Virt-manager connection problems... if you can ping your server (can can ssh to it so that confirms past that), then:

Another problem that I've seen occasionally is that sometimes the ~/.ssh/ directory has an owneship issue where it it taken over by root... and can't right the new key to the known hosts file...But (again) if you already ssh'ed to that host, it is not that.
Thanks for your help.
I managed to get it working after some tinkering, something about sending it a key.... but hey it works.
Now im just waiting to get a rack unit and some ram and I will do another install with less generic login passwords as I only set home on the LVM.
So next install I will set the whole drives as LVM :-), Also since im going to run it as a ClearOS fire wall would you recommend I get an extra Ethernet port so I can ssh into the main OS?

---


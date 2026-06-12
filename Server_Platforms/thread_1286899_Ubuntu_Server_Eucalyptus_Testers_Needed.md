---
title: "Ubuntu Server Eucalyptus Testers Needed"
date: 2009-10-09
forum: Server Platforms
---

### Post by Technoviking on 2009-10-09
From: [http://fridge.ubuntu.com/node/1925](http://fridge.ubuntu.com/node/1925)

> 
Koalas love eucalyptus, they spend three hours a day munching away on the sturdy plant. Likewise, Ubuntu 9.10 Karmic Koala loves Eucalyptus, the Open Source system for implementing on-premise private and hybrid clouds using the hardware and software infrastructure that is in place, without modification. This allows you to run your own private cloud on your own hardware and infrastructure. Sound interesting? It really is, and this a rocking new feature in the new Ubuntu Server edition.

As we build to release, we could really use your help to make sure that Karmic Koala’s Eucalyptus support is rock solid. This post outlines how you can test this functionality, and provide some valuable feedback.

What You Will Need

You need two machines, one of which has to be capable of handling [KVM]([https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)). The following command will check to see if your CPU has the correct VT extensions for running KVM (though you might have to additionally enable VT in your BIOS):

egrep '(vmx|svm)' /proc/cpuinfo

Each machine will also need 1GB of RAM and 80GB of free space. Documentation for all this is provided here.

You will also need to download the latest daily Ubuntu Server ISO image and burn it to CD.

Performing The Tests

Testing the *Ubuntu Enterprise Cloud* support with Eucalyptus involves three steps: setting up the cluster, the nodes and activating the cloud. Let’s look at it in three easy steps:

The Cluster Machine

This machine will control the nodes, it does NOT need KVM support. You can install it via the Ubuntu Enterprise Cloud task in the installer and select Cluster as the type.

Step-by-step instructions are here.

The Nodes

After you have installed a controller you are ready to add *nodes*. This is the machine that needs the KVM support. Install it via the *Ubuntu Enterprise Cloud* task in the installer and select *Node* as the type.

Step-by-step instructions are here.

Activating Your Cloud

After you have got the cluster and the node all installed and ready to go you’re ready for the final steps which are available here.

Testing and Filing Bugs

Each of these steps should be relatively pain free, after that you’re ready to start testing Eucalyptus.

The Eucalyptus Getting Started Guide contains commands you may want to try. Please Note: the Getting Started Guide is for version 1.5.2. Karmic Koala includes version 1.6, so there are some differences involved. You can however take a look to the on going work of the version 1.6 documentation.

Bugs should be filed in Launchpad in the Ubuntu eucalyptus package. You can see this list of bugs at [https://bugs.launchpad.net/ubuntu/+source/eucalyptus](https://bugs.launchpad.net/ubuntu/+source/eucalyptus). Bugs should be reported using the ubuntu-bug tool. This tool is shipped with Ubuntu Server. To file a bug, simply type in:

ubuntu-bug eucalyptus

This tool will send relevant debugging content to Launchpad to help identify and resolve the bug. More details on ubuntu-bug can be found here.

Discussion and Getting Help

Discussion about Eucalyptus can be posted directly to the ubuntu-devel mailing list and you are welcome to join the server development team in the #ubuntu-server IRC channel on irc.freenode.net.

---

### Post by Mewto on 2009-11-05
The thought about spending time on a eucalyptus cloud sounds appealing to me.   Do you still need more testers?   I guess you do otherwise the note would not be still up here.   

I am putting together a system with AMD Phenom II X4 CPU.   I am pretty sure it would support KVM.   It is not up and running yet so I cannot verify it.   Been putting it off for a week, now it is time to get it up.   The computer I am on now can be the console node.  I don't believe it supports KVM 

egrep '(vmx|svm)' /proc/cpuinfo

returns nothing.   I'll check the BIOS when I get off but I doubt it.   

Guess I'll get an email notice.   Have a great day

---

### Post by grenoml on 2009-11-24
There have been a number of bugs found in eucalyptus 1.6 and I think ubuntu needs to upgrade to 1.6.1 or 1.6.2 before getting testers involved.  The version released in karmic was a pre-release 1.6bzr... version.

---

### Post by rek2 on 2009-11-24
see [http://ubuntuforums.org/showthread.php?p=8378529#post8378529](http://ubuntuforums.org/showthread.php?p=8378529#post8378529)

---

### Post by holastickboy on 2009-12-02
My Athlon X2 64 3800+ supports VT, so I would imagine your Phenom 2 would do it quite nicely.  I was under the impression that practically all cpus from Core 2 Duo to Athlon x2 supported VT or their brand specific version of it?

---

### Post by munky99999 on 2009-12-02
> **holastickboy said:**
> My Athlon X2 64 3800+ supports VT, so I would imagine your Phenom 2 would do it quite nicely.  I was under the impression that practically all cpus from Core 2 Duo to Athlon x2 supported VT or their brand specific version of it?

Yep. More or less.

Even the intel atoms in these netbooks support hypervisors.

Personally I'm currently trying to hijack a few computers in my class to be able to test out this. However they are occupied atm :(

PErsonally I just dont have the physical machines in order to test this at home :(

---

### Post by IkeLewis on 2009-12-03
I am going to be trying this. I have a bunch of computers sitting around that will work, and I have thousands of photos to try to backup, so it might be worth it to try the cloud...

---

### Post by munky99999 on 2009-12-03
So I have the cluster running. I just need hardware to run the node. Everything seems to be setup and working well.

edit/
So tempted to build myself a cluster now.

100$ mini-itx mobo
8 gigsram 
flash bios allows xeons and higher end core 2 duos.
gigabit nic
8 usb ports, 3 sata

Roughly 400$ per node. If only I really had a need for it. :(

---

### Post by n1md4 on 2009-12-18
Hi all,

  I'd like to get involved in testing, on a beginners level.

I've 2 servers that have the required hardware, and the UEC install CD.

I've followed the tutorial, which for Cluster and Node installation is pretty much point and click through the install.  I accepted most defaults for the Cluster install, which appeared to run flawlessly.  Installing the Node was not as successful.

The Cluster has 2 ethernet ports; eth0 public and eth1 private, eth1 is connected to a 24 port switch.   The Node has 1 ethernet port, and is connected to the switch.

The Node breaks an automated install at attempting a DHCP acquisition with the Cluster Controller.  Instead I set the Node with a static IP, and can connect to the box from the Controller via SSH, but public internet access is broken from the Node.

Ideally, I'd be looking for an idiot proof install, is this possible?  Is anyone else having problems with this?

I'd like to help with testing, I'm keen, but I'm unsure at this point what I can offer.  Let me know if there's a way I can assist.

Thanks,

---

### Post by johnrusso on 2010-03-26
I have been working on an Ubuntu Enterprise Cloud Configuration off and  on since December.

I have an odd set of parameters, some resources and some time to devote  to this.  Let me describe the environment and if I can add to your  testing effort, I would be delighted to lend a hand.

First, I have a number of older,non-VT enabled multi core Xeon servers.   I have used 3 of them to set up separate Cloud (CRC), Walrus (WS3) and  Cluster/Storage (CC+EBS) Controllers.

In the process, I discovered a small installation "bug" where a file on  the Walrus controller does not install automatically.

Where I am stuck now, is that I have two types of hardware, the  aforementioned non-VT machines and some very capable, multi-core  VT-enabled machines.

The non-VT machines are abundant and not being used.  I am trying to  figure a way to utilize them.  I have learned that XEN will work with  them, and if I do a CentOS installation, install Xen and the NC  Controller, I am in business.  I am told by the Eucalyptus folks that  the UEC environment relies on XVM and XVM requires VT.

I would like to offer them as a platform to configure an Ubuntu/XEN  version of an NC Controller package.  If this is something you would  like to pursue, let me know.

The VT enabled machines are currently running CentOS, and are highly  tuned for DBMS testing.  I can make them available 80% of the time they  are not in demand, but I cannot reconfigure them.  Possibly dual-booting  them is an option.

Let me know if any of this has any interest.

Kind regards,

John Russo

---

### Post by px43 on 2010-04-06
A few comments on some troubles I have had during my test deployment..
following [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)
Using the 10.04 beta install disk, installing all components on a single piece of hardware

First of all, when trying to run either emi-DF89105E or emi-DF89105E, which are the only 32 and 64 bit ubuntu server images currently available in the store, ec2-init hangs for about an hour before the instance starts up sshd, which is damn annoying, and I haven't figured out how to get past that on first run (the first thing I normally to when I can log in is apt-get remove ec2-init).

Once ssh is running, I have found that the user I need to use is actually "root", not "ubuntu" as described in the documentation.  Even then, pubkey authentication occasionally will fail on some instances.

One thing I have also had trouble with is my instances not surviving reboots.  The files for the instances usually seem to be there after a reboot, and euca-describe-instances says they are pending for a while, and then terminates them and wipes all the files (including the console log).  I figured out that I could set MANUAL_INSTANCES_CLEANUP to 1 in the eucalyptus.conf, which saves the images from being wiped (sometimes), but even then, I have no idea how to launch the instance again.  I even used ps aux to grab the kvm command and all the proper arguments, but running the command manually still failed.

How am I supposed to install kernel updates etc if all my instances die when I reboot the host?  Is there some sort of euca-save-instance euca-restore-instance command that I am just not seeing or something?  I am not really even sure what logs I should be looking at.  The only ones I have really been looking into was the cc.log, nc.log, and the console.log in the instance directory.  Any tip or advice on something I may have overlooked would be greatly appreciated, thanks.

---

### Post by kjordan2001 on 2010-04-10
Nevermind what I wrote here if anyone saw my previous stuff, apparently I can do "sudo service eucalyptus stop" and that stops all services and then I can do "sudo service eucalyptus-cc start" which starts that and the eucalyptus-sc service to get just a CC and SC running on a server without having the cloud controller there.  I figure since I might have multiple clusters later on, that's the best way to set it up to have the cluster controller and storage controller for that cluster on one box and another box for tying them all together.

@px43, I'm not sure why you'd want to get that same instance running again unless you had some piece of data that you just needed from it.  Otherwise, just start up another instance and mount a volume for persistent information.  It also sounds like something is somewhat messed up when you start an instance since the root user shouldn't be the user that gets your login key.  I've had mine take a while to startup before too as it copied and prepared the image.  After that though, it should cache the image.  Hopefully at some point using the web UI eucalyptus will let you move an instance to another server so that you can do maintenance on that server, but at the moment if you reboot a server or it crashes, you lose all instances.  The manual cleanup was mostly meant for debugging an instance and not starting it back up through it.

---

### Post by dbrooke on 2010-05-17
I can't seem to spark any conversation about Cloud Computing And/Or Eucalyptus on the "Server Platforms" discussion. What's the deal here, is this too new of a service that people don't know anything about it? Am in the wrong place? Is it too complicated? Do I smell? ... maybe all 4. ;-)

Donovan

---

### Post by Rusty au Lait on 2010-06-17
Hello everyone. I started studying UEC late last summer. After a month or so I gave up thinking I needed to know more about linux before I could go on. I got clobbered with the network issues.
Long story short, I picked it up again in May. Downloaded the Lucid version and started again. It did not install the first time but it only took me a day or two to set it up. Started up an instance, ssh'd in, downloaded Apache just as quick as you please. Lesson?
Two steps:
(1) start and end with a clean install.
(2) if anything fails go to step 1.
So. I'll let you know how things are going. Ciao
:guitar:

---

### Post by bmullan on 2010-06-24
> **dbrooke said:**
> I can't seem to spark any conversation about Cloud Computing And/Or Eucalyptus on the "Server Platforms" discussion. What's the deal here, is this too new of a service that people don't know anything about it? Am in the wrong place? Is it too complicated? Do I smell? ... maybe all 4. ;-)

Donovan

I've sent an email to the forum admins asking if there could be a separate forum section for UEC ... since it doesn't really fit specifically with the "server" section.

I've not heard or seen any addition tho'

---

### Post by Rusty au Lait on 2010-06-24
OK. I made it. I'm in the clouds. Tiny clouds in my basement. Two instances up w/ apache on both. I can reach each from the CLC but not from another host. This host has Ubuntu Desktop. I can start instances from this host using the command line but not elasticFox. I can not reach the instances that are running from this host (web, nor ssh, nor ping). Private keys or something like that. So, now to save instances that have changed and i'm ready to build my own. Any ideas?
later

---

### Post by ddemarco on 2010-06-28
I am having some issues with 10.4 and the cloud. Is there a sub forum for this sort of stuff? I've posted to the dev-list, made a post here, and on the Euca open site.
 
What I'm looking for is a community dedicated/subsection for Cloud on Ubuntu. I've got 15-20 nodes and activly testing.

---

### Post by Rusty au Lait on 2010-06-29
If you have 15 nodes up then you are way ahead of me. I have 1 node. I'm not even to a managed-novlan. I have not found any other thread but this one. Can now ping the instance from a host on the network but no web (I installed lamp). I can however, get to the instance's web page from CLC using w3m. Good luck.
Did you mean 10.04 Lucid Lynx?

---

### Post by santhony on 2010-07-31
Is this thread still active??

I've been working on my cloud installation the past month.

2 Computers, 1 for Node and 1 for CC,SC,Walrus.

CC,SC,Walrus (aka server1 192.168.1.10):
AMD 3 Core
4 GB DDR2 @ 1066
500 MB SATA HD
eth0-static 192.168.1.10
bios virtualization disabled


NODE Controller (aka server2 192.168.1.11):
AMD 4 Core
4 GB DDR2 @ 1066
500 GB HD
eth0-manual
br0-static 192.168.1.11
bios virtualization enabled

I have no issues getting VNET_MODE="MANAGED_NOVLAN" working.

I cannot get VNET_MODE="SYSTEM" mode working....

I have been using the install instructions of:
[https://help.ubuntu.com/community/UEC](https://help.ubuntu.com/community/UEC)

What I need to confirm is the eucalytpus.conf and eucalytpus.local.conf
of both the Server1 and Server2.

Here are my eucalytpus.conf Files:

server1:
eucalytpus.conf:

EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
DISABLE_ISCSI="Y"
JVM_MEM="512m"

# Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
VNET_PUBINTERFACE="eth0"
VNET_PRIVINTERFACE="eth0"
VNET_MODE="SYSTEM"

# Affects: CC
# See: **NOTE** below
CC_PORT="8774"
SCHEDPOLICY="ROUNDROBIN"
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"
NC_SERVICE="axis2/services/EucalyptusNC"
#VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
#VNET_DHCPUSER="dhcpd"
NODES=""
#VNET_ADDRSPERNET="32"
#VNET_SUBNET=""
#VNET_NETMASK=""
#VNET_DNS=""
#VNET_PUBLICIPS=""

# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=0
VNET_BRIDGE="br0"
INSTANCE_PATH="/var/lib/eucalyptus/instances/"

server1 eucalytpus.local.conf
# /etc/eucalyptus/eucalyptus.local.conf

# This file is read and written by euca_conf(8)
# WARNING: You should *never* edit this file directly.

# To modify Eucalyptus parameters, either use euca_conf(8), or
# edit /etc/eucalyptus/eucalyptus.conf according to eucalyptus.conf(5).


# network configuration from the input configuration file
VNET_MODE="SYSTEM"
#VNET_SUBNET="172.19.0.0"
#VNET_NETMASK="255.255.0.0"
#VNET_DNS="192.168.1.2"
#VNET_ADDRSPERNET="32"
#VNET_PUBLICIPS="192.168.1.30-192.168.1.139"


server2 eucalyptus.conf

  # /etc/eucalyptus/eucalyptus.conf
#
# These are the Ubuntu Enterprise Cloud's default Eucalyptus parameters.

# Affects: All
# See: **NOTE** below
EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
DISABLE_ISCSI="Y"
JVM_MEM="512m"

# Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
VNET_PUBINTERFACE="eth0"
VNET_PRIVINTERFACE="eth0"
VNET_MODE="SYSTEM"

# Affects: CC
# See: **NOTE** below
CC_PORT="8774"
SCHEDPOLICY="ROUNDROBIN"
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"
NC_SERVICE="axis2/services/EucalyptusNC"
#VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
#VNET_DHCPUSER="dhcpd"
NODES=""
VNET_ADDRSPERNET="32"
#VNET_SUBNET=""
#VNET_NETMASK=""
#VNET_DNS=""
#VNET_PUBLICIPS=""

# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=0
VNET_BRIDGE="br0"
INSTANCE_PATH="/var/lib/eucalyptus/instances/"

server2 eucalytpus.local.conf (it is Empty)

# /etc/eucalyptus/eucalyptus.local.conf

# This file is read and written by euca_conf(8)
# WARNING: You should *never* edit this file directly.

# To modify Eucalyptus parameters, either use euca_conf(8), or
# edit /etc/eucalyptus/eucalyptus.conf according to eucalyptus.conf(5).

---

### Post by Rusty au Lait on 2010-08-16
I am not experienced yet. Mine works in system mode. Did you disable bios virtualization on the node?

---

### Post by MatthewMetzger on 2010-08-17
I guess I'm a UEC tester. I'm trying to deploy a test cloud and I'm having trouble getting instances started. They start, shut down, and terminate. I haven't gotten one running yet after quite a few hours working on it.

My first attempt with a node had 64 bit hardware, but no VT (found this out afterward). My second node installation is a new Dell Poweredge T310. However, I still haven't had success starting instances. 

I can't make much sense out of the error logs. For example: "Cluster cluster1 storage #2 doesn't exist, retrying in 10 seconds." appears in /var/log/eucalyptus/registration.log - I'm guessing this is my problem, but I don't know what it means or how to fix it.

Is there a forum or IRC where UEC testers and experts congregate?

thanks,

Matthew
[http://orangecomputerlax.com/](http://orangecomputerlax.com/)

---

### Post by santhony on 2010-08-18
I'm sure my Virt mode is enabled in the BIOS...

Can you post your config that you use for "SYSTEM" mode?

Matt, did you follow the install @ [https://help.ubuntu.com/community/UEC](https://help.ubuntu.com/community/UEC) ?

I have another good link with instructions.. but I have to find it again... I'll come back and repost it later on..

---

### Post by MatthewMetzger on 2010-08-18
Thanks for your reply, santhony.

I think my problem may be disk space. I installed the Front End controller on a 10 GB partition. I can mount another partition and symlink all the Eucalyptus stuff to the larger partition.

Is it all located under /var/lib/eucalyptus/ ?

thanks for your time,

Matthew
[http://orangecomputerlax.com/](http://orangecomputerlax.com/)

---

### Post by MatthewMetzger on 2010-08-19
I'm following all the online documenation (and I even have the Official Ubuntu Server Book - 2nd Edition [http://amzn.to/bj68pn](http://amzn.to/bj68pn) ). Still can't get instances to stay up. They automatically shutdown after trying to start them.

I reinstalled the Front End controller on a different computer. Same result.

---

### Post by Rusty au Lait on 2010-08-20
Are you both having the same problem? My problems included a DHCP server on my linsynk router. I disabled it and used static addresses for everyone including CLC and NC. Eucalyptus's DHCP handled the instances. All during this experience the instances terminated. It may have been the storage space I gave to the NC. According to the literature the CLC does not need the VM, only the NCs.
Another problem was about ipchain issues on the CLC allowing access to the instance once it was running.

Matthew. I guess you know the conf files are in /etc/eucalyptus and there is also /usr/lib/eucalyptus.

santhony, 

#VNET_PUBLICIPS="192.168.1.110 192.168.1.111 192.168.1.112 192.168.1.113"
is the only line in .conf in CLC that is not the default

and the NC:
# /etc/eucalyptus/eucalyptus.conf
#
# These are the Ubuntu Enterprise Cloud's default Eucalyptus parameters.

# Affects: All
# See: **NOTE** below
EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
DISABLE_ISCSI="Y"
JVM_MEM="512m"

# Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
VNET_PUBINTERFACE="eth0"
VNET_PRIVINTERFACE="eth0"
VNET_MODE="SYSTEM"

# Affects: CC
# See: **NOTE** below
CC_PORT="8774"
SCHEDPOLICY="ROUNDROBIN"
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"
NC_SERVICE="axis2/services/EucalyptusNC"
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
VNET_DHCPUSER="dhcpd"
NODES=""
VNET_ADDRSPERNET="32"
#VNET_SUBNET=""
#VNET_NETMASK=""
#VNET_DNS=""
#VNET_PUBLICIPS=""

# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=0
VNET_BRIDGE="br0"
INSTANCE_PATH="/var/lib/eucalyptus/instances/"

eucalyptus-nc.conf contains a reference to my cluster's name.


I had to set up the DHCP server on the CLC myself. Just so it didn't give away my static IPs.

---

### Post by Zanthir on 2010-09-19
I have a couple of machines, both are about 5-7 years old. I'm planning on putting Ubuntu on both of them, but haven't decided what flavor yet. I assume the standard Ubuntu Server install is recommended for this setup?

---

### Post by Rusty au Lait on 2010-09-19
Yes, the ubuntu server live/cd has the eucalyptus install as an option. Check the hardware requirements. CPU's for any NC host must be VM. If your machines are not VM I would use them for network storage or bitTorrent.

---

### Post by PCFreak2 on 2011-07-24
I have one PC I can test with
It has 250 gigs of hard drive, 1 GB DDR2 Ram, AMD Athlon 64 X2

[HP's Specs]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01053975&tmp_task=prodinfoCategory&cc=us&dlc=en&lang=en&lc=en&product=3440586")

[HP's Specs 2]("http://h10025.www1.hp.com/ewfrf/wc/product?product=3440586&lc=en&cc=us&dlc=en&lang=en&tmp_track_link=ot_we/prodlink/en_us/3440586/loc:0&cc=us")

---

### Post by trungvkvk on 2011-08-04
This topic is very dynamic.
 hopefully I'll get experience from people.

---


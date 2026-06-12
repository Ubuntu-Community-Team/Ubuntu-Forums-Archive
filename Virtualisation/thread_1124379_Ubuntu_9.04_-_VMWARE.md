---
title: "Ubuntu 9.04 - VMWARE"
date: 2009-04-13
forum: Virtualisation
---

### Post by kpayton on 2009-04-13
Any hopes VMWare 9.04 is a little more friendly with VMWare?  I know 8.04 or 8.10 one of the two there was chaos trying to get drivers to take.

---

### Post by D00mM4r1n3 on 2009-04-13
The only problem i've seen and experienced was vsock failing to compile. There is a patch in another thread that fixes the issue. I've had no other problems.

---

### Post by kpayton on 2009-04-13
> **D00mM4r1n3 said:**
> The only problem i've seen and experienced was vsock failing to compile. There is a patch in another thread that fixes the issue. I've had no other problems.

Well there was a lot of commmand line interfaces in previous versions of ubuntu that I think would deter a lot of people away from using it.  Not sure if that holds true for 9.04 or not.

---

### Post by bodhi.zazen on 2009-04-13
Just to clarify a few things :

1. 9.04 has not been released yet.

2. VMWare depends on the kernel and not the version of Ubuntu.

With that said, I have VMWare up and running in 9.04 Beta, see the sticky at the top of these forums.

Vmware does not as far as I know support Ubuntu as a host, let alone pre-releases, so expect to do some debugging.

---

### Post by kpayton on 2009-04-13
> **bodhi.zazen said:**
> Just to clarify a few things :

1. 9.04 has not been released yet.

2. VMWare depends on the kernel and not the version of Ubuntu.

With that said, I have VMWare up and running in 9.04 Beta, see the sticky at the top of these forums.

Vmware does not as far as I know support Ubuntu as a host, let alone pre-releases, so expect to do some debugging.


I knew it wasn't released yet but there is only 10 days left until production release.

I referring to running Ubuntu as a GUEST as opposed to a guest.  I don't want to run it as a a host just want to toy with it.

---

### Post by bodhi.zazen on 2009-04-13
I have not had any problem running Ubuntu in VMWare as a guest.

Can you describe your problem in more detail ? Are you talking about installing the Toolbox ?

If so, that has not changed.

[https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)

It is a few commands in a termal, not really *that* difficult. Virtualbox is similar for the VirtualBox Additions.

---

### Post by dcstar on 2009-04-14
> **bodhi.zazen said:**
> I have not had any problem running Ubuntu in VMWare as a guest.
.........

Exactly, it is super simple to install as a VMWare guest (or downloaded as a VM that someone else has already installed).

I have Ubuntu VMs running in Ubuntu and Windows VMWare Server hosts without any problems at all.

---

### Post by dnaxx on 2009-04-20
Has someone tested the most recent version of VMWare Workstation in latest RC of Ubuntu 9.04 as host and WinXP SP3 as guest?

My winxp guest is almost unuseable because mouse-clicks are very delayed.

---

### Post by bodhi.zazen on 2009-04-20
*Off topic*  It is sad, but I have moved away from VMWare as it is getting harder and harder to install and run.  

I know it has advantages, and I miss some of the features.  But Server 2.0 is buggy, particularly the web interface, and has LESS features then 1.x.  

OpenVZ and KVM have become my preferred visualization tools.  I built an openvz template for ubuntu 9.04 I shall submit to the OpenVZ project, the guest uses 4 Mb RAM. I have LNMP (Linux - Nginx - Mysql - PHP5) running and the guest uses just over 100 Mb (112 Mb) .

 There are several web interfaces for OpenVZ, all of which are far superior, IMO, to VMWare Server 2.0.

 IMO it is just sad to see VMWare fall so far behind.

 [http://www.montanalinux.org/proxmox-ve-review.html](http://www.montanalinux.org/proxmox-ve-review.html)  

And check out this video :  [http://pve.proxmox.com/wiki/Hardware_setup_for_KVM_guests_%28Video%29]("http://pve.proxmox.com/wiki/Hardware_setup_for_KVM_guests_%28Video%29")  

I know it is running a windows guest on a Vista interface, still it is far superior to VMWare , IMO :)  

/end *off topic*

---

### Post by fjm03 on 2009-04-20
Installed VMware Server (1.0.9) on both 32 and 64 bit versions of 9.04 RC1 this past weekend. Installation is still bumpy, requiring patience and a firm knowledge of the process. The patch for the 2.6.27 kernel is required and the CD ROM can be detected in the 9.04 host as either* /dev/scd0* or through the use of *auto detect*. Installing PAE's to allow more than 4GB of physical memory in either the 32 or 64 bit host is an *unsupported *but doable endeavor. The *getlibs-all.deb* package is a useful tool when installing 32 bit programs such as TweetDeck or Adobe Air on the 64 bit host system.

---

### Post by veloce on 2009-04-20
> **bodhi.zazen said:**
> *Off topic*  
OpenVZ and KVM have become my preferred visualization tools.  
/end *off topic*

Continuing your off topic conversation - I'm loathe to create a separate thread for this or it will become a distro war..

OpenVZ appears be ideal for a decent dedicated virtual machine server.  

On the other hand, I need virtualisation on my Ubuntu laptop to run a couple of XP vms.  I use rdp to access the vms so just need them to be running with an accessible virtual ethernet connection.  I'm using vmware now and can't help but agree with you that v2 is too limited (can't use physical disks) and is buggy.  

So, what would be your preferred tools for this setup?  kvm+qemu?

---

### Post by bodhi.zazen on 2009-04-21
If you have the hadware, check out KVM.

Otherwise try VirtualBox. 

qemu is too slow, even with kqemu.

If neither KVM or VBox do what you need, I agree VMWare Server 1.x is the way to go.

Personally it is becoming tiring to continue to debug vmware and again personally I am finding other options will do what I need.

Personally my solution is KVM + qemu. I understand KVM requires "modern" 64 bit CPU, but these will be more widly available in the future and they are not *that* expensive. Bothe KVM and qemu are opensource in the true sense of Opensource (ie no liscencing agreement).

KVM does, however, lack some features (mouse integration for example).

So as always it depends on your needs and I did not intend to start a flame war. I am just frustrated with VMWare (Vmware *used* to be my prefered platform). They do make some very nice products, just not server, IMO.

---

### Post by veloce on 2009-04-21
> **bodhi.zazen said:**
> If you have the hadware, check out KVM.


Thanks for that, the laptop does have the appropriate hardware so I'll give it a go.

While wary of starting a flame war, I've read enough of your posts to value your opinion on the matter.

---

### Post by bodhi.zazen on 2009-04-21
Thank you for your respect, I would be interested in what your think of KVM. I suspect the biggest stumbling points with KVM are graphics and mouse integration.

---

### Post by wcorey on 2009-04-25
Whatever happened to "Ubuntu, It just works!"?

I was running VMWare Workstation 6.5.1 just fine under U8.10. Whether people like or dislike VMWare is a value judgement that is irrelevant to getting it to work. As was posted elsewhere, VMWare doesn't specifically support a distro, rather a kernel level. If there is a bug in the Linux kernel fix the kernel, These problems should not require users to adopt Linux Systems Programmer style labors of love in order to fix. 

And for users, these threads are for people having issues with getting something to work, not to pontificate on who likes what package better. If someone spends $150 for a software package, they are pretty much committed to it especially when they say it stopped working.

---

### Post by bodhi.zazen on 2009-04-25
Well, VMWare is a 3rd party application, so you can not hold Ubuntu responsible for if it works or does not work, let alone the Linux kernel developers.

If you go to the VMWare site they clearly list the OS (and kernels) that are supported.

If you want something that "just works" and is supported by Ubuntu, your options are KVM and OpenVZ, both of work out of the box.

I understand your frustration, just direct it at VMWare, and not Ubuntu or the Linux kernel developers. The linux kernel and Ubuntu are open source, is it not VMWare's responsibility to adapt to a modern kernel ? Or the buyer's responisibilty to install on supported hardware / host ?

---

### Post by dpj23 on 2009-04-25
AS a guest 9.04 installed great...

---

### Post by ppafin on 2009-04-26
I did installations to several computers, which have now 64 bit 9.04 as host and vmware server 2.01 as virtualization platform. Everything went smoothly. Much cleaner than 8.10.

---

### Post by filmnyc on 2009-04-28
I'm unable to install vmware-tools into my new install of Ubuntu 9.04.  I've never had a problem installing tools on previous versions of ubuntu.  I've uninstalled and re-installed the tools program to no avail using the procedure outline on the ubuntu site.

What should I do, re-install Ubuntu?

Thanks
Jon

---

### Post by openthreads on 2009-04-28
There are bugs with the existing vmware-tools with ubuntu 9.04 jaunty as a client.  Specifically with the new X.org in ubuntu 9.04, among others.

For ubuntu 9.04 to work fully as a VMware client, we'll have to wait for new releases to VMware products.

---

### Post by theDaveTheRave on 2009-04-29
Hi all

I've recently installed VMware Server, and the install seems to have worked fine in one instance of Ubuntu but not the other....

I recently installed on an XP terminal also, and it worked equally well there too?

I have a problem though.

When I attempt to log into the web interface on the ubuntu box (running the Hardy LTS) my password doesn't work!?

From what I understand this should be the same as for my "normal login" into the system (as it is on my XP system). So what have I don't wrong for the install??

but I have also read on this [site]("http://www.virtuatopia.com/index.php/VMware_Server_2.0_Security_-_Access,_Roles_and_Permissions#VMware_Server_2.0_Access_Controls")
> 
As such, a user can only log into the VI Web Access interface if they have a valid login and password on the system hosting VMware Server 2.0. In addition, the user must have been assigned the appropriate login permissions by a VMware Server administrator (by default, all users on the host system are configured to have no access). The first administrator was created during the VMware Server 2.0 installation process, though other users may be assigned administrative privileges through the VI Web Access interface.

another couple of "annoyances", which may be related...

I don't have an icon anywhere for loging onto the vmware Server - like I do with the succesfully installed system that is on the other ubuntu box.

I'm not sure exactly what I did that was different between the 2 systems?

All I know is that I followed the instructions for installing from the various tar.gz files?

Another quick gripe (may or may not be related) when I installed the server version succesfully on Ubuntu I was unable to create a virtual machine - but it worked fine when I did it through XP?

I'm wondering if I have a kernel issue??

Looking at the VM site they don't seem to support ubuntu to host the server since 6.06 (but do support ubuntu 8.04 as a guest system)

is this correct?

thanks in advance

David

---

### Post by veloce on 2009-04-29
> **theDaveTheRave said:**
> When I attempt to log into the web interface on the ubuntu box (running the Hardy LTS) my password doesn't work!?

vmware-config sets up just the vmware administrator account.  The default for this is root - which doesn't work very well for Ubuntu because there isn't a root password by default. To get in you should re-run vmware-config and specify a normal user to be the administrator.

> **theDaveTheRave said:**
> 
I don't have an icon anywhere for loging onto the vmware Server - like I do with the succesfully installed system that is on the other ubuntu box.

VMWare server 2 doesn't install an icon for vmware because it only uses the web interface.  Are you sure both installation were the same version of vmware?
> **theDaveTheRave said:**
> 
Another quick gripe (may or may not be related) when I installed the server version succesfully on Ubuntu I was unable to create a virtual machine - but it worked fine when I did it through XP?

I'm wondering if I have a kernel issue??

No, that is not a kernel issue - you wouldn't get any response from vmware at all if that were the case.
> **theDaveTheRave said:**
> 
Looking at the VM site they don't seem to support ubuntu to host the server since 6.06 (but do support ubuntu 8.04 as a guest system)

is this correct?


Yes, that is correct.  However, you're not quite on your own as there are people on this forum (not me - I just pick up other's solutions) who have just about every problem sorted - except for VMWare's design issues. Those we are all stuck with.

---

### Post by theDaveTheRave on 2009-04-30
Veloce

Thanks for your helpfull and informative response.

I think I may have a kernel issue!

I'm running the 2.6.24-23 kernel on the server, and I may have upgraded to intrepid on the desktop (although it is running the "server" version of Ubuntu).

Both are AMD64 cpu's. both seem "problematic" with the vmware server!

So I decided to remove the VMware Server2 and go for server1.09 (as this seems to be working for most people).

During the install I persistently get a error stating that one of the files is "returning an integer as a pointer requires a cast" which seems fair enough - in fact I get the same error 4 times, in the same file!

so I hunted down the file and had a look, each time it is the same return statement!

So I attemtped to edit the statement

from
```


return this-variable
```

to now read
```
 return (int *)this-variable
```

and ran the install script again.... but no luck, I get the same errors on exactly the same line number - and I put in a comment before the line to push the error to the next line down in the file!

So obviously my C programing skills are as bad as I thought they where! or I'm edditing the wrong file? but I'm certainly using the file in the error message?

I can't supply the error message at the moment as I have turned the server off.... to be honest I'm a bit peeved with the process at the moment, and I would rather be doing more interesting things (like the programming in Java that i should also be doing).

I'll try to get a copy of the error message next time I'm on the server, and copy it here.

Thanks so far.

David

---

### Post by bodhi.zazen on 2009-04-30
I am sorry you are still having problems. 

To be honest, this is why I switched to KVM with VirtualBox as a fall back.

All Virtualization platforms have issues though, especially with the latest greatest kernel.

My advice (in order of my personal preferance) is to :

1. Go with KVM or VirtualBox.

2. If those do not work, go with a supported host and use VMWare / OpenVZ / Xen etc. These second options all work fine as long as you use a supported host, which in Ubuntu is 8.04.

The bottom line, it is not reasonable to expect to use VMWare on un-supported hosts. You could also try ESXi :

[http://www.vmware.com/products/esxi/](http://www.vmware.com/products/esxi/)

Personally I have switched to Proxmox :

[http://www.montanalinux.org/proxmox-ve-review.html](http://www.montanalinux.org/proxmox-ve-review.html)

Or openvz on cetnos, although you will need to run openvz on the command line if you go that route.

---

### Post by veloce on 2009-04-30
I have followed Bodhi's advice and moved to kvm on my laptop (as it's chip supports VT). However, this was after I had got vmware working on it. It is running 9.04 Desktop 64 bit. (My switch to kvm was mainly to be more open source, but I also was getting sick of the flakey web interface.)

I still have vmware running on the vm server we are running.  It is a Dell SC1420 with dual dual-core Xeons but unfortunately doesn't support VT. It is running 9.04 Server 32 bit.

I also have vmware running on my old laptop running 9.04 Desktop 32 bit.

All of these were running either vmware 2.01 or 2.00.

My experience with these three machines was that vmware-config worked exactly the same on 9.04 as 8.10.  That is, the machine on which I hadn't patched for the vsock error still had the same error and the others all worked perfectly.

Dave: It sounds like you are using the only combination I don't have: Server 64 bit.  Also sounds like it's the only one that doesn't work!

---

### Post by theDaveTheRave on 2009-05-07
Bodhi and Veloce

thanks for that advice, I'll see how it goes down with my boss!

However, I've just read something interesting onthe VMWare site about needing a correctly configured xinetd.

I did a quick google, and hunted on this forum but I'm not catching anything that seems to explains what I need to do for configuring it for VMware, or will "any configuration" work?

If it is the case that "any" will work, then the fact that i am set for using it (successfully) with VNC would suggest I have it correctly configured, are there any specifics I should be aware of?

thanks in advance

David

---

### Post by bodhi.zazen on 2009-05-07
Part of installing VMWare includes xinetdd. Basically, vmware is a service and it's boot scripts are written to be compatible with xinetd. Since Ubuntu uses upstart, you simply need to install xinetd.

[http://www.xinetd.org/faq.html](http://www.xinetd.org/faq.html)

---

### Post by dcstar on 2009-05-08
I don't really understand this thread - I have VMWare Server 1.0.9 installed and happily working on my 9.04 64-bit Ubuntu Desktop system, and I even have the 3D graphics option enabled for the XP and Ubuntu Guests VMs (a mix of 32 and 64-bit guests) that I have.

It just works.

What did I do right that others who are apparently having problems didn't?

---

### Post by theDaveTheRave on 2009-05-09
dcstar

You'll probably find that your system hardware is more "open" to these software packages??

I must admit that I have tried on numerous occasions to install various programs for use under wine, and none of them ever work, even though on the wine site they are often given 4 or 5 stars. However I am able to make notepad function, which would suggest that there isn't a problem with the configuration.

I just don't have the time to really fully get a handle on what is wrong and how to solve it, after 3 or 4 hours in a day trying to get a certain function to go I will often quietly give up and hope the boss doesn't ask me how it is going in that respect.... I don't know how to tell him it doesn't do what he wants!

Currently he really is working with the VM solution (using it as a "thin client" almost, for taking away a linux installed with a mysql DBase server. In a way it seems sensible, but I'm not fully convinced myself, especially as his argument is around the stability of MySQL on one of the more important systems, that is holding about 8TB of data (4 months of work) which he understandably doesn't want to loose, (what make me smile is that he is using windows vista on 90% of the terminals, and solutions I implement on linux and XP desktops work fine, but fail intermitently on the Vista systems :confused:)

Oh well...

David

---


---
title: "Any VMware ESX or ESXi users out there?"
date: 2009-02-17
forum: Virtualisation
---

### Post by rouben on 2009-02-17
Hi everyone!

I've spent over a year now running Ubuntu 6.06 and 8.04 (LTS releases) in a virtual datacenter here at U of T in Canada. Throughout that time I've acquired some experience in running Ubuntu under VMware ESX (not Workstation, Fusion, Server or Player). While these products are all similar, ESX really is quite different from all of these, if anything given its different virtual hardware (e.g. lack of *virtual USB* support or *shared folders* between the guest and the host).

I've seen VMware-related documentation mature quite nicely on the Ubuntu wiki, and I am also seeing a lot of discussion on the same topic. However, it seems to me like whenever folks discuss VMware on here, they tend to focus a lot more on the workstation/desktop line of products (mentioned above) rather than ESX. A perfect example of this lack of interest can be seen by visiting the VMwareESX page on the wiki [https://help.ubuntu.com/community/VmwareEsx?action=show](https://help.ubuntu.com/community/VmwareEsx?action=show) that redirects you to the generic VMware page, which is very non-ESX.

In a nutshell, I am trying to accomplish two things here:
[LIST]
[*]See how many people are in the same boat as I am
[*]If there's enough interest, establish a community of ESX users
[*]Wiki docs, scripts to rebuild ESX-ready VMware tools, etc...
[/LIST]

Let me know what you think... Thanks!

---

### Post by incudie on 2009-02-17
Hi Rouben,

I am running ESX on two Dell 2950s at the office with Ubuntu Server loaded (things like Cacti, SugarCRM, etc). I am in love with how well it has been working.

Cacti updates? No problem let me clone it and do snapshots incrementally.

I am also hosting a Windows VM on ESX with seamless RDP setup on my desktop Linux install (Ubuntu with E17).

I'm all for more documentation regarding Linux and ESX.

---

### Post by bodhi.zazen on 2009-02-17
The wiki has several divisions and is in part community maintained.

It would be wonderful if you were willing to contribute.

I suggest you at least introduce yourself on the mailing list.

See : [https://wiki.ubuntu.com/DocumentationTeam/WikiTeam](https://wiki.ubuntu.com/DocumentationTeam/WikiTeam)

[https://wiki.ubuntu.com/DocumentationTeam](https://wiki.ubuntu.com/DocumentationTeam)

---

### Post by slick666 on 2009-02-17
I've been using ESXi on and off for my personal use. My biggest problem is the fact that I have to use windows under vm to be able to manage the ESXi server.

---

### Post by rouben on 2009-02-18
Well, I actually run dozens of Ubuntu VMs (mostly 8.04 now and 64-bit) under ESX 3.0.2 (planning to upgrade to 3.5 sometime in the nearest future) on six physical Dell 2950s.

How do you handle kernel upgrades and recompiling VMware tools? As I mentioned before (I think), I use module-assistant to accomplish this, alongside the [VMware's ESX Tools Repo]("http://packages.vmware.com/tools"). Basically I grab the source kernel module packages and rebuild/install binaries using m-a as required, on every reboot, invoked from /etc/rc.local. Thankfully m-a is smart enough not to recompile these every reboot if the same kernel loads, so boot times aren't too long. This strategy works, but is rather kludgy... I would much rather use something like [DKMS]("http://linux.dell.com/projects.shtml#dkms") to do this. Seems to me like a much cleaner solution. On a sidenote, have you guys every checked out just how much work Dell has done for Linux lately? WOW!!! :D Kudos to Dell!! :KS

Anyway, back to original topic... Do any of you run the 64-bit version of Ubuntu as a guest? Did you notice any performance differences? I did... 64-bit seems to run much faster and be much more responsive (especially with I/O) than 32-bit. Weird... :o

And to keep this alive, I wonder if there are enough users to even start our own wiki page? In hindsight I wish VMware was more proactive with their support; if they kept up with Ubuntu's kernel updates, I wouldn't need the kludgy aut-update procedure I described above. I don't know if Canonical's doing anything to build a bridge with VMware. IMO they should, because VMware at the moment is very, very RedHat centric, and IMO Ubuntu is just so much nicer. :D I don't mean to start a distro religious war here, but I will mention that I am a convert. :p

Well thanks for listening! :D

---

### Post by redbrain on 2009-02-19
Ah yeah we use it here in our data centre running ubuntu. Any tips i am unsure.

Personal i really don't like vmware. The problem i find is you will be in too much vendor lock-in at the moment your better off with xen from SLES or Xen in ubuntu or if you can risk it KVM.

KVM is great but its just not quite there yet to be reliable it works great for debian and ubuntu guests but i find its lacking for the likes of SLES10
or some redhat stuff. 

The problems i find with vmware are you need to pay tonnes of money....

You need a windows machine unless you get the web interface in the newer versions of ESX not in ESXi because the management client is windows only. And it is quite un-reliable sometimes in a high latency network. Because it uses CIM. ESXi is something you MUST stay away from aswell its soo basic its silly. You don't have enough control to automate some-things. You cant even really ssh to the server unless you do a small hack there is not even a proper shell its basic and dd works funny if you want to save your disks

Its a pain to dual boot between as you have to pretty much just replace your MBR each time.

Its a pain you cant really just keep your virtual machines and move to xen or kvm unless you are using much much more recent kernels like ubuntu/debian systems SLES and redhat are a pain SLES works if your using the SLES11 beta.

But i guess i am being pretty harsh on vmware. If you are going to have a realllly static data centre its ok... you just need a spare windows machine around. But really Xen does the job and you have pretty similar preformace disk i/o is still a little slower if your using full virtulisation because its based of qemu also. Citrix does a decent job at Xen but its still quite vmware'ish as you need the spare windows machine to manage it all but the Xen build't into SLES or Ubuntu would probably do the job.

One thing to look at would be play with OpenVZ and see if it does what you want because its seems like a nice way of doing it all. But i duno how well it is to manage in large data centres. I guess Vmware has the best management

So in overview

Vmware have the best management
Citrix have pretty much the same 

But you need a windows box
you will have vendor lockin with vmware 
Citrix is more free

KVM is great no vendor lock in at all acess to the latest and coolest features all the time

Xen on SLES/Ubuntu etc. pretty much same as KVM but more stable and reliable no vendor lockin lacks a little in overall data centre management but that will change soon enough with libvirt being worked at alot recently.

OpenVZ seems like a nice choice for a webserver setup in a data centre but i duno how well management will be for the sys admin. :)

Hope this gives you a good overview. But i would stay away from ESXi tbh its really a bad decision in my view it doesnt really scale for you or decent control over your box. But if you dont care maby its ok...

But tbh if you want a scaling data centre you cant use it. ESX would do a better job but your goign to be paying ALOT of money in licenses over and over and over and you just get locked in and its a pain. But atleast with ESX you can have more control over your server.

---

### Post by bobdob on 2009-02-20
Hi Rouben
Good to be in the same boat, we run a large number of Ubuntu guest machines on a number of ESX 3.5 and ESXi hosts and have gone through the pain from 6.0.6LTS to 8.04.2

Here is the biggest problem as an Enterprise customer right now, and i have mentioned it to Canonical.

>8.04.2 the latest Ubuntu LTS is not officially supported by VMware on ESX 3.5 U3, it drives me nuts.

>Kernel upgrades are a nightmare, every time a new one comes out its a big deal. We test on a few machines over 2days, tweak them using guess work, and then manually compile the rest after that, There are lots of weird things that happen to our Ubuntu machines, but no real way to troubleshoot them.

as for the other comments..

-ESXi is most excellent, it does have specific hardware requirements, and management is limited, but so is the management on KVM and Xen. The real advantage is its a rock solid hypervisor, supports Windows Guests, gets regular updates, is a better alternative to VMware Server 2.0 and performance wise is as good as Xen, and thats why people spend lots of time tweaking it and hacking it. 

-We used to use Xen and still have small KVM implementations. There great if everything is exactly the same Guest wise, so we had 25 Ubuntu 6.0.xLTS Guests on a single Xen box for example, but try putting a Windows guest machine into the mix or try and do anything fancy like HA or Storage or even troubleshoot it. 

Then if you have more than one Xen/KVM server and want to centrally manage them or get performance stats from particular Guest machines, with the commercial virtualisation solutions what your paying for is the management and the warm fuzzy vendor lock-in support.

BTW, our sysadmins are impressed with your use of "module-assistant" in that way, slightly insane, but most impressive.

Bob

---

### Post by rouben on 2009-02-20
> **bobdob said:**
> Hi Rouben
Good to be in the same boat, we run a large number of Ubuntu guest machines on a number of ESX 3.5 and ESXi hosts and have gone through the pain from 6.0.6LTS to 8.04.2

Here is the biggest problem as an Enterprise customer right now, and i have mentioned it to Canonical.

>8.04.2 the latest Ubuntu LTS is not officially supported by VMware on ESX 3.5 U3, it drives me nuts.

>Kernel upgrades are a nightmare, every time a new one comes out its a big deal. We test on a few machines over 2days, tweak them using guess work, and then manually compile the rest after that, There are lots of weird things that happen to our Ubuntu machines, but no real way to troubleshoot them.

as for the other comments..

-ESXi is most excellent, it does have specific hardware requirements, and management is limited, but so is the management on KVM and Xen. The real advantage is its a rock solid hypervisor, supports Windows Guests, gets regular updates, is a better alternative to VMware Server 2.0 and performance wise is as good as Xen, and thats why people spend lots of time tweaking it and hacking it. 

-We used to use Xen and still have small KVM implementations. There great if everything is exactly the same Guest wise, so we had 25 Ubuntu 6.0.xLTS Guests on a single Xen box for example, but try putting a Windows guest machine into the mix or try and do anything fancy like HA or Storage or even troubleshoot it. 

Then if you have more than one Xen/KVM server and want to centrally manage them or get performance stats from particular Guest machines, with the commercial virtualisation solutions what your paying for is the management and the warm fuzzy vendor lock-in support.

BTW, our sysadmins are impressed with your use of "module-assistant" in that way, slightly insane, but most impressive.

Bob

I agree, Canonical's relationship with VMware seems to be rather mysterious... I'm guessing VMware's to blame in this one, since most of their customers are Windows shops, a small portion of those also run RHEL and an even smaller portion run Ubuntu. I can understand if VMware's not particularly interested in supporting Ubuntu, because you are correct, the support is fairly nonexistent. The package repo I mentioned seems to have been abandoned as of December, which is unacceptable, IMO, for enterprise level support.

The only thing I can blame on Canonical at this point is that they pulled open-vm-tools from their repos. Debian ships those, and they work quite nicely with all kernel upgrades.

Bob, a tip if I may. Ditch VMware's official VMware tools. Use open-vm-tools from that repository, or get the source off sourceforge if you want, it's like night and day. VMware's Linux tools that ship with ESX are pretty much RedHat-only as far as I'm concerned. Work like a charm on CentOS/RedHat, but anything else is painful with really weird performance and stability issues.

Lastly, I'd love to trade notes on Xen and Windows. Can that be done, or is one basically stuck with KVM when it comes to running Windows guests under Xen? Because I'd much rather use VirtualBox if that were the case... or just stick to ESX.

---

### Post by bobdob on 2009-02-23
Hi Rouben
The "open-vm-tools" we had a discussion internally about them, but there not "vmware offical", so we weren't allowed to use them. might give them a bash on "Ubuntu Jaunty", seeing as the tools dont compile there :(

as for XEN and Windows, we gave up in the end and went with "VMware Server" on Ubuntu, then ESXi. It was early days for Windows support with Debian/Ubuntu XEN, so kernel patching was the order of the day. Our KVM setup is Ubuntu guests only, and were moving to ESXi medium term.

what also might be handy is some sort of "Kernel crash dump" functionality on Ubuntu or some way to better diagnose "weird" issues.

Bob

---

### Post by andreas.macke on 2009-05-11
> **rouben said:**
> 


Bob, a tip if I may. Ditch VMware's official VMware tools. Use open-vm-tools from that repository, or get the source off sourceforge if you want, it's like night and day. VMware's Linux tools that ship with ESX are pretty much RedHat-only as far as I'm concerned. Work like a charm on CentOS/RedHat, but anything else is painful with really weird performance and stability issues.



rouben,
could you elaborate a bit on the really weird performance and stability issues? How do they manifest? We've got some interesting challenges with MySQL running on Ubuntu 6.06LTS with ESX Server, and hearing about others' experiences might help us sort how much of it is based on application/database performance issues. One particular thing we're struggling to explain is why we're seeing high i/o waits in the OS, yet the traffic to and from the SAN is barely a trickle, and disk access is really nowhere near what the SAN is capable of. Weird indeed - but related to Ubuntu/VMWare weirdness?

Cheers,
-Andreas

---

### Post by usafe7ret on 2009-06-03
I have just installed ESXi 3.5 U4 on a Dell 2650 and so far, I am having some success with it.  I just finished creating a Jaunty VM and had to struggle with the VMWare Tools as well.  

I did find a thread here with instructions on installing open-vm-tools with m-a and it was fine up to a point.  The last instructions on initframs failed.

I finally went into the package manager and installed another portion of open-vm tools, rebooted the Ubuntu VM and it started working. 

I don't know why, as I am a real novice with Ubuntu and using the terminal, but thanks to this  forum, I have been able to overcome most issues with Ubuntu.

I have been reading about and dabbeling in virtualization as it is the shiny new apple everyone is going to want.  I started back in October 08 and now my company is looking into getting into supporting VMWare in the near future.

As far as using windows as the guest OS, VMWare is pretty much point and click from what I've seen so far, but my test lab is really tiny at this point and I have to keep it away from our production networks under penalty of death, so I haven't been able to do too much with NFS or NAS devices.  

I would definitely be a dedicated user to any VMWare ESXi or VSphere forum that develops and would at least be able to contribute some "don't do stupid things like this.." lessons learned.

---


---
title: "Can't get Ubuntu 13.04 to work in Virtual Box"
date: 2013-07-19
forum: Virtualisation
---

### Post by carmen2012 on 2013-07-19
I've installed Ubuntu 13.04 in Virtual Box (VB) and it is incredibly slow.  I've Googled this and have found a ton of people that have this issue but no real solution.  Some of the things I have tried to do include updating to the latest version of VB, installing guest additions, enabling 2D and/or 3D acceleration, increasing RAM/HD space to the VM, but the issue remains.

There are lots of suggestions, but I haven't come across a post that has a solution.  It seems this issue has been outstanding since last year.

Would anyone know how to fix this issue?

Thank you

---

### Post by su:bhatta on 2013-07-19
How much RAM are you giving to the Virtual Box Machine? If it is near 2GB then it shouldn't be slow. 

Anything less than that  & you might want to try Xubuntu!

---

### Post by carmen2012 on 2013-07-19
> **bhattabhishek said:**
> How much RAM are you giving to the Virtual Box Machine? If it is near 2GB then it shouldn't be slow. 

Anything less than that  & you might want to try Xubuntu!

The master PC has 8GB RAM and I have tried all configurations from 2-4GB RAM.  From what I have read, it is an incompatibility between Virtual Box and the more recent versions of Ubuntu.

Since it has been outstanding since last year, I would think there would be a fix or a workaround available?

---

### Post by wildmanne39 on 2013-07-19
I have 13.04 running in virtualbox and I did nothing extra to get it working.

---

### Post by wildmanne39 on 2013-07-19
*Thread moved to **Virtualisation**.*

---

### Post by carmen2012 on 2013-07-19
> **Wild Man said:**
> I have 13.04 running in virtualbox and I did nothing extra to get it working.

All I can say is that you are fortunate to have been able to do it.  A Google search on "ubuntu 13.04 slow virtualbox" shows that people are raising this issue on a variety of different forums.

---

### Post by bodie-ci5 on 2013-08-01
Oh wow, I thought this was just me. I also installed 13.04 on VMWare Player, and it's running like a champion! (but no 3D capability until I actually purchase the software :frown: )

I'm spewing, though, I've always wanted to try out VB.

---

### Post by RichardET on 2013-08-01
My suggestion is to go vmware.

---

### Post by carmen2012 on 2013-08-01
> **RichardET said:**
> My suggestion is to go vmware.

I did think about vmware but because I'm so familiar with virtual box, my preference is to stick with that.  For now, I'm going to just wait it out, hopefully down the road, Canonical and/or Virtual Box will be able to sort out the issue although in researching this, the issue has been outstanding for months.

---

### Post by RichardET on 2013-08-09
I have never tried virtual box, so perhaps I am biased.  I have been a registered user of VMWare workstation since version 6 was introduced, now using version 9.03.  I have used it natively on both linux (Suse) and various versions of Windows (vista, 7, 8).  Since I am fairly pro-linux, it would be my main dream to run Ubuntu natively on this Lenovo W530, which is what I use now, but the reconfiguring is too much of a hassle for me right now, so I took the path of least resistance, and run VMware on top of Win 8, and I have two versions of Ubuntu setup by me as virtual machines, each with 2 gig of ram, and 200 gig drives.  When I run full screen, it's impossible to tell the difference between native and virtual, and I spend my time enjoying my hardware, instead of constantly tweaking it, something for which I have zero patience.

---

### Post by SchnappiJedi on 2013-08-09
Don't go to vmware (unless you want to that is). 13.04 works absolutely fine across multiple machines with virtualbox. Can you give more details about your hardware and exactly where the issue is occurring (aka if 13.04 is responding slowly over shh maybe it has something to do with the network).

---

### Post by TheFu on 2013-08-09
> **RichardET said:**
> I have never tried virtual box, so perhaps I am biased.  I have been a registered user of VMWare workstation since version 6 was introduced, now using version 9.03.  I have used it natively on both linux (Suse) and various versions of Windows (vista, 7, 8).  Since I am fairly pro-linux, it would be my main dream to run Ubuntu natively on this Lenovo W530, which is what I use now, but the reconfiguring is too much of a hassle for me right now, so I took the path of least resistance, and run VMware on top of Win 8, and I have two versions of Ubuntu setup by me as virtual machines, each with 2 gig of ram, and 200 gig drives.  When I run full screen, it's impossible to tell the difference between native and virtual, and I spend my time enjoying my hardware, instead of constantly tweaking it, something for which I have zero patience.

WMware workstation is an impressive product. I started using it in the late 1990s for software development and testing. It has only gotten better. In a business, mainly running MS-Windows and testing - 100% - VMware Workstation is the best choice. I have no doubt whatsoever.

However, for all other purposes ... when it comes to desktop-on-desktop virtualization, VirtualBox is the equal to everything that anyone else puts out.  For server-on-server virtualization, KVM is the winner now for Linux.  No need to bother with ESXi or Xen or anyone else for general purpose virtualization needs.  Further, for Desktop-on-Server VMs, KVM is surpassing all other solutions thanks to Spice, but that is a little unstable still.  If you need stability and remote desktops, then FreeNX running inside the VM ... NOT the hypervisor ... is the best solution I've found.  For KVM, using a remote virt-manager tool (over ssh connection) completely rocks to manage upto 100 VMs. If you get any larger than that, perhaps (VMware ESXi and vSphere ) or OpenStack are really what you want?

Finally, I haven't seen this thread marked as solved, so I'll add a link to my VirtualBox Performance "How-To" - [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)  Seriously, this configuration makes it so close to native performance on C2D or better CPUs, it isn't even funny.  Please ask is there are any questions. Things can always be improved and I've given 4 presentations about these seeings on 3 different continents. Feedback is highly appreciated.

---


---
title: "My perceptions of Virtualization in Ubuntu ..."
date: 2009-09-08
forum: Virtualisation
---

### Post by cwmoser on 2009-09-08
I'm no expert on Ubuntu Visualization and I post my perceptions from all the reading I have been doing.  Correct me where I have the wrong perception.

1- VMware works.  Vmware Server 2.0 is slow and uses a clumsy browser interface.  I got 1.06 working well (its really a decent product) and once I got my VM's created, I removed Vmware Server and used VMware Player 2.5.3.  You cannot have both Server and Player installed at the same time.  Most everything you need to work with VMware is high quality and free.  The newest VMware Server 2.0 sucks.  VMware VM's will run in any VMware environment be it Linux, Windows, or Mac - very transportable.

2- KVM - not sure what QEMU is in relation to KVM but perceive it is related.  Read that you can convert VMware VM's to work under KVM, tried the process but it did not work for my VMs.  I find How To's for KVM very lacking - seems a lot of information is missing.  Perceive that KVM should be the fastest environment for VM's but not transportable to other OS hosts.  Not really sure KVM is ready for prime time.

3- Xen - hear that it is good - have not tried it.

4- Virtual PC - hear a lot of positive comments about Virtual PC.  Wish there was a way to migrate VMware VM's to work under Virtual PC.  Plan on testing Virtual PC soon.  Not sure what Sun Microsystems is doing with it.

My perception is that the fastest to the slowest VM's are:  KVM, then Virtual PC, then VMware.  I have only tried VMware and KVM - but while VMware really works, I could not get KVM to work.  VMware has a lot of How To's and pertinent documentation, KVM is really lacking.

Comments?

Carl

---

### Post by dk06 on 2009-09-08
The only one I can remember running in Ubuntu is Sun's VBox, I use other distros for VMware(CentOS,openSUSE, Fedora) 

Haven't tried Xen (downloaded the hypervisor couple weeks ago but still need to decide which machine I want to devote to Xen) & haven't tried the App yet either.

I like VMware Workstation and agree with you on VMware Servers "slow and uses a clumsy browser interface"

I've also been using ESX 4.0 and I absolutely love it. I use another distro to run a 2k8 VM in VMware Workstation and installed the VI Client in the 2k8 VM to manage ESX. (b/c there is no VI Client for Linux yet...so, it's kind of a workaround)

But for basic Virtualization in Ubuntu, VirtualBox has been really easy to install & use (for me) & Cant remember if I've used VMware in Ubuntu before.

____________________________________________

For Microsoft's Virtual PC, I think it's...not so great. I've used it and it doesn't compare w/VMware or any of the the others in my opinion. I used it about a year ½ ago and unless they made some serious changes, I think it's probably still ..not so great. Haven't tried Hyper-V yet and not really in a big rush to check it out...seems like Microsoft's lame attempt at trying to get into the corporate virtualization market.

Haven't used KVM yet either but just checked out the website:
[http://www.linux-kvm.org/page/Main_Page](http://www.linux-kvm.org/page/Main_Page)

Just my experience/observations/opinions

---


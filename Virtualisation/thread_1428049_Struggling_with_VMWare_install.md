---
title: "Struggling with VMWare install"
date: 2010-03-12
forum: Virtualisation
---

### Post by bigsigh on 2010-03-12
What can I say,

For the last week I've been struggling with VMware Player and server in various distros of Ubuntu, the virtual adaptors never get created, no vmnet0 or whatever in /dev, so the virt machines have no connectivity.

I already have a working install of Ubuntu with vmware player running nst for awhile now so I've made it work before.
I have another Ubuntu install running opennms, so I can usually figure stuff out.

I've been all over google with searches about this.

I have followed the instructions in the Ubuntu help pages.

I recreated the Ubuntu install and VMware player installation I already have running.

I even had to register on this site to dl the patch in my attempt to install vmware server. 

Because I had to register I figured I'd create a very detailed post about the dozens of configurations I have done and ask for help, but, this stupid forum software made it disappear when I hit submit, of course I was too stupid to copy it before submitting.

Right now, I'm so frustrated at the wasted time and general ignorance about how to figure out what my problem with this is I want to smash something, a lot.

And I realize that, unfortunately, no matter what, we'll always be stuck with Microsoft, because Linux will never really work without years of study for its users, so the general public will never actually use it.

If anyone out there has any suggestions for getting these virt adapters installed I would be much appreciative.

If any of you keyboard warriors who think they know everything and love shooting their mouths off from behind the safety of their keyboards would like to chime in with terse, cryptic comments about what a stupid linux newb I am, even that would probably be appreciated, if your comments led to a solution......

---

### Post by howefield on 2010-03-12
Make life easier for yourself.

Try Virtualbox. :p

---

### Post by Beowulf.1000 on 2010-03-12
Ditto. I tried both vmware and virtualbox and I think vmware stinks. I will not use vmware, took it off my system. I find virtualbox more elegant, better performing, and no worries about $ like vmware.

---

### Post by dcstar on 2010-03-13
> **bigsigh said:**
> What can I say,

For the last week I've been struggling with VMware Player and server in various distros of Ubuntu, the virtual adaptors never get created, no vmnet0 or whatever in /dev, so the virt machines have no connectivity.
......
If anyone out there has any suggestions for getting these virt adapters installed I would be much appreciative.
......

Without any details whatsoever about what you did or what messages/errors were returned it is impossible to make any worthwhile suggestions.

Provide sufficuent relevant information and someone may be able to help.

---

### Post by bigsigh on 2010-03-14
I have put the hammer down and have backed away from the inclination to smash something.

I moved to another machine that I use daily, I'd set it up dual boot with win7 and ubuntu 9.04, the same distro with which I have a working vmware install on another machine, also a dual boot win7/ubuntu, that I'd created some time back, and this current machine I'm attempting an install on has full net connectivity with both os'.

I installed build-essentials and it's other packages successfully, linux-headers was already installed for the current kernel, -18 I believe.

I installed vmware 3.0.1 using the sudo command.

I looked in the /dev folder, with the view all files setting, and there were no vmnet files created, as exist on my working installation.

When running the premade virtual machine, the same machine I run in another machine, the error is "Could not connect Ethernet0 to virtual network "/dev/vmnet0"."

Because.....Mar 14 10:01:52.507: vcpu-0| VNET: MACVNetPortOpenDevice: Ethernet0: can't open vmnet device (No such file or directory).

This occurs whether I run the vmware player as the user or as root.

I'm wondering if the .bundle I'm using is corrupt and that is why it is not creating the virtual adapters during install. Perhaps it was corrupted by the content filtering of my Astaro gateway. I don't recall if I'd bypassed it or not, so I'm out of time for this now and will uninstall the vmplayer install and try again with a fresh .bundle dl as some point in the near future.

Are there any observations or suggestions based the the information above?

Thank You.

---

### Post by dcstar on 2010-03-15
> **bigsigh said:**
> I have put the hammer down and have backed away from the inclination to smash something.

I moved to another machine that I use daily, I'd set it up dual boot with win7 and ubuntu 9.04, the same distro with which I have a working vmware install on another machine, also a dual boot win7/ubuntu, that I'd created some time back, and this current machine I'm attempting an install on has full net connectivity with both os'.

I installed build-essentials and it's other packages successfully, linux-headers was already installed for the current kernel, -18 I believe.

I installed vmware 3.0.1 using the sudo command.

I looked in the /dev folder, with the view all files setting, and there were no vmnet files created, as exist on my working installation.

When running the premade virtual machine, the same machine I run in another machine, the error is "Could not connect Ethernet0 to virtual network "/dev/vmnet0"."

Because.....Mar 14 10:01:52.507: vcpu-0| VNET: MACVNetPortOpenDevice: Ethernet0: can't open vmnet device (No such file or directory).

This occurs whether I run the vmware player as the user or as root.

I'm wondering if the .bundle I'm using is corrupt and that is why it is not creating the virtual adapters during install. Perhaps it was corrupted by the content filtering of my Astaro gateway. I don't recall if I'd bypassed it or not, so I'm out of time for this now and will uninstall the vmplayer install and try again with a fresh .bundle dl as some point in the near future.

Are there any observations or suggestions based the the information above?

Thank You.

Yes, you need to configure VMware to use the Ethernet interface on the hardware you are using, you **cannot** assume it will be the same as other hardware you may have been using.

---

### Post by bigsigh on 2010-03-15
> **dcstar said:**
> Yes, you need to configure VMware to use the Ethernet interface on the hardware you are using, you **cannot** assume it will be the same as other hardware you may have been using.

On its face, your statement seems to point out the ridiculously obvious.
Most assuredly falling under my definition of terse and cryptic.
Normally, after that statement I'd blow you off as one of those know it all, but in reality, knows nothing, prolific posters, but, your username does have over 8 thousand beans, posts I presume, as well as a difference in icon appearance.
So perhaps there's something you know, of value, and you're trying to hint to it.

Having considered that this morning. I think back upon my hours of readings of the vmware installation manual, the ubuntu help page, the various postings throughout the internet, the adaptor settings within the vmware gui, and the reality that, as I recall, on a Dell laptop, the .bundle installer, created whatever networking components it needed without interaction from myself, I have to wonder, what's different about a gigabyte intel mb with its onboard adapter as well as an intel pci nic installed, or the msi amd motherboard with its onboard adapter that would give the .bundle installer cause to not create the necessary networking components.

Having attempted vmware player, vmware server and virtualbox, installed from synaptic, and none of these are creating the components necessary for networking connectivity from with the virtual environment, I would then assume that there is something fundamental missing from these three separate Unbuntu installs, that I installed on the Dell. 

But damned if I know what.

And so, another big sigh.

---

### Post by bigsigh on 2010-03-16
Comparing the synaptic list on the working installation on the Dell laptop to non-working test station I see....

The working install of vmware player 3.0.0, has Nagios3, Opennms, php5, mysql, jnettop, firestarter, postgresql, along with apache2 and sun java6.
Interestingly, the working install doesn't list dkms though the non-working test install does, as I recall this is installed with build essentials, which is installed on both units.
The working install is a test unit, all the listed programs were working in environment at one time. 

A couple lib of possible interest on the working station are libadnsl and libappconfig....,
also bison and autotools.dev, both units have matching perl installs.

Another late night attempt with the virtualbox install on the test unit yielded a eth0 not connected error from the start up messages of the guest, though I swapped the cable between eth1 and 0, and adjusted the adaptor settings in virtualbox accordingly, I noted no error messages from virtualbox.

What is it about these ubuntu installations, errrrrrrrrrrrrr!!!!!?

---

### Post by bigsigh on 2010-03-21
So, at this point I have discovered, contrary to the user manual, that virtualbox apparently no longer has a bridge option in the network attach to, but the host interface option works to bridge, unlike vmware player, even better, it's in promiscuous mode, so that is working for my needs.

I also attempted another virtual machine installation on my working vmware player unit, lo and behold, that attempt ends with a /dev/vmnet0 error, even though this unit has the vmnet files in /dev, sigh, the working virtual machine continues to work with its 'custom' option, for /dev/vmnet0, but damned if I've seen how to create this custom option when creating a new machine.

Isn't this fun!

---


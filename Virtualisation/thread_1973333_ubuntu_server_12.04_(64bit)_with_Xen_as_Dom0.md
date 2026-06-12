---
title: "ubuntu server 12.04 (64bit) with Xen as Dom0"
date: 2012-05-04
forum: Virtualisation
---

### Post by mhoulier on 2012-05-04
Hi,

I want to experiment with Xen to run multiple HVMs (Windows XP,7 & Linux).
I'd like to get vga passthrough working.

My hardware: AMD FX4100, Gigabyte GA-970A-D3 (Bios F6), 16gb DDR3 , AMD RadeonHD 7750.
Afaik my hardware supports virtualization (AMD-v and IOMMU both enable in bios).

I've had a look at several wiki/tutorials about Xen on Ubuntu and it's unclear on what the appropriate setup is.
My intent was to just use Xen with the xl toolstack, no XEND/xm, no XAPI or libvirt.

- Is anyone using such setup?

- Should I skip Xen 4.1.2 and use 4.2 unstable from source?

Ubuntu 12.04 is supposed to work as [_Dom0 for Xen_]("http://wiki.xen.org/wiki/Dom0_Kernels_for_Xen") apparently.
I've installed Ubuntu server 12.04 (64bit).
I got Xen packages (xen-hypervisor-4.1-amd64 and dependencies), if I understand correctly, this basically installs [_Xen 4.1.2_]("https://launchpad.net/ubuntu/precise/+package/xen-hypervisor-4.1-amd64").

[_On the Xen wiki_]("http://wiki.xen.org/wiki/Choice_of_Toolstacks"), I understand that "xl" is supposed to be the default toolstack starting with Xen 4.1.
But, when I boot on Xen, 'xl info' returns:
**ERROR: A different toolstack (xm) have been selected!**

- So, I guess I need to set "TOOLSTACK=xl" in /etc/default/xen?

Now, when I boot on Xen, 'xl info' returns valid details.
But, 'xl list' result is somewhat incorrect, Dom0's name is "(null)" instead of "Domain-0".

- Any idea why it can't get the domain 0 name?

I noticed that when I log in Xen, I get a core dump caused by /usr/bin/landscape-sysinfo, line 11:
```
from twisted.internet import reactor
```

- I've no idea what's going on, especially since I haven't selected Landscape when installing Ubuntu Server.
Any suggestions? thanks.

This crash doesn't terminate Xen, so I guess I can live with it?

Also in a [_Xen Ubuntu community tutorial_]("https://help.ubuntu.com/community/XenProposed#Basic_Installation"), it is mentioned to disable "xend" service: 'update-rc.d xend disable'
And, in a [_XCP/debian tutorial_]("http://wiki.xen.org/wiki/XCP_toolstack_on_a_Debian-based_distribution#Workaround_XAPI_conflicts_with_XEND_.28Debian_and_Ubuntu.29"), it suggests to modify /etc/init.d/xend and disable "xendomains": 'update-rc.d xendomains disable'

It seems, disabling both xend and xendomains services, breaks "xl" setup, since 'xl info' won't work anymore.

I saw someone mentions of /etc/init.d/xencommons, but it doesn't exist on my install.

- Does anyone know what is the correct setup?

Any insight would be much appreciated, thanks!

---

### Post by king9174 on 2012-05-29
Hi, I am currently looking into this same thing to use for work and found a wiki page which seemed promising but i havent tried it out yet. Please let me know if you get the problem solved and how incase I run into the same bother on my journey into xen.

[http://wiki.xen.org/wiki/XAPI_on_Ubuntu](http://wiki.xen.org/wiki/XAPI_on_Ubuntu)

---

### Post by mhoulier on 2012-05-29
As I mentioned I tried first getting it to work with a default toolstack provided with Xen 4.1.

Apparently, the 'xl' toolstack wasn't quite ready with 4.1.2, and I understand there are significant improvements coming with Xen 4.2.
I couldn't get it to create the guest image, sthg was going wrong, but I can't remember what that was exactly.
I know I first had to fix the keymaps location as mentioned in the wiki page you pointed out.
I went through various older forums/mailing list posts, but couldn't find sthg to help me solve the issue.

I didn't want to focus too much time getting Xen 4.1 working when 4.2 isn't too far away. Maybe I'll give Xen 4.2 from source a try as soon as I've time.

I then tried 'xm' toolstack (which will be officially deprecated in 4.2).
When trying to create the guest image, it kept crashing in some Python code involving some basic math operations. Python debugging (with pdb) wasn't helpful, and in dom0, for some unkown reason, trying to debug the python interpreter with gdb was actually crashing gdb, so  I gave up on that.

I did know about this wiki page, and tried XCP/xapi toolstack.
Maybe I did sthg wrong, but I couldn't get the 'xe' commands to work at all.

Since other people seems to be able to easily get Xen running, I'm probably missing sthg.

Sorry I couldn't help much, I hope you'll have more luck than me.
I'll post sthg about Xen 4.2 when I manage to try it.

---

### Post by levk on 2012-05-29
I use Xen 4.1.2 from Debian reps at home - I'm on Debian unstable, should be close to latest and greatest Ubuntu. I've had trouble with the xl toolstack; undo everything you had done to get it to work and use xm instead. xm is the default toolstack once you install xen-hypervisor and do nothing to configure it.

I haven't had any python trouble with the xm stack, I have packages python and python2.7 both installed, versions 2.7.2-10 and 2.7.3~rc2-2.1 respectively.

I'm fairly sure VGA passthrough works, I had tried it once but was too lazy to dig up a monitor to connect to the other card; I have no use for it and I don't need it for what I'm doing but I got no error messages from any sources available to me. PCI passthrough works with appropriate sacrifices. Including the same radeon 5450 card I tried in VGA and does GPGPU stuff just fine.

As far as installing 4.2 from source; this is my personal opinion but I would strongly recommend against that for a user. It's not easy and you'll basically be tied down to whatever kernel you compile it against or you'll have to go through it every time you want to upgrade. This is a complete kernel compile, it's not a DKMS package with all the pains and ample opportunities to hang yourself. And it's not a fact that whatever is there on any given day would function in any capacity at all.

---

### Post by mhoulier on 2012-05-30
Hi,
I tried each time from a fresh install of ubuntu server 12.04 (without packages auto updates) to make sure the issues weren't dependencies from previous changes.

I've checked already that my python is up to date (2.7.3).
The crash occurs in random.py with:
NV_MAGICCONST = 4 * _exp(-0.5)/_sqrt(2.0)

The closest issue I could find in a forum post, was a float overflow bug which was reported. But as far as I remember this concerned a much older version of python and was fixed since then.
And since gdb crashes when I try to debug the python interpreter, I don't know how to investigate the issue further.

- If anyone could suggest what to try from then, it would be much appreciated!


I'm not even close to try vga pass through unfortunately, but since many people have, I'm starting to wonder if there is some issue with either my bios or hardware in some way. Not sure exactly what I can do about it at that point.

About trying Xen 4.2 from source, that would be just a one time, to  see how it goes, since every other solutions I've tried this far didn't work. If this work, I'll wait for the release, I'm in no hurry, this is just for experimentation. Maybe in the mean time, I'll try KVM.

---

### Post by levk on 2012-05-30
Since you're doing fresh installs you might as well try Debian, you'll feel right at home there with same apt and things falling in the same places. Once you install Debian change 'squeeze' to 'unstable' in /etc/apt/sources.list and update then install Xen same as you would on Ubuntu.

---


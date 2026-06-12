---
title: "Using old PC as host for virtual servers?"
date: 2010-09-21
forum: Virtualisation
---

### Post by memilanuk on 2010-09-21
Hello,

I've got somewhat of an itch to try setting up an old PC as a host for a few virtual servers.  This is strictly for home use/ educational purposes - no more than a couple users at any point in time.  I've used Virtualbox on my main desktop PC (quad-core processor with 6GB RAM and plenty of HDD space) but in this case I was wanting to set things up on an older P4 2.4 GHz Sony Vaio desktop with 1GB of RAM.  Kind of kicking around the idea of doing a minimal install from the Server disc, and then setting up a couple VMs inside - maybe a basic LAMP server, maybe a virtual appliance or two from turnkeylinux.org.  

Like I said, this is mainly for educational purposes; at this point I think most of the 'services' for my home LAN are going to be running off a separate machine (another used PC) so if I b0rk this one its not the end of the world.  I am mainly wondering is it going to be too dog-slow to be usable, and since this is an older single-core processor with no virtualization add-ons, etc. is it going to work at all?  Would KVM or Xen work on this sort of setup, or are they too specialized?

TIA,

Monte

---

### Post by TheFu on 2010-09-22
A P4 doesn't have VT-x support, so Xen and KVM are out.  Actually, Xen may work for paravirtual DomUs, but definitely will not work for HMV installs.  All those cheap CPUs that Intel has pushed the last few years don't have VT-x. If you are interested in virtualization, VT-x is a must (or whatever AMD calls theirs).  VirtualBox should work.

1GB of RAM will be less than ideal, but you aren't really risking anything, so go ahead and try it.  Smaller distros will be better - check out TinyCore or DSL instead of Ubuntu Server, which needs 600MB min.  I consider 2GB min - 1 for the host and 1 for the DomU, but almost any Linux will run well enough for testing in 256-512MB of RAM.

---

### Post by memilanuk on 2010-09-23
> **TheFu said:**
> A P4 doesn't have VT-x support, so Xen and KVM are out.  Actually, Xen may work for paravirtual DomUs, but definitely will not work for HMV installs.  All those cheap CPUs that Intel has pushed the last few years don't have VT-x. If you are interested in virtualization, VT-x is a must (or whatever AMD calls theirs).

That was kind of what I was afraid of.  Seems like if I want to actually do 'real' virtualization I may have to pony up for some 'real' hardware instead of old-broken-hand-me-down desktops ;)  Either that or wait until used desktops that are capable of hardware virtualization start showing up... though I'm guessing its next to impossible to tell if something off of craigslist is going to meet that requirement ;)


> consider 2GB min - 1 for the host and 1 for the DomU, but almost any Linux will run well enough for testing in 256-512MB of RAM.

Given that there are Linux VPS out there with 256MB of RAM [(or less)]("http://www.lowendbox.com/blog/yes-you-can-run-18-static-sites-on-a-64mb-link-1-vps/") for web servers... I figured that basic home server stuff shouldn't be to strenuous as long as I'm not trying to do something like media streaming (eventually, but not right now and not on this hardware).

Thanks,

Monte

---

### Post by TheFu on 2010-09-24
> **memilanuk said:**
> That was kind of what I was afraid of.  Seems like if I want to actually do 'real' virtualization I may have to pony up for some 'real' hardware instead of old-broken-hand-me-down desktops ;)  Either that or wait until used desktops that are capable of hardware virtualization start showing up... though I'm guessing its next to impossible to tell if something off of craigslist is going to meet that requirement ;)


All my desktops the last 4 yrs have had VT-x support, but I've gone out of my way to ensure that.  Intel and AMD are still producing low end CPUs without it, so even today, you need to be careful and lookup both the specific CPU capabilities AND the BIOS capabilities for the system you build/purchase.  Some vendors have removed the ability to toggle HW Virt support in the consumer BIOSes and only put it into the "business class" systems.  My new Dell Studio 1558 (Core i5/6GB) came with VT-x enabled, I didn't need to manually toggle it.

VirtualBox doesn't need VT-x and is reported to actually run faster without out. Seems the original VirtualBox developers knew more about CPU virtualization and were able to use less code than Intel. I joke, but still there were concrete reports about the performance being better in older versions of VirtualBox. While I can't recommend VirtualBox for servers due to my stability issues with it, it is very usable for desktops and processing that needs just a few days.  RAM is more important and CPU in virtualization.

---

### Post by snowpine on 2010-09-24
I have a 3ghz Pentium 4 with 1.5gb RAM. Despite the lack of VT-x, it runs VirtualBox pretty well; I use it to test-drive full-featured GUI distros all the time. Not blazing fast but it gets the job done. I'm sure yours will be fine for some low-resource educational projects. :)

---


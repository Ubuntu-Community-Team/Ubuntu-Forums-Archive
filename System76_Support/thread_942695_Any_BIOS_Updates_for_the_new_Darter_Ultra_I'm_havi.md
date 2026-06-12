---
title: "Any BIOS Updates for the new Darter Ultra? I'm having some virtualization issues"
date: 2008-10-09
forum: System76 Support
---

### Post by tikkun on 2008-10-09
Does anyone know where I might find a BIOS update that properly supports VT-x? If not, who do I need to beg/complain/offer my first born to regarding the issue?

Backstory:

I'm trying to get VirtualBox 2.0.2 to install a 64-bit Vista guest on a brand new Darter Ultra and Vista fails during install (I get an error message reporting that the CPU isn't compatible with 64-bit mode ). I've enabled VT-x/AMD-V for the VM in VBox, but this doesn't resolve the issue

Looking at the VBox.log file I see:

HWACCM: No VMX or SVM CPU extension found. Reason VERR_VMX_MSR_LOCKED_OR_DISABLED 

Which according to the post below:

[http://www.virtualbox.org/ticket/2196](http://www.virtualbox.org/ticket/2196)

Means that either my CPU doesn't support virtualization (it's a P9500 which does), or there isn't proper support from my bios.

---

### Post by thomasaaron on 2008-10-09
I kinda don't think it's a BIOS upgrade issue. But let's not take that off the table yet.

The guy in that post fixed the problem as follows:

> Trusted Extensions was on in the BIOS, preventing anything new from using the hardware extensions. All I did was turn Trusted Extensions off and both Solaris 10 and OpenSolaris? were able to run in 64-bit mode. 

I've seen the trusted settings in BIOSes before, but I don't know if it's in the DarU3's BIOS (and I'm not near one at the moment). You may want to check that first.

There is also a setting in there for Installed O/S under the advanced tab. You might want to play with that as well.

Tell me what BIOS version you have, and I'll see what I can find out...
```
sudo dmidecode -s --bios-version
```

---

### Post by tikkun on 2008-10-09
Thanks for the quick reply, I greatly appreciate it :)

> **thomasaaron said:**
> I've seen the trusted settings in BIOSes before, but I don't know if it's in the DarU3's BIOS (and I'm not near one at the moment). You may want to check that first.

Unfortunately I don't see anything in the BIOS for this on my DarU3.

> **thomasaaron said:**
> There is also a setting in there for Installed O/S under the advanced tab. You might want to play with that as well.

Initially at Vista, set to XP, does not resolve the issue, set to Other, does not resolve the issue.

> Tell me what BIOS version you have, and I'll see what I can find out...

Running sudo dmicode -s bios-version produced 1.00.18S.

Thank you again for your assistance!

---

### Post by thomasaaron on 2008-10-09
OK, that is definitely the latest BIOS. 

I've referred this to the R&D department, and they will see what they can figure out.

Just a quick question, though: You *did* install the 64-bit VirtualBox from Sun Microsystems, right?

---

### Post by tikkun on 2008-10-09
> **thomasaaron said:**
> Just a quick question, though: You *did* install the 64-bit VirtualBox from Sun Microsystems, right?

Right.

I installed the virtualbox-2.0 package using apt-get after adding the line below to my sources.list file:

```
deb http://download.virtualbox.org/virtualbox/debian hardy non-free
```

I followed the steps from Sun at the link below to download and register their public key (it's also where I got the line for my sources.list file):

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

I was curious if I had somehow borked something, so I just ran

```
ls /var/cache/apt/archives/ | grep box
``` 

The result is:

```
virtualbox-2.0_2.0.2-36488%5fUbuntu%5fhardy_amd64.deb
```

---

### Post by Vadi on 2008-10-10
This isn't a BIOS but a CPU issue. Yours doesn't have the virtualization extension.

Means you can only run 32bit guests in virtualbox, or upgrade your cpu (to one that has virtualization).

---

### Post by tikkun on 2008-10-13
> **Vadi said:**
> This isn't a BIOS but a CPU issue. Yours doesn't have the virtualization extension.

Means you can only run 32bit guests in virtualbox, or upgrade your cpu (to one that has virtualization).

I wish it were that easy. When I was researching what to buy I went to Intel's website and found that it does support Virtualization:

[http://ark.intel.com/cpu.aspx?groupID=35566](http://ark.intel.com/cpu.aspx?groupID=35566)

Feel free to correct me if I'm wrong, or if the material from Intel is misleading.

---

### Post by thomasaaron on 2008-10-13
I not an expert on virtualization, but I'm willing to run some tests. I've asked R&D for information and am still awaiting a response from them.

Can you create a 64-bit Ubuntu VM? In theory, that should fail too, right?

---

### Post by tikkun on 2008-10-13
> **thomasaaron said:**
> Can you create a 64-bit Ubuntu VM? In theory, that should fail too, right?

Right, very good suggestion . I'll try that tonight when I get home from work.

On a similar line of thought, I get the same problem with Vista x64 installing into a VMWare Workstation 6.5 VM, so I don't think it's a VirtualBox issue.

In other news I found conflicting information from Intel. In the links below, Intel does not mention that the P9500 support Virtualization technology, while the older T9500 explicitly says so:

[http://processorfinder.intel.com/details.aspx?sSpec=SLB4E](http://processorfinder.intel.com/details.aspx?sSpec=SLB4E)
(P9500)

[http://processorfinder.intel.com/details.aspx?sSpec=SLAZA](http://processorfinder.intel.com/details.aspx?sSpec=SLAZA)
(T9500)

Some marketing folks at Intel have crossed the wrong I and dotted the wrong T somewhere, but unfortunately I can't tell where exactly from their web pages alone.

---

### Post by tikkun on 2008-10-13
Attempting to install Ubuntu 8.04 AMD64 using the alternate install CD produces the error message below:

"This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot - please use a kernel appropriate for your CPU".

I guess this is the price I pay for being an early adopter :KS

---


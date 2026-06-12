---
title: "Ubuntu Moblin Remix Confirmed"
date: 2009-06-02
forum: The Cafe
---

### Post by ghindo on 2009-06-02
> **Computex, Taipei, June 2, 2009** – Today, Canonical announced support of Moblin, an optimized open source Linux software stack and application framework, by committing to the development of a product based on the recently released Moblin v2 for Intel® Atom™ processor-based platforms. Moblin v2 provides the core infrastructure, applications and user experience that Canonical will integrate into an Ubuntu-based product.[http://www.ubuntu.com/news/canoical-commits-ubuntu-moblin](http://www.ubuntu.com/news/canoical-commits-ubuntu-moblin)

---

### Post by drawkcab on 2009-06-02
Nice!

---

### Post by floborg on 2009-06-02
So this is still the Atom-tailored Moblin, rather than the Clutter desktop environment?

---

### Post by Mr. Picklesworth on 2009-06-02
Moblin 2 does use the Clutter toolkit, floborg. And it is very pretty, on both the inside and the outside :)

---

### Post by dirtylobster on 2009-06-02
I don't really get the purpose of this. What's wrong with Moblin by itself?

---

### Post by handy on 2009-06-02
I think? It means that Canonical are looking at Moblin as the standard for Netbooks, rather than splitting Linux distro's up for the same job, they have chosen to focus on the best tool for the job.

I could of course be wrong. :)

---

### Post by drawkcab on 2009-06-02
Isn't moblin beta built on fedora now?  I took it to mean that it would be developed atop ubuntu if this is correct.

---

### Post by dirtylobster on 2009-06-02
So... they're scrapping UNR and rebrand/fork Moblin?

---

### Post by gloscherrybomb on 2009-06-02
Only happy if it works on a 701.

---

### Post by gnomeuser on 2009-06-02
> **drawkcab said:**
> Isn't moblin beta built on fedora now?  I took it to mean that it would be developed atop ubuntu if this is correct.

Moblin is based on a mix of Fedora and openSUSE, it is built using Novell' Open Build Service. 

This means that Canonical will be porting over the patches, probably integrating what isn't yet upstream, and rolling their own Moblin like release. Just like openSUSE, Linpus and Xandros are doing. I believe Fedora will aim to upstream the work and then package the Moblin specific parts so users can install or roll their own Moblin based on Fedora.

---

### Post by Deamos on 2009-06-02
Very Very Awesome!

---

### Post by binbash on 2009-06-02
It is cool

---

### Post by floborg on 2009-06-03
> **Mr. Picklesworth said:**
> Moblin 2 does use the Clutter toolkit, floborg. And it is very pretty, on both the inside and the outside :)

What I meant was "is this just like the vanilla Moblin, only able to run on certain Intel processors?"

---

### Post by Mr. Picklesworth on 2009-06-03
Well one issue with Moblin by itself as a distribution is that it doesn't have Ubuntu's more pragmatic model of including drivers for everyone out of the box. (Partly because current images straight from the Moblin project are previews). Ubuntu, on the other hand, doesn't mind the ugly Broadcom wifi adapters used in many netbooks.

Oh, and I for one am used to Ubuntu's layout of packages and have fallen in love with my list of installed packages (which I can clone onto a new machine by importing a simple package list, courtesy of dpkg and synaptic).

---

### Post by ghindo on 2009-06-03
> **Mr. Picklesworth said:**
> Oh, and I for one am used to Ubuntu's layout of packages and have fallen in love with my list of installed packages (which I can clone onto a new machine by importing a simple package list, courtesy of dpkg and synaptic).Wow, that sounds cool.  How do you do that?

---

### Post by monsterstack on 2009-06-03
> **ghindo said:**
> Wow, that sounds cool.  How do you do that?

I did this a few times. ([COLOR="Red"]Edit[/COLOR]: but somebody else has a better way of doing it below.)

Still an entirely terminal-way of doing it is to run this on your old machine,

```
dpkg --get-selections > ~/installed-software.log
```

Then copy the file over to your new installation and run,

```
sudo dpkg --set-selections < ~/installed-software.log
```

That will tell dpkg of your must-get packages. The next thing to do is fire up "sudo dselect" (you might not have it installed) and choose option "i" to install your packages.

---

### Post by Mr. Picklesworth on 2009-06-03
I just fire up Synaptic, use File -> Save Markings As..., tell it to save the full state (although this regrettably breaks the tracking of autoinstalled packages, so dependant packages look like they were installed by you explicitly) and choose where to save.

Then in a new install I open up Synaptic, go to File -> Read Markings and it's done :)

---

### Post by monsterstack on 2009-06-03
> **Mr. Picklesworth said:**
> I just fire up Synaptic, use File -> Save Markings As..., tell it to save the full state (although this regrettably breaks the tracking of autoinstalled packages, so dependant packages look like they were installed by you explicitly) and choose where to save.

Then in a new install I open up Synaptic, go to File -> Read Markings and it's done :)

That's much better than my method. Thanks. :)

---

### Post by ghindo on 2009-06-03
> **Mr. Picklesworth said:**
> I just fire up Synaptic, use File -> Save Markings As..., tell it to save the full state (although this regrettably breaks the tracking of autoinstalled packages, so dependant packages look like they were installed by you explicitly) and choose where to save.

Then in a new install I open up Synaptic, go to File -> Read Markings and it's done :)Thanks!

---

### Post by omegamormegil on 2009-06-04
From [https://wiki.ubuntu.com/Specs/MobileKarmicMoblinRemix](https://wiki.ubuntu.com/Specs/MobileKarmicMoblinRemix)

[INDENT]An out-of-archive one-time remix of Ubuntu will be prepared including the identical set of software as the Moblin 2.0 Release for demonstration and comparison purposes. This is **not expected to be an ongoing release series**, but rather a means of experimenting with integration between the Moblin project and other software in Ubuntu.[/INDENT] 

[INDENT]Ubuntu Moblin Remix presents the **Moblin interface and user experience on the solid base of Ubuntu 9.04**, providing a platform for development and experimentation for those interested in the next generation of user interfaces for Mobile computing.[/INDENT]

So according to that spec this will be a one time release for experimentation purposes only, in order to "better understand how the Moblin software can improve Ubuntu".  Sounds like the Moblin interface is just being added onto an Ubuntu backend.  

Of course, I imagine this experiment could cause bits of Moblin to be permanently integrated into an ongoing Ubuntu release - perhaps Ubuntu Netbook Remix?

---


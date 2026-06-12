---
title: "[SOLVED] VirtualBox Ubuntu Server 8.04.1 / 8.10"
date: 2008-12-02
forum: Virtualisation
---

### Post by DGortze380 on 2008-12-02
I had an Ubuntu LAMP (8.04.1) set up in a virtual machine in Virtual Box.

Reformatted my drive.

Went to install a new LAMP Virtual Machine (tried 8.04.1 and 8.10), now I'm getting this error message after grub:

The kernel requires the following features not present on the CPU: 0:6
Unable to boot - please use a kernel appropriate for your CPU

Nothing has changed. Still an i386 virtual machine, still the same 8.04 i386 iso. What am I missing here?

---

### Post by bodhi.zazen on 2008-12-02
Power off The Ubuntu Guest.

In Virtualbox, Click Machine -> Settings -> General -> Advanced
Check Enable PAE/NX
Click OK

Re-Start Virtual Machine

If that fails, try installing the generic kernel in the guest.

[http://blog.networkfoo.org/?p=170](http://blog.networkfoo.org/?p=170)

[https://answers.launchpad.net/ubuntu/+question/23343](https://answers.launchpad.net/ubuntu/+question/23343)

---

### Post by DGortze380 on 2008-12-02
> **bodhi.zazen said:**
> Power off The Ubuntu Guest.

In Virtualbox, Click Machine -> Settings -> General -> Advanced
Check Enable PAE/NX
Click OK

Re-Start Virtual Machine


That worked. Isn't PAE net boot? What is NX? I'm not familiar with them, just trying to figure out why it caused such a problem.

---

### Post by bodhi.zazen on 2008-12-02
PAE : [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

NX : [http://en.wikipedia.org/wiki/NX_bit](http://en.wikipedia.org/wiki/NX_bit)

---

### Post by cfuentea on 2008-12-03
i've tried to select this option, but my virtualbox app has this disabled.. it's normal?

Thanks

---

### Post by DGortze380 on 2008-12-03
What version of VirtualBox? I'm running 2.0.6 non-OSE for OS X.
Not sure if the OSE version includes this setting or not, I've heard it's much less compatible.

---

### Post by bodhi.zazen on 2008-12-03
> **cfuentea said:**
> i've tried to select this option, but my virtualbox app has this disabled.. it's normal?

Thanks

These options will only be available if your CPU supports them.

If virtualbox is running no need to worry, if you are having problems, what is the exact error message ?

---

### Post by Lemony Fresh on 2008-12-12
Nice!!! Thanks for the help!

---

### Post by Lemony Fresh on 2008-12-12
Nice!!! Thanks for the help!

---

### Post by joeinbend on 2008-12-16
...Just because I didn't see the question answered...  "Isnt PAE net boot?"

You are thinking of "PXE"

:)

---

### Post by rukshankb on 2009-03-16
> **bodhi.zazen said:**
> Power off The Ubuntu Guest.

In Virtualbox, Click Machine -> Settings -> General -> Advanced
Check Enable PAE/NX
Click OK

Re-Start Virtual Machine

If that fails, try installing the generic kernel in the guest.

[http://blog.networkfoo.org/?p=170](http://blog.networkfoo.org/?p=170)

[https://answers.launchpad.net/ubuntu/+question/23343](https://answers.launchpad.net/ubuntu/+question/23343)

Great explanation:D

---


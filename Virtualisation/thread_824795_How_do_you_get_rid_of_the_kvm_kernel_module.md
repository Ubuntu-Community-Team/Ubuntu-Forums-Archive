---
title: "How do you get rid of the kvm kernel module"
date: 2008-06-10
forum: Virtualisation
---

### Post by Methuselah on 2008-06-10
I tried out KVM after having problems with the virtualbox-ose in add/remove. KVM was also useless though, couldn't boot from any hard disk. So I ran apt-get remove on all the packages I added. However, it didn't remove the kernel module.

Now, I have installed the virtualbox from Sun's website and it's complaining about the KVM kernel module being present. I don't know how to remove it though. sudo modprobe -r kvm doesn't work because it says the module is in use and refuses to unload it. Trying to remove kvm-intel in teh same way gives no error but it still shows up in the list of modules.

Sadly, I haven't gotten much help on these forums.
I guess my questions are too hard. :(
Here's hoping for better luck this time.

---

### Post by tighem on 2008-06-10
Hit escape at the boot menu and select recovery mode.

When the menu appears select root shell and type:

rm -rf /lib/modules/2.6.24-18-generic/kernel/arch/x86/kvm

This assumes you are running the -18-generic kernel. You will need to replace that section depending on kernel type and version. 

This will physically remove the modules, and they will not be able to load. This generates an error message on startup but it doesn't stop startup and you won't see it if the splash screen is up.

The kernel devs made the decision to include KVM by default in Hardy so it gets reinstalled during each kernel upgrade. In my bug report with VirtualBox on this, their devs labeled the decision "stupid". Virtualbox 1.6 actually froze the machine hard if the kvm modules were loaded. I found their attitude quite unprofessional.

---

### Post by wootah on 2008-06-10
> **tighem said:**
> Hit escape at the boot menu and select recovery mode.

When the menu appears select root shell and type:

rm -rf /lib/modules/2.6.24-18-generic/kernel/arch/x86/kvm

This assumes you are running the -18-generic kernel. You will need to replace that section depending on kernel type and version. 

This will physically remove the modules, and they will not be able to load. This generates an error message on startup but it doesn't stop startup and you won't see it if the splash screen is up.

The kernel devs made the decision to include KVM by default in Hardy so it gets reinstalled during each kernel upgrade. In my bug report with VirtualBox on this, their devs labeled the decision "stupid". Virtualbox 1.6 actually froze the machine hard if the kvm modules were loaded. I found their attitude quite unprofessional.

```

rm -rf /lib/modules/$(uname -r)/kernel/arch/x86/kvm

```

:)

---

### Post by Methuselah on 2008-06-10
Thanks!
That technique worked!

---

### Post by Methuselah on 2008-06-10
Unfortunately, this version of virtualbox still has the bug which causes win2k installation to reboot at some point before it's complete. The only solution that has worked so far for me is qemu but I don't yet know how to build kqemu on Ubuntu.

---

### Post by bored_shiva on 2008-06-21
I have a similar problem with kvm-intel (though rmmod works well on my system (Hardy)) but I was hoping for a less destructive solution. Instead of physically removing the module, is there any way to just prevent it from loading at bootup?

Alternatively (and actually, better): I would like to launch virtualbox from a script so that it does roughly this:

-----
if (kvm-intel is loaded)
  sudo rmmod kvm-intel

launch virtualbox, block until done.

sudo ismod kvm-intel 
-----

unfortunately, I don't know anything about scripting, so I don't know how to actually "say" that. Also, that approach would require me to type in a password twice, which kind of defeats the idea of automation. Any suggestions?

---

### Post by slim180 on 2008-08-21
I have Ubuntu 8.04 too .. I'm trying out different visualization programs including KVM and VirtualBox.  I just discovered these steps to temporarily unload the KVM module so that I can run VirtualBox...


/etc/init.d/libvirt-bin stop

less /proc/modules and search for kvm...   I have an Intel chip so I had two hits: kvm-intel and kvm .. next, simply remove them in order:


modprob -r kvm_intel
modprob -r kvm

There was no complaining this time about the module being in-use.  VirtualBox is free to run know without tripping over the module.  These modules will return after a reboot or by running the modprob commands again to load the modules:

modprobe kvm_intel
modprobe kvm
/etc/init.d/libvirt-bin start

-jc

---

### Post by your_gnu_spuddy on 2008-08-31
used method descibed here [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

first remove kvm

sudo apt-get remove --purge kvm

then to stop module from loading

sudo rm -rf /etc/kvm/ /etc/udev/rules.d/45-kvm.rules /etc/init.d/kvm

---


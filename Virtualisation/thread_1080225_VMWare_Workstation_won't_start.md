---
title: "VMWare Workstation won't start"
date: 2009-02-25
forum: Virtualisation
---

### Post by mister_playboy on 2009-02-25
I've just installed VMWare Workstation on Ubuntu 8.10 64 bit.  If I try to run Workstation from Apps > System Tools, a box in the lower panel says it's starting, then nothing happens.

If I run "vmware" from command line, I get this:

modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
/usr/bin/vmware: line 31:  4941 Segmentation fault      "$BINDIR"/vmware-modconfig --appname="VMware Workstation" --icon="vmware-workstation"

I installed using the GUI installer, and the files do exist in /usr/bin.

Any ideas?

---

### Post by darco on 2009-02-25
I would try reinstalling. Do you have the guide on installing? Check the Sticky above for how to or go to vmware's website on installing.
 
darco

---

### Post by veloce on 2009-02-26
> **mister_playboy said:**
> I've just installed VMWare Workstation on Ubuntu 8.10 64 bit.  If I try to run Workstation from Apps > System Tools, a box in the lower panel says it's starting, then nothing happens.

If I run "vmware" from command line, I get this:

modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
/usr/bin/vmware: line 31:  4941 Segmentation fault      "$BINDIR"/vmware-modconfig --appname="VMware Workstation" --icon="vmware-workstation"

I installed using the GUI installer, and the files do exist in /usr/bin.

Any ideas?

Does workstation have "vmware-config.pl"?  Normally it is called sometime during installation to create the modules for your kernel.  

If you can find it, try running it to (re)create the modules.

---

### Post by AnimalMagic on 2009-02-27
Is 8.10 supported yet? I thought vmware-config.pl failed on 8.10...

---

### Post by veloce on 2009-03-01
> **AnimalMagic said:**
> Is 8.10 supported yet? I thought vmware-config.pl failed on 8.10...

I certainly have it working.  Can't remember whether I needed to patch vmware-config.pl (from memory I needed to on some machines and not others, though why 64bits v 32 bit or desktop v server should make any difference escapes me.)

---

### Post by jsodini on 2009-03-01
What's happening is VMware Workstation is looking for its kernel modules and isn't finding any. Run /usr/bin/vmware-config.pl to solve. You'll have to do this every time you update the kernel.

-James

---

### Post by darco on 2009-03-02
> **jsodini said:**
> What's happening is VMware Workstation is looking for its kernel modules and isn't finding any. Run /usr/bin/vmware-config.pl to solve. You'll have to do this every time you update the kernel.

-James

I just upgraded to 27-11 and on first running of vm ws, it automatically upgraded the modules...nice

darco

---

### Post by veloce on 2009-03-03
> **darco said:**
> I just upgraded to 27-11 and on first running of vm ws, it automatically upgraded the modules...nice

darco

Hopefully that functionality will "trickle down" to the free versions ...

---

### Post by mister_playboy on 2009-03-13
The file vmware-config.pl doesn't exist.  After digging around the web, it seems it was removed in the most current versions, and that this leads to various problems.

I'm just going to try some other virtualization program, as I'm not interested in screwing around with this.  They should have a working installer for Ubuntu, plan and simple.  I'm not impressed.

---

### Post by veloce on 2009-03-15
> **mister_playboy said:**
> The file vmware-config.pl doesn't exist.  After digging around the web, it seems it was removed in the most current versions, and that this leads to various problems.

I'm just going to try some other virtualization program, as I'm not interested in screwing around with this.  They should have a working installer for Ubuntu, plan and simple.  I'm not impressed.

It certainly exists in the latest version of vmware-server.

Given that workstation is a non-free version, you should ask for your money back.  That should get them giving you a hand to get it set up.

I use the free vmware-server, so when it takes a bit longer to get set up I recognise that the additional time I have to spend is my problem.

Good luck with other virtualization programs.  I think that VirtualBox is considered the easiest to install on Ubuntu.

---

### Post by mister_playboy on 2009-03-16
I had just been using the trial version, so I hadn't spent any money.

I got VirtualBox, which installed and works fine.

I just wanted to play with Haiku and have a XP machine to run my printer.

Right now, I'm forcing myself to type with Dvorak... so I don't mind a challenge!  I just got so tired of booting into unbearably slow Vista to print anything, and there were many alternatives to try, so why bother?

---

### Post by yelirekim on 2009-03-18
I just ran:

```

mv /usr/lib/vmware/modules/binary /usr/lib/vmware/modules/binary.old
vmware-modconfig &#8211;console &#8211;install-all

```

I think after 6.5 the python config script is wrapped up as a binary "vmware-modconfig", the first line deletes/backs up your original binary kernel configurations for vmware.

---

### Post by mister_playboy on 2009-03-21
Obligiatory post from my XP virtual machine... works great!  Networking worked right out of the box, and now I can use my printer without having to disrupt everything else to boot into Vista.  :D

---

### Post by spinwood on 2009-05-04
> **yelirekim said:**
> I just ran:

```

mv /usr/lib/vmware/modules/binary /usr/lib/vmware/modules/binary.old
vmware-modconfig –console –install-all

```

I think after 6.5 the python config script is wrapped up as a binary "vmware-modconfig", the first line deletes/backs up your original binary kernel configurations for vmware.

This worked for me... Thanks!

---

### Post by jtsop on 2009-07-07
this happens only in the 64bit version this solves it:

sudo mv /usr/lib/vmware/modules/binary /usr/lib/vmware/modules/binary.old  
sudo vmware-modconfig –console –install-all --icon="vmware-workstation" --appname="VMware Workstation"

---


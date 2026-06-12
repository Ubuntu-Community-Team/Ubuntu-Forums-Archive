---
title: "Security tips for inspecting/isolating a VM"
date: 2016-09-01
forum: Virtualisation
---

### Post by chad_b2 on 2016-09-01
Hello all, are there any tried-&-true Best Practices for scanning/cleaning a virtual machine that might have some malicious scripts/spyware/etc? I've got a CentOS vm to run in Virtualbox which a subcontractor has loaded with software of my specification (mostly developer tools...Anaconda3, Rodeo, etc), but now I wonder if that was a good idea, seeing as there *could* be extra goodies on there to get access to IP-sensitive files I would load there later.

I briefly searched this subforum for 'security' and didn't see any titles that lined up with the general concern.

If there's no way to scan a VM with high confidence of detection capability, is there a way to get a log of the software packages added so I can make a fresh VM and have it automatically download and install the suite of packages?

---

### Post by &amp;KyT$0P# on 2016-09-01
In this specific case it's no different from a bare-metal machine.  So here's how to list installed packages on CentOS -
```
yum list installed
```

Compare /etc/yum.repos.d as well

---

### Post by chad_b2 on 2016-09-01
Thanks, halogen. So would Lynis, chrootkit, rkhunter or another package be effective in detecting any malicious scripts present in this VM, or for sake of caution and time, should I just start with a new VM and mirror the installed packages list?

---

### Post by &amp;KyT$0P# on 2016-09-01
If you think there's any chance of malware on the machine, it's much wise and safer to just start over.  Set up a separate VM yourself from scratch, using theirs as a guideline only, **do not** copy stuff from their running system (re-type it all yourself).  Don't even trust the iso(s) they gave you they used to set up the VM, download or verify it yourself.
* Oh, and make sure that their VM is totally disconnected from any network - unplug all virtual network cables and set network adapters to "Not attached".  No exceptions.  Depending on the malware, it might be able to exploit the network connection, find your other machines and at least try to wreak havoc...

OK so depending how much you trust the people who set up that VM, some of that might be excessive caution, so decide your own paranoia level.  But keep in mind that whoever set up that VM had root access - and with Linux systems, you need to assume that you can't detect a compromise from the system where the root account is compromised.

---

### Post by Habitual on 2016-09-02
If it were "me"....
I'd isolate the infected machine and take a dd of the partitions to file and then move the output off the infected host.
Offline and rebuild the infected host.
Rebuild partitions from dd file in a sandboxed Virtual environment.

But that's just me.

---

### Post by TheFu on 2016-09-07
I'd blow it away and start over if there is **any** chance of malicious settings or code by a contractor or former employee.  OTOH, since I've been one of those 'contractors', I also know that my reputation isn't worth screwing around with systems, even if the company/boss sucked.  Out of 10,000 IT professionals, only 1 would do malicious stuff.  Incompetence is completely different. That happens all the time. Heck, I'm incompetent in many areas too.

---


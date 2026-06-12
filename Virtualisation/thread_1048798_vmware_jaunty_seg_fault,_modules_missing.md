---
title: "vmware jaunty seg fault, modules missing"
date: 2009-01-23
forum: Virtualisation
---

### Post by unclecameron on 2009-01-23
I just upgraded to jaunty alpha3 and the kernel doesn't seem to find the vmware modules, then it seg faults with a core dump, does anyone know why? Everything else on my upgrade works fine. I'm using VMWare workstation 6.5.

---

### Post by unclecameron on 2009-01-26
ok, I figured it out, at least partly, you have to:

mv /usr/lib/vmware/modules/binary /usr/lib/vmware/modules/binary.old

then

vmware-modconfig --console --install-all

now I'm screwing around with the network bridges I had before to make them work again, I have the host network (wireless) working by deleting the networks in the vmware network editor, but now my guests don't work, so I think I have to recreate them somehow...

---

### Post by Dedoimedo on 2009-01-26
Shouldn't this go into alpha/beta/zeta jones testing section?
There's a reason why alpha/beta software is called what it's called...
Dedoimedo

---

### Post by unclecameron on 2009-01-26
unless vmware updates 6.5 before jaunty releases, I don't think it will know that it needs to rebuild the kernel modules, so others may still have the same problem.

---

### Post by unclecameron on 2009-01-27
got the network up, basically NAT on the guests crashes things, so I deleted the NAT network and just bridged everything to the host, then gave the guests a static IP and it works. Hope this helps someone else trying to get this setup running :)

---

### Post by pisces107 on 2009-02-03
Doing:

mv /usr/lib/vmware/modules/binary /usr/lib/vmware/modules/binary.old

then

vmware-modconfig --console --install-all


...worked for me. Thanks unclecameron

Ubuntu 9.0.4 
Kernel 2.6.28-6-generic
platform x86_64

---

### Post by dlzerocool on 2009-02-12
Awesome it worked perfectly, I've been looking for this few days ago.
> 
sudo mv /usr/lib/vmware/modules/binary /usr/lib/vmware/modules/binary.old
sudo vmware-modconfig --console --install-all

Thank you !

---

### Post by vmatherly on 2009-03-14
I tried the manual mod rebuild solution with Jaunty alpha 7 but vmware-workstation will not start.

```

vmatherly@devstation:~$ vmware
/usr/bin/ldd: line 117: 28779 Bus error               (core dumped) LD_TRACE_LOADED_OBJECTS=1 LD_WARN= LD_BIND_NOW= LD_LIBRARY_VERSION=$verify_out LD_VERBOSE= "$@"
/usr/lib/vmware/bin/vmware-modconfig: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory


```

Any suggestions


oops I mean Alpha 6

---

### Post by vmatherly on 2009-03-15
Tried to fix this by linking the missing lib file to the existing one. 

```
sudo ln -s /usr/lib/libexpat.so.1.5.2 /usr/lib/libexpat.so.0
```

still not working now I get:

```
/usr/bin/ldd: line 117:  7152 Bus error               (core dumped) LD_TRACE_LOADED_OBJECTS=1 LD_WARN= LD_BIND_NOW= LD_LIBRARY_VERSION=$verify_out LD_VERBOSE= "$@"
/usr/bin/vmware: line 31:  7132 Bus error               (core dumped) "$BINDIR"/vmware-modconfig --appname="VMware Workstation" --icon="vmware-workstation"

```

---

### Post by selivanow on 2009-03-24
This would seem to be a VMware bug.  The installer does not check to see if the modules actually load and rebuild them if it doesn't.  I tried to install vmplayer 2.5.1 from a fresh jaunty install and still had the errors.  Rebuilding the modules did the trick.

---

### Post by rfbaum on 2009-03-24
I tried this on a Toshiba Z305D notebook & it worked network & sound
Richard

---

### Post by CeNoBiTa on 2009-04-24
Thanks a lot!!!

Worked perfect. You saved me a lot of trouble!!

---

### Post by parsim on 2009-04-25
Brilliant. Thank you!

---

### Post by kanamor on 2009-05-12
Thankyou very much! works fine!

---


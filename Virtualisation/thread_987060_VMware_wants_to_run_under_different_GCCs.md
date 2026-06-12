---
title: "VMware wants to run under different GCCs"
date: 2008-11-19
forum: Virtualisation
---

### Post by fester225 on 2008-11-19
I'm running 8.04 (Hardy) and attempting to upgrade to VMware 1.0.8. The install script says I've installed successfully. When I run the program from the desktop icon, not much happens. When I run 'vmware' from a terminal prompt, I get;

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

How do I load GCC 3.4 in addition to GCC 4.2? Better yet, how do I get VMware to compile everything using GCC 4.2?

---

### Post by bodhi.zazen on 2008-11-19
Opinions vary on what to do with this error message and no "expert" has weighed in.

Some say to compile any ways (ignoring the warnings) and seem to be able to do so without any issues.

If you wish, set your gcc version

see the first post on this thread for how to do this : 

[http://ubuntuforums.org/showthread.php?t=65638](http://ubuntuforums.org/showthread.php?t=65638)

---

### Post by fester225 on 2008-11-19
I've decided the way to go for now is to re-install gcc-4.2.3 since the installer with any-any seems to want it.
I downloaded gcc-4.2.3, but there is no runme.pl file in it. Apt-get install gcc-4.3.2 gives me a 'can't find the file' diagnostic. How do I install it?

---

### Post by helmi03 on 2008-11-22
> **fester225 said:**
> I'm running 8.04 (Hardy) and attempting to upgrade to VMware 1.0.8. The install script says I've installed successfully. When I run the program from the desktop icon, not much happens. When I run 'vmware' from a terminal prompt, I get;

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

How do I load GCC 3.4 in addition to GCC 4.2? Better yet, how do I get VMware to compile everything using GCC 4.2?

Hey I got same error message. Google is your best friend, this one works for me:

```
sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
```

---

### Post by ariebs on 2008-11-22
Helmi03 had it pretty close when he said to use


```
sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
```


However, I've been having problems with `ln -sf` lately -- it doesn't always seem to be forcibly replacing existing symlinks.

The problem: VMware distributes a version of the libgcc library that's older than what the rest of the system uses. The solution, it turns out, is easy:

```

sudo mv /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1{,.old}

```

VMware is looking first at its own libraries for libgcc, which is what is responsible for looking for the wrong things, so we simply change the name of their libgcc library to keep it from being used. You could also delete the VMware version, but you never know when or why you might want it in the future :)

---


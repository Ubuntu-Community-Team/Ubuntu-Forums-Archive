---
title: "apt-get broken"
date: 2012-06-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Cheesemill on 2012-06-23
The title says it all really. Any takers?```
root@quantal:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch but it is not installable
E: Unmet dependencies. Try using -f.
root@quantal:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  aquaria ia32-libs
0 upgraded, 0 newly installed, 2 to remove and 194 not upgraded.
1 not fully installed or removed.
After this operation, 4235 kB disk space will be freed.
Do you want to continue [Y/n]? 
dpkg: error: file triggers record mentions illegal package name `libglib2.0-0' (for interest in file `/usr/lib/x86_64-linux-gnu/gio/modules'): ambiguous package name 'libglib2.0-0' with more than one installed instance
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by mc4man on 2012-06-23
Possibly you upgraded to a bad dpkg version - see here for how to fix & then upgrade to the latest one

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1015329](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1015329)

you could also read here
[http://ubuntuforums.org/showthread.php?t=2006840](http://ubuntuforums.org/showthread.php?t=2006840)

---

### Post by Curtis6767 on 2012-06-23
Post deleted after reading bug report with suggested solutions.

---

### Post by Cheesemill on 2012-06-23
> **mc4man said:**
> Possibly you upgraded to a bad dpkg version - see here for how to fix & then upgrade to the latest one

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1015329](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1015329)

you could also read here
[http://ubuntuforums.org/showthread.php?t=2006840](http://ubuntuforums.org/showthread.php?t=2006840)

Thanks a lot, that first link fixed it for me.

---

### Post by jerrylamos on 2012-06-25
> **mc4man said:**
> Possibly you upgraded to a bad dpkg version - see here for how to fix & then upgrade to the latest one

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1015329](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1015329)

you could also read here
[http://ubuntuforums.org/showthread.php?t=2006840](http://ubuntuforums.org/showthread.php?t=2006840)
mc4man, 25 June Daily Build apt-get broken.  Is there a way to get the "bad dpkg" fixed in the Quantal Daily Build"?

Let me try your suggestions.

Jerry

I did.

As of 25 June the bug is still in the Quantal Daily Build.

Did an
sudo apt-get update
now apt-get install is working.

Either a change since today's daily build was made today or daily build didn't do an update.

Anyway install successful up and running just before Alpha 2. Some pain with wireless WPA which is another bug #.

Jerry

---


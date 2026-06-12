---
title: "How to check if Ubuntu has cleared serious vulnerability?"
date: 2013-10-07
forum: Security
---

### Post by resander on 2013-10-07
specifically for CVE-2013-2094:
that uses buggy increment and decrement paths to force the kernel to eventually transfer execution to a known  address in userspace that contains malicious code which elevates the credentials of the process allowing it to execute a shell as root.

A bad as it can get...

I stumbled upon this vulnerability when looking for something else a couple of days ago:

1. [http://timetobleed.com/a-closer-look-at-a-recent-privilege-escalation-bug-in-linux-cve-2013-2094/](http://timetobleed.com/a-closer-look-at-a-recent-privilege-escalation-bug-in-linux-cve-2013-2094/)
2. [http://people.canonical.com/~ubuntu-security/cve/2013/CVE-2013-2094.html](http://people.canonical.com/~ubuntu-security/cve/2013/CVE-2013-2094.html)
x. a lot more through googling on cve-2013-2094

Have several:
64-bit Ubuntu: 12.04.3 LTS;  
kernel 3.2.0-54-generic #82-Ubuntu SMP Tue Sep 10 20:08:42 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

32-bit Ubuntu: 12.04.3 LTS; 
kernel 3.8.0-31-generic #46-precise1 Ubuntu SMP Wed Sep 11 20:08:42 UTC 2013

I don't want to leave these computers open to this (kind of) attack. I was looking at link 2 above, but I am still not sure if this vulnerability has been cleared. The link contains a list of References and Packages (and more). For example, the first package listed is:

```

Package
Source: linux-armadaxp (LP Ubuntu Debian)
Upstream:	released (3.9~rc8)
Ubuntu 10.04 LTS (Lucid Lynx):	        DNE
Ubuntu 12.04 LTS (Precise Pangolin):	released (3.2.0-1619.29)
Ubuntu 12.10 (Quantal Quetzal):	released (3.5.0-1614.21)
Ubuntu 13.04 (Raring Ringtail):         DNE
Ubuntu 13.10 (Saucy Salamander):        DNE

```

Don't know what to make out of:
Q1. Upstream:	released (3.9~rc8)
Q2. Ubuntu 12.04 LTS (Precise Pangolin): released (3.2.0-1619.29) 
Q3. DNE for Ubuntu 10.04, 13.04, 13.10  (problem does not exist, solution does not exist???)

for the purpose of finding out if and when a vulnerability has been cleared. Am I looking in the right place?


I check for Ubuntu updates daily, but I am not sure exactly what vulnerabilities are cleared by these.
 
Would be grateful for advice.

---

### Post by Hungry Man on 2013-10-07
Security patches should be backported to kernels, so if you're up to date you shouldn't still be vulnerable to this.

---

### Post by cariboo on 2013-10-07
> Don't know what to make out of:
Q1. Upstream:	released (3.9~rc8)

This means that fix was released in the 3.9-rc8 kernel

> Q2. Ubuntu 12.04 LTS (Precise Pangolin): released (3.2.0-1619.29) 

Ubuntu doesn't use the same version numbering as the main kernel, if you are running the kernel with that version number then the vulnerability has been fixed. To check what kernel you are running, open a terminal and type:

```
uname -a
```

the output of the above command should look something like this:

```
Linux alexis 3.12.0-031200rc2-generic #201309231935 SMP Mon Sep 23 23:37:12 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

**Note**: I'm running Saucy + 3.12-rc2 mainline kernel.

> Q3. DNE for Ubuntu 10.04, 13.04, 13.10 (problem does not exist, solution does not exist???)

The vulnerability doesn't exist in 10.04, due to an older kernel, and the problem doesn't exit in 13.04 and 13.10 due to the use of newer kernels

---

### Post by resander on 2013-10-08
Thanks for the information.

I still don't understand how to interpret the vulnerability information from Canonical, for example how to use it to confirm that CVE-2013-2094 has been cleared for my Ubuntus (I check for updates every day).

Link 2 [http://people.canonical.com/~ubuntu-...2013-2094.html](http://people.canonical.com/~ubuntu-...2013-2094.html) in my original post has this at the top:

```

Description
The perf_swevent_init function in kernel/events/core.c in the Linux kernel
before 3.8.9 uses an incorrect integer data type, which allows local users
to gain privileges via a crafted perf_event_open system call.

```

Clicking on [http://www.ubuntu.com/usn/usn-1825-1](http://www.ubuntu.com/usn/usn-1825-1) in the References section brings up:
```

Ubuntu Security Notice USN-1825-1
15th May, 2013
    Ubuntu 12.04 LTS
....
....
The problem can be corrected by updating your system to the
following package version:

Ubuntu 12.04 LTS:
    linux-image-3.2.0-43-powerpc64-smp 3.2.0-43.68
    .... 
    linux-image-3.2.0-43-generic 3.2.0-43.68 

```

Then finally clicking linux-image-3.2.0-43-generic brings up:
```

“linux” package in Ubuntu

    Ubuntu
    “linux” package
block-modules-3.8.0-19-generic-di: Block storage devices
crypto-modules-3.8.0-19-generic-di: crypto modules
...
linux-headers-3.8.0-19: Header files related to Linux kernel version 3.8.0
linux-headers-3.8.0-19-generic: Linux kernel headers for version 3.8.0 on ARM (hard float) SMP
linux-image-3.8.0-19-generic: Linux kernel image for version 3.8.0 on ARM (hard float) SMP
linux-image-extra-3.8.0-19-generic: Linux kernel image for version 3.8.0 on 32 bit x86 SMP

```


The Description says that Linux kernels before 3.8.9 have the cve-2013-2094 vulnerability.
Then the number (3.2.0-43) in the linux-image (shown in the References section) cannot be
the Linux kernel because it is before 3.8.9 and still in the vulnerable version range.

Q1. what does 3.2.0-43 refer to?

Then clicking on linux-image-3.2.0-43-generic shows a list of package parts each carrying the number
3.8.0-19, that certainly seems to be nearer 3.8.9.

Q2.  what does 0-19 refer to? ...range 0 to 19? (then if it had been 3.8.9-19 I would have 
understood)

---


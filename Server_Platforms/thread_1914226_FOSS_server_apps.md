---
title: "FOSS server apps"
date: 2012-01-23
forum: Server Platforms
---

### Post by samkct on 2012-01-23
Hi;
 
I wish to know if there is any particular FOSS Apps for the following applications:
 
Internet Browsing/Software Firewall: [MS Equivalent= ISA or TMG]
Terminal Desktop Presentation: [MS Equivalent= MS Terminal server, Citrix Presentation Server]
Operation and Patch/Software Management Software: [MS Equivalent= SCOM, SCCM]
 
Can anyone help me out here?
Regards
SD

---

### Post by spynappels on 2012-01-24
For number 1, have a look at Squid.
For number 2, depends on whether it is over the LAN or WAN, for LAN look at LTSP (Linux Terminal Server Project)
For number 3, depends on whether you have a mixed (Win/Linux/Solaris/..) environment, most will focus on a single type of environment like *nix, look at Puppet.

---

### Post by samkct on 2012-01-24
> **spynappels said:**
> For number 1, have a look at Squid.
For number 2, depends on whether it is over the LAN or WAN, for LAN look at LTSP (Linux Terminal Server Project)
For number 3, depends on whether you have a mixed (Win/Linux/Solaris/..) environment, most will focus on a single type of environment like *nix, look at Puppet.
Are the applications Squid/LTS/Puppet compatible with Ubuntu Server edition . Do i have to separatly download them from their relative website or is there any particular version available along with the server edition itslef?

---

### Post by SeijiSensei on 2012-01-24
It sounds like you're unfamiliar with how software distribution works in the Linux world.  There are literally tens of thousands of "packages" available for Ubuntu, indeed for all the major distributions like Debian, RedHat, and CentOS.  Because all of these are available in source code, distribution maintainers carry out the work of compiling, testing and then "packaging" these applications.  The packages are kept in "repositories" where they are maintained and updated as new versions of the software are released.

If you already know the name of a package, squid for example, you can install it from the command prompt simply by running
```
sudo apt-get install squid
```
The easiest way to see if a package already exists is to search Google for "ubuntu program_name" and see what comes up.  A search for "ubuntu puppet" brings up [this page]("https://help.ubuntu.com/10.10/serverguide/C/puppet.html") detailing how to install and use the program.  

If you're on a system with a GUI you can browse the entire array of programs from a tool like [Synaptic]("https://help.ubuntu.com/community/SynapticHowto").  Ubuntu Server doesn't include a graphical desktop environment like KDE or GNOME by default, but you can add them.  An even easier approach is to browse the repositories on a desktop Ubuntu machine, then use the apt-get command on the server to install the packages you need.

This whole approach of centralizing software distribution is quite at variance with the commercial world where third-parties sell and maintain their own software independent of the operating system manufacturer.  Centralized distribution makes installing and managing servers much easier; the fact that the software is "free" in both senses just makes it all that much better.

I recommend reading the [Ubuntu Server Guide]("https://help.ubuntu.com/11.10/serverguide/C/index.html") to get an overview of the wide array of software available for the Ubuntu Linux platform.

---

### Post by samkct on 2012-01-30
> **spynappels said:**
> For number 1, have a look at Squid.
For number 2, depends on whether it is over the LAN or WAN, for LAN look at LTSP (Linux Terminal Server Project)
For number 3, depends on whether you have a mixed (Win/Linux/Solaris/..) environment, most will focus on a single type of environment like *nix, look at Puppet.
incase we have to monitor and manager servers of mixed platform : Windows/Linux/Mac, what can be the best system monitoring FOSS application?

---

### Post by spynappels on 2012-01-30
Nagios is a cross platform monitoring system, have a look at that. There are numerous plugins available to get more detail from specific servers running specific OS variants.

---


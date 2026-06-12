---
title: "[kernel] Recompile acpi-cpufreq as a module !!!"
date: 2009-04-04
forum: Ubuntu Brainstorm
---

### Post by Supermattt on 2009-04-04
Hi ! I'm using Linux PHC for a while now, By simply replacing the acpi-cpufreq.ko module, I'm able to manually change voltage of the CPU. The goal here is not to overclock but to undervolt using the good abilities of Core 2 Duos
On my laptop, it saves 20 minutes of battery and 20°C when CPU is 100% used.

for more, info you can go on [that thread]("http://ubuntuforums.org/showthread.php?t=786402&page=1")

BUT, since the 2.6.28-9, the acpi-cpufreq module is hard-coded in the kernel and it's totally impossible to do something without recompiling the whole thing !

WHY WHY WHY WHY did you hard-coded that functionality ?

Could you, please re-set it as a module ?

If you had serious reasons to do that, could you patch that before the compilation ?

---

### Post by Supermattt on 2009-04-04
The patch is available here :

[http://www.linux-phc.org/](http://www.linux-phc.org/)

---

### Post by Black16V on 2009-04-05
To hard-code the acpi-cpufreq module was the stupids idea ever... want the module back!!

---

### Post by mister_playboy on 2009-04-07
I agree... I'm sticking with the 2.6.28-8 kernel solely because of this.  I run Folding@Home, and undervolting makes a huge difference.

---

### Post by stillka on 2009-04-10
Or could someone create a repository with patched kernel(s)? 

We will use it instead of original from Ubuntu repository....

---

### Post by fixstern99 on 2009-04-10
[https://launchpad.net/~linux-phc/+archive/ppa](https://launchpad.net/~linux-phc/+archive/ppa)


But how can i stop the upgrade to the newer kernel version ...-41

---

### Post by stillka on 2009-04-11
> **fixstern99 said:**
> [https://launchpad.net/~linux-phc/+archive/ppa](https://launchpad.net/~linux-phc/+archive/ppa)


But how can i stop the upgrade to the newer kernel version ...-41

Hello,

all is explained on this page: 
[https://help.launchpad.net/Packaging/PPA#Adding a PPA to your Ubuntu repositories](https://help.launchpad.net/Packaging/PPA#Adding a PPA to your Ubuntu repositories)

"If you're creating an alternative version of a package already available in Ubuntu's repositories, you should ensure that:

    * your package supersedes the official Ubuntu version
    * future Ubuntu versions will supersede your package. 

To do this, increase the Ubuntu version number and add a suffix of ~ppan (where n is your package's revision number).

For example: you're creating an experimental version of the myapp_1.0-1 package. Your PPA package would be named myapp_1.0-2~ppa1."


p.s: repository is there but no packages... :-P

---

### Post by pelle.k on 2009-04-22
Bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355232](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355232)

---


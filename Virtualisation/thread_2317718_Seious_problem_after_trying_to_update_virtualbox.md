---
title: "Seious problem after trying to update virtualbox"
date: 2016-03-18
forum: Virtualisation
---

### Post by michael2009 on 2016-03-18
I initially had a similar problem as the one reported here: [http://ubuntuforums.org/showthread.php?t=2304606&highlight=serious+problem+update+virtualbox](http://ubuntuforums.org/showthread.php?t=2304606&highlight=serious+problem+update+virtualbox) with the  same message: [VT-x is disabled in the BIOS.  (VERR_VMX_MSR_VMXON_DISABLED)]
followed by: [Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ConsoleWrap
Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}].

Checked  the BIOS and all the virtualisation options were already enabled. I had  been running virtual box with xp as a virtual OS very successfully  previously on the same computer.

Using the code given on this thread, these were the results from the terminal:

-OptiPlex-755:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
stepping    : 11
microcode    : 0xc1
cpu MHz        : 2000.000
cache size    : 4096 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags         : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat  pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm  constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64  monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm  tpr_shadow vnmi flexpriority
bogomips    : 4654.96
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:


After  rebooting the computer, and trying to run the vbox guest os, I got an  update notification for the latest version: 
 [virtualbox-5.0_5.0.16-105871~Ubuntu~trusty_amd64]. I followed the prompt,  and it opened my web browser, which then froze up completely. However, I  had a download screen pop up showing the open/save options for this  version, so I clicked to save it. After this the browser would not close  so I had to restart the computer.

After this it just got more wierd.  When I tried to install the new package version with deb package  manager, the installation would not complete, and I could not close the  package manager. I tried using synaptic, but it would not even start,  giving me the following message:
E: The package virtualbox-5.0 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report. 

I  always keep the archive of my installed packages in  /var/cache/apt/archives/. Now I cannot see the packages there, as it has  been locked and I can't open it. I have tried the terminal with apt-get  check and I get the same message. When I try to install updates, I get  this notification:
Failed to load the package list

This is a serious problem. Try again later. If this problem appears again, please report an error to the developers.


So what can I do now about this 'serious problem'? I've been running Ubuntu for years, but never had a problem like this before.

---

### Post by deadflowr on 2016-03-19
Moved to Virtualization

---

### Post by ajgreeny on 2016-03-19
If you downloaded that VBox deb file after the message you received from opening VBox the package will now be sitting wherever your browser downloaded files go to, probably Downloads in your home.

Only packages that are downloaded by the package manager itself will go to /var/cache/apt/archives, so that is exactly what I would expect.  You could install gdebi, (or is that what you already are using?), and right click on the VBox .deb file in Downloads and open it, ie, reinstall it using that utility to see if a reinstallation helps.

You might like to consider enabling the VBox repository as suggested in the page at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) in the  **Debian-based Linux distributions** section; I have been using it for some time with complete success, and it ensures that VBox is updated along with all other packages as VBox packages are released.

Your error about the BIOS problem, is however, something I can not really comment on.  Perhaps disabling it in BIOS, rebooting and then again enabling it again may jog the system into accepting that it really is enabled, otherwise I have no ideas to add.

---

### Post by MAFoElffen on 2016-03-21
... But Oracle's upgrade/install instructions say that if you have a previous version of VirtualBox installed, that you need to uninstall the old version before installing the new version . The script in the .deb package for the new version does not do that, so has to be done manually.

If you don't do that, it will end up trying to use the older vbox kernel module with the newer program, instead of all being the same version of pieces.

---

### Post by ajgreeny on 2016-03-21
I installed VBox 5 from the repos mentioned above, with synaptic when it first appeared a while ago, and synaptic automatically removed the VBox 4 version I previously had; one good reason perhaps for using the package manager to do the job for you rather than manual installation.

---

### Post by MAFoElffen on 2016-03-23
did you install the appropriate version of Extended Pack from Oracle? (It replaced the Guest additions Iso, and is now an add-on to VB) You are probably getting a message about USB 2.0 support? 

Hint: Download and install the Extended Pack...

---


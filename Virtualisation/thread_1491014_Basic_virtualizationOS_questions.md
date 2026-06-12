---
title: "Basic virtualization/OS questions"
date: 2010-05-23
forum: Virtualisation
---

### Post by gauchotodd on 2010-05-23
I'm new to linux, and trying to comprehend this whole virtualization thing. I recently built my first PC, a quadcore i7 CPU, 6GB RAM, and an ATI 4860 GPU, with a second I could crossfire (or not).

I use a 22" LCD and often also use my 46" with the HDMI on my GPU.  When using Win7, my TV gives me an extension of the desktop; when using Ubuntu 10, it's a replica of my 22" monitor.  I understand there's a way to make it an extension also, but I'm more interested in booting them simultaneously.

Dual-booting is fine, but it would be very nice if I could run Ubuntu and view it on my 46" while simultaneously running Win7 on my 22".  Since I have a quad core, I presume it should be possible, but not the easiest thing in the world to do.

I have the OS's partitioned on my 100GB SSD, about 60-40 Win7-Ubuntu, and now that I think about it, am unsure if it's possible for the SSD to run both of them simultaneously.  Would I need to boot them from separate drives?  I'm using a second HDD for storage, but would prefer not to put an OS on it because let's face it - once you go SSD, you never go back.

I feel like what I described above would be a physical way to parallel boot (is that a proper term for it?), or I could get software to virtually load the second OS inside the first, correct?  From what I gather, the performance loss of doing so rather than booting one at a time can be relatively minimal.  But after reading several wikis and posts about it, still don't really feel comfortable with this notion, much less the how-to-do-it.

Can someone help explain how either method would work or direct me somewhere that simply describes it for (quick-learning) n00bs?  Also, a side-note: I have two ATI Radeon 4860s but am only using one because I feel like I don't have a use for two GPUs; what cool utilizations can I make of it other than video editing and gaming, neither of which I have time for?  I'm assuming it wouldn't help directly with the simultaneous OS booting at all.

Thanks in advance for your patience and knowledge!

---

### Post by TheFu on 2010-05-24
Wikipedia is often a good place to start learning a new topic. [http://en.wikipedia.org/wiki/Hardware_virtualization](http://en.wikipedia.org/wiki/Hardware_virtualization) is what you are asking about, but probably now what you really want.  [http://en.wikipedia.org/wiki/Virtualization](http://en.wikipedia.org/wiki/Virtualization) is a good jump point. Here's another Introduction: [http://www.kernelthread.com/publications/virtualization/](http://www.kernelthread.com/publications/virtualization/)  A little googling will easily help you find more sources.  You probably want to limit your searches to "desktop virtualization" since server virtualization is a very different question.

Your "parallel boot" idea isn't possible with x86 hardware. I doubt you have the right kind of hardware for "parallel boot" - Sun Microsystems "domains, HP NPARs [http://en.wikipedia.org/wiki/HP_nPar_%28Hard_Partitioning%29]("http://en.wikipedia.org/wiki/HP_nPar_%28Hard_Partitioning%29") and similar can do this, but those systems are hundreds of thousands of $$$.

As to running multiple operating systems at the same time, you definitely can, but you'll need to pick 1 as the "host OS."  If you want to run non-trivial MS-Windows games, then you probably **need** to choose Windows as the host OS.  There is definitely a performance hit for virtualization in the client machines, but with your hardware, you probably won't care. Only the graphics performance will be lesser for the client virtual machine. Everything, including graphics will be full speed for the Host_OS since it will have direct access to the hardware and video cards. There currently is no way to provide direct access to the 2nd video card to a client-OS. Sorry.

A typical setup:

Host_OS-Win7-x64
|____Client_OS-1-Fedora
|____Client_OS-2-WinXP
|____Client_OS-3-FreeBSD
|____Client_OS-4-OpenSolaris
|____Client_OS-5-CentOS
|____Client_OS-6-Ubuntu
|____Client_OS-7-Win7
 |____Client_OS-8-Joes-OS

Clearer?  By having Windows as the Host-OS, you'll not have many issues with drivers and graphics performance will be as good as it gets. If you use Linux as the host-OS, then the graphics performance will probably be less since the Linux drivers aren't usually as good for Linux as for Windows. The downside for Windows as the host are the normal Windows security and larger Host-OS requirements.  In this mode, check out VirtualBox and VMware Player for the Host-OS virtualization software.  You can run any where from zero to all client OSes at the same time. The only limitation is your host hardware, usually RAM for a home user.

If you don't care about gaming on Windows, then you can make a Linux system your Host-OS and be VERY happy. You can run all the same Client-OSes too AND your host OS requirements are much, much less than Windows as a Host demands.  In this mode, check out  VirtualBox and KVM for the Host-OS. I understand that VMware Player runs on Windows now, but the last time I used any thing from VMware on Linux, it was a hassle every time there was a new kernel. A year ago, I would also have recommended that you look at Xen, but Xen kernel support isn't provided by Redhat or Canonical / Ubuntu in their latest OS releases.

Once you've decided which virtualization method you will use, and there are many choices [http://en.wikipedia.org/wiki/Comparison_of_platform_virtual_machines](http://en.wikipedia.org/wiki/Comparison_of_platform_virtual_machines), then you'll want to ask any questions in the specific virtualization forums for that tool.

I'd honestly suggest you go with a **Windows7 x64 Host-OS** and **VirtualBox**  to start. Actually, since you are already dual-booting, you can try VirtualBox under Linux too and see which you prefer.

To make use of your GPUs, perhaps BIONC scientific computing would be useful? I don't do this except to burn in new hardware before the warranty period ends.  [http://setiathome.ssl.berkeley.edu/](http://setiathome.ssl.berkeley.edu/)

Good luck and have fun!

---

### Post by JGraphite on 2010-05-25
I am currently trying to setup VirtualBox with PC Linux OS 2007 and keep getting a screen with the following message "Fatal: No bootable medium found! System Halted." The host OS is Windows XP. I have recreated the vm using the automatic partitioning and formating option, along with a dynamic drive of 32 Gb. Any suggestions would be appreciated as to what may be wrong with this installation method.
 
Thank you in advance for the help and information.

---

### Post by TheFu on 2010-05-25
> **JGraphite said:**
> I am currently trying to setup VirtualBox with PC Linux OS 2007 and keep getting a screen with the following message "Fatal: No bootable medium found! System Halted." The host OS is Windows XP. I have recreated the vm using the automatic partitioning and formating option, along with a dynamic drive of 32 Gb. Any suggestions would be appreciated as to what may be wrong with this installation method.
 
Thank you in advance for the help and information.

Did you connect the PCLinuxOS ISO or physical DVD/CD device to the virtual machine in the **Storage** settings so it would be seen at boot? There's another thread here all about connecting a CD/DVD to a VirtualBox VM.

---

### Post by JGraphite on 2010-05-27
I tried both ways of installing using the ISO file and also a DVD that I had burned and verfiied. I am able to get PCLinuxOS 2007 installed, but when I restart the VM I get the error "Fatal: No bootable medium found! System Halted". This only occurs after I have removed the ISO file or the DVD from the drive, depending on the original installation. If I do not remove the installation storage device then the VM loads the Live version. I beleive that I read somewhere that the PCLinuxOS automatic formatting and partitioning sometimes does not work correctly. Could you give me a listing of suggested sizes, types and mount positions for a typical Ubuntu install. I have also tried using a dynamic drive and a fixed virtual drive but neither option helps to get rid of the error. Thank you in advance for any help.

---

### Post by TheFu on 2010-05-27
Interesting ... Do you remember when you setup the HDD virtual disk whether it was marked as  "boot"?  I'm reaching here.  That setting doesn't appear in the GUI for 3.1.6, but I recall it going through the new VM wizard.

The last issue I can think of is to check the boot loader (grub/grub2) and root file system type for compatibility inside the VM.  I had an issue with grub2 and xfs not working together. I think that ext3 is the best answer for inside a VM provided your host OS uses something better.

I doubt any of these are really your issue, but at least it is something to check.

---


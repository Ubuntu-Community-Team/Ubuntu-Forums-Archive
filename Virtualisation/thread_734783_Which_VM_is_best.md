---
title: "Which VM is best?"
date: 2008-03-25
forum: Virtualisation
---

### Post by luisjorge on 2008-03-25
Hi everyone! I use Ubuntu as my only OS, and I just bought a Dell Inspiron 1525, which will come with Vista home premium. I plan to install Ubuntu only (7.10 gutsy, or evaluate 8.04), but I wanted to install the Vista it comes with in a virtual machine. Which one would be best to use? I tried VirtualBox once with WinXP, and it was fine, but I also wanted to know if I can use it (or any other VM) for gaming, or is it best to use Wine for that?
Also, I wanted to know how can I keep the Dell Media Direct partition functional after installing Ubuntu instead of Win Vista, because last time I installed Ubuntu in place of WinXP, I couldn't use Media Direct anymore. Does anyone know how to do it?
Also, I think the Intel Core 2 Duo processor it has is 64 bit. What sort of pros and drawbacks could I encounter using a 64bit version of ubuntu? What's the difference with using the 32bit version? 

Thanks very much in advance! And sorry if there are too many questions.

Luis Jorge.

---

### Post by pointone on 2008-03-25
VitualBox and VMware are probably the two most common virtualization solutions. Both are very powerful and simple to use. VMware requires you to register, but it is free. VirtualBox is in the default Ubuntu repositories. I prefer VirtualBox, but they're very similar. Try them both, why not?!

Parallels is another alternative with some very nice features, but is not free.

None of these allow you to run recent games, though, because they use specialized video drivers without 3D acceleration. Some day, maybe... but not today. Wine is what you want for this.

64-bit may give slightly better performance, especially in memory-intensive applications. 64-bit is a must if you're running with 4 GB of RAM or more. Otherwise, there's not much of a difference. Not all software is available for 64-bit yet, but 32-bit is all-around well supported. I run 32-bit on my Core 2 laptop; I have no need to 64-bit.

---

### Post by gmcrews on 2008-04-02
Received my Inspiron 1525 with Ubuntu 7.10 preinstalled a couple of days ago. I bought it with virtualization in mind and so got a extra GB of RAM (2 GB total). Everything worked great right out of the box. (Had to configure for my encrypted wireless router of course.)

Last night I created MS WinXP Pro virtual machines using both VMware and VirtualBox (256 MB RAM, 6 GB HD, 8 MB video). Unlike my many other experiences with creating VMs using an Ubuntu host, neither of these went perfectly.

First I downloaded (from the Sun site) and tried VirtualBox, but the deb-packaged binaries would not install -- some missing or out of date module -- I can't recall the details.

So I went to the VMware website and downloaded VM Server. Did not go smoothly because xinetd was not installed. So I installed it from the Ubuntu repositories. Then everything went fine except for the usual Perl glitch that I always ignore.

When I ran the WinXP client under VMware Server there was no networking or sound. Otherwise performs and looks great. I plugged in my network cable and turned off the wireless and networking started to work. Still no sound. Fiddled around some more but could make no further progress.

Decided to update Ubuntu. Downloaded and installed about 90 packages!

Still no wireless access or sound using the WinXP client. Downloaded and installed VMware Player. (This uninstalls Server, which means I can only play -- not create -- virtual machines.) Still no wireless networking or sound.

Figured VirtualBox would install now that I had updated Ubuntu and I was right. Created a WinXP Pro client from scratch. The virtual machine runs speedily and I like the way VirtualBox handles the mouse better than VMware. Also, wireless worked! Unfortunately -- still no sound. Guess I won't be listening to any Netflix on-demand movies using it. And, for some reason, I have to re-enter my wireless WPA key each time I start up the virtual machine.

I intend to surf the web tonight to see if I can find out what to do next.

My vote on the best VM? My experience so far says: VirtualBox.

---

### Post by dendrobates on 2008-04-04
As of Hardy Heron, KVM is officially supported in Ubuntu.  I suggest you check it out.  We will be testing KVM with every kernel update and fixing bugs throughout the support life of Hardy.  

BTW, in Hardy you can use virt-manager to create and manage both KVM and Xen VM's

Rick 

Manager Ubuntu Server Team

---

### Post by wesley_of_course on 2008-04-05
```
wesley@Ratdog-3:~$ egrep '^flags.*(vmx|svm)' /proc/cpuinfo
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm

```       I'm using Virtual Box in Gutsy , will definitely have to try this in Hardy instead of the other two . Excellent !

   Thank You Devs !

---

### Post by MountainX on 2008-04-05
[http://davestechshop.net/archive/2008/01/31/1825.aspx](http://davestechshop.net/archive/2008/01/31/1825.aspx)
Five Reasons to use VMware Workstation instead of VirtualBox

---

### Post by Ripfox on 2008-04-05
> **wesley_of_course said:**
> ```
wesley@Ratdog-3:~$ egrep '^flags.*(vmx|svm)' /proc/cpuinfo
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm

```       I'm using Virtual Box in Gutsy , will definitely have to try this in Hardy instead of the other two . Excellent !

   Thank You Devs !

@Ratdog eh? Bob Weir fan?

---

### Post by linuxbeatswin on 2008-04-05
I use Virtualbox in Gutsy, and VMWare in Mandriva. They are both really nice, but I think that Virtualbox is a bit faster than VMWare.

I'm honestly thinking of switching Mandriva over to Virtualbox. Don't know why, though- I use Ubuntu more than Mandriva. I should have been using Ubuntu the whole time, I'm finding out.

Thanks to the developers for such a fantastic O/S!!!

---

### Post by scannerdarkly on 2008-04-05
I've always had a better experience with VM Server.  I have it installed on Ubuntu 7.10 and on Vista on my laptop.  Right off the bat any VM works better under Linux then under windows.  In my opinion anyway.

---

### Post by wesley_of_course on 2008-04-05
> **ripfox said:**
> @Ratdog eh? Bob Weir fan?
  Never made the connection !   She's sneaky and smart , too .

---

### Post by Ripfox on 2008-04-05
> **wesley_of_course said:**
> Never made the connection !   She's sneaky and smart , too .

Who, it isn't your machine? :confused:

---

### Post by wesley_of_course on 2008-04-05
> **ripfox said:**
> Who, it isn't your machine? :confused:

      Machine and Chihuahua ;  6 yr., old > the dog   :)

---

### Post by MountainX on 2008-04-05
> **dendrobates said:**
> As of Hardy Heron, KVM is officially supported in Ubuntu.  I suggest you check it out.  We will be testing KVM with every kernel update and fixing bugs throughout the support life of Hardy.  

BTW, in Hardy you can use virt-manager to create and manage both KVM and Xen VM's

Rick 

Manager Ubuntu Server Team

Where can I find a list of features of KVM? I am looking for something like vmWare Workstation 6.x. In particular, I need snapshots, good USB support, and dual monitor support in guests.

---

### Post by LinuxGuy1234 on 2008-04-05
I've had my opinion on VirtualBox. As a matter of fact, my laptop's hard drive space is used up because of it! (Also those distros and other OS' I install in VirtualBox)

---


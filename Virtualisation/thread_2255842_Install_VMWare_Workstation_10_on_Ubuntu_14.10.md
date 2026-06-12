---
title: "Install VMWare Workstation 10 on Ubuntu 14.10"
date: 2014-12-08
forum: Virtualisation
---

### Post by JBayley_Visuals on 2014-12-08
Hello, im trying to install VMWare workstation 10 on Ubuntu 14.10. I ran the .bundle file and it successfully copied the nessisary files however when running the program it asks for a link to kernel Header 3.13.0-24-generic.
I am a relitivly inexperienced linux user (Transphered from 15+ years of windows to ubuntu as primary 6 months ago).

Here is the dialog from VMware...

[[IMG]http://s1.bild.me/bilder/120914/6103762VMware_kernalHeaders.jpg[/IMG]]("http://www.bild.me")

> Before you can run VMware, several modules must be compiled and loaded into the runnung kernel.

Kernel Headers 3.13.0-24-generic

Kernal headers for version 3.13.0-24-generic were not found. If you installed them in a non-default path you can specify the path below. Otherwise refer to your distribution's documentation for instalation insructions and click refresh to search again in default locations.

When I run the command 'uname -a' I get the response 

> 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


To me it looks like I am already running the correct kernel version, however in usr/src the linux headers are for version 3.16.0-25-generic. So somehow I need to get the 3.13.0-24-generic files? Not sure why there is an apparent version missmatch here.

I did not change any default perameters in either the OS install or VMware. It might be worth mentioning that just recently my system upgraded itself from 14.04 LTS to 14.10. I did not make any alterations to the default upgrade process. Also I have disabled restricted resources. I did not previusly have VMware instaled on a linux machine so I dont know if leaving LTS is cause for the problem.

Through internet searches I have came across this page that has potential fixes for the problem...

[VMware technical help]("http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1035767")

What I have discovered is that the file [FONT=Courier New]'/usr/bin/vmware-config-tools.pl[/FONT]' was not part of the VMware instalation. Did a full system search for vmware-config-tools.pl and came up with nothing. Suposedly you have to edit that file to point VMware to use the system default headers. I belive the information thats been found on this problem is either outdated or somthing is wrong with the instalation.

Anyone know how to get this working? #-o 

Thanks

---

### Post by ajgreeny on 2014-12-08
It seems strange that are still running the trusty kernel 3.13.0-24 on 14.10.

Have you fully updated the system, as you should be using 3.16?

Can you check in software-centre, or synaptic, if you use it, that you have the 3.16 kernel installed (linux-image-3.16.0-??).  I don't know to where utopic has got in exact kernel version, but it certainly should be 3.16.*something*.

---

### Post by JBayley_Visuals on 2014-12-08
I looked in software centre and it shows the green check mark on "Linux kernel image for version 3.13.0 on 64 bit x86 SMP", nothing on any of the 3.16.0... packages. Should I be installing the newer kernel?
Maybe I should do a clean install, just don&#8217;t have time to do that right this moment.

---

### Post by ajgreeny on 2014-12-08
So have you installed the linux-headers packages of the same version as your running kernel?

Normally you need the **linux-headers-*version*** and **linux-headers-*version*-generic** for your installed kernels.

---

### Post by JBayley_Visuals on 2014-12-08
As far as I know I haven&#8217;t. If I do a search for "linux-headers-3.13.0-24-generic" on the software center it says "No items match...". There is no header file for 3.13.0... in usr/src  

[[IMG]http://s1.bild.me/bilder/120914/2014347headerFiles.jpg[/IMG]]("http://www.bild.me")

I just thought of something, some months ago I installed Xubuntu from the software centre as I wanted to try Xfce desktop environment. I have since removed Xfce however when the computer boots it does display 'Xubuntu' not 'Ubuntu'. However that is the only place Xubuntu is ever shown. If I go to the "About this computer" it displays "Ubuntu 14.10". Don't know if this could be effecting the system.

---

### Post by ajgreeny on 2014-12-09
I have not looked at 14.10 and do not intend to do so, so I'm not sure about the availability of headers for 3.13.0-## kernels in the version, but I would suggest you install **synaptic** package manager as it allows you to search for packages a great deal more easily that the software-centre, which I have never used in my 9 years of using Ubuntu.

---


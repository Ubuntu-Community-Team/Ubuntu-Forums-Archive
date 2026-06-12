---
title: "Virtual PC 2007 help"
date: 2009-01-29
forum: Virtualisation
---

### Post by FarmersHighSchool on 2009-01-29
[COLOR="Navy"]First of all, I'm fairly new to Ubuntu, so any help you provide will have to be detailed.

I'm running Windows Vista Home Premium x64.  I downloaded Microsoft Virtual PC 2007 x64 from Microsoft, and I downloaded Ubuntu 8.10 x86, which I installed in the virtual machine from the Live CD.

I followed the advice from here: [http://arcanecode.wordpress.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/]("http://arcanecode.wordpress.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/") explaining how to install Ubuntu on VPC2007. (particularly the post by "Robert" on May 8, 2008.) The install went smoothly, and Ubuntu does work in the virtual machine.


But I cannot get the sound to work, and it keeps putting me in low graphics mode because it says it can't detect my display (it's a laptop).  Even though I followed the instructions to adjust the sound and video in the link I provided above.

Also the additional updates to VPC 2007 to integrate my mouse will not autorun, so I have to hit right alt to release my mouse every time I want to switch back to my host.


Anyone have experience using VPC 2007 and know a fix to these problems?


Thanks in advance![/COLOR]

---

### Post by thomasr on 2009-01-30
You might want to try VirtualBox or VMware as alternatives to VirtualPC.

Here are some comparisons:
[http://www.wilderssecurity.com/archive/index.php/t-168825.html](http://www.wilderssecurity.com/archive/index.php/t-168825.html)
[http://www.johnmee.com/2008/04/vmware-vs-virtualpc-vs-virtualbox/](http://www.johnmee.com/2008/04/vmware-vs-virtualpc-vs-virtualbox/)
[http://technorati.com/videos/youtube.com%2Fwatch%3Fv%3DpcAhHplFseI](http://technorati.com/videos/youtube.com%2Fwatch%3Fv%3DpcAhHplFseI)

---

### Post by Neural oD on 2009-01-30
I second Virtualbox -get that and to boot it's not ms software ;)

---

### Post by FarmersHighSchool on 2009-01-30
[COLOR="Navy"]Thanks.  I'll think about it.  I'm actually seriously considering setting up a dual boot.[/COLOR]

---

### Post by Ziggy72 on 2009-01-30
I have no experience of using MS Virtual PC 2007. However, I do use VirtualBox and run Ubuntu 8.10 as a VirtualBox guest on Vista Ultimate.

Your sound problem is probably caused by a documented bug in Ubuntu 8.10 - see [http://ubuntuforums.org/showthread.php?t=966436](http://ubuntuforums.org/showthread.php?t=966436), "No sound effects..."

I had the sound problem in VirtualBox that you have in MS Virtual PC. I fixed my problem by following the instructions at [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578).

I hope this works for you. Good luck....

---


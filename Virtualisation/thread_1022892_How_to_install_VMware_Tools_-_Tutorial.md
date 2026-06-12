---
title: "How to install VMware Tools - Tutorial"
date: 2008-12-27
forum: Virtualisation
---

### Post by Dedoimedo on 2008-12-27
Hi all,

After quite a lot of people asked me how to achieve this, namely install vmware tools, especially for Linux hosts, I realized the task is not as trivial as it seems and decided to write this tutorial.

It demonstrates, step-by-step, how to install vmware tools, both on Windows and Linux guest. For Linux guests, the tutorial also shows how to work with archives, how to compile packages from the command line, the preliminary installation of compilation-necessary packages - make, gcc, kernel source, kernel headers, setting up vmware tools to run at startup, and more.

The linux demo is done on Linux Mint 4, which is very similar to Ubuntu, but the idea is the same for all distros, since we use archives and command line interface rather than rpm or deb packages.

The next article will show you how to install guest addons in VirtualBox, again both on windows and linux hosts - that's in 2 days.

These two articles are an introduction to: 3d acceleration in virtual machines, a three-article series showing how to do this for windows and linux hosts, windows and linux guests, which I'll post in the following days.

I hope this will help you, regardless of the 3d thingie ... plus, stay tuned for the entire series! The article will come up this week, so you won't have to wait too long.

Here we go:

[http://www.dedoimedo.com/computers/vmware-tools.html](http://www.dedoimedo.com/computers/vmware-tools.html)


Comments and suggestions are most welcome.

Regards,
Dedoimedo

---

### Post by sh4d0w808 on 2008-12-29
Thanks, great article. Keep up this good work.

---

### Post by Dedoimedo on 2008-12-29
Thank you. Keep up the good work: always :)
Later today, virtualbox tutorial, wednesday: beginning of 3-article saga on 3d acceleration in virtual machines :)
Dedoimedo

---

### Post by Couchsurfer on 2008-12-29
Thanks for a great tutorial, 

Just found out that VMware recently have packaged vmware tools as OSP's (operating system specific packages) so that you can use native Linux tools to install and update vmware tools. 
Just add the vmware repository and use apt-get. 

I haven't tried it out yet but it is a brilliant idea. 

As for now RedHat Ent Linux 5, SuSe Ent linux 9 & 10 and Ubuntu 8.04 are supported. 

Have a look at: 

[http://www.vmware.com/pdf/osp_install_guide.pdf](http://www.vmware.com/pdf/osp_install_guide.pdf)


/ Couchsurfer

---

### Post by Dedoimedo on 2008-12-29
According to the documentation, this is only for ESX ...
Dedoimedo

---


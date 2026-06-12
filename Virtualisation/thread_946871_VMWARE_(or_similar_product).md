---
title: "VMWARE (or similar product)"
date: 2008-10-13
forum: Virtualisation
---

### Post by snorkytheweasel on 2008-10-13
I want to boot into Ubuntu but be able to run other distros and Windows. VMPLAYER is a good, free solution that works well when run under a Windows host. I haven't tried VMPLAYER - or any alternative product - with a Linux host system.

VMPLAYER is available as an .RPM and as a .BUNDLE

This suggests several questions: 
[LIST=1]
[*]What is a .BUNDLE? Is a .BUNDLE useful for installing when Ubuntu is the HOST O/s?
[*]Is there a way to use an .RPM for installing when Ubuntu is the HOST O/S?
[*]Is there a GOOD alternative to VMPLAYER?
[*]Is there a package for installing said GOOD VMPLAYER alternative?
[*]Is there a package for VMPLAYER - or another product for running virtual machines/virtual appliances that will include guest O/Ss such as windows XP, Vista, and possibly other Linux flavors?
[*]Are there instructions for installing VMPLAYER from a tarball?
[/LIST]

I think Xubuntu would be the best distro for the host O/S because it is relatively gentle with the available resources, thus leaving more system resources for the VMs. Xubu definitely outperforms other Ubus on older, low-powered PCs. However, I'm open to suggestions. 

I want to stick with the Ubu family if possible - for all of the reasons that are obvious to us Ubu fans.

---

### Post by ju2wheels on 2008-10-13
I would recommend Virtualbox over VMware, its less of resource hog and runs much much faster than VMware.

---

### Post by Liv3dN8as on 2008-10-13
I too would suggest VirtualBox. I use it and love it.

---

### Post by kk0sse54 on 2008-10-13
I prefer Vmware since I don't like the performance of Virtualbox. I would recommend installing Vmware server since you'll be able to install your own OS's without having to download pre-made vmware images for the vmware player. You can convert an RPM to a deb package using alien but I would recommend download the tarball and installing through that route. Included within the packages should be a readme on what commands you should run(which is really just one script I believe) in order to install. Once you're done installing you should be able to isntall guest OSs such as *BSD, various linux distros, and windows.
Edit: Here's some documentation for Vmware server 2 [http://vmware.com/support/pubs/server_pubs.html](http://vmware.com/support/pubs/server_pubs.html)

---

### Post by GoodPanos on 2008-10-13
Yep, I would go with VirtualBox too.  Works a lot better.

---

### Post by bodhi.zazen on 2008-10-13
+1 VMWare Server.

Last time I tried 2.0 It was not so stable, but it seems to be getting good reviews ...

[How to VMWare in Ubuntu 8.04 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=779934") 

(I plan to update that thread when 8.10 is released).

Vbox is also nice.

If you have the hardware, IMO KVM is a better open source solution then VBox. The open source edition of VBox has "issues".

---

### Post by brianfreytag on 2008-10-13
+1 Virtual Box... it's fairly system friendly, and extremely useful.

---


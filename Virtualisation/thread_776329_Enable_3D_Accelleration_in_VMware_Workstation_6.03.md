---
title: "Enable 3D Accelleration in VMware Workstation 6.03.80004"
date: 2008-04-30
forum: Virtualisation
---

### Post by bmwman on 2008-04-30
I am trying to enable the 3D Accelleration for XP guest machine. I was testing VMware Workstation 6.5beta and there was an option to enable it from the settings. I was having some problems with the sound so I installed 6.03. Everything works great except no 3D. My video adapter shows as 16mb and with 6.5 was showing as 128mb. I read the manual and they state that you can edit the .vmx configuration file and add "mks.enable3d = "TRUE"" and "svga.vramSize = "67108864"" but every time i do that and power on the machine, the video is still 16mb. I open the .vmx and shows as "mks.enable3d = "FALSE""

Does anyone know how to get it work right?
Thanks.

---

### Post by Kalenjin on 2008-05-01
I thought there was no 3d acceleration in 6.03. And seeing that VMware lists 3d accelleration as one of the new features in 6.5. I think we have to wait till the release of 6.5... but maybe someone else knows how it can be done...

6.5 release notes: [http://www.vmware.com/products/beta/ws/releasenotes_ws65_beta.html](http://www.vmware.com/products/beta/ws/releasenotes_ws65_beta.html)

---

### Post by jimmux on 2008-05-15
It can be done, but I believe it is experimental and not supported in any way. 

In my experience it is not worth doing if you intend to use for gaming or any serious use, as it is fairly buggy.

---


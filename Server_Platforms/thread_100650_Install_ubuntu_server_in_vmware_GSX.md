---
title: "Install ubuntu server in vmware GSX"
date: 2005-12-08
forum: Server Platforms
---

### Post by jlist on 2005-12-08
I installed ubuntu/kubuntu as guest OS in vmware workstation 4.5 for Windows. Ubuntu 5.10 both GUI and server installations work fine. They work right out of the box. However, when i installed ubuntu server installation on vmware GSX server 3.2, network adaptor is not detected, not even after I install vmtools. Any ideas?

---

### Post by jlist on 2005-12-08
Later on, I read in an article regarding suspend and resume with ubuntu in vmware. It suggests to add "auto eth0" in /etc/network/interfaces. I did that and it worked. I am not sure if this fixed the problem, or reinstalling vmtools fixed the problem, or switching between vlance and vmnet fixed the problem though :(

---


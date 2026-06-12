---
title: "How to install Ubuntu Server OS on HP Proliant DL380e Gen8 server"
date: 2013-07-19
forum: Server Platforms
---

### Post by jgtumusiime on 2013-07-19
[COLOR=#000000][FONT=Arial]I just purchased a HP Proliant DL380e Gen8 server. I'm stuck trying to install ubuntu server 12.04 on the server. According to [http://h18004.www1.hp.com/products/servers/linux/hplinuxcert-canonical.html#DL](http://h18004.www1.hp.com/products/servers/linux/hplinuxcert-canonical.html#DL), the server supports ubuntu 12.04.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Can someone help me find a step by step process of installing ubuntu server OS on this server that works. Been googling all afternoon.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I do not know where to start. I have never worked with this kind of hardware before and non of the Operating Systems supported by Intelligent Provisioning are Open Source. So when I choose to set up the server using Intelligent Provisioning, the only OS options I have to choose from are Windows Server/Red hat/ Suse Enterprise and VM Ware.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]How do I install Ubuntu Server?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thank you.[/FONT][/COLOR]

---

### Post by SeijiSensei on 2013-07-19
If those are your choices, and you are forced to use one of them, I'd install [CentOS 6.4]("http://mirror.us.leaseweb.net/centos/6.4/isos/i386/") choosing the RedHat provisioning instead of Ubuntu Server.  Are you committed to Ubuntu Server?  

What is provisioning anyway?  Can you not avoid all this and simply boot the Ubuntu Server [CD]("http://releases.ubuntu.com/precise/") directly?  Perhaps a setting in the BIOS might help?

---

### Post by m3talman on 2013-07-31
> **SeijiSensei said:**
> 
What is provisioning anyway?  Can you not avoid all this and simply boot the Ubuntu Server [CD]("http://releases.ubuntu.com/precise/") directly?  Perhaps a setting in the BIOS might help?

[http://h18013.www1.hp.com/products/servers/management/intelligentprovisioning/](http://h18013.www1.hp.com/products/servers/management/intelligentprovisioning/)

Stuff that earlier was located on CD's (Smartstart) that is now, on gen8's, fitted onto a flash chip. Easier driver updating and other things. Copied from hp's website, "[COLOR=#000000][FONT=Arial]Provides step-by-step HP ProLiant server deployment assistance in a simple and consistent manner. [/FONT][/COLOR]"

---

### Post by LHammonds on 2013-07-31
Easy solution, install VMware's ESXi server, then use vSphere to manage it and create a virtual server and install Ubuntu Server on it.  That is how I run all my Ubuntu Servers...on top of ESXi.

---


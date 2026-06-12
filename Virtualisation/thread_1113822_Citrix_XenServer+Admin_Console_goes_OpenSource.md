---
title: "Citrix XenServer+Admin Console goes OpenSource"
date: 2009-04-02
forum: Virtualisation
---

### Post by juancarlospaco on 2009-04-02
**[SIZE="5"][CENTER]Citrix XenServer+Admin Console goes OpenSource[/CENTER][/SIZE]**

i been reading here :

[LIST]
[*][http://blogs.zdnet.com/open-source/?p=3826](http://blogs.zdnet.com/open-source/?p=3826)
[/LIST]

*" In a move designed to accelerate uptake of its open source virtualization platform, Citrix announced today worldwide availability of its free enterprise ready open source XenServer. "*

And go to Citrix.com, make a NewUser for Free and **Download for Free :**

-Citrix XenServer 5 (update 3) Enterprise.
-Citrix XenCenter Centralized Administration Console
-Citrix XenServer Linux Guest Support
-Citrix XenConvert
-Citrix XenConvert x64
-Citrix Standalone XenCenter Installer
-Citrix Essentials 1.0 for Microsoft Windows 2008 / Hyper-V (beta)
-Citrix Provisioning Server
-Citrix XenServer SDK
-Citrix Lab Manager OSS
-Citrix Project Kensho
-Source Code of some of items above

[LIST]
[*]This is NOT the Xen from Xen.org
[*]This is the XenServer from Citrix!
[/LIST]




:p

---

### Post by juancarlospaco on 2009-04-06
No ones is gonna say Something...?
[I]
i have the feel this new is too good to be ignored...[/I] :p

---

### Post by UranUtan on 2009-04-06
> **juancarlospaco said:**
> No ones is gonna say Something...?
[I]
i have the feel this new is too good to be ignored...[/I] :p

Oh yes mate, thanks for the news, and indeed this is excellent new. Wonderful timing, I am trying to explore XEN. Do you think that Citrix makes XenServer freeware in response to the free VMWare ESXi?

---

### Post by juancarlospaco on 2009-04-07
YES, Citrix makes XenServer Open Source in response to the free VMWare ESXi, 
and because the Xen.org still abandoned(?), no new development since Xen.org 3.3.
yes yes yes, theres a Link to Download the source code of XenServer and Admin Console, etc.

You have to Register, but is Free, 
then you can download XenServer and Admin Console with sources, ISO file format.
i have sucessfully installed on bare metal, and im testing it.

You need Intel VT or AMD Pacifica to run Windows Guest,
you DONT need Intel VT or AMD Pacifica to run Linux/BSD Guest,
the Admin Console is Fully working, tomorrow im gonna try XenConvert (VM disk format converter)

they offer "Citrix Provisioning Server" for free too, but i dont know what they do.

---

### Post by UranUtan on 2009-04-07
You can jump directly to the download page here:
[http://www.citrix.com/lang/English/lp/lp_1688615.asp](http://www.citrix.com/lang/English/lp/lp_1688615.asp)

And indeed, the offer is impressive. Reading comments from knowledgeable users in the Virtualization.info blog, some said that people will now have hard time to justify paying for VMWare ESX Server.

---

### Post by juancarlospaco on 2009-04-07
**I prefer XenServer because they post the Sources !!!**
and have Updates for the hypervisor's kernel, more hardware compatible than ESXi.
*maybe can run on no-pure Intel hardware... i dont know.*

---

### Post by davim on 2009-08-13
Did you managed to get Ubuntu installed on XenServer in PV mode / with xentools? How?

---


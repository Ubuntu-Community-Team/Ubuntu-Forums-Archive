---
title: "VMWare Workstation - how??"
date: 2008-05-12
forum: Virtualisation
---

### Post by jcbray on 2008-05-12
I'm not responding in the VMWare sticky, as it isn't directly related, but i'm sure it is much the same.

I'm attempting to install VMWare workstation in Ubuntu 8.04.

I followed along, initially installing VMWare Server, which installed and ran my guest OS fine.

 Unfortunatly, it didn't seem to like the idea of workstation installed alongside it, and appears to have uninstalled server. not much of a problem, except I can't get Workstation to work.

attempting to run it tells me:

```
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```

I tried running the any-any patch again, but it fails to shut down two services and aborts. the same goes if i try to run vmware's own config setup.


Does anyone know if the instruction above should work for the workstation edition aswell, and if not, how I can uninstall this, so I can use Server until it IS possible to run Workstation?


 Any and all help appreciated.

---

### Post by jcbray on 2008-05-12
I'm not sure what exactly fixed the issue, but, following the guide, I reinstalled vmware server, which failed, unlike my first attempt, saying it could not patch the kernel, or some such.

 I then started from the beginning again, this time installing vmware workstation, and it completled successfully.

 The stickied guide is exactly right. People installing Workstation should note that it will not ask for a serial number during the process, as it did with Server, instead, you enter it from within the application once it loads.

 A small difference, but hopefully it stops someone giving up thinking an error has occured.

---


---
title: "VMWare Host?"
date: 2007-12-11
forum: The Cafe
---

### Post by Mr. Electric Wizard on 2007-12-11
Hey guys,
I am about to finish up building a server and I am trying to decide which OS I will install.
Configuration will be a secure base install with VMWare Workstation 6.0.2 (linux) with multiple virtual servers.
At first I was thinking of using 7.10 as the host OS but it appears that I need X for VMWare to run, which made me think that 7.10 Desktop would probably work better.

I am not opposed to running a different host OS (slackware, debian, etc.) or running a scaled down desktop manager like fluxbox.

Any of you have any suggestions?

Thanks in advance.

---

### Post by popch on 2007-12-11
Is there a particular reason why the virtual servers have to be run in VMWare Workstation and not in VMWare Server? If not, I think you could run the server without a GUI (if you want to. I think).

---

### Post by Mr. Electric Wizard on 2007-12-11
I already own VMWare Workstation.
Seems to run fine.

---

### Post by toupeiro on 2007-12-11
Keep a few things in mind:  VM's = no Graphic acceleration 

Also, vmware Workstation x.xx doesn't dynamically balance system resources between VM's and is bloatier than vmware server because of its intended usage.

If you are building with the intent to be servers, I would use vmware server.  If you are doing application development in a virtual session, I would consider vmware workstation.

---

### Post by HermanAB on 2007-12-11
Note that Vmware Server doesn't work with RHEL5 or Centos5.  You need Workstation for that.

Cheers,

Herman

---

### Post by toupeiro on 2007-12-11
> **HermanAB said:**
> Note that Vmware Server doesn't work with RHEL5 or Centos5.  You need Workstation for that.

Cheers,

Herman

*begs to differ*  Are you saying that you can't run rhel5 IN vmware server, or you can't run vmware server ON rhel5?

---

### Post by Mr. Electric Wizard on 2007-12-11
Well, the first Virtual Machine that I will be migrating to this box is a ClarkConnect server.
This OS does not have its own desktop environment as it is a Server OS.
I am moving from a current production system of HP Pavillion w/ AMD K6 (~10 years old), so I don't think there will be any problems of the VMWare implementation being any slower.:)

So, since I need X in order to configure VMWare I guess I probably would be better off using a locked down 7.10 Desktop version of Ubuntu.

*edit*
I guess I could use something like this?
[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---


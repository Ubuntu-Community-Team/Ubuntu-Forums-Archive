---
title: "windows terminal server session"
date: 2008-03-22
forum: Server Platforms
---

### Post by HereInOz on 2008-03-22
Hi all,

I know very little about terminal services in Ubuntu, so forgive any ignorance.

Is it possible to set up an Ubuntu server, with terminal services, and then install a windows installation as the client session?

I don't need to know how it is done at this stage - just whether it is possible.

---

### Post by HermanAB on 2008-03-22
Not quite no.

You could install VMware on Linux, then install Windows 2003 inside that and activate Windows Terminal Services in Win2003.  Win2003 supports 2 remote users by default.  more would require a license for terminal services, or you could use VNC for additional remote users.

---

### Post by Maxtorm on 2008-03-23
> **HereInOz said:**
> Is it possible to set up an Ubuntu server, with terminal services, and then install a windows installation as the client session?
If you're talking about terminal services in a generic sense (as opposed to specifically Microsoft Terminal Services), NX is probably your best bet for running a similar environment under Ubuntu. See: [http://www.nomachine.com/](http://www.nomachine.com/)

---

### Post by netlogic on 2008-03-23
> **HereInOz said:**
> Hi all,

I know very little about terminal services in Ubuntu, so forgive any ignorance.

Is it possible to set up an Ubuntu server, with terminal services, and then install a windows installation as the client session?

I don't need to know how it is done at this stage - just whether it is possible.

Do you mean running Windows apps inside Ubuntu Server?
Two options

**option 1**

1. install NX server
2. install wine
3. run the win32 apps wrapped around wine (wine will be 1.0 soon. it has matured a lot).

**option2**
1. install VMWARE
2.  install XP inside VMWARE
3. Remotely run Windows Desktop.

---

### Post by netlogic on 2008-03-23
You can test drive NX through their java plugin. I think it is faster than RDP.

[http://www.nomachine.com/testdrive-webcompanion.php](http://www.nomachine.com/testdrive-webcompanion.php)

---

### Post by koenn on 2008-03-23
> **HereInOz said:**
> 
Is it possible to set up an Ubuntu server, with terminal services, and then install a windows installation as the client session?

I don't need to know how it is done at this stage - just whether it is possible.
You're probably aware that with 'terminal services', applications run on the server. So what you want to do is run linux applications on a server, but let people use them from a windows client, right ? 

if not - what exactly is it that you're trying to do ?

---

### Post by HereInOz on 2008-03-23
Sorry, should have explained more.

I am wondering if I can set up an Ubuntu server, set up LTSP-5 on it, and then have windows sessions running on that server, accessible from thin client workstations.

My guess is that the answer is no, and I will need to run VMWare or similar, but Linux in general continually surprises me with its capabilities, so I thought I would ask the question.

---

### Post by HermanAB on 2008-03-23
VMware.

---

### Post by netlogic on 2008-03-24
You have many options. Have you also looked into 2xthinclient server?

---


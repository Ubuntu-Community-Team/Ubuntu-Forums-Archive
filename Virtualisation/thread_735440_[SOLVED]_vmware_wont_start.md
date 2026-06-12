---
title: "[SOLVED] vmware wont start"
date: 2008-03-25
forum: Virtualisation
---

### Post by upthelum on 2008-03-25
I had to sudo /usr/bin/vmware-config.pl to restart vmware the 2nd time. After this i had to sudo /usr/bin/vmware-config.pl again but get this error:
Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Blocking file system:                                               done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Workstation

Execution aborted.

I havn't applied riven0's fix either yet, should I?

---

### Post by BL00dFox on 2008-03-25
Have you tried Virtualbox? It works like a charm, does everything vmware does.

---

### Post by seanc7 on 2008-03-25
What version of VMWare are you running?

---

### Post by upthelum on 2008-03-25
Workstation 6 and how do i install virtualbox?

---

### Post by upthelum on 2008-03-26
So i ran /usr/bin/vmware-config.pl again after a cold restart and it worked but vmware didn't open. I ran it again and the service error came back. Can anyone give a fix i really need to get it working.

:sad:

---

### Post by cataics on 2008-05-09
I get the same problem, after each restart a 'not-configured' file appear in /et/vmware, and the vm don't start unless I delete this file or run the install script.

How is this solved?

---


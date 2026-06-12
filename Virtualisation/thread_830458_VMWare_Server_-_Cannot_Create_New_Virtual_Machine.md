---
title: "VMWare Server - Cannot Create New Virtual Machine"
date: 2008-06-15
forum: Virtualisation
---

### Post by kkazlowski on 2008-06-15
Hi, I installed VMWare Server 1.06 build-91891 under Ubuntu 8.04 last night. VMWare Server Console starts up fine, with no error messages, but when I go to create a new virtual machine (File -> New -> Virtual Machine), the option for "Virtual Machine" is grayed out. I tried running this using "sudo vmware", and that didn't help. :(

Thanks in advance for any help.

---

### Post by PilotJLR on 2008-06-15
When you ran the vmware-config.pl script, did the path you chose to store the VM's exist? You may want to run that script again, and make sure the path is valid.

Running "vmware" as root unfortunately won't help, because the "vmware" program is only the console, which is just a client for the server component.

---

### Post by kkazlowski on 2008-06-15
> **PilotJLR said:**
> When you ran the vmware-config.pl script, did the path you chose to store the VM's exist? You may want to run that script again, and make sure the path is valid.

I'm not sure if it existed originally when I ran vmware-config.pl, but I ran it again and checked that it existed, and it does.

---

### Post by Traxter on 2008-08-11
I don't know if you've fixed it yet but I had this problem and it was because I pressed "Cancel" at start of vmware console instead of connecting to localhost. When I did that I could create a new virtual machine.

/Traxter

---

### Post by kkazlowski on 2008-08-11
> **Traxter said:**
> I don't know if you've fixed it yet but I had this problem and it was because I pressed "Cancel" at start of vmware console instead of connecting to localhost. When I did that I could create a new virtual machine.

/Traxter

Whoops, forgot about this thread, sorry. After playing with it for a while, that's what I figured out and it worked. Thanks though. =)

---


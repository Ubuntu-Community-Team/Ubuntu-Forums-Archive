---
title: "VMware dual boot with Active Directory authentication"
date: 2008-08-19
forum: Virtualisation
---

### Post by nkrick on 2008-08-19
I have a dual boot laptop setup so that I can boot to Ubuntu 8.04 or Windows XP.  When I boot to Ubuntu, I can use VMware to start the physical Windows partition in a virtual machine.  When I set this up, I had to add my user to the "disk" group so that it had sufficient access to read the physical disk.  

I recently "joined" Ubuntu to Active Directory using the instructions found here:  [http://jaysonrowe.wordpress.com/2008/04/21/ubuntu-804-active-directory-integration-w-likewise-open/](http://jaysonrowe.wordpress.com/2008/04/21/ubuntu-804-active-directory-integration-w-likewise-open/) .  This works well and I can log into the domain.  But when I log into the domain I cannot start the VM from the physical partition because my AD user account is not a member of the disk group.  I tried to add the user to the disk group, but I received an error that the user account does not exist.  

How can I give an Active Directory user account disk access so I can start this VM?

Thanks in advance for the help,

Nathan

---

### Post by HermanAB on 2008-08-19
I don't think you can do it that way.  Try changeing the permissions of the directories, or run the VM as root.

Cheers,

Herman

---

### Post by nkrick on 2008-08-19
I don't think there is a folder to change permission on.  When performing a dual boot where the physical partition is used as a VM, it is necessary to have read write access to the full disk, not a folder on the disk.  Generally the solution is just to add the linux user account to the "disk" group.  In this case, it is not possible to add an Active Directory user account to the disk group, so I am looking for a workaround.  

I will try using root privileges tomorrow.  I am currently logged in as a local user in order to run the VM and I don't want to shut everything down right now.

---


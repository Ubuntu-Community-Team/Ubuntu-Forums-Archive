---
title: "Manipulating System Files"
date: 2018-09-21
forum: Security
---

### Post by Geoff_Lane on 2018-09-21
Folks,

Is the terminal the only way that system files can be altered? 

Reason I ask is that I use shared keys to access a couple of Ubuntu machines via ssh and am just wondering if other servers pose a risk.

I appreciate computers can be vulnerable via malicious programs that can read data but am more concerned with actual control of a machine.

Geffers

---

### Post by joegry on 2018-09-21
Your system's files can be altered by commands you or others run in a terminal session and by programs executing commands on the computer as well.

---

### Post by TheFu on 2018-09-22
There are many ways for files on a system to be altered. Many.
"Shared keys" is vague. Please be specific.  Are these ssh-keys?  Do they have a strong unlock key/password or a trivial one?
Control of machines is possible using all sorts of different methods. A tiny weakness discovered is enough.  

There aren't any 100% secure computers that are powered on.  If someone has physical access, pretty much the game is over. If they can boot a system using their own flash drive, then anything short of whole disk encryption is 100% open to them.  SELinux, AppArmour, ACLs, and permissions mean nothing.  People overlook this all the time.  Physical access completely negates all the permissions on a system, unless it is strongly encrypted with a sufficiently complex decryption key/access mode.  Don't use the same unlock for your encrypted disks as you use on your luggage.  Even 6-5-4-3-2-1 isn't good enough.

---

### Post by archphoenix on 2018-09-23
System files can be altered by any process with sufficient privileges.
You can run **xed** as **root** and edit **/etc/passwd** if you have enough privileges for that, meaning write permission granted by direct unix file permission (owner, group or other if you're the owner or in correct group, or if other permission was altered to allow writing), ACL permissions (if added to the file via **setfacl**, as not present by default) and if **AppArmor** or **SELinux** isn't reducing your privileges on that file (If active and if applicable).

If your "shared key" is an access to a user account with sufficient privileges to execute process without restriction, then yes it is a security threat to these systems if your key isn't properly protected.

Shared keys should be public key, private key should not leave your computer and be password protected or be stored on safe encrypted removable storage.

---


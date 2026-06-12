---
title: "USB flash drive - how to set access permissions"
date: 2011-01-23
forum: Security
---

### Post by gr@ss_h@pper on 2011-01-23
Hi All,

What should I do if I want to allow access to USB flash drive selectively - Say for e.g. All permissions for "root", "Read/Write" for user "A", Only "Read" for user "B" and user "C" shouldn't be able to access or mount (no permissions) the USB flash drive at all. 
Also I want to do it by modifying entries in some files or by some commands (so that it can be done programatically if needed); I think GUI way would not help much.
I am using Ubuntu 10.04 (But a generic solution is very much appreciated). 

Thanks in advance :)

---

### Post by gr@ss_h@pper on 2011-01-23
On searching various forums I got some info but it's not helping much. May be somebody can put more light on it.
----------------------------------------------------------------------------------------------------------------------------------------
1. Read about udev rules at a lot of places. I tried adding a rule in  rules.d dir specific for a particular Owner (say user "C") to set his  Mode as "0000" (No permissions) for flash drive. Restarted the udev  daemon. But this didn't work for me. When I am logged in as User "C",  USB is still getting auto mounted and is accessible. I might have  written the rule wrongly or... Am I missing something??

2. Some people have suggested to unload the usb_storage module itself  and remove it from its usual path. But disabling usb this way is not  desirable for root or the eligible users.

3. Some asked to edit /etc/modprobe.conf file to stop the module load or  to add entries in blacklist.conf file. This also is undesirable just  because of the reason stated in point 2.
BTW does ubuntu 10.04 not have /etc/modprobe.conf file?

---

### Post by cariboo on 2011-01-24
The directory you're looking for is /etc/modprobe.d, that's true Ubuntu doesn't have a modprobe.conf any more

---

### Post by gr@ss_h@pper on 2011-02-14
Please help on the original problem... 
To simplify I just wanted to do something so that if I plug-in the usb to a user A, user A should be able to get it mounted, but when I am logged in as user B and I plug in usb, I should not be able to mount it at all. (I am not looking for the scenario that I plug in usb once and try to access it through different users.)

By default usb is mounted with permission 700. That means current user has all the permissions and others don't have any.  
 
Now I think if I can achieve somehow the configuration that user A has permission to do the mounting and user B doesn't, then it would work. May be some group setting. I tried removing user B from plugdev group but it didn't work. 
Please somebody help...

---

### Post by HermanAB on 2011-02-15
Howdy,

You can probably do that with a udev rule, but good luck with that...

It will be much easier to do with groups and ACLs, but that requires that you reformat the flash drives with a real Linux file system such as Ext3 instead of the default FAT.

---

### Post by Jive Turkey on 2011-02-15
I think encrypting the contents of the flash drive will better accomplish overall access restrictions.  

I have encountered some flash drives that have a read only partition and found the partition was mounted as an iso-9660. I found it difficult to make it writable.

---


---
title: "KVM virsh managed save on Host shutdown"
date: 2012-10-04
forum: Virtualisation
---

### Post by patrcik111 on 2012-10-04
Hi,
i got 2 windows guest und virt-manager installed. I managed to get the 2 machines autosatrted when the host (Ubuntu Server 12.04) boots.
 
Now i'm searching for a possibility to save the two machines automatically when the server (host) shuts down.
 
Isn't there an out of the box solution? I think i'm not the only who has this requirement.
 
Thanks in advance.

---

### Post by albandy on 2012-10-04
Make an init.d script with this contents:

In the start section:
virsh restore path_to_save_file
In the stop section:
virsh save virtualmachinename path_to_save_file

---

### Post by patrcik111 on 2012-10-04
- Don't i run into Problem with upstart when the save machines process takes longer than the shutdown of the host?

---

### Post by albandy on 2012-10-04
RedHat does something similar by default.
Download the libvirt-client-0.9.6-3.9.1.i586.rpm from rpmfind and extract it using file-roller.
Search for a file called libvirt-guests and open it. Probably you have to modify it to make it work under Ubuntu

---


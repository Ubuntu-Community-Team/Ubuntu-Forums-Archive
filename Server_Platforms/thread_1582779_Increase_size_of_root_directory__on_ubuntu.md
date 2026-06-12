---
title: "Increase size of root directory / on ubuntu"
date: 2010-09-27
forum: Server Platforms
---

### Post by Thyagaraj on 2010-09-27
Is it possible to increase the size of the root directory / on ubuntu 9.10?.
  Please need instructions...

---

### Post by amauk on 2010-09-27
You can't change a partition while using it

Boot to a LiveCD, then use parted to resize the partitions

Always backup important stuff before hand

---

### Post by prshah on 2010-09-27
> **Thyagaraj said:**
> Is it possible to increase the size of the root directory / on ubuntu 9.10?.

yes, please see the thread [Out of space error when Upgrading to Intrepid]("http://ubuntuforums.org/showpost.php?p=6477747&postcount=2") for details. You can also look over the entire thread if you prefer to.

---

### Post by Thyagaraj on 2010-09-27
Thanks for your help. 
What if it is a cloud server which is located at remote location? and I connect to this via ssh.

---

### Post by amauk on 2010-09-27
> **Thyagaraj said:**
> Thanks for your help. 
What if it is a cloud server which is located at remote location? and I connect to this via ssh.
then you'll probably have to contact the company that provides the service

---

### Post by the_original_billq on 2010-09-27
If you have serial console or KVM on the server, can you PXE boot the box to a net install image, then go to a single user shell?  Do you have parted available for net boot?  That would do what you need.

-Bill

---


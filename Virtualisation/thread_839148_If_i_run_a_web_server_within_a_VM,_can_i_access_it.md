---
title: "If i run a web server within a VM, can i access it from host machine?"
date: 2008-06-24
forum: Virtualisation
---

### Post by Brinstar on 2008-06-24
i.e. can the guest OS be 'viewed' from outside?

---

### Post by inevaexisted on 2008-06-24
Depends I guess on how you set up the VM software.

Short Answer: Yes

Long Answer:
I know that if you are using VMware you can configure the VM machine to be on a virtual network that only the VM machine and the host machine are a part of. Other alternatives offered by VMware is that you can make the VM machine appear as a machine on your local network(if this is how you set it up, its a simple matter of setting up your firewalls as necessary to allow access). Finally there is some functionality offered for copy/pasting between VM environment and host environment though this is usually fairly limited, as well as 'Shared Folders'.

--Yes

-Ineva.

---

### Post by Brinstar on 2008-06-24
Thanks for the info :-D

> **inevaexisted said:**
> Depends I guess on how you set up the VM software.

Short Answer: Yes

Long Answer:
I know that if you are using VMware you can configure the VM machine to be on a virtual network that only the VM machine and the host machine are a part of. Other alternatives offered by VMware is that you can make the VM machine appear as a machine on your local network(if this is how you set it up, its a simple matter of setting up your firewalls as necessary to allow access). Finally there is some functionality offered for copy/pasting between VM environment and host environment though this is usually fairly limited, as well as 'Shared Folders'.

--Yes

-Ineva.

---


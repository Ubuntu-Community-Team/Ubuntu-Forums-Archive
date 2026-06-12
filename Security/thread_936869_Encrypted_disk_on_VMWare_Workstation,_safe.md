---
title: "Encrypted disk on VMWare Workstation, safe?"
date: 2008-10-03
forum: Security
---

### Post by peterlauri on 2008-10-03
Hi,

We need to protect the content of a machine, but still allow someone to use the service. So I was thinking to have a encrypted Ubuntu installed on a VMWare Workstation. Will this be save? Or can someone read the information in the "Virtual Disks", or will it be as safe as to have a encrypted Ubuntu on a normal disk?

The service that will be available is a normal web application. No one will be able to login to the machine as root or any other normal user.

/Peter

---

### Post by hyper_ch on 2008-10-03
as far as I understand it will be as save as fully encrypt ubuntu on a normal install. In the end the VM is just one huge file that "emulates" a harddisk and during installation you then encrypt that stuff.

---


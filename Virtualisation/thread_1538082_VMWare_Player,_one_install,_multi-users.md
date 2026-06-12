---
title: "VMWare Player, one install, multi-users"
date: 2010-07-24
forum: Virtualisation
---

### Post by cwwilson721 on 2010-07-24
I had this worki9ng on another box, but I have no access to it at the moment.

My question is:

I install the guest os/hdd in a "common" folder. What permissions (and how) do I set the "common" folder?
i.e. /VMWare is where the guest is located at. What do I type to make the guest usuable to all users on this computer in Ubuntu 10.04?

---

### Post by dcstar on 2010-07-25
> **cwwilson721 said:**
> I had this worki9ng on another box, but I have no access to it at the moment.

My question is:

I install the guest os/hdd in a "common" folder. What permissions (and how) do I set the "common" folder?
i.e. /VMWare is where the guest is located at. What do I type to make the guest usuable to all users on this computer in Ubuntu 10.04?

You can not run the same VM in multiple instances, you need a separate copy of the VM available for each instance you want to run.

---

### Post by cwwilson721 on 2010-07-25
> **dcstar said:**
> You can not run the same VM in multiple instances, you need a separate copy of the VM available for each instance you want to run.WRONG. Done. I just changed the permissions of all folders/files in the common /VMWare folder.

Works great. Now all users on this box uses just one vm

---

### Post by fjgaude on 2010-07-25
But... but you have only one user at a time? Is this correct?

---

### Post by cwwilson721 on 2010-07-26
Did I say "*multiple simultaneous users*"? Or did you assume that?

If you read the OP, in no place did I say  "*multiple simultaneous users"*. 

Thus, the title "**VMWare Player, one install, multi-users**"

---


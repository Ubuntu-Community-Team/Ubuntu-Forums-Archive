---
title: "running ubuntu live on a virtual machine"
date: 2009-07-31
forum: Virtualisation
---

### Post by laplace/d on 2009-07-31
i want to run an ubuntu 8.04 live version on virtualbox-OSE (using ubuntu 8.04 as host as well) and be able to use the guest additions as well so i can share folders....any ideas?

---

### Post by pmlxuser on 2009-07-31
Not Possible i think. unless you are talking of folders on a network machine its possible. (have tried several times it doesnt work)

---

### Post by laplace/d on 2009-07-31
> **pmlxuser said:**
> Not Possible i think. unless you are talking of folders on a network machine its possible. (have tried several times it doesnt work)

i shared the folders with samba, even the usb...cool!
in the guest
```
sudo apt-get install smbfs
sudo smbmount //10.0.2.2/shared_folder mountpoint  #10.0.2.2 is the host

```
it asks for a password, i typed '0' (without the '') and IT WORKED!!!
that worked for me and i could access my host files

---


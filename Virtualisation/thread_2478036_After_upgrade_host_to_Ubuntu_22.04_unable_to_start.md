---
title: "After upgrade host to Ubuntu 22.04 unable to start all VMs"
date: 2022-08-15
forum: Virtualisation
---

### Post by satimis on 2022-08-15
Hi all,

Previous host - Ubuntu20.04 desktop

After upgrade the host to Ubuntu 22.04 desktop, all VMs unable to start

Warning:```

Failed to open a session for the virtual machine multisite02.

The VM session was aborted.

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: SessionMachine
Interface: ISession {c0447716-ff5a-4795-b57a-ecd5fffa18a4}

```

Please help.  Thanks in advance.

Regards

---

### Post by SeijiSensei on 2022-08-15
VirtualBox? KVM?

---

### Post by satimis on 2022-08-16
> **SeijiSensei said:**
> VirtualBox? KVM?
VirtualBox

Problem solved after download and install the extension pack; 
virtualbox-6.1_6.1.36-152435_Ubuntu_jammy_amd64.deb

all VMs can be started

Regards

---


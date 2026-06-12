---
title: "uvt-kvm: error: timed out waiting for dnsmasq lease"
date: 2020-05-09
forum: Virtualisation
---

### Post by Gvarelov on 2020-05-09
Hi,
Following the official Ubuntu Server guide, I am trying to create and start a CLI-only virtual machine via the uvt-kvm tool:

```
uvt-kvm create some_vm release=vivid
uvt-kvm wait some_kvm
```

as is recommended by the guide to give time to the VM to boot. An error message comes back stating that:

```
uvt-kvm: error: timed out waiting for dnsmasq lease for 52:54:00:5f:4d:9c
```
I installed virtualization packages as was described in the guide:
```
sudo apt -y install uvtool
```
I am running Ubuntu 20.04 (not server, but the guide says it should not be a problem.

I would really like to continue using uvt-kvm tool. Is there anything else to be installed or configured to make the uvt tool working?

---


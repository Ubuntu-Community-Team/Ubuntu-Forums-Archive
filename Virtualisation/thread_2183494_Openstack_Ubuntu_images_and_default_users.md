---
title: "Openstack Ubuntu images and default users"
date: 2013-10-25
forum: Virtualisation
---

### Post by rjharv on 2013-10-25
Hi all,

I have a quick question. I've got a fully working openstack (havana) environment built on Ubuntu 12.04 and I've imported the ubuntu 12.04 images into glance. I'm setting a root password for the system when I create it via the web console and I've updated libvrt to allow this to happen.

However what confuses me is that the SSH key I choose for the instance is not only being set for the ubuntu user but also for the root user. I don't want the root user logging in at all, not via password or via ssh key.

Looking at cloud-init there is a flag:

disable_root: 1

I'm guessing this just changes the sshd config to only allow keys.

Does anyone know why this key is being set for the root user and how to disable it?

Ric

---


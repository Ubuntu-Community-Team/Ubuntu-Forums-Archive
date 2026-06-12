---
title: "Juju bootstrapping issue"
date: 2015-04-30
forum: Ubuntu Cloud and Juju
---

### Post by jon87 on 2015-04-30
I'm in the process of creating a private cloud for my College for research however, I have had little previous experience with networking. I have already configured MAAS and enlisted 8 nodes however when I attempt juju bootstrap I receive the following error:

Failed to bootstrap environment: bootstrap instance started but did not change to Deployed state: instance <my instance> is started but not deployed.

I'm wondering how to fix this... I am able to deploy nodes through the MAAS UI by selected Acquire and start node. 

My environment.yaml reads as follows:
maas:
  type: maas
  maas-server: 'my-mass-server'
  maas-oauth: 'my-oauth'
  admin-secret: secret
  default-series: trusty
  authorized-keys-path: ~/.ssh/id_rsa.pub
  disable-network-management: true. 

Any ideas?

---

### Post by Elizine on 2015-06-04
Hi,

Please refer to the following URLs - 
[https://maas.ubuntu.com/docs/juju-quick-start.html](https://maas.ubuntu.com/docs/juju-quick-start.html)
[http://askubuntu.com/questions/490000/juju-bootstrap-using-maas-unable-to-ssh-into-nodes](http://askubuntu.com/questions/490000/juju-bootstrap-using-maas-unable-to-ssh-into-nodes)

Hope this will help you.

---

### Post by blakehenderson on 2016-05-02
make sure you did not use any tabs in your yaml file--- yaml does not like that.  Use spaces.

---

### Post by howefield on 2016-05-02
Old thread closed.

---


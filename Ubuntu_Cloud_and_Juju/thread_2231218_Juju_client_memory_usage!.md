---
title: "Juju client memory usage!"
date: 2014-06-24
forum: Ubuntu Cloud and Juju
---

### Post by DrivenMink on 2014-06-24
I am currently trying to bootstrap an initial environment on work's Azure cloud account.

I've had success with Juju and MAAS on my home systems - and was able to spin up a number of instances without issue. Now I have access to a cloud account, how hard could it be?

Turns out, not quite as easy as it was at home.

Firstly - the juju client grows massively in memory usage when attempting to bootstrap, and bombs out very quickly on my low-powered Windows desktop at the office (only 4GB ram, boo). My home Windows desktop has 16GB, and that had no problems bootstrapping.. but that was to MAAS, not Azure.

I have a Mac here too so tried it on that. Set up my keys, added to the account, and when firing up the juju process grows to 6GB initially and then hovers around the 4GB region before sitting there at around 70-80% cpu. **There is no network traffic at all**. Debug mode just says 'opening environment "azure"'. Performance on the whole machine takes a massive nosedive. There is no supporting log or other information to go off here that I can see..

Juju is 1.18.4 
OSX is 10.9.3
machine is an i7 with 8GB RAM

environments.yaml is configured correctly as per the docs.

What the hell is going on with this?

---

### Post by DrivenMink on 2014-06-24
**Update...**

On said mac, if I run a Virtualbox instance of Ubuntu 14.04, and fire up a local LXC instance, it works. If I try to deploy to Azure from the same VM, it sits and spins. Perhaps more verbose logging would be of some use here...?

Go figure.

---

### Post by DrivenMink on 2014-06-24
**FURTHER UPDATE:**

Finally found: [https://bugs.launchpad.net/ubuntu/+source/juju-core/+bug/1250007](https://bugs.launchpad.net/ubuntu/+source/juju-core/+bug/1250007). 

Still doesn't help though because it says I should point at the .pem certificate in my config. Tried this, now I get a 403 forbidden error DESPITE having uploaded the public key to the azure account. 

Tried deleting and regenerating openssl keypair based on this: [https://bugs.launchpad.net/juju-core/+bug/1214178](https://bugs.launchpad.net/juju-core/+bug/1214178).

**This is a lie. **Still does not work.

Some of this may be due to lack of understanding of PKI, but seriously - following the documentation just sends me round in circles.

---


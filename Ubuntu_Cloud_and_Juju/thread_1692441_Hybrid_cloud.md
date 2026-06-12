---
title: "Hybrid cloud"
date: 2011-02-21
forum: Ubuntu Cloud and Juju
---

### Post by bonzi on 2011-02-21
I have some concerns in hybrid cloud. How do we ensure security while setting up a hybrid cloud. For example if I want to use EC2 or Rackspace then how can I make sure that the connectivity between the private and the public cloud is secure? Do we havr to set up a VPN? If yes do we have to set it up manually?

---

### Post by raymdt on 2011-02-21
hi,
this is a very important topic. Unfortunately there are only few people who are interested in Security on Hybrid cloud.
- You can use a ssh-tunnel to exchange Data between the private-cloud and the public-cloud

- You can(should) use Euca2ools(for Eucalyptus, Openstack and AWS)  for interaction between private and public cloud. 
Euca2ools uses the M2crypto-library for python, to encrypt the communication.

Yesterday i found a security issue in Euca2ools. Ich will first check it again, befor filling a Bug report.

---

### Post by bonzi on 2011-02-21
Thanks for the info. 
 Is there any reason why you prefer ssh-tunnel over openvpn? 

Currently I'm trying to find out more info about how Euca2ools is using M2crypto to provide secure connectivity. (Any info will be appreciated :) )

Thanks again

---

### Post by raymdt on 2011-02-22
Hi,
ssh is easier to use than Openvpn an it is not easy to configure Openvpn on the Cloud(But you can try it). What do you want to do with your hybridcloud? Do you need Openvpn??

Euca2ools use M2crypto to encrypt the image ,(Example when you use euca-bundle-vol and euca-upload-bundle to bundle and  upload image to the cloud).

The Eucalyptus' source code is in Python. Also you can read it like a book

---

### Post by kim0 on 2011-02-23
Hi, while I agree ssh is easier to start with, I would definitely recommend openvpn for anything that resembles production work

---


---
title: "What is this pem key thing"
date: 2012-08-16
forum: Server Platforms
---

### Post by hartz on 2012-08-16
For years I've known about and used SSH with keys to automate login.  I've always simply used the ssh-keygen and copied the public key into the authorised keys wherever I needed to log in into.

A couple of months ago I started with AWS and they have a thing called key pairs, which I am sure is closely related to the keys that I know.... but it isn't exactly the same thing.  These strange keys do work - I can use them as per the instruction on EC2, but not the same way I'm used to.

Could someone explain to me the difference, and more specifically what the .PEM file is that works with the -i flag in SSH.  What is the advantages of the one over the other, etc.

I've now taken to adding the normal kind of keys to my EC2 instance user authorised_keys files since I know it better... and could not find a way to automate dolphin and scp and most other tools (I could only get ssh itself to work with the PEM file)

I have not yet managed to hit the right google search terms so my knowledge and understanding of PEM is still near nil.

Thanx,
  _Johan

---

### Post by Habitual on 2012-08-16
[http://www.gagravarr.org/writing/openssl-certs/ca.shtml](http://www.gagravarr.org/writing/openssl-certs/ca.shtml)

AWS will generate a .key and .pem file for the initial setup of an instance. This is used to guarantee a temporary access to the instance for you, and underlying access to some of the "other" AWS Services you can tie to your instance. 

You should generate or add an existing key.pub contents to the instance's /root/.ssh/authorized_keys or the appropriate /home/$user/.ssh/authorized_keys since root login is disabled on new AWS instances... (you'll have to either enable it or use sudo from the ubuntu user account)

HTH.

---


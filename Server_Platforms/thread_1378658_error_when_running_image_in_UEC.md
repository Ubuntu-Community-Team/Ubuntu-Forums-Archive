---
title: "error when running image in UEC"
date: 2010-01-11
forum: Server Platforms
---

### Post by egeier on 2010-01-11
Setting up UEC for the first time. I'm trying to run an image on a Node Controller computer but get an error:
**EC2_access_key environment variable must be set**

This happens when running the two commands on the Node Controller computer:
euca-describe-groups
euca-authorize default -P tcp -p 22 -s 0.0.0.0/0

using the instructions at [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

Thanks!
Eric

---

### Post by munky99999 on 2010-01-12
[https://help.ubuntu.com/community/UEC/CDInstall#STEP%205:%20Obtain%20Credentials](https://help.ubuntu.com/community/UEC/CDInstall#STEP%205:%20Obtain%20Credentials)

Basically you need to download the credentials. Then run the eucarc file. Whereever it ends up.

Doing

echo "[ -r ~/.euca/eucarc ] && . ~/.euca/eucarc" >> ~/.bashrc

So that everytime you logout/restart you dont have to keep rerunning those credentials.


That's what sets the env: variable.

---

### Post by egeier on 2010-01-12
I followed those instructions for doing the Credentials on the Cloud Controller and i also created a keypair on the Node Controller.

Have any other ideas? Thanks!

---

### Post by vivekjuneja on 2010-01-21
Hi,

Please execute the commands to start the instance from the Cloud controller and not from the Node Controller. That will solve the problem.

Cheers,
Vivek Juneja

---


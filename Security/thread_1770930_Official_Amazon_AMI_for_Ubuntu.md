---
title: "Official Amazon AMI for Ubuntu?"
date: 2011-05-29
forum: Security
---

### Post by sneakyimp on 2011-05-29
I'm hoping to set up an Amazon EC2 compute instance running the latest Ubuntu.  Does anyone know how I can find an "official" one, perhaps published directly by canonical?

This company professes to publish "official" ones but I have no way to confirm that:
[http://alestic.com/](http://alestic.com/)

---

### Post by spynappels on 2011-05-30
From the Ubuntu Wiki:

[https://help.ubuntu.com/community/EC2StartersGuide](https://help.ubuntu.com/community/EC2StartersGuide)

---

### Post by sneakyimp on 2011-05-30
Thanks for the great link.  I visited the #ubuntu-cloud IRC chat yesterday and found the official list of ubuntu machine images.  Any idea what the difference between these two are?
[http://uec-images.ubuntu.com/releases/11.04/release/](http://uec-images.ubuntu.com/releases/11.04/release/)
[http://uec-images.ubuntu.com/natty/current/](http://uec-images.ubuntu.com/natty/current/)
They have different ami IDs.

Also, I've got the EC2 API tools set up but it's kind of a bummer to use the certificates for authentication.  This tends to bind your activity to one particular account and I have a personal one I use for my private development efforts and will need to use a different account for my client's project.  I wonder if there's a more convenient way to switch accounts...

---

### Post by spynappels on 2011-05-30
If you have an encrypted USB drive, you could always place the private key on it and use it on different systems, not the most secure option, but if access from different systems is a must, I'd look for a hardware encrypted USB key and install something like Portable Apps with PuTTY Portable and with the private key stored on the USB drive.

---

### Post by sneakyimp on 2011-05-30
It's not so much that I want to move to different machines but rather that on a given machine I have to re-export my variables when I want to access the EC2 API tools using a different cert and private key.

---


---
title: "Create additional log in users with Amazon EC2"
date: 2010-09-10
forum: Ubuntu Cloud and Juju
---

### Post by Ritty on 2010-09-10
I want to be able to have several users log in to an instance of Ubuntu 10.04 hosted on Amazon EC2 based on Ubuntu provided AMI images. The default user is "ubuntu." I'm wondering if there is a way to add users so that they can log in remotely.

---

### Post by Ritty on 2010-09-10
Nevermind, figured it out.

Change PasswordAuthentication to yes in /etc/ssg/sshd_config

---

### Post by sofasurfer.ch on 2011-07-16
If you'r looking for a simple howto to add new user check out this link:

[http://blog.sofasurfer.ch/2011/07/16/ubuntu-ec2-add-new-admin-user/]("http://blog.sofasurfer.ch/2011/07/16/ubuntu-ec2-add-new-admin-user/")

---


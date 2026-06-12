---
title: "Change hostname and add other users on Ec2"
date: 2011-01-20
forum: Ubuntu Cloud and Juju
---

### Post by MSPdwalt on 2011-01-20
I've recently been playing around with Ubuntu on Amazon Ec2.  One thing that bugs me is the default host names it gives your instances.

[LIST=1]
[*]Is it permissible to change the hostname of your instance?
[*]Are there any negative consequences?
[*]How does adding users work with the certificate based authentication?
[/LIST]

I've never used cert based authentication before, I've been told it's more secure.  If I add a user
```
useradd dude
```
Does he login using the same cert or do I have to generate a cert for each user?

---

### Post by kim0 on 2011-01-21
For changing hostnames, you could use a "boothook" in Maverick (10.10) or later.  That code will run very early in boot. You need to pass the following as user-data (either thru amazon console, or --user-data-file)


#cloud-boothook
#!/bin/sh
echo "my.new.host" > /etc/hostname
hostname "my.new.host"

For the certificates question, I think you're probably confused between ec2 users, and Linux users inside the VM! "useradd" results in normal users inside the VM, that use username/passwords for authentication

---

### Post by MSPdwalt on 2011-03-16
This link: 

[http://cloud.lib.wfu.edu/blog/tech/2010/09/28/managing-users-on-amazon-ec2/](http://cloud.lib.wfu.edu/blog/tech/2010/09/28/managing-users-on-amazon-ec2/)

helped me with the the problem of giving other users SSH access.

I'm still looking for documentation on if it is best practice to change the hostname of an Ec2 instance and if there is a proper/improper way to do it.

Kim0 I appreciate the response, I'm running Lucid and as I'm not familiar with boothooks I've opted not to try your idea.  I'm still googling.

My fear is that I will get the hostname changed and get locked out of the box, or break the certificate based SSH or something like that.

I don't fully understand how Ec2 works from a "hardware" standpoint so I'm nervous on messing with anything boot or SSH related.

---

### Post by MSPdwalt on 2011-04-20
I can't believe I didn't think of this earlier, I just spun up another instance quick and changed the host name like you would on a normal physical machine, rebooted, and it worked just fine.

Sometimes I think someone should make a browser add-on that checks ones caffeine level before posting lol

---

### Post by sylvester_0 on 2011-04-22
You'll want to make sure your /etc/hosts file reflects this name change as well. Some daemons (rabbitmq-server) flat out refuse to start if everything doesn't match up.

---


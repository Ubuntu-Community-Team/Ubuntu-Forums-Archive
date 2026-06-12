---
title: "Which Amazon image?"
date: 2010-09-28
forum: Ubuntu Cloud and Juju
---

### Post by blippy on 2010-09-28
I've recently obtained an Amazon EC2 account, and I've managed to get a stock Fedora image working. After a bit of consideration, I would prefer to work with an Ubuntu image. None are provided by default, so I'm looking up the community defaults. There are so many of them. Which one do I search for? I'm looking for a Lucid micro image.

How do I know I can "trust" the community images, and that they aren't filled with malicious compromises?

Also, what's the difference between an instance-store and an ebs?

As you can probably guess, I'm very new to the whole cloud thing.

---

### Post by blippy on 2010-09-28
> **blippy said:**
> Which one do I search for? I'm looking for a Lucid micro image.

OK, I found one: ami-1234de7b . It mentions about searching for 20100923, an updated inage which possibly fixes a rebooting problem that I have been hearing about.

---

### Post by smoser on 2010-10-01
You can always find AMIs for the latest released Ubuntu Images by traversing [http://uec-images.ubuntu.com/releases/](http://uec-images.ubuntu.com/releases/) .  Additionally, that same information is availalble in a machine friendly format at [http://uec-images.ubuntu.com/query/](http://uec-images.ubuntu.com/query/) .

The 20100923 images address a reboot issue on t1.micro instances.  However, they include another bug ([https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/649591](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/649591)).

The bug text mentions a work around, and the lucid update is in progress.

---

### Post by blippy on 2010-10-13
I'm still confused. The images only seem to be for small and medium, but not for micro. When will micro ones be available?

---

### Post by kim0 on 2010-10-15
micro requires an ebs backed image. So choose an AMI with ebs and it should work

---

### Post by blippy on 2010-10-16
> **kim0 said:**
> micro requires an ebs backed image. So choose an AMI with ebs and it should work

Ah, I see. The trick is to look in AMIs, Viewing EBS Images. Ubuntu, and search for Maverick.

---


---
title: "VirtualBox in root"
date: 2008-10-07
forum: Virtualisation
---

### Post by HuXu on 2008-10-07
So I've seen multiple posts on people running VirtualBox as root, but when I run VB as root it acts like there are no Virtual Machines and I have to create one, but I already have one made under my normal main account.  How do I run my virtual machines as root?!

---

### Post by tuxxy on 2008-10-07
When you start the virtualbox app as root it wont have your existing virtual drives loaded.

Click on the **New** button as if you were to setup a new drive and enter the information needed, once you get to virtual hard disk option select **existing drive** and then manually locate and select the drive you need.

---

### Post by snowpine on 2008-10-07
Isn't the whole point of Virtualbox to run a virtual machine that can't mess up the host environment? What is the advantage of running Virtualbox as root?

---


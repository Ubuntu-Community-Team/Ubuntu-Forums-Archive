---
title: "General doubt about UEC"
date: 2011-04-12
forum: Ubuntu Cloud and Juju
---

### Post by drpsycho on 2011-04-12
Hi, I'm used to work with vmware where I have each vm with its hard disk and the files still are there when restart the vm. But in UEC we have a lot of instances of the same hard disk and when we restart them we lost all the changes. I think I'm missing something conceitual about all of this, because what would be the advantage in using UEC in servers if when we restart the instance we lost the modifications??

Please clarify this to me. Thanks

---

### Post by sdamron on 2011-04-12
You need to save a snapshot of the system to a volume in order to maintain the state (installed software, change to any system files, etc.) and then convert that snapshot to an AMI in order to use it as you may have it in an end state prior to termination.

---

### Post by drpsycho on 2011-04-12
> **sdamron said:**
> You need to save a snapshot of the system to a volume in order to maintain the state (installed software, change to any system files, etc.) and then convert that snapshot to an AMI in order to use it as you may have it in an end state prior to termination.

And how can I do that using the web interface or command line, or some api like hybridfox?? Sorry about my questions, I'm a very begginer in this and I didn't found much documentation about the theory and conceitual, only tutorials that don't explain a lot of things, only gives me steps without explanation. And sorry about my Enlish too, I'm brazilian..

Thanks

---

### Post by kim0 on 2011-04-18
Hi there,
Well in the cloud world, instances are basically disposable. You should treat them as such. You shouldn't put important information inside them. Where to put important info? well, they should be put on ebs volumes. So you start an instance, attach a volume to it, and you're in business

For a pretty good understanding of things work, check out this great article about running and backing up mysql in the ec2 cloud (same concepts apply)
[http://aws.amazon.com/articles/1663?_encoding=UTF8&jiveRedirect=1](http://aws.amazon.com/articles/1663?_encoding=UTF8&jiveRedirect=1)

---


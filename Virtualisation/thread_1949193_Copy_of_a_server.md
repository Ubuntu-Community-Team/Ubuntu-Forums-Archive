---
title: "Copy of a server"
date: 2012-03-29
forum: Virtualisation
---

### Post by al_mic on 2012-03-29
Hi,

I am trying to make some copies of the same servers I have in production.
The purpose of this is to test on the copy whatever updates I need to add (linux package updates or other software update - like source code for a web site)

So far I know that VMware is able to copy a server to a virtual machine if you can provide the root password for that original server.

Is there anyone there that tried making copies of production servers and using them for testing purposes?
Should I consider Amazon EC2 as an alternative? Like making an image from my prod server and uploading it as an AMI to Amazon and then start as many instances as I want?

I'm not sure what is the fastest, less expensive and easiest solution for making a test instance from a running server.  


Thanks.

---

### Post by CharlesA on 2012-03-29
I suppose you can clone the servers and restore them to a VM and then clone the virtual drive and go from there.

---

### Post by Habitual on 2012-03-29
> **al_mic said:**
> ...Is there anyone there that tried making copies of production servers and using them for testing purposes?
Should I consider Amazon EC2 as an alternative?...

I have and I use AWS AMIs for this very purpose.
Eric Hammond at [http://alestic.com/](http://alestic.com/) has a few, (ok a LOT of) Ubuntu-flavored AMIs already to go.
Once you have customized it/one "just so" you can save it, copy it, make your own AMI to be used for another instance.

AWS bills on [usage]("http://aws.amazon.com/ec2/pricing/") of resources, so if you aren't developing, shut down the instance and you won't be charged [I]for a running instance.
[/I]Instances in US-EAST1 are less expensive than US-WEST1, I believe.

I think they still give micro instances out for free for a year? See the usage link for details.

Also, a lower-cost alternative could be Virtualbox/VMWare

Good luck.

HTH.

---

### Post by al_mic on 2012-03-30
Hi,

Thank you both for your replies.

I know that Amazon AMIs are good to test on, but not all my servers are on Amazon.
Some of them are dedicated servers with various linux distributions.

Have you tried bundling such a server into an AMI and uploading it to Amazon?
Does it work?



Thanks.

---

### Post by Habitual on 2012-03-30
> **al_mic said:**
> ...Have you tried bundling such a server into an AMI and uploading it to Amazon?...

I have not, sorry.

---


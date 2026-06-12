---
title: "Ubuntu Cloud Support Windows Images?"
date: 2009-11-11
forum: Server Platforms
---

### Post by abarringer on 2009-11-11
Simple question:

Does Ubuntu Enterprise (Private) Cloud Support Windows Images?

Thanks!

---

### Post by abarringer on 2009-11-12
Anyone??? 

Is there a better forum to post this to?

---

### Post by Thirtysixway on 2009-11-12
Are you referring to an image of a windows operating system, or pictures?  Cloud would be able to store and distribute any file, so perhaps I'm reading your question wrong.

---

### Post by abarringer on 2009-11-12
I'm referring to the new Enterprise Private Cloud see here: [http://www.ubuntu.com/cloud/private](http://www.ubuntu.com/cloud/private)

Can I upload and run a windows AMI or Image or VM or whatever you want to call it as a virtual machine?

If it uses KVM the answer is NO. 

If it uses Xen then the answer is maybe. 

I can't tell from the marketing mumbo jumbo which it is. 

Obviously ubuntu wants to force everyone onto KVM but I do not know if they have taken this to the extreme of not supporting Xen hypervisor.

KVM is of course all the Hotness, but only if you don't have to support windows systems. 

Eucalyptus which ubuntu private cloud is based on obviously supports multiple hypervisors and you can run windows on it but not "officially" [http://forum.eucalyptus.com/forum/viewtopic.php?f=4&t=1209&p=5049&hilit=windows#p5049](http://forum.eucalyptus.com/forum/viewtopic.php?f=4&t=1209&p=5049&hilit=windows#p5049)

unless you give them huge stacks of cash for "enterprise edition" see here

[http://www.eucalyptus.com/products/tour](http://www.eucalyptus.com/products/tour)

---

### Post by abarringer on 2009-12-08
Just talked to an Ubuntu Engineer the official word is. "It's technically possible but not supported."

It will (probably) be supported in the release due in April 2010.

Andy

---

### Post by munky99999 on 2009-12-08
Windows can be done. Currently not supported. Also fairly difficult relative to the other bundles you might do. Though tbh you really shouldnt be using ubuntu's cloud in a production manner. Not yet. April 2010 or so should be a good production time. Thusly where should you worry about "supported"

Personally got the cloud running up nice and well. But the Firefox extension just wouldnt work. So pretty much everything was commandline and ssh. Which essentially wasnt very useful to me. As I wanted to do a presentation using it.

Basically what you want to do is convert windows into a working virtual under kvm/xen then you bundle those files over to the cloud basically. Then it works. There's no real way of getting like an empty container that you can install into.

---


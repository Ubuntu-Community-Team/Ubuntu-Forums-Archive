---
title: "Eucalyptus"
date: 2009-07-30
forum: Virtualisation
---

### Post by SergeiFranco on 2009-07-30
Hi,

I am looking at using eucalyptus as "cloud" infrastructure.

Now all the guides there assume that reader used amazon tools before.
I have no idea how they work and what they do.

So I am following this doc
[https://help.ubuntu.com/community/Eucalyptus](https://help.ubuntu.com/community/Eucalyptus)

The following question comes in:
you have to specify kernel/ramdisk/image, but if you create a KVM image it is all on the image?
So what kernel do I specify?
What if I want to run 64bit host and 32bits guests?

Anyway, I followed the instruction word for word (except specifying existing kernel)

and here is the result:
```
ec2-describe-images
IMAGE   emi-2A3B0D14    image/root.img.manifest.xml     admin   available       public          x86_64  machine eki-46021263    eri-987B13C0
IMAGE   eki-46021263    kernel/vmlinuz-2.6.28-13-generic.manifest.xml   admin   available       public          x86_64  kernel
IMAGE   eri-987B13C0    ramdisk/initrd.img-2.6.28-13-generic.manifest.xml       admin   available       public          x86_64  ramdisk
```

Now I got up to step 6, and I am stuck on this command:
```
ec2-run-instances $EMI -k mykey
```

Which brings this error message:
```
Server: SERVICE: FinishedVerify PROBLEM: Not enough resources available:  addresses (try --addressing private) MSG-TYPE: RunInstancesType
```

Obviously it failed. Did it fail because it could not get a network address?
Why would it fail on that?
How can I check that it cannot get network address from dhcp?
I am using bridge configuration, which allows direct access to real network.

At this stage I am frustratingly confused due to lack of information on the error above.

Is anyone actually using eucalyptus in real life situation?

The cluster we currently have in production is running xen/debian and virtual machines are managed manually from each physical host.
We have similar sturcture to this: [http://www.rightscale.com/images/site_diagram.gif](http://www.rightscale.com/images/site_diagram.gif)

---

### Post by Jelly_sh on 2009-08-11
hi , dear friend . Now i  also setup env with cloud on ubuntu9.04 server , but reference link as the same to yours  :[https://help.ubuntu.com/community/Eucalyptus](https://help.ubuntu.com/community/Eucalyptus) 
 
i go to step 5 ,  i couldn't register  my cloud to rightscale account  (i create new account) . why ? you tell me the reason , thanks a lot !
 
 
you have already do the same thing ,i hope you tell me or how to check it .thanks a lot again!

---

### Post by Jelly_sh on 2009-08-11
> **Jelly_sh said:**
> hi , dear friend . Now i also setup env with cloud on ubuntu9.04 server , but reference link as the same to yours :[https://help.ubuntu.com/community/Eucalyptus](https://help.ubuntu.com/community/Eucalyptus) 
 
i go to step 5 , i couldn't register my cloud to rightscale account (i create new account) . why ? you tell me the reason , thanks a lot !
 
 
you have already do the same thing ,i hope you tell me or how to check it .thanks a lot again!
 
 
 
cloud computing server it must be pulic IP? i need to make sure it .

---


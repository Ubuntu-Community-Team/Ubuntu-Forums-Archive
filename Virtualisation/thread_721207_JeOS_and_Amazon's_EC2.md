---
title: "JeOS and Amazon's EC2"
date: 2008-03-11
forum: Virtualisation
---

### Post by centinall on 2008-03-11
While there's been plenty of talk about Ubuntu and [[COLOR="Sienna"]_Amazon EC2 (Elastic Compute Cloud)_[/COLOR]]("http://www.amazon.com/gp/browse.html?node=201590011"), there doesn't seem to be any mention of creating a [_[COLOR="Sienna"]JeOS (Just Enough Operating System)[/COLOR]_]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos") [[COLOR="Sienna"]_AMI (Amazon Machine Image)_[/COLOR]]("http://aws.amazon.com/ec2").

Would this be because JeOS is not really ideally suited to such a role? Or perhaps there's just a lack of interest in the [[COLOR="Sienna"]_AWS's (Amazon Web Services)_[/COLOR]]("http://aws.amazon.com/ec2")? 

Personally, I think JeOS and EC2 could be a match made in heaven and really dying to getting my hands on such an AMI. Think about it. A tiny (>200M) OS with only the bits that you need. I'm sure it would be better than any of those [[COLOR="Sienna"]_~700M AMI's that are out there right now_[/COLOR]]("http://developer.amazonwebservices.com/connect/kbcategory.jspa?categoryID=101").

Does anyone know of any effort to create such an image? Or perhaps do people think it's just not a good idea? I would really love to hear what people think about this. 

Just in case you're wondering, I want to create an image with Apache and either Jetty or Tomcat to run a web application. 

Thanks a lot in advance.

PS: I'm not completely sure if I posted this in the right place, so please move if I was wrong.

---

### Post by ehammond on 2008-05-14
I've been maintaining the Ubuntu AMIs listed at [http://alestic.com](http://alestic.com) and the base install AMIs are fairly light weight as public AMIs go.  The 8.04 Hardy base install AMI currently uses 470MB of disk.  It loads and boots in about 40 seconds which compares very favorably to the other distributions.

I looked into JeOS a bit and from my research it seemed that it required a custom Linux kernel.  Unfortunately, EC2 requires all AMIs to run on specific Xen kernels provided by Amazon and you can't build your own.

If Amazon ever changes this policy, I'd love to help build a JeOS AMI as it sounds like a good fit.

--
Eric Hammond
[http://www.anvilon.com](http://www.anvilon.com)

---


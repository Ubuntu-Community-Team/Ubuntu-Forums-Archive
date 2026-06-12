---
title: "ec2-ap-tools package"
date: 2011-01-19
forum: Ubuntu Cloud and Juju
---

### Post by cjreyn on 2011-01-19
Hi,
I was considering palying with OpenStack, which proclaims to be EC2 capable. We have some existing components that use the ec2-api-tools package to submit to an existing Eucalyptus cloud, and I'm wondering whether they'll work with OpenStack. According to [http://wiki.openstack.org/Nova/EucalyptusFeatureComparison](http://wiki.openstack.org/Nova/EucalyptusFeatureComparison) OpenStack lacks support for SOAP. 

My question is: does the ec2-ap-tools package use SOAP exclusively, or can it support Query based HTTP communication as well (OpenStack proclaims to support this)?

Cheers!

---

### Post by kim0 on 2011-01-19
As per [http://ubuntu-smoser.blogspot.com/2011/01/using-euca2ools-rather-than-ec2-api.html](http://ubuntu-smoser.blogspot.com/2011/01/using-euca2ools-rather-than-ec2-api.html)

The ec2-api-tools use the SOAP interface and thus use the "EC2_CERT" and "EC2_PRIVATE_KEY". The euca2ools sit on top of the excellent boto project. Boto uses the AWS REST api

---

### Post by kim0 on 2011-01-19
As per [http://ubuntu-smoser.blogspot.com/2011/01/using-euca2ools-rather-than-ec2-api.html](http://ubuntu-smoser.blogspot.com/2011/01/using-euca2ools-rather-than-ec2-api.html)

The ec2-api-tools use the SOAP interface and thus use the "EC2_CERT" and "EC2_PRIVATE_KEY". The euca2ools sit on top of the excellent boto project. Boto uses the AWS REST api

---

### Post by kim0 on 2011-01-19
As per [http://ubuntu-smoser.blogspot.com/2011/01/using-euca2ools-rather-than-ec2-api.html](http://ubuntu-smoser.blogspot.com/2011/01/using-euca2ools-rather-than-ec2-api.html)

The ec2-api-tools use the SOAP interface and thus use the "EC2_CERT" and "EC2_PRIVATE_KEY". The euca2ools sit on top of the excellent boto project. Boto uses the AWS REST api

---


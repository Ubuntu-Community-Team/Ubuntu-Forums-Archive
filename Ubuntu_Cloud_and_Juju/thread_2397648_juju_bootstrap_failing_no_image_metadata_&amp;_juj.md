---
title: "juju bootstrap failing: no image metadata &amp; juju metadata failing: no controller"
date: 2018-08-01
forum: Ubuntu Cloud and Juju
---

### Post by bjonesv4n on 2018-08-01
I am inside a clean xenial VM inside a private OpenStack, trying to use conjure-up to install Kubernetes into the same OpenStack instance. This fails with an error: 

**ERROR failed to bootstrap model: no image metadata found.  **

To generate metadata I have attempted the instructions here ( [https://docs.jujucharms.com/2.4/en/howto-privatecloud#create-image-metadata-with-juju](https://docs.jujucharms.com/2.4/en/howto-privatecloud#create-image-metadata-with-juju) ) and all "juju metadata generate-image" commands fail with:

**ERROR No controllers registered.**

All attempts at juju bootstrap commands fail with:

**ERROR failed to bootstrap model: no image metadata found**

This feels like a chicken-and-egg problem but I know I've got to be missing something.  Where do I start troubleshooting this, or is there another doc that I should be referencing?  I've exhausted the first four pages of search results for any combination of related search terms I could think of.

juju --version
2.4.0-xenial-amd64

conjure-up --version
conjure-up 2.6.0

openstack --version
openstack 2.3.1

---

### Post by newleaf2 on 2018-10-13
Running into the same problem here. Did you ever resolve this? Looking though bug reports and can't find anything related to this.

---

### Post by newleaf2 on 2018-10-13
Okay, I may have a workaround. I created a Juju/LXD environment on an OS (OpenStack) instance. I was then able to generate the metadata after creating a local controller (indeed chicken-and-egg). I copied the metadata JSON files (simple stream folder) to my local machine and was able to initiate the Juju controller provisioning to a registered OS cloud. However, it is now trying to connect to the instance using an IP address private to the OS internal network. So I'll probably need to provision a small OS instance first, then deploy Juju from there using the copied metadata. Ugh.

---

### Post by northway on 2018-12-18
Thanks for the tip, it worked for me as well.

The whole scenario:

 - We just finished upgrading our OpenStack to Queens, it seems v3 API is crucial.
 - In my k8s tenant, I created a base VM and bootstrapped a localhost (LXD) controller node with Juju.
 - After the boostrap were completed, I was able the create a metadata image into my home folder.
 - With the generated metadata image, Juju was able to create a dedicated controller VM in my k8s tenant.
 - After all these steps, *juju deploy canonical-kubernetes *&#8203;started without any error.

---


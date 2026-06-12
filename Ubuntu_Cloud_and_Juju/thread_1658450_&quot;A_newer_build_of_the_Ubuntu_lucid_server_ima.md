---
title: "&quot;A newer build of the Ubuntu lucid server image is available. &quot; How to update ?"
date: 2011-01-02
forum: Ubuntu Cloud and Juju
---

### Post by poiuytrez on 2011-01-02
Hello,

I have been running the an ubuntu server for 1 month. This morning, I read "A newer build of the Ubuntu lucid server image is available." when I connect to my server in ssh.
I have tried an apt-get update/upgrade, it does not change anything.

What is the update path ? Do you usually recommend to update ? 

Thanks !
:p

---

### Post by raymdt on 2011-01-02
Hi,
does your server run on your Eucalyptus-Cloud or on Amazon?
Is it just a test server or for production use ?

---

### Post by IWantFroyo on 2011-01-02
Use the update manager. I know Alt-F2, update-manager -d would give you 11.04 if run on a 10.10 system. I'm not sure about 10.04...
Be careful.

---

### Post by poiuytrez on 2011-01-02
> **raymdt said:**
> Hi,
does your server run on your Eucalyptus-Cloud or on Amazon?
Is it just a test server or for production use ?

I'm on amazon ec2. It's a production server, but I can of course duplicate it for testing purposes.

---

### Post by kim0 on 2011-01-03
The update notes have this to say

"If you are using a previous release, you should update in order to receive
the kernel change. The kernel cannot be changed in an Ubuntu 10.04 based
image by package upgrade.

Other changes can be obtained via software update (apt-get upgrade). The
only cost is in time to perform the update (and working around
bug 683379)"

So basically, you should rebuild your server based on the new image to get the new pv-grub kernel thing. However, if you don't want that, you already have everything with a normal dist-upgrade

---

### Post by raymdt on 2011-01-03
> 
So basically, you should rebuild your server based on the new image to get the new pv-grub kernel thing 
This guide can help you do that.
[http://ubuntu-smoser.blogspot.com/2010/04/upgrading-ebs-instance.html](http://ubuntu-smoser.blogspot.com/2010/04/upgrading-ebs-instance.html)

---

### Post by poiuytrez on 2011-01-03
Do you mean that the last image version of LTS 10.04 supports the pv-grub and not the previous one ?

---

### Post by kim0 on 2011-01-04
That is my understanding yes

---

### Post by grenoml on 2011-01-18
Has this new pv-grub capability been bundled into a new Lucid AMI on EC2 yet?

What is the new AMI id?

The only ones I can find are from October.

Maybe we need to wait for fix to bug: [https://bugs.launchpad.net/ubuntu/+source/euca2ools/+bug/672986](https://bugs.launchpad.net/ubuntu/+source/euca2ools/+bug/672986)

---

### Post by progre55_icky on 2011-01-19
> **grenoml said:**
> Has this new pv-grub capability been bundled into a new Lucid AMI on EC2 yet?

What is the new AMI id?

The only ones I can find are from October.

Maybe we need to wait for fix to bug: [https://bugs.launchpad.net/ubuntu/+source/euca2ools/+bug/672986](https://bugs.launchpad.net/ubuntu/+source/euca2ools/+bug/672986)
[COLOR=Navy]you can find the latest AMIs on [http://alestic.com](http://alestic.com)[/COLOR]

---

### Post by progre55_icky on 2011-01-19
_)_[COLOR=Navy][]("http://alestic.com")[/COLOR]

---

### Post by kim0 on 2011-01-20
You can also find the latest amis on [http://cloud.ubuntu.com/ami/](http://cloud.ubuntu.com/ami/)

---


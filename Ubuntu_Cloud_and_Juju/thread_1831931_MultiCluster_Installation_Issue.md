---
title: "MultiCluster Installation Issue"
date: 2011-08-24
forum: Ubuntu Cloud and Juju
---

### Post by vahid_63 on 2011-08-24
Hi 
I have a problem with adding NC to CC in separated cluster.
I have a CC separate from CLC with two network card.
My NC has been connected to eth1 of CC and eth0 is connecetd to public network which CLC is in it. when i installed NC from natty-11.04-amd64 everything was fine and in Cloud Controller I gave the IP of CLC which is in public network and rest of installation was completed automatically.

For adding NC to cloud I used euca_conf --register-nodes in CC and I can sse it from CLC with the cmmand of euca_conf --list-nodes.
But when I use euca-describe-availability-zone verbose resources are zero.

I checked /var/log/eucalyptus/registration in CC I saw key synchronization error so I give passwordless capability to eucalyptus user for ssh from CC to NC but zero resource still persist what can I should do?
Im out of any idea.


Another question about upgrading NC. when I upgraded eucalyptus with command bellow it stuck in a last part like this:

sudo apt-get upgrade eucalyptus
.
.
.
.
Setting up eucalyptus-common (2.0.1+bzr1256-0ubuntu4.1) ...
eucalyptus start/running, process 7258
<stuck here forever>

Is this a kind or bug or what?
Im using natty 11.04 as a UEC CD installation.

---

### Post by Rusty au Lait on 2011-08-26
My thoughts:

Shouldn't CLC be able to access NC? If so, does your CC's network route request to NC from CLC (and the other way)?
Check this link: [https://help.ubuntu.com/community/UEC/PackageInstallSeparate](https://help.ubuntu.com/community/UEC/PackageInstallSeparate)

I've not heard of using apt-get this way
sudo apt-get upgrade eucalyptus
Try
sudo service eucalyptus stop
sudo apt-get install eucalyptus
to re-install eucalyptus

Check the man pages.

My 2¢

---


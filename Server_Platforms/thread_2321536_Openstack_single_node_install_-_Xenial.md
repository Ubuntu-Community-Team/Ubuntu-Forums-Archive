---
title: "Openstack single node install - Xenial?"
date: 2016-04-22
forum: Server Platforms
---

### Post by roderick on 2016-04-22
I recently installed Ubuntu Server 16.04 and wanted to try out OpenStack in a single node setup. 

In earlier versions of OpenStack-installer, you could choose to install a single node setup and it would automate the setup. 

I'm confused on how to achieve the same under 16.04. This option no longer appears to be present, and I cannot find any documentation related to how to achieve this or why this change occurred.

Can anyone assist? I'm just looking for a quick way to start a single node install of OpenStack on my test machine.

Thank,
Rod

---

### Post by MAFoElffen on 2016-04-24
One note is that the metal needs to be vt-x or amd-v capable. It's been about a year ago for me for a single install, but:
```

sudo apt-add-repository ppa:cloud-installer/stable
sudo apt-get update
sudo apt-get install openstack
sudo openstack-install
```
Installing from that PPA, the install script will install as a single node cloud.

OpenStack is cloud service, and sat a while without a response. I think that this thread would more exposure in Specialized Support > Server > Cloud, MAAS, Juju Section, so moved.  PM me if you feel that assumption was wrong and want back in the normal server support section.

---

### Post by roderick on 2016-04-25
I found my answer. Version 2.0 of juju and newer openstack on Xenial uses a program called conjure-up to "conjure up" a new openstack and can be used to create the single server install similar to the old script openstack-install.

This was a bit buried in the devel docs. :)

---

### Post by MAFoElffen on 2016-04-25
-- Left here... (Two alternate answers) Happy that you found a solution.

Please revisit this thread > Use the Link at the top right of the page, named "Thread Tools" > Select "Mark Thread as Solved." That will help others to find a solution to their similar problems.

---


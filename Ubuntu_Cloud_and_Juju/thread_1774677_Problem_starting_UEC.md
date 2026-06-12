---
title: "Problem starting UEC"
date: 2011-06-03
forum: Ubuntu Cloud and Juju
---

### Post by NigelRen on 2011-06-03
I'm having some configuration problems and I've tried re-installing.  The only error I get in the log file ( cloud-error.log ) is

[INDENT]21:51:25 [SystemUtil:main]  ERROR com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap lvm version  error: 
com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap lvm version  error: 
	at edu.ucsb.eucalyptus.util.SystemUtil.run(SystemUtil.java:91)
	at edu.ucsb.eucalyptus.storage.LVM2Manager.getLvmVersion(LVM2Manager.java:154)
	at edu.ucsb.eucalyptus.storage.LVM2Manager.checkPreconditions(LVM2Manager.java:134)
	at com.eucalyptus.bootstrap.BlockStorageBootstrapper.load(BlockStorageBootstrapper.java:99)
	at com.eucalyptus.bootstrap.SystemBootstrapper.load(SystemBootstrapper.java:175)
21:51:25 [SystemBootstrapper:main]  ERROR BlockStorageBootstrapper threw an error in load( ): Is lvm installed?
com.eucalyptus.util.EucalyptusCloudException: Is lvm installed?
	at edu.ucsb.eucalyptus.storage.LVM2Manager.checkPreconditions(LVM2Manager.java:136)
	at com.eucalyptus.bootstrap.BlockStorageBootstrapper.load(BlockStorageBootstrapper.java:99)
	at com.eucalyptus.bootstrap.SystemBootstrapper.load(SystemBootstrapper.java:175)
21:51:25 [SystemBootstrapper:main]  FATAL com.eucalyptus.util.EucalyptusCloudException: Is lvm installed?
com.eucalyptus.util.EucalyptusCloudException: Is lvm installed?
	at edu.ucsb.eucalyptus.storage.LVM2Manager.checkPreconditions(LVM2Manager.java:136)
	at com.eucalyptus.bootstrap.BlockStorageBootstrapper.load(BlockStorageBootstrapper.java:99)
	at com.eucalyptus.bootstrap.SystemBootstrapper.load(SystemBootstrapper.java:175)[/INDENT]

Can anyone suggest what to do next.


For info - I'm trying to install it on a desktop version of 10.04, using the packages.

---

### Post by kim0 on 2011-06-04
Hi,
Two things,
- It seems lvm is not installed ?
apt-get install lvm2

- Also, it seems you're not installing via the integrated cloud installer. It's recommended that you use that. Here are the instructions
[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

---

### Post by NigelRen on 2011-06-04
> **kim0 said:**
> Hi,
Two things,
- It seems lvm is not installed ?
apt-get install lvm2

- Also, it seems you're not installing via the integrated cloud installer. It's recommended that you use that. Here are the instructions
[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

Sorry - I should have posted in the first place - but running apt-get install lvm2 gives

[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
lvm2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/INDENT]
so - unless I'm missing something else, then lvm is installed.

I'm adding the cloud packages to my desktop machine - so I don't want to install from the CD - I'm following  [https://help.ubuntu.com/community/UEC/PackageInstall]("https://help.ubuntu.com/community/UEC/PackageInstall") for the installation instead.

---


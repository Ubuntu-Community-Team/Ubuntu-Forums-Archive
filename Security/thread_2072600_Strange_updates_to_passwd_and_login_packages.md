---
title: "Strange updates to passwd and login packages"
date: 2012-10-18
forum: Security
---

### Post by CamiciaAPua on 2012-10-18
I am running a few servers on Rackspace using Ubuntu Server 12.04 (their standard distribution).
Lately running "apt-get update && apt-get upgrade" tell me that ther are updates for login, passwd and  wpasupplicant. The strange thing is that if I run aptitude, the version number of the old and new versions are the same. See [http://d.pr/i/zjtc](http://d.pr/i/zjtc)

Any specific reason why login and passwd need to be updated and the old and the new versions match?

For a while I had the feeling that some hackers on Rackspace had the control at hypervisor level and probably the aptitude's repositories. Is it something that I should worry about or I am just a little paranoiac ? 

Best,
   Chris

There is also a mismatch between what it is reported at login and what apt-get upgrade says. At login I get: 
9 packages can be updated.
6 updates are security updates.
The mismatch has been going on for a while.

This is the output of apt-get instead:

```
# apt-get update && apt-get upgrade
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Ign [http://mirror.rackspace.com](http://mirror.rackspace.com) precise InRelease                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Ign [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates Release.gpg
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise Release           
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates Release                          
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/main Sources                             
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/restricted Sources
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/universe Sources  
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/multiverse Sources
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/main amd64 Packages
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/restricted amd64 Packages
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/universe amd64 Packages
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/multiverse amd64 Packages
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/main i386 Packages
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/restricted i386 Packages
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/universe i386 Packages
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/multiverse i386 Packages
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/main TranslationIndex
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/multiverse TranslationIndex
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/restricted TranslationIndex
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/universe TranslationIndex
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/main Sources
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/restricted Sources
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/universe Sources
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/multiverse Sources
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/main amd64 Packages
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/restricted amd64 Packages
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/universe amd64 Packages
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/multiverse amd64 Packages
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/main i386 Packages
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/restricted i386 Packages
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/universe i386 Packages
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/multiverse i386 Packages
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/main TranslationIndex
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/multiverse TranslationIndex
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/restricted TranslationIndex
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/universe TranslationIndex
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/main Translation-en
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/multiverse Translation-en
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/restricted Translation-en
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise/universe Translation-en
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/main Translation-en
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/multiverse Translation-en
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/restricted Translation-en
Hit [http://mirror.rackspace.com](http://mirror.rackspace.com) precise-updates/universe Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-virtual linux-image-virtual linux-virtual
The following packages will be upgraded:
  login passwd wpasupplicant
3 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 1,739 kB of archives.
After this operation, 5,120 B of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

### Post by jerrrys on 2012-10-18
Apt-get upgrade will not do a kernel upgrade and is why it holds those packages.  For a complete upgrade use:

sudo apt-get dist-upgrade

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

And welcome to the forums  :)

---

### Post by CamiciaAPua on 2012-10-18
Thanks, yes, apt-get dist-upgrade will do it but in the past apt-get upgrade was enough to upgrade the kernel (maybe for a minor release 3.2.0.24.x ?).
At Rackspace they told me that the Kernel 3.2.0.24.26 is the last one tested on their virtual environment so I think they explicitly set something on aptitude to prevent the upgrade. 

Anyway, this is not what I was mostly concerned with. My concerns are about why login and passwd need to be updated and the old and the new version number match on aptitude.

Did everybody saw login and passwd packages in their list of packages to be upgrade?

---

### Post by CharlesA on 2012-10-18
apt-get upgrade won't install new packages. aptitude safe-upgrade will.

In any case, I saw the update the other day, but you could always check the official page:
[http://packages.ubuntu.com/precise/passwd](http://packages.ubuntu.com/precise/passwd)

As far as the "mismatch" at logon, not all new packages are released due to security updates.
I' using the official repos, not the ones provided by rackspace though.

---

### Post by CamiciaAPua on 2012-10-18
I figured out why the version seemed the same. it is truncated in the aptitude interface.

However, according to the link you posted the last change is on April 2012 [http://changelogs.ubuntu.com/changelogs/pool/main/s/shadow/shadow_4.1.4.2+svn3283-3ubuntu5/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/s/shadow/shadow_4.1.4.2+svn3283-3ubuntu5/changelog) :
shadow (1:4.1.4.2+svn3283-3ubuntu5) precise; urgency=low    * Build-depend on gettext:any for cross-building support.   -- Colin Watson <cjwatson@ubuntu.com>  Mon, 09 Apr 2012 00:28:03 +0100But on my Ubuntu machine aptitude talk about 
1:4.1.4.2+svn3283-3ubuntu5.1See: [http://d.pr/i/SqzD](http://d.pr/i/SqzD)

That .1 is not on the link you sent.

---

### Post by CharlesA on 2012-10-18
```
ii  passwd                               1:4.1.4.2+svn3283-3ubuntu5.1        change and administer password and group data
```

Same as the one I have then.

---

### Post by anonymouschief on 2012-10-19
It appears as though the passwd and shadow packages were updated due to the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/523896](https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/523896)

I check the following website too to verify updates I am suspicious about: [http://www.ubuntuupdates.org/](http://www.ubuntuupdates.org/)

---

### Post by claracc on 2012-10-20
> **CamiciaAPua said:**
> I figured out why the version seemed the same. it is truncated in the aptitude interface.

However, according to the link you posted the last change is on April 2012 [http://changelogs.ubuntu.com/changelogs/pool/main/s/shadow/shadow_4.1.4.2+svn3283-3ubuntu5/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/s/shadow/shadow_4.1.4.2+svn3283-3ubuntu5/changelog) :
shadow (1:4.1.4.2+svn3283-3ubuntu5) precise; urgency=low    * Build-depend on gettext:any for cross-building support.   -- Colin Watson <cjwatson@ubuntu.com>  Mon, 09 Apr 2012 00:28:03 +0100But on my Ubuntu machine aptitude talk about 
1:4.1.4.2+svn3283-3ubuntu5.1See: [http://d.pr/i/SqzD](http://d.pr/i/SqzD)

That .1 is not on the link you sent.

The passwd packages I have are:

My passwd software package is 1:4.1.4.2+svn3283-3ubuntu5.1, updated about one day ago. 

The available releases for passwd I have are shown in the image attached.

So I think you don't need to be worried since it is a normal security update.

---


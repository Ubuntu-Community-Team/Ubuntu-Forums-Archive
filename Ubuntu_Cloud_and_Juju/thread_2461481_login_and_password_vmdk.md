---
title: "login and password vmdk"
date: 2021-05-01
forum: Ubuntu Cloud and Juju
---

### Post by pcfreak492 on 2021-05-01
i have little problem i downloaded the bionic-server-cloudimg-amd64.vmdk for vmware but someone needed the login and password

---

### Post by TheFu on 2021-05-01
Well, whoever created it would need to provide the userid and password.  Ubuntu sets those during the install based on inputs by the installer. **There is no default.**

Do you really want to trust someone else's setup?  I think that is a bad idea.  Just do the install yourself into your VM hypervisor. Should take 10-15 minutes, tops.

---

### Post by pcfreak492 on 2021-05-01
> **TheFu said:**
> Well, whoever created it would need to provide the userid and password.  Ubuntu sets those during the install based on inputs by the installer. **There is no default.**

Do you really want to trust someone else's setup?  I think that is a bad idea.  Just do the install yourself into your VM hypervisor. Should take 10-15 minutes, tops.



it's because this version i downloaded this from the site [https://cloud-images.ubuntu.com/bionic/current/](https://cloud-images.ubuntu.com/bionic/current/) this has standard ssh port open and want to know how it works

---

### Post by TheFu on 2021-05-01
> **pcfreak492 said:**
> it's because this version i downloaded this from the site [https://cloud-images.ubuntu.com/bionic/current/](https://cloud-images.ubuntu.com/bionic/current/) this has standard ssh port open and want to know how it works

It uses the userid and password signed up to get ubuntu core, I think.
> The Ubuntu Cloud image can be run on your personal Ubuntu Cloud, or on public clouds that provide Ubuntu Certified Images.
Try using your landscape account?  I don't have one - call it a personal privacy consideration - can't test. sorry.

You can just install any ubuntu (desktop or server flavor) into any VM, install ssh or ssh-server and play with ssh as much as you like between any two systems.
ssh is one of the top 5 things to know on computers.  [https://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-sshhas](https://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-sshhas) a small list of things ssh allows.

---

### Post by pcfreak492 on 2021-05-03
> **TheFu said:**
> It uses the userid and password signed up to get ubuntu core, I think.

Try using your landscape account?  I don't have one - call it a personal privacy consideration - can't test. sorry.

You can just install any ubuntu (desktop or server flavor) into any VM, install ssh or ssh-server and play with ssh as much as you like between any two systems.
ssh is one of the top 5 things to know on computers.  [https://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-sshhas](https://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-sshhas) a small list of things ssh allows.

sorry de link not working 

No it doesn't work tried everything in vmware, different login and pass are used but doesn't work

---

### Post by TheFu on 2021-05-03
> The Ubuntu Cloud image can be run on your personal Ubuntu Cloud, or on public clouds that provide Ubuntu Certified Images. 
That seems to be true.  [https://stackoverflow.com/questions/29137679/login-credentials-of-ubuntu-cloud-server-image](https://stackoverflow.com/questions/29137679/login-credentials-of-ubuntu-cloud-server-image) has a solution. Appears that setting the login credentials is expected by the cloud provider.  For someone new trying to run that image on their local VM, it will be too hard.

Just do a normal 20.04 Ubuntu  or Xubuntu install, then do these things:
```
sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall
sudo apt install ssh fail2ban
```
Those commands will get you fully patched, some proprietary drivers loaded, then  install and activate the ssh-server daemon.  Probably need to reboot the system for any new kernel updates to be used.  Once a week, run the first 2 commands to stay patched.

From a different system, you can use ssh or putty or any ssh client to connect by IP address to your username/password created as part of the install process.
From a Unix client, you'll probably want to run **ssh-keygen** and **ssh-copy-id** to create then push ssh keys to the other system for key-based authentication.  Life is much better that way.  Doing something similar is possible from Windows, but harder because the shell sorta ... just sucks.

Which link doesn't work?  My blog only blocks subnets where someone attacked first. Right now, 6951 subnets are blocked. If your subnet is on one of those, I'm sorry. Maybe google's cache or the *wayback machine* would work?  Also, my web servers only support TLS 1.3, so clients on v1.2 and earlier don't work.  The TLS change drastically reduced (100x fewer) the number of attacks from 1 specific country.

---

### Post by pcfreak492 on 2021-05-11
I get the following messages


16 packages can be upgraded. Run 'apt list --upgradable' to see them.
tim @ ubuntu: ~ $ sudo apt full upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
tim @ ubuntu: ~ $ sudo ubuntu-drivers autoinstall
sudo: ubuntu-drivers: command not found

---

### Post by deadflowr on 2021-05-11
Run the command from the error message:
```
sudo dpkg --configure -a
```

---

### Post by TheFu on 2021-05-11
> **pcfreak492 said:**
> I get the following messages


16 packages can be upgraded. Run 'apt list --upgradable' to see them.
tim @ ubuntu: ~ $ sudo apt full upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
tim @ ubuntu: ~ $ sudo ubuntu-drivers autoinstall
sudo: ubuntu-drivers: command not found


**sudo apt full upgrade** is NOT the command. Use the correct one.
**sudo ubuntu-drivers autoinstall** works here on 20.04 and 18.04. I suspect the vmdk file is pre-customized for typical VMware ESXi hardware.

However, regardless, when someone posts commands with a clear order to them, stop doing anything if one of them fails.  DO NOT ATTEMPT THE NEXT COMMAND!  Bad things can happen.  In this situation, I doubt anything bad happened, but I've never touched the version you are using.

Hopefully, someone else with experience for the exact vmdk will reply.

Is there a reason you don't just get a desktop or server ISO and install that? Installs are 10-15 minutes of effort into a VM.  I'm confused what lead to picking the vmdk file?

---

### Post by pcfreak492 on 2021-05-12
> **TheFu said:**
> **sudo apt full upgrade** is NOT the command. Use the correct one.
**sudo ubuntu-drivers autoinstall** works here on 20.04 and 18.04. I suspect the vmdk file is pre-customized for typical VMware ESXi hardware.

However, regardless, when someone posts commands with a clear order to them, stop doing anything if one of them fails.  DO NOT ATTEMPT THE NEXT COMMAND!  Bad things can happen.  In this situation, I doubt anything bad happened, but I've never touched the version you are using.

Hopefully, someone else with experience for the exact vmdk will reply.

Is there a reason you don't just get a desktop or server ISO and install that? Installs are 10-15 minutes of effort into a VM.  I'm confused what lead to picking the vmdk file?


yes i downloaded an iso image from [http://old-releases.ubuntu.com/releases/bionic/](http://old-releases.ubuntu.com/releases/bionic/) that would be the same according to the version, this version I use but the other version [https://cloud-images.ubuntu.com/bionic/](https://cloud-images.ubuntu.com/bionic/) is directly open ssh you don't know login password not, anyone knows why

---

### Post by TheFu on 2021-05-12
There is a checkbox during install to include an ssh-server.  Check that.  That's the end of the "configuration" effort to get it working.  That doesn't mean you shouldn't harden ssh a little more and prevent 99% of the world from connecting, but that can come later.

The Server or Desktop install takes 10 minutes.

Sorry that nobody who knows something about the way you want to use a vmdk version it has responded.  This is the first thread I've ever seen about this type of release.

---

### Post by CharlesA on 2021-05-12
> **TheFu said:**
> There is a checkbox during install to include an ssh-server.  Check that.  That's the end of the "configuration" effort to get it working.  That doesn't mean you shouldn't harden ssh a little more and prevent 99% of the world from connecting, but that can come later.

The Server or Desktop install takes 10 minutes.

Sorry that nobody who knows something about the way you want to use a vmdk version it has responded.  This is the first thread I've ever seen about this type of release.

I think another difference between the cloud vmdk and the version installed via iso is that the vmdk includes the cloud-init package on the assumption the hosting provider would hook into it to set up the SSH keys and other configuration.

But in real life, that isn't a big difference unless you need to deploy a few instances with the same config. If it's a one-off, you can just do it manually.

---

### Post by TheFu on 2021-05-12
I've been purging the cloud-init packages from my server installs a few years. 
```
$ dpkg -l 'cloud*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  cloud-guest-ut 0.30-0ubuntu all          cloud guest utilities
ii  cloud-init     21.1-19-gbad all          Init scripts for cloud instances
ii  cloud-initramf 0.40ubuntu1. all          copy initramfs modules into root 
ii  cloud-initramf 0.40ubuntu1. all          write a network interface file in
un  cloud-utils    <none>       <none>       (no description available)
```

These were purged previously, but Canonical started forcing them through dependencies.  My 2 other servers don't have them, so I don't know which dependencies force them. Regardless, they ARE in the normal Ubuntu Server ISO.

---

### Post by CharlesA on 2021-05-12
> **TheFu said:**
> I've been purging the cloud-init packages from my server installs a few years. 
```
$ dpkg -l 'cloud*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  cloud-guest-ut 0.30-0ubuntu all          cloud guest utilities
ii  cloud-init     21.1-19-gbad all          Init scripts for cloud instances
ii  cloud-initramf 0.40ubuntu1. all          copy initramfs modules into root 
ii  cloud-initramf 0.40ubuntu1. all          write a network interface file in
un  cloud-utils    <none>       <none>       (no description available)
```

These were purged previously, but Canonical started forcing them through dependencies.  My 2 other servers don't have them, so I don't know which dependencies force them. Regardless, they ARE in the normal Ubuntu Server ISO.

Good catch! I checked my 18.04 box that's hosting some production stuff and I didn't see any cloud-init stuff. I haven't used any of the newer versions though.

---

### Post by sergiots on 2022-03-17
Working for me with similar problem.
Thanks!

---


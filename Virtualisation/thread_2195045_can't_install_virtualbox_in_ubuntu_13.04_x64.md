---
title: "can't install virtualbox in ubuntu 13.04 x64"
date: 2013-12-22
forum: Virtualisation
---

### Post by colormyth on 2013-12-22
Hello, 

I am a beginner and I installed virtual box 4.3.6, i have read in other posts but i can't find the solution.

After that i have installed "[COLOR=#FF0000][FONT=sans-serif]sudo apt-get install dkms[/FONT][/COLOR]" - and is all ok i use root user.

Then when i try to sutup the virtual box modules sudo /etc/init.d/vboxdrv setup :

```
sudo /etc/init.d/vboxdrv setupStopping VirtualBox kernel moduleslibkmod: ERROR ../libkmod/libkmod-module.c:1567 kmod_module_new_from_loaded: could not open /proc/modules: No such file or directory
Error: could not get list of modules: No such file or directory
libkmod: ERROR ../libkmod/libkmod-module.c:1567 kmod_module_new_from_loaded: could not open /proc/modules: No such file or directory
Error: could not get list of modules: No such file or directory
libkmod: ERROR ../libkmod/libkmod-module.c:1567 kmod_module_new_from_loaded: could not open /proc/modules: No such file or directory
Error: could not get list of modules: No such file or directory
 ...done.
Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMSError! Your kernel headers for kernel 3.10.23-xxxx-grs-ipv6-64 cannot be found.
Please install the linux-headers-3.10.23-xxxx-grs-ipv6-64 package,
or use the --kernelsourcedir option to tell DKMS where it's located
 ...failed!
  (Failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)



```

in /var/log/vbox-install.log there is:

```
Uninstalling modules from DKMS  removing old DKMS module vboxhost version  4.3.6


------------------------------
Deleting module version: 4.3.6
completely from the DKMS tree.
------------------------------
Done.
Attempting to install using DKMS


Creating symlink /var/lib/dkms/vboxhost/4.3.6/source ->
                 /usr/src/vboxhost-4.3.6


DKMS: add completed.
Failed to install using DKMS, attempting to install without
Makefile:183: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.

```

Kernel is installed and updated.

How can i fix this? Thank you.

---

### Post by QIII on 2013-12-22
VirtualBox should be very easy to install in Ubuntu.

Could you post a url to the instructions you followed?

---

### Post by Bucky Ball on 2013-12-22
*Thread moved to **Virtualisation**.*

Just wondering why you didn't install from Software Centre?

---

### Post by colormyth on 2013-12-22
If i install it from Software Centre there is the same issue. The virtual machine won't start!

Here are the instructions: [http://www.howopensource.com/2013/04/install-virtualbox-ubuntu-ppa/](http://www.howopensource.com/2013/04/install-virtualbox-ubuntu-ppa/)

---

### Post by QIII on 2013-12-22
OK.  Let's take a step back.

When you installed from the Software Centre, it installed correctly?

---

### Post by colormyth on 2013-12-22
Yes the installation is made in both cases. But when i try to start a created virtual machine it gave me [http://thenubbyadmin.com/wp-content/uploads/2011/02/SecondError.png](http://thenubbyadmin.com/wp-content/uploads/2011/02/SecondError.png)

---

### Post by Bucky Ball on 2013-12-22
So you have Virtualbox installed fine, you just can't get a *virtual machine* running? I think we helpers are a little confused here. ;) :-k

---

### Post by QIII on 2013-12-22
Could you post the results of 

```
uname -r
```

please?

---

### Post by monkeybrain20122 on 2013-12-22
Just run the command in the error message

sudo /etc/init.d/vboxdrv setup

---

### Post by colormyth on 2013-12-22
So... virtual box was installed, but i think that some modules were not configured properly.
Such that, i can configure a virtual machine, but when i hit "start" it gives me [http://thenubbyadmin.com/wp-content/uploads/2011/02/SecondError.png](http://thenubbyadmin.com/wp-content/uploads/2011/02/SecondError.png)

then i tried that command and the output is in the first post!

---

### Post by monkeybrain20122 on 2013-12-22
Just run the command in the error message

```
sudo /etc/init.d/vboxdrv setup
```

For some reasons it needs to rebuild the vbox kernel module.

---

### Post by colormyth on 2013-12-22
root@ns3361674:~# uname -r
3.10.23-xxxx-grs-ipv6-64

---

### Post by colormyth on 2013-12-22
> **monkeybrain20122 said:**
> Just run the command in the error message

```
sudo /etc/init.d/vboxdrv setup
```

For some reasons it needs to rebuild the vbox kernel module.

The output of "sudo /etc/init.d/vboxdrv setup" is in the first post.

---

### Post by QIII on 2013-12-22
Take a look at the first group of code you posted, and you'll see this:

```
Please install the linux-headers-3.10.23-xxxx-grs-ipv6-64 package,
```


The headers have to be installed for dkms to do the build.  It doesn't look like you are using the kernel that comes OOTB with 13.04.  Did you update using a PPA or something.

---

### Post by monkeybrain20122 on 2013-12-22
This is a custom kernel.

[https://www.centos.org/forums/viewtopic.php?t=13458](https://www.centos.org/forums/viewtopic.php?t=13458)

Same issue in this thread(they give no solution other than to ask the people who provide the kernel)

---

### Post by colormyth on 2013-12-22
Oh God! You are right monkeybrain, this is a dedicated server from OVH too... so they modified the kernel...

@QIII I tried this but no luck:

```
root@ns3361674:~# apt-get install linux-headers-$(uname -r)Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-headers-3.10.23-xxxx-grs-ipv6-64
E: Couldn't find any package by regex 'linux-headers-3.10.23-xxxx-grs-ipv6-64'
root@ns3361674:~#



```

I think i can't update this kernel with a good one?!

---

### Post by monkeybrain20122 on 2013-12-22
You can install as many kernels as you want and choose among them at boot. If you install a "normal" kernel it will just be alongside your custom one instead of 'upgrading" it. So you can log into it a use vbox there.

---

### Post by QIII on 2013-12-22
That custom kernel and its headers will not be in Canonical's repos, so you won't find it there.

Without the headers, the module can't be built.

The version of VirtualBox from both the repo and the .deb file from VirtualBox.org are built with the assumption that the kernel you are building to is available.

So, +1 to monkybrain20122's suggestion.

Edit:  I also see that you are running as root instead of using sudo.  Why are you doing that?  Are you in recovery mode?

---

### Post by Bucky Ball on 2013-12-22
> **QIII said:**
> 

Edit:  I also see that you are running as root instead of using sudo.  Why are you doing that?  Are you in recovery mode?

Indeed. Avoid that unless you have good reason to be in as root or you risk serious breakage ...

Just use 'sudo' whenever possible.

---

### Post by monkeybrain20122 on 2013-12-22
BTW, to show the grub menu at boot so that you can choose the kernel to boot into, hold the "shift" key at boot.

---

### Post by colormyth on 2013-12-22
Ohhhh! In the end i solved it with your help.


I didn't know that is a custom kernel by OVH!! So i have installed a new kernel and updated the GRUB such that it will start with the new one.
Thank you guys so much for your help!! 

And thank you for that root observation, in future i will take care!!! 
[COLOR=#333333]
[/COLOR]

---


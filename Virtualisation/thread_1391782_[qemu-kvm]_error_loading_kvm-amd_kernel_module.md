---
title: "[qemu-kvm] error loading kvm-amd kernel module"
date: 2010-01-27
forum: Virtualisation
---

### Post by drawita on 2010-01-27
Hi,

I'm new to QEMU/KVM, and tries to install 'qemv-kvm' apt package on my 32bit Ubuntu 9.10 system (with CPU of AM3 X4 945) but encounter errors while loading 'kvm_amd' module.

Here's the installation process:

# apt-get install qemu-kvm
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sendmail-base procmail sensible-mda sendmail-cf
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  bridge-utils
Suggested packages:
  ubuntu-vm-builder kvm-pxe uml-utilities qemu-kvm-extras
The following NEW packages will be installed:
  bridge-utils qemu-kvm
0 upgraded, 2 newly installed, 0 to remove and 153 not upgraded.
Need to get 2,624kB of archives.After this operation, 7,614kB of additional disk space will be used.Do you want to continue [Y/n]?Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main bridge-utils 1.4-5 [31.6kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main qemu-kvm 0.11.0-0ubuntu6.3 [2,592kB]
Fetched 2,624kB in 10s (253kB/s)
Selecting previously deselected package bridge-utils.
(Reading database ... 117230 files and directories currently installed.)
Unpacking bridge-utils (from .../bridge-utils_1.4-5_i386.deb) ...
Selecting previously deselected package qemu-kvm.
Unpacking qemu-kvm (from .../qemu-kvm_0.11.0-0ubuntu6.3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for sreadahead ...
sreadahead will be reprofiled on next reboot
Setting up bridge-utils (1.4-5) ...
Setting up qemu-kvm (0.11.0-0ubuntu6.3) ...
update-rc.d: warning: qemu-kvm stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
 * Loading kvm module kvm_amd
FATAL: Error inserting kvm_amd (/lib/modules/2.6.31-17-generic-pae/kernel/arch/x86/kvm/kvm-amd.ko): Operation not supported
   ...fail!
invoke-rc.d: initscript qemu-kvm, action "start" failed.


# apt-show-versions qemu-kvm
qemu-kvm/karmic-updates uptodate 0.11.0-0ubuntu6.3

# apt-show-versions virtualbox-3.1
virtualbox-3.1/karmic uptodate 3.1.2-56127_Ubuntu_karmic

# uname -varnm
Linux duck 2.6.31-17-generic-pae #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 i686 GNU/Linux

 
Notice that I do have VirtualBox installed ok on my system.  I noticed from some other forum that the kvm module for VirtualBox is incompatible with qemu/kvm's, but don't know how to fix it.  

Any hint on how to fix the error here?

---

### Post by bodhi.zazen on 2010-01-27
KVM and Virtualbox conflict with each other.

So as far as I know, you can run one or the other, but not both.

You can remove the virtualbox kernel module with rmmod and you will likely be able to install KVM.

If you are not comfortable with manually changing kernel modules, probably better to stay with one or the other.

There are a number of discussions on the topic, here is one:

[http://forums.virtualbox.org/viewtopic.php?f=7&t=15720](http://forums.virtualbox.org/viewtopic.php?f=7&t=15720)

---

### Post by nandakishore.ms on 2011-04-20
E:Package qemu-kvm does not have installation candidate
can anyone please help me how to fix the bug
thank  so much

---

### Post by bodhi.zazen on 2011-04-20
What version of Ubuntu are you using and what repositories have you enabled ?

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kvm&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kvm&searchon=name&subword=1&version=all&release=all)

---


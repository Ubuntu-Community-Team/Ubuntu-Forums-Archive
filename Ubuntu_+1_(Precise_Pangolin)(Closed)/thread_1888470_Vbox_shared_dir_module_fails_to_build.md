---
title: "Vbox shared dir module fails to build"
date: 2011-11-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by TerryNewton on 2011-11-29
After the 3.2.0-2 kernel update, the VirtualBox (4.1.6) guest addition's shared folder support module fails to build. The other modules build OK. The install log provides the following clues...

[FONT="Courier New"][from /var/log/vboxadd-install.log]
/tmp/vbox.0/utils.c: In function ‘sf_init_inode’:
/tmp/vbox.0/utils.c:113:9: error: assignment of read-only member ‘i_nlink’
/tmp/vbox.0/utils.c:122:9: error: assignment of read-only member ‘i_nlink’
/tmp/vbox.0/utils.c:132:9: error: assignment of read-only member ‘i_nlink’
/tmp/vbox.0/utils.c: In function ‘sf_nlscpy’:
/tmp/vbox.0/utils.c:563:13: warning: passing argument 3 of ‘utf8_to_utf32’ from incompatible pointer type [enabled by default]
include/linux/nls.h:53:12: note: expected ‘unicode_t *’ but argument is of type ‘wchar_t *’
make[2]: *** [/tmp/vbox.0/utils.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxsf] Error 2
[/FONT]

Just a testing note for VB users.. probably an issue (or incompatibility) with Vbox, brand new kernel so likely will have to put up with it until Vbox catches up. In the mean time copy/paste still works and can set up a local-only FTP server on the host for doing file transfers (which is how I used to do it before figuring out how to do the shared folder thing).

---

### Post by effenberg0x0 on 2011-11-29
> **TerryNewton said:**
> After the 3.2.0-2 kernel update, the VirtualBox (4.1.6) guest addition's shared folder support module fails to build. The other modules build OK. The install log provides the following clues...

[FONT=Courier New][from /var/log/vboxadd-install.log]
/tmp/vbox.0/utils.c: In function &#8216;sf_init_inode&#8217;:
/tmp/vbox.0/utils.c:113:9: error: assignment of read-only member &#8216;i_nlink&#8217;
/tmp/vbox.0/utils.c:122:9: error: assignment of read-only member &#8216;i_nlink&#8217;
/tmp/vbox.0/utils.c:132:9: error: assignment of read-only member &#8216;i_nlink&#8217;
/tmp/vbox.0/utils.c: In function &#8216;sf_nlscpy&#8217;:
/tmp/vbox.0/utils.c:563:13: warning: passing argument 3 of &#8216;utf8_to_utf32&#8217; from incompatible pointer type [enabled by default]
include/linux/nls.h:53:12: note: expected &#8216;unicode_t *&#8217; but argument is of type &#8216;wchar_t *&#8217;
make[2]: *** [/tmp/vbox.0/utils.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxsf] Error 2
[/FONT]

Just a testing note for VB users.. probably an issue (or incompatibility) with Vbox, brand new kernel so likely will have to put up with it until Vbox catches up. In the mean time copy/paste still works and can set up a local-only FTP server on the host for doing file transfers (which is how I used to do it before figuring out how to do the shared folder thing).

I'm running VirtuBox (From Oracle site, not from the repos) with 3.2.0-2 normally. Were you manually building the kernel modules or that was the output when dkms was auto-building it? 
Have you tried to sudo apt-get install --reinstall virtualbox-dkms virtualbox-guest-dkms  (or use virtualbox-ose-dkms and virtualbox-ose-guest-dkms depending on what you are running)?

[B]EDIT:
[/B]I was expecting a build error with iommu.c/.h with VirtualBox in this kernel, probably in vboxpci.c. It seems there's no mention to it?

---

### Post by TerryNewton on 2011-11-29
> **effenberg0x0 said:**
> I'm running VirtuBox (From Oracle site, not from the repos) with 3.2.0-2 normally. Were you manually building the kernel modules or that was the output when dkms was auto-building it? 
Have you tried to sudo apt-get install --reinstall virtualbox-dkms virtualbox-guest-dkms  (or use virtualbox-ose-dkms and virtualbox-ose-guest-dkms depending on what you are running)?

[B]EDIT:
[/B]I was expecting a build error with iommu.c/.h with VirtualBox in this kernel, probably in vboxpci.c. It seems there's no mention to it?

To clarify, 12.04 is running inside VirtualBox as a guest so I can work out traditional desktop strategies and all that stuff, my production system is 10.04 and will remain that way until I'm brave enough to actually upgrade, many months from now. Running under VirtualBox isn't much good for actual bug testing but works great for overall functionality testing without risk.

Anyway, whenever the kernel gets upgraded I have to re-install the guest additions using a Vbox menu option that mounts a virtual CD and causes a prompt to pop up where I select the autorun option, give it my password then it rebuilds the kernel modules (build-essential, headers, etc have to be installed for that to work). The bug regarding iommu.c when installing Vbox on a 3.2 kernel host has already been reported and AFAIK patched or fixed. Usually installing the guest additions (at least in Ubuntu) is fairly painless and routine, but it doesn't like the new kernel so when that happens either have to put up with it until VB fixes it, or roll stuff back.

In my case I've already worked around the file transfer issue by installing proftpd-basic on my host, creating a directory in my home dir and editing /etc/proftpd/proftpd.conf to add these lines...

[FONT="Courier New"]#restrict ftp usage to a specific directory
DefaultRoot /home/username/ftpfiles
ServerIdent On "Internal FTP server"
[/FONT]

...of course edited to point to the dir I made... then used ifconfig to show my ethernet address, started proftpd then used gFTP in the virtual 12.04 to connect. So I'll do it that way until VBox fixes their driver.
I mainly use this to copy my notes, scripts and any other files I need to transfer between the virtual machine and my host system, not as convenient as the shared folder but works.

---

### Post by thushw on 2011-12-05
This can be overcome by modifying utils.c file to use the set_nlink function instead of setting the i_link directly.

---

### Post by TerryNewton on 2011-12-06
> **thushw said:**
> This can be overcome by modifying utils.c file to use the set_nlink function instead of setting the i_link directly.

It is my understanding that the next VirtualBox version will fix the problem. Can work around the shared folders module (using FTP) but it also blocks the building of the openGL module, so no Unity 3D or Gnome Shell. So.. until the fixed VirtualBox comes out I temporarily removed the linux image and header metapackages and went back to the 3.1 kernel, which works fine for me and avoids having to build the VB dev code from source. Fortunately I installed my 12.04 while kernel 3.1 was available...

---

### Post by TerryNewton on 2011-12-06
Ok, got it working with the current kernel...

Installed virtualbox-guest-source and virtualbox-guest-utils from repos
Edited /usr/src/vboxguest-4.1.6/vboxsf/utils.c and replaced 3 instances of...
inode->i_nlink = 1;
...with...
set_nlink(inode, 1);
(not compatible with kernel < 3.2 so real fix needs to be conditional)
Reinstalled the 3.2 kernels I removed (linux-generic and linux-headers-generic)
Rebooted into kernel 3.2
In the directory /usr/src/vboxguest-4.1.6 did..
sudo make
sudo make install
Rebooted, all seems well now. Thanks thushw for the tip.

---

### Post by sergiomb on 2011-12-10
> **TerryNewton said:**
> 
Edited /usr/src/vboxguest-4.1.6/vboxsf/utils.c and replaced 3 instances of...
inode->i_nlink = 1;
...with...
set_nlink(inode, 1);
(not compatible with kernel < 3.2 so real fix needs to be conditional)

upsteam solution is here : 
[https://www.virtualbox.org/changeset/39224](https://www.virtualbox.org/changeset/39224)

---

### Post by TerryNewton on 2011-12-10
Cool, that pretty much confirms the fix will be in the next release and in the mean time it's not difficult to fix the issue manually, so solved.

---


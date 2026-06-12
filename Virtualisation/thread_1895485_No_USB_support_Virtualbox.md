---
title: "No USB support Virtualbox"
date: 2011-12-14
forum: Virtualisation
---

### Post by chairfootstool on 2011-12-14
Hello. I am running Virtualbox 4.1.6 (Ubuntu 11.10 as host and Ubuntu 10.04 as the guest). Attempting to get Virtualbox to recognize my USB drive I installed the Virtualbox extension pack. However, I still do not have a 'vboxusers' group.

So, I tried un-installing and re-installing Virtualbox and re-added the extension pack. Still no 'vboxusers' group. Finally, I tried forcing things, and manually added a 'vboxusers' group from the command line and added myself to it.  Still, though, I get the following error:

[CENTER][I]Failed to access the USB subsystem.

Virtual box is not currently allowed to access USB devices You can change this by adding your user to the '**vboxusers**' group...

[/I][LEFT]Is there something obvious that I am missing, and, if not, is there some workaround?
Thanks.
[/LEFT]
[/CENTER]

---

### Post by ofnuts on 2011-12-15
> **chairfootstool said:**
> Hello. I am running Virtualbox 4.1.6 (Ubuntu 11.10 as host and Ubuntu 10.04 as the guest). Attempting to get Virtualbox to recognize my USB drive I installed the Virtualbox extension pack. However, I still do not have a 'vboxusers' group.

So, I tried un-installing and re-installing Virtualbox and re-added the extension pack. Still no 'vboxusers' group. Finally, I tried forcing things, and manually added a 'vboxusers' group from the command line and added myself to it.  Still, though, I get the following error:

[CENTER][I]Failed to access the USB subsystem.

Virtual box is not currently allowed to access USB devices You can change this by adding your user to the '**vboxusers**' group...

[/I][LEFT]Is there something obvious that I am missing, and, if not, is there some workaround?
Thanks.
[/LEFT]
[/CENTER]
Which version of VB are you using? IIRC there is no USB support in the Open Source edition (aka OSE).

---

### Post by haqking on 2011-12-15
it is just a user group, you can create it yourself and put yourself into it.
```

sudo usermod -a -G vboxusers username 
```

where username is your username obviously to put into the group

and you need to restart or log out and back in to refresh your groups membership

---

### Post by chairfootstool on 2011-12-15
[LEFT]Thanks for the help. Actually, I got USB support (it was no longer greyed out), but I had to open VirtualBox as root user (not a great solution). So, I was wondering:

[CENTER]What could be the permissions problem that such the group 'vboxusers' does not exist when running everything as a normal user?

[LEFT]Thanks again.
[/LEFT]
[/CENTER]
[/LEFT]

---

### Post by haqking on 2011-12-15
> **chairfootstool said:**
> [LEFT]Thanks for the help. Actually, I got USB support (it was no longer greyed out), but I had to open VirtualBox as root user (not a great solution). So, I was wondering:

[CENTER]What could be the permissions problem that such the group 'vboxusers' does not exist when running everything as a normal user?

[LEFT]Thanks again.
[/LEFT]
[/CENTER]
[/LEFT]

does not exist ? it either exists or not whether using root or not.

If it doesnt exist then create it and log back in.

Whatever happended along the line, reinstall if you need to and create the group manually and reboot for group membership to take effect

---

### Post by chairfootstool on 2011-12-15
Yeah, thanks. I realize I should have been more careful with what I said. When I run Virtualbox as root user, everything works great. However, when I turn off everything (virtual machine and Virtualbox) and restart Virtualbox without elevated permissions, I now no longer have permissions to even run the virtual machine. So I go into wherever the directory is and *chmod* things so that I now have permissions to open the virtual machine. 

Then, I click on settings to check out what USB filters I have, and I get the error that VirtualBox has failed to access the USB subsystem. It seems that there must be a permissions problem somewhere down the line. I was wondering if there were some ideas on what it could be? 

Also, to haqking:
I tried your method of manually creating and then adding myself to the vboxusers group without success. Also, I tried un-installing and re-installing VMware, but that did not get rid of the "VirtualBox has failed to access the USB system" error.

---

### Post by haqking on 2011-12-15
> **chairfootstool said:**
> Yeah, thanks. I realize I should have been more careful with what I said. When I run Virtualbox as root user, everything works great. However, when I turn off everything (virtual machine and Virtualbox) and restart Virtualbox without elevated permissions, I now no longer have permissions to even run the virtual machine. So I go into wherever the directory is and *chmod* things so that I now have permissions to open the virtual machine. 

Then, I click on settings to check out what USB filters I have, and I get the error that VirtualBox has failed to access the USB subsystem. It seems that there must be a permissions problem somewhere down the line. I was wondering if there were some ideas on what it could be? 

Also, to haqking:
I tried your method of manually creating and then adding myself to the vboxusers group without success. Also, I tried un-installing and re-installing VMware, but that did not get rid of the "VirtualBox has failed to access the USB system" error.

Did you install and create the VM as root ?

If i was you i would purge it all.  Make sure you download the correct version and not from the repos, either from oracle site or virtual box website, and install extensions pack.

Then build your machine as normal user and not as root.

---

### Post by chairfootstool on 2011-12-15
> **haqking said:**
> Did you install and create the VM as root ?

If i was you i would purge it all.  Make sure you download the correct version and not from the oracle website, and install extensions pack.

Then build your machine as normal user and not as root.


Ah, well. I was hoping it would not come to re-installing the VM, but better to be safe than sorry. Thanks again for all the help. It did not cross my mind that installing the VM as root would have caused all this to happen.

---

### Post by JKyleOKC on 2011-12-15
Just FYI, VirtualBox installs its configuration files (including all of the VMs created) in the home directory of the user who installs it. Before version 4.0, they were put into a hidden subdirectory named ".VirtualBox" but with 4.0 the definitions were split between that directory and another, visible, one still in the user's $HOME. By installing it as root, you put everything in an area that's not accessible to a normal user.

Getting the packages from Oracle's download site is, IMO, preferable to using the repository. Versions in the repository don't always get updated rapidly. The Oracle site has instructions on adding it to your repository list so that Update Manager can handle it. This is the sole exception I've found, so far, to the general rule that using the official repository is preferable!

---


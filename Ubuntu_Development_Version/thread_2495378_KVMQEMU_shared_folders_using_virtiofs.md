---
title: "KVM/QEMU shared folders using virtiofs"
date: 2024-02-16
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2024-02-16
In Jammy I have used shared folders using virtiofs for some time now without a problem using the method shown in [https://www.debugpoint.com/share-folder-virt-manager/](https://www.debugpoint.com/share-folder-virt-manager/).
On trying the same method in a Noble host, ie, adding a virtiofs filesystem using the details display of virt-manager I at first found that it was not possible as no virtiofsd was found to be available.
A quick search found that virtiofsd is now a separate package in Noble and must be installed before sharing is possible.  Previous Ubuntu versions have not offered a separate package for this and sharing was possible without any extra packages being needed, so there has obviously been a change in the requirements for this sharing between host and guest.

The system works faultlessly again now virtiofsd is installed in the Noble host Xubuntu 24.04.

---

### Post by MAFoElffen on 2024-02-17
Oh Dang. It has always been touchy in previous versions to get to work. I know you have helped many users in the Virtualization Section on getting that working for them.

This new change in the 'one-more-step' for Noble support will be something to remember for that after it is released. Thank you for sharing that change. 

So this is really a "Solved"? Or maybe we should file a Bug Report so that package is a 'default depends', brought in automatically installed with the KVM packages??? So that way, it isn't really a change for the KVM Users of Noble... If it was brought in automatically before, then that would be the thing to do now to make it the same as previous, right? 

Then installing it separately in the meantime is a good work-around to get it working until that is done. What is the package name of that?

Just thinking out loud.

---

### Post by ajgreeny on 2024-02-17
Yes, it's a pain in the neck and as you say another step to trip up users of KVM who want to share with the host.

I have not looked at the intermediate versions between 22.04 and 24.04 to know if the situation is the same in those, but in 22.04 **virtiofsd** is not even available as a separate package as far as I can ascertain; it's certainly not in the normal repos of 22.04.

So where do we go from here? I'm not sure, but it would make life much easier if this all worked after simply installing virt-manager and all it's dependencies as it has done in the past.
If you believe it makes sense to file a bug report and ask that **virtiofsd** is made a dependency of **virt-manager** I can easily do so.

Interestingly in the Debian-sid that I am using at this moment I see that virtiofsd is also available as a separate package, so maybe that is why it is also separate in Noble.
I will shortly boot back into my Jammy 22.04 main system and see what else I can find about the package and whethtr it is one of the many files included when virt-manager is installed.

Watch this space!

---

### Post by ajgreeny on 2024-02-17
I have spent some time searching in my jammy 22.04 install for the source package that supplies virtiofsd and can not find anything useful.
It must be one of the many things that arrives when installing some package of the KVM/QEMU system but searching every way that I can think of has found nothing.

Any ideas?

---

### Post by MAFoElffen on 2024-02-18
It lloks like it appeared as separate in Mantic.

In the changelog,:
> 
Instead of Breaking/Replacing qemu-system-common <8.0, add dpkg diversion
    for /usr/share/qemu/vhost-user/50-qemu-virtiofsd.json.
    To be removed in bookworm+2 when qemu is definitely >=8.0
    (bookworm has 7.2).

Because of this:
> 
 Initial package (Closes: #1007152)

^^^ I don't see this issue or bug anywhere...

I think I remember something about some applications reporting that virtiofs needed to be installed and how that was worded confusing that with replacing the virtiofs daemon from QEMU... Or "something" like that. It's a little foggy.

But logically, if that were true, then it should still be pulled in automatically with KVM and/or virt-manager. At least that is what I am thinking would be how it should work to match what was done previously.

---

### Post by ajgreeny on 2024-02-18
Rightly or wrongly I have filed a bug [https://bugs.launchpad.net/ubuntu/+bug/2054222](https://bugs.launchpad.net/ubuntu/+bug/2054222) which hopefully will bring this to the attention of others.
I could not file the bug against **virtiofsd** as launchpad just says that it is not a package in 24.04 so for now it is left as an "I do not know" in the package area. Perhaps it should have been listed against **virt-manager**?

We now wait to see if this goes any further

---

### Post by MAFoElffen on 2024-02-19
Joined it as affected, to bump it into being confirmed. Added comment.

---


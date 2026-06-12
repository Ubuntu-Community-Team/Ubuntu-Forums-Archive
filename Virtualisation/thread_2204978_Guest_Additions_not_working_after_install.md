---
title: "Guest Additions not working after install"
date: 2014-02-11
forum: Virtualisation
---

### Post by brucezepplin on 2014-02-11
Hi I am running a Windows 7 host, with ubuntu guest. I have mounted the guest additions .iso onto the ubuntu guest and ran

```
sudo sh ./VBoxLinuxAdditions.run
```

which worked fine, and was then under the impression that by restarting the virtual machine Guest Additions automatically kicks in. This is not the case and I am without the use of a mouse within the guest, with only keyboard access working.

Anyone have any suggestions? Is there something else I am required to do after running ./VBoxLinuxAdditions.run?

Thanks very much.

---

### Post by slickymaster on 2014-02-11
Your Guest Additions might not be installed properly. What you can try is to access a root shell (if you don't know how to achieve this, just follow [this tutorial]("http://askubuntu.com/questions/92556/how-do-i-boot-into-a-root-shell")) and from there run the following commands:

```
mount /dev/cdrom /mnt 
cd /mnt
./VBoxLinuxAdditions.run
reboot
```

---

### Post by jdeca57 on 2014-02-11
I see that your tag mentions Virtualbox 3.0 but is that correct? I mean, Oracle has maintenance releases but the most recent Virtualbox is 4.3.6 and your problem might be solved using the most recent version of the software.
I have Ubuntu 13.10 working here under VB 4.3.6 but what I also did before installing the additions was add the build-essential and dkms to the software.
Afterwards, the best test is to maximize the window the VM runs in. If it adjusts, all went well.
By the way, the mouse should work with or without guest additions. If my first remark is correct then simply uninstall your version and install the latest Virtualbox.

---

### Post by slickymaster on 2014-02-13
@brucezepplin

In case you haven't fixed it yet, the problem is that the actual VBoxGuestAdditions version, currently 4.3.6, doesn't recognize the latest release of X.Org Server, which is now 1.15, so they fail to install. 

The workaround is to use the pre-release VBoxGuestAdditions 4.3.7, already available [here]("https://www.virtualbox.org/download/testcase/VBoxGuestAdditions_4.3.7-92075.iso").

Let us know how it went.

---


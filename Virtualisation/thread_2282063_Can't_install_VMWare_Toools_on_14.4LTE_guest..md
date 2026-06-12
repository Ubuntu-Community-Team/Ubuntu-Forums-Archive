---
title: "Can't install VMWare Toools on 14.4LTE guest."
date: 2015-06-11
forum: Virtualisation
---

### Post by richard_baguley on 2015-06-11
Hey all, I am trying to install VMWare tools on a 14.04LTE guest OS (Windows 8 is the host, running using VMWare Player 7.1.0), but it isn't working. Specifically, I can't get the host folder sharing feature to work.

I followed the instructions here: [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1022525](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1022525), installing VMware tools version 9.9.2.

I have run the vmware-tools-install.pl file, which said it completed okay, but did produce an error partway through: "error 'struct dentry has no member named 'd_alias'"

This seemed to cause a number of other errors of similar type, but the script reported it had installed successfully. 

After rebooting, though,  I get nothing in the /mnt/hgfs folder, where the shared folder is supposed to mount. 

I'm out of my depth on this: the shared folder thing is the only feature of vmware tools I need


Any thoughts on what might be going wrong?

---

### Post by au10tic on 2015-06-11
i am in the same boat as you, from what i've read vmhgfs isnt compatible with some of the latest kernel releases, i was able to get that feature to work following the steps mentioned [here]("https://github.com/rasa/vmware-tools-patches") i cannot recall the error message i got on the output but the shared folder feature works and so does copy/paste and drag and drop from guest to host [running vmware workstation 11.1.0 build-2496824 on win8.1 64bit] hope that helps. 

As an alternative you can also browse your hosts file system via smb:// from the file explorer in ubuntu.

---

### Post by nlee2 on 2015-06-23
Just install open-vm-tools

[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2073803](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2073803)

**VMware support policy**

 
[LIST]
[*]VMware recommends using open-vm-tools redistributed by operating system vendors. 
[/LIST]

---


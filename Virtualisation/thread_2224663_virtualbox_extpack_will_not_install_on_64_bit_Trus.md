---
title: "virtualbox extpack will not install on 64 bit Trusty Tahr"
date: 2014-05-17
forum: Virtualisation
---

### Post by skiff-bp on 2014-05-17
I am running Ubuntu 64 bit 14.04 LTS on my old gateway laptop. I installed virtualbox from virtualbox-4.3_4.3.12-93733~Ubuntu~raring_amd64.deb and when i attempt to install the extension pack, I get the following error:

Failed to install the Extension Pack /home/brad/xfer_files/Oracle_VM_VirtualBox_Extension_Pack-4.3.12-93733.vbox-extpack.


The installer failed with exit code 1: VBoxExtPackHelperApp: error: The owner is not root: '/usr'.


Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ExtPackManager
Interface: IExtPackManager {3295e6ce-b051-47b2-9514-2c588bfe7554}

This is the same error regardless of how I install the extpack. I tried via sudo VBoxManage extpack install, gksudo virtualbox and selecting it from preferences, uninstalling everything and retry from a clean download. The same error every time. It still tells me the owner is not root ... however it IS.

Any help is appreciated. skiff-bp

---


---
title: "VMWARE CLIENT 4.4 on UBUNTU 16.04.2 LTS"
date: 2017-05-19
forum: Virtualisation
---

### Post by Nathaniel_Reyes on 2017-05-19
Hey everyone,
Just wanted to throw something out here on the forums so if anyone is having issues having their VMWARE HORIZON v4.4 client and smart cards working, this is what made it work for me on UBUNTU 16.04.2 LTS x64bit.

Things that you'll have to make sure that you have installed/build

1. pcsc-lite    [https://alioth.debian.org/frs/?group_id=30105&release_id=2049#pcsclite-_1.8.20-title-content](https://alioth.debian.org/frs/?group_id=30105&release_id=2049#pcsclite-_1.8.20-title-content)

2. pcsc-tools

3. the correct driver for your smart card reader (go to OEM website, download it, and then install/build)

4. Libffi     [https://packages.debian.org/wheezy/amd64/libffi5/download](https://packages.debian.org/wheezy/amd64/libffi5/download)

5. there are a couple others, but when you run the wizard for the VMWARE CLIENT, make sure that you run a "scan" at the end to show you what all you're missing.


Anyways, onward to the meat and potatoes on what I found to work. I followed this guide step by step but skipped when the author was creating links (I skipped that part since I had the packages needed for the install) and I have verified that it does work for me stable. Again, thought I'd share the knowledge since VMWARE HORIZON CLIENT doesn't officially support 16.04.2 LTS yet, but 14.x.x.

[https://techblog.jeppson.org/2015/12/configure-vmware-view-smartcard-in-ubuntu/](https://techblog.jeppson.org/2015/12/configure-vmware-view-smartcard-in-ubuntu/)

---

### Post by deadflowr on 2017-05-19
Moved to Virtualization

---


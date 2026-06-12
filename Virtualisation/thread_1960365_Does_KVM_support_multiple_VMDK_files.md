---
title: "Does KVM support multiple VMDK files?"
date: 2012-04-17
forum: Virtualisation
---

### Post by btindie on 2012-04-17
As the title suggests, does KVM/QEMU support multiple VMDK files? If it does how do you get it to use them :confused:

I've downloaded the mediawiki bitnami stack from [http://bitnami.org/stack/mediawiki](http://bitnami.org/stack/mediawiki) and that comes as multiple VMDK files.

```
bitnami-mediawiki-1.17.1-0-ubuntu-10.10-s001.vmdk
bitnami-mediawiki-1.17.1-0-ubuntu-10.10-s002.vmdk
bitnami-mediawiki-1.17.1-0-ubuntu-10.10-s003.vmdk
bitnami-mediawiki-1.17.1-0-ubuntu-10.10-s004.vmdk
bitnami-mediawiki-1.17.1-0-ubuntu-10.10-s005.vmdk
bitnami-mediawiki-1.17.1-0-ubuntu-10.10-s006.vmdk
bitnami-mediawiki-1.17.1-0-ubuntu-10.10-s007.vmdk
bitnami-mediawiki-1.17.1-0-ubuntu-10.10-s008.vmdk
bitnami-mediawiki-1.17.1-0-ubuntu-10.10-s009.vmdk
bitnami-mediawiki-1.17.1-0-ubuntu-10.10.vmdk
```

I've got it working by converting it to a single QCOW2 image with
```
qemu-img convert -O qcow2 bitnami-mediawiki-1.17.1-0-ubuntu-10.10-s00?.vmdk mediawiki.qcow2
```
but I'd rather leave it in VMDK format if at all possible...

Thanks.

---


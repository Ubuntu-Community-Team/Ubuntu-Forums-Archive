---
title: "LUKS encrypt multiple disks, one passphrase at boot"
date: 2009-07-08
forum: Security
---

### Post by sej7278 on 2009-07-08
I'm trying to get LUKS encryption working on 8.04 - so far I can encrypt a disk, and get it to ask for a passphrase at boot, mount the partition etc.

Eventually I want to have multiple drives encrypted (data, not boot disk) using the same passphrase. I do not want them all to be one big LVM, which is the obvious way to do it, I want separate disks with one partition on each, I'm not keen on using a keyfile stored on the 1st disk to unlock the 2nd either.

You can do this in Fedora - it passes the same passphrase to every LUKS key it finds.

I'm thinking of having a server that can boot without asking for a passphrase, but then you manually mount its data drives later over SSH - not automatically from GDM using your login password etc.

---

### Post by HermanAB on 2009-07-08
You'll have to make a little script.  There are some weird tricks to it though.  Have a look at my wizard Perl code to see how to do this.
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)

---


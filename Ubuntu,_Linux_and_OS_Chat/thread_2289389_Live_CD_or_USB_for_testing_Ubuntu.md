---
title: "Live CD or USB for testing Ubuntu"
date: 2015-08-03
forum: Ubuntu, Linux and OS Chat
---

### Post by saidbakr on 2015-08-03
**This post is just a feature request**. It meant by the live CD functionality which seems that it depends on creating a virtual drive on the System's RAM. This way, the user that needs to test Ubuntu from another OS, he/she could not able to make complete experience, due to the shutdown will lead to loss any data the user has  introduced during the session.

I suggest that the live CD able, as an option, to make some area of the hard-drive or the USB stick to work as a real and continuous storage. i.e something like the deprecated WUbi. It should allow the user to has a real experience with more and real improved performance through multiple session till he/she take the decision of migration to Ubuntu.

---

### Post by sudodus on 2015-08-03
I think the feature you request is already available.

Persistent live drives can store data files and installed program packages, but not install new kernels. If you create a file named **casper-rw** and create a linux file system inside it (typically ext2), it will be found automatically and used for persistence. It is even better to create a partition with the label **casper-rw**, it will be found automatically and used for persistence

1. With a USB boot drive you can have persistence in the boot drive itself.

2. With a CD/DVD boot disk you can have persistence in the internal drive or a USB pendrive or USB HDD.

3. You can install Ubuntu into a USB like it were into an internal HDD, and test 'everything' like a regular installed system.

Persistent live systems as well as installed systems depend a lot on the data transfer speed of the drive, so external drives with eSATA and USB3 are much better than drives with USB2.

See this link

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by saidbakr on 2015-08-03
Very good. Thank you very much!

---


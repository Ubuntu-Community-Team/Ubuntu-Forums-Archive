---
title: "Invalid Ubuntu Server 12.04 x64 LTS ISO file"
date: 2012-07-06
forum: Server Platforms
---

### Post by Andrey Bushman on 2012-07-06
Hi all.

I two times downloaded [this]("http://www.ubuntu.com/download/server/thank-you?distro=server&release=lts&bits=64") ISO file (Ubuntu Server 12.04 LTS), and tried to install it on VMware virtual machine. But I always got error:

[IMG]http://s2.ipicture.ru/uploads/20120706/yOSZn6t2.png[/IMG]

Fix [this]("http://www.ubuntu.com/download/server/thank-you?distro=server&release=lts&bits=64") ISO file, please.

Regards
______________________________
P.S. Sorry for my bad English.

---

### Post by trundlenut on 2012-07-06
This isn't really the best place to mention problems with the ubuntu website.

You could try downloading the image from a different mirror.

You should be able to find the MD5 checksum for the image, but I can't seem to find it on the ubuntu website.

---

### Post by kennethconn on 2012-07-06
The MD5 check as trundlenut mentioned.
 
Also, what is your installation media (hard drive, USB stick, DVD drive)? You may need to change that.

---

### Post by ajgreeny on 2012-07-06
> **trundlenut said:**
> This isn't really the best place to mention problems with the ubuntu website.

You could try downloading the image from a different mirror.

You should be able to find the MD5 checksum for the image, but I can't seem to find it on the ubuntu website.
The md5sum hashes are all at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes).

---

### Post by trundlenut on 2012-07-09
> **ajgreeny said:**
> The md5sum hashes are all at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes).

Ah ha, thank you.  I couldn't find them but I didn't spend long looking.  A link from the download page would be handy.

---

### Post by Cheesemill on 2012-07-09
Also if you download the ISO as a torrent you can be guaranteed that it's OK.

Torrent downloads check the hash of the file as it is downloading as part of the bittorrent specification.

---

### Post by CharlesA on 2012-07-09
> **Cheesemill said:**
> Also if you download the ISO as a torrent you can be guaranteed that it's OK.

Torrent downloads check the hash of the file as it is downloading as part of the bittorrent specification.
+1.

Verify the MD5SUM in order to make sure the ISO is good.

Since it is being installed in VMware, are you burning it to a CD, or just using the ISO?

---


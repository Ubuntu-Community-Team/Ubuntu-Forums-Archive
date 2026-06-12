---
title: "Any &quot;fresh&quot; LUKS tutorials available ( for Jaunty ) ?"
date: 2009-07-08
forum: Security
---

### Post by credobyte on 2009-07-08
99% of all tutorials on how to use LUKS are for 6.xx and 7.xx - none for Jaunty ( some steps can differ ). Does anybody know a good tutorial on how to encrypt my partitions ( want to test it on my server ) ?

Thnx in advance :)

---

### Post by duanedesign on 2009-07-08
This forum post looks pretty good. This post describes how to encrypt your entire hard disk. It was prepared while upgrading to Jaunty 9.04 from Intrepid 8.10. The author was following MaddMatts post.

[HTML]http://ubuntuforums.org/showthread.php?t=1205372[/HTML]

MaddMatts post - this is the post which the previous was based.

[HTML]http://ubuntuforums.org/showthread.php?t=1034910[/HTML]

here is one that is fairly recent. It shows you encrypted partitions over LVM with LUKS, instead of LVM-on-LUKS.

[HTML]http://www.debuntu.org/how-to-encrypted-partitions-over-lvm-with-luks[/HTML]

Here is a wiki page on encrypting Intrepid Ibex.

[HTML]https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid[/HTML]

---

### Post by credobyte on 2009-07-09
Excellent - that's exactly what I needed :)

---

### Post by HermanAB on 2009-07-09
Howdy,

The best thing you can do is to read the man pages:

$ man cryptsetup
$ man crypttab
$ man luks-tools

The man pages are the definitive source of information.  Everything else should be taken with a pinch of salt.

If you want to see recent examples, read the Perl code of my LUKS wizards:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)

---

### Post by credobyte on 2009-07-09
> **HermanAB said:**
> Howdy,

The best thing you can do is to read the man pages:

$ man cryptsetup
$ man crypttab
$ man luks-tools

The man pages are the definitive source of information.  Everything else should be taken with a pinch of salt.

If you want to see recent examples, read the Perl code of my LUKS wizards:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)

man pages are the main source of information unless you need suggestions ( real-life experiences ) :) Thnx for the link - will definitely take a look at it !

---


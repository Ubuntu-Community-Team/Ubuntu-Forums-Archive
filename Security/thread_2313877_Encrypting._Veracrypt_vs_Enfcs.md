---
title: "Encrypting. Veracrypt vs Enfcs"
date: 2016-02-16
forum: Security
---

### Post by juan53 on 2016-02-16
Hi
I write this post because I'm considering securing certain files stored in my laptop. I know that since TrueCrypt was out of business, there is no generaly used encryptation program in the landscape.
As far I know, Veracrypt is highly used, but Encfs is presented in Ubuntu official documentation.
I do suppose that Encfs is trusty, but, is Veracrypt trusty too? Virus Total gives some positives in its website, and I don't know what to think.
In the other hand, in orther to make Encfs handy, I suppose that it's a good idea to install gnome Encfs manager (which comes to a foreign repository). Is this repository manained rightnow? And should I suppose this to be trusty too?
About compatibiliy, and usage, does both have any issue?

Thanks a lot for the answer.

---

### Post by sabina2 on 2016-02-16
Cryptkeeper is based on Encfs but it appears to be buggy from time to time and may not run on Unity.

---

### Post by Irihapeti on 2016-02-16
I've been using Gnome EncFS Manager for a few years now with no problems. I don't know how it behaves with Unity, though.

---

### Post by kurt18947 on 2016-02-16
I've used cryptkeeper with Ubuntu-Gnome. It works pretty well but is designed to work with the old 2 panel gnome. I use the Window List extension and the indicator for cryptkeeper shows up there.  There is also this:

[https://defuse.ca/audits/encfs.htm](https://defuse.ca/audits/encfs.htm)

I guess it depends on how sensitive the encrypted contents are. I was really just wanting to encrypt folder contents, not whole disk or all of /home. The Disks app has a utility to encrypt removable devices such as flash drives. It won't just encrypt a folder as far as I can tell. 7zip is a simple to use utility and uses AES256 encryption. I guess it depends on how strong and secure you need.

---

### Post by gordintoronto on 2016-02-17
I'm using Cryptkeeper on a dual-boot system with Xubuntu 15.10 and Linux Mint 13. No problems so far. The encrypted file is in Mint, but I have no trouble accessing it from Xubuntu. I have an offline unencrypted backup.

---

### Post by juan53 on 2016-02-19
Okk. Thanks for the adds! I take note. :)

---


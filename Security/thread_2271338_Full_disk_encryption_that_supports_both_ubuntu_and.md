---
title: "Full disk encryption that supports both ubuntu and windows"
date: 2015-03-29
forum: Security
---

### Post by gott-des-todes666 on 2015-03-29
This is my first time posting to the forum I hope I am posting it to the right area.  For a while I have been looking for encryption software. I have a newer laptop that has UEFI and windows 8.1. I am looking for a full disk encryption software that will support both Ubuntu and Windows 8.1. I have a fair amount of external HDD that i would like to perform a volume encryption on and be bale to mount in both windows and Ubuntu.

Does anyone know of any such software?  At the moment I am using BestCrypt Volume Encryption for windows and its great but they only have a container version for ubuntu so that won't mount the encrypted volumes that I already encrypted.


Thanks in advance.

Mark

---

### Post by ryan151 on 2015-04-01
Maybe VeraCrypt?

It is a fork of TrueCrypt that patched some of the security bugs.

I know you can do full disk encryption on Windows and you should be able to encrypt your partition for Ubuntu.

---

### Post by HermanAB on 2015-04-02
FreeOTFE can do LUKS on Windows.

---

### Post by sudodus on 2015-04-02
Another alternative: install Ubuntu into a USB pendrive (and use the whole pendrive for 'Encrypted disk').

You have Windows 8.1, so I guess you have a new computer, and probably USB 3. Then you can use a fast USB 3 pendrive  and get a rather responsive Ubuntu system. A fast  USB 3 pendrive helps  in a USB 2 port too, because the flash hardware is often limiting the  speed.

See this link [Pendrive speed test]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

---


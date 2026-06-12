---
title: "Computer shutdown during ubuntu 11.04 install."
date: 2011-04-29
forum: Security
---

### Post by zaeb on 2011-04-29
My laptop randomly shuts off, at first I thought it was an issue with the laptop overheating but during the install of 11.04 I made sure the laptop had a fan blowing on it constantly and checked it and determined it couldn't have overheated. My problem now is that I was able to use a live cd to access my old files but was presented with only two files stating that my files were encrypted, I'm don't ever recall encrypting my files and so I'm without a passphrase.

What I'm wondering, is there a way to gain access without the passphrase? Or is there a way to fix the corrupt install? Thanks for the help.

---

### Post by raja.genupula on 2011-04-29
> **zaeb said:**
> My laptop randomly shuts off, at first I thought it was an issue with the laptop overheating but during the install of 11.04 I made sure the laptop had a fan blowing on it constantly and checked it and determined it couldn't have overheated. My problem now is that I was able to use a live cd to access my old files but was presented with only two files stating that my files were encrypted, I'm don't ever recall encrypting my files and so I'm without a passphrase.

What I'm wondering, is there a way to gain access without the passphrase? Or is there a way to fix the corrupt install? Thanks for the help.




[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

this thing will gives you

---

### Post by zaeb on 2011-04-29
I wasn't able to find any passphrase so I guess that's not going to work, which is what I figured. Is there a way to fix the corrupt install and get the computer to mount my same files? Or a way to undo the installation?

UPDATE:

I've gotten into the the encryption and I see my files in terminal, how can I copy them to an external hard drive? I know I can do it through terminal but I'm wondering if I can open up a window to see the files and copy what I need instead of the entire drive.

---

### Post by cariboo on 2011-04-29
You should be able to recover the files in your encrypted directory using the Natty Live CD. See [here]("http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html").

---

### Post by zaeb on 2011-04-30
I was able to mount the files and used chroot folder to copy them over. Thanks for the help!

---


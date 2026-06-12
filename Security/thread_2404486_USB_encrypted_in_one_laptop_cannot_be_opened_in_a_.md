---
title: "USB encrypted in one laptop cannot be opened in a different laptop"
date: 2018-10-24
forum: Security
---

### Post by brownitai on 2018-10-24
Hello all,

I have encrypted a USB via the default procedure ubuntu 16 is offering.
I formatted the laptop I made the encryption with and installed windows 10.

Trying to open the USB in several Ubuntu laptops didn't work due to permission issue.

What can I do to get access to the USB?

Thank you all!

---

### Post by TheFu on 2018-10-24
Sorry, I don't know "default procedure", but if you can say which of these it is, someone might be able to help:
* LUKS
* Encryptfs
* encfs

I'm very familiar with LUKS.  The other laptop would need to have the correct decryption tools installed. After that dependency is met, you can "open" the LUKS encrypted storage.  Depending on what is inside, you can either mount the file system or use LVM tools to open the PVs, VGs, and mount the LVs as desired. If LVM is used, those tools would also be dependencies required on the other machine.

---

### Post by brownitai on 2018-10-24
I don't remember which encryption method I used.

What is the default method used in the ubuntu 16.045 operating system offered in the official website?

[http://releases.ubuntu.com/16.04/ubuntu-16.04.5-desktop-amd64.iso.torrent?_ga=2.239917059.1890859880.1540403342-1794699396.1540403342](http://releases.ubuntu.com/16.04/ubuntu-16.04.5-desktop-amd64.iso.torrent?_ga=2.239917059.1890859880.1540403342-1794699396.1540403342)

---

### Post by C.S.Cameron on 2018-10-25
oops

---

### Post by TheFu on 2018-10-25
> **brownitai said:**
> I don't remember which encryption method I used.

What is the default method used in the ubuntu 16.045 operating system offered in the official website?

[http://releases.ubuntu.com/16.04/ubuntu-16.04.5-desktop-amd64.iso.torrent?_ga=2.239917059.1890859880.1540403342-1794699396.1540403342](http://releases.ubuntu.com/16.04/ubuntu-16.04.5-desktop-amd64.iso.torrent?_ga=2.239917059.1890859880.1540403342-1794699396.1540403342)

It depends.  How did you choose to encrypt?  Whole disk or Home directory during install?  Or did you use a specific tool and say "encrypt?"

I doubt anyone can help based on the provided description.  Linux is VERY flexible, so there are many built-in methods to accomplish things.  The underlying encryption could be dm-crypt, encryptfs, ZIP, gpg, openssl, or a few others.

---

### Post by HermanAB on 2018-10-25
So, instead of wondering what is going on, use the tools of the various encryption systems to tell you what it is that you are dealing with:

$ man cryptsetup
isLuks <device>
returns true, if <device> is a LUKS partition. Otherwise, false.

---

### Post by C.S.Cameron on 2018-10-25
Herman: getting isLuks sdc2 > isLuks: command not found. with 18.04.

---

### Post by HermanAB on 2018-10-26
Err... isLuks is a parameter of the cryptsetup program.  You need to read the man page of cryptsetup otherwise you will not get far.

---

### Post by C.S.Cameron on 2018-10-26
Oops, I thought you meant it as a command, sorry.
That man page is pretty hefty, thanks for the link.

---

### Post by brownitai on 2018-11-01
This is the tutorial I used to encrypt my USB:

[https://www.linux.com/learn/easily-encrypt-your-flash-drives-linux](https://www.linux.com/learn/easily-encrypt-your-flash-drives-linux)

does this help?

---

### Post by TheFu on 2018-11-02
dm-crypt uses LUKs.
Have you installed cryptsetup?  That should pull in any LUKS dependencies.

BTW, LUKS encryption isn't the default for many people.

For a flash drive, I use **caja** to decrypt LUKS stuff. It prompts when needed.  Caja isn't mandatory, it is just part of the Mate desktop and I know it works on my 16.04 system when the dependencies are installed.

I've posted how to unlock a luks encrypted partition in these forums a few times.  Use a terminal/shell and the **cryptsetup open**  command and option. You'll need to read the manpage, since more inputs are required.  If you search for my userid and "cryptsetup" and "mount", you should find those threads here.

---


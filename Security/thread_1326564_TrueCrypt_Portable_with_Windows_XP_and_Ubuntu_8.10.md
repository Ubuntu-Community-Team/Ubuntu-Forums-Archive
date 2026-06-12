---
title: "TrueCrypt Portable with Windows XP and Ubuntu 8.10 and 9.04"
date: 2009-11-14
forum: Security
---

### Post by nab on 2009-11-14
Just for as a reminder for myself, perhaps it helps somebody else :-)

I want to access TrueCrypt Portable with containers on an USB-Stick both from Ubuntu and Windows (I have on both boxes admin rights)

I installed TrueCrypt Portable 6.1a on the windows site.

I downloaded from [www.truecrypt.org](www.truecrypt.org) the same version for Ubuntu X86 and stored it temporarily on the desktop. (You will receive a file named truecrypt-6.1a-ubuntu-x86.tar.gz.)

I unziped the file using the Archive Manager, which I reached by right click and got truecrypt-6.1a-setup-ubuntu-x86. Now I double-clicked this file and clicked in the pop-up window on Extract. Deb package file. Afterwards I accepted the license terms.

The data were extracted to the / tmp folder. (message: Installation package file truecrypt_6.1a-0_i386.deb extracted and placed in /tmp)

I opened the folder, where the file was unpacked and opened truecrypt_6.1a-0_i386.deb with a right click to open with Archive Manager.

I extracted the file  ./usr/bin/truecrypt (approximately 4.4 MB) with a right click and unpacked it on the USB stick, preferably in the TrueCrypt for Windows created folder. 

That's it!

From now on when working on linux simply double-click on the USB drive the file truecrypt (without extension), then select via "Select file" your container file and open it via the Mount. 

However you must have root privileges (corresponding to the administrative privileges on Windows).

---


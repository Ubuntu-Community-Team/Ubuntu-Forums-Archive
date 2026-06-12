---
title: "virus found in usr folder"
date: 2012-06-19
forum: Security
---

### Post by strugglingbadly on 2012-06-19
Have run clam on whole system and multiple instances of PUA.Win32.Packer.Upolyx-5 FOUND in /usr/lib/mono

Looking further I find that /usr/lib/mono appears to be full of MS type files / executables and all appear to be owned by ROOT.

What's going on?

---

### Post by uRock on 2012-06-19
Moved to *Security Discussions*

---

### Post by Hungry Man on 2012-06-19
Probably false positives. I have .exe's and .dll's in my Mono folder as well.

---

### Post by QIII on 2012-06-19
Packers are not necessarily malicious.  They are the tools that compress/decompress the files included in a "pack"age "pack"ed for installation.

I would still recommend researching that particular one, since packers can be malicious.  It probably won't be any problem for you on your Linux machine, but you could unwittingly cause a Windows user some grief.

You might even see if you can find a Mono forum and ask there.

---

### Post by anewguy on 2012-06-19
You may want to check [this]("http://v.virscan.org/PUA.Win32.Packer.Upolyx-5.html") site.  As already mentioned, unless you are running Wine, or running a VM with Windows in it, and this file is found in the .wine folder or in the VM folder, chances are extremely high it won't do a thing - it's not for linux.  As also mentioned, the danger comes if you email someone or give them some other media that has the file on it.

Dave ;)

---

### Post by OpSecShellshock on 2012-06-20
Couple things: the prefix PUA stands for "potentially unwanted application," a designation which tends to be made for things that are at worst annoying but not specifically malicious, and which tend to have been put there by the user. In this specific case the most likely reason for the files being detected as PUA is because they are packed or otherwise compressed in a way that the Clam engine is unable to determine what's in them, thus it's pointing them out but not removing them (as they might be perfectly fine).

Also, one of the main purposes of Mono is to enable compatibility with certain Microsoft languages and platforms, so it's likely that's why those files are there.

These detections are almost certainly false positives.

---

### Post by Enigmapond on 2012-06-20
> **OpSecShellshock said:**
> Couple things: the prefix PUA stands for "potentially unwanted application," a designation which tends to be made for things that are at worst annoying but not specifically malicious, and which tend to have been put there by the user. In this specific case the most likely reason for the files being detected as PUA is because they are packed or otherwise compressed in a way that the Clam engine is unable to determine what's in them, thus it's pointing them out but not removing them (as they might be perfectly fine).

Also, one of the main purposes of Mono is to enable compatibility with certain Microsoft languages and platforms, so it's likely that's why those files are there.

These detections are almost certainly false positives.

+1 Nothing to be alarmed about.

---

### Post by strugglingbadly on 2012-07-16
Thanks for all the feedback.  Recent scans using clam have not identified any threats in the mono folder. I assume this is due to changes in the clam virus signature list.

Have now upgraded to 12.04 and no threats reported.

---


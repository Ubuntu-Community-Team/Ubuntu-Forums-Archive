---
title: "ppc builds of backports?"
date: 2005-01-05
forum: Ubuntu Backports
---

### Post by cutterjohn on 2005-01-05
Hello.  Has anyone happened to have made any non-x86 builds of the backports that I haven't noticed?  I've looked through a fair number of the announcements, and they appear to all be x86 binary builds...

---

### Post by tiiim on 2005-01-05
[QUOTE=cutterjohn]Hello.  Has anyone happened to have made any non-x86 builds of the backports that I haven't noticed?  I've looked through a fair number of the announcements, and they appear to all be x86 binary builds...[/QUOTE]
 yes i like ppc builds too!

---

### Post by jdong on 2005-01-05
I'm still trying to figure out how to handle alternative architecture builds. I don't own anything but i386 and one AMD64, currently not intending on using a 64-bit Linux, either.

I'm struggling with the whole 'trust' concept of letting someone else backport but release them under the Ubuntu Backports name.

---

### Post by fng on 2005-01-06
I'm certain some people are willing to help you with backporting (like me).  I'm especially interrrested in the warty-extra's repository.

---

### Post by tiiim on 2005-01-06
[QUOTE=fng]I'm certain some people are willing to help you with backporting (like me).  I'm especially interrrested in the warty-extra's repository.[/QUOTE]
 if there was away to access the new ppc debs i prob help test them under the ppc side.

---

### Post by jdong on 2005-01-06
[QUOTE=fng]I'm certain some people are willing to help you with backporting (like me).  I'm especially interrrested in the warty-extra's repository.[/QUOTE]

I know I can find people who are willing to maintain ppc and amd64 builds. However, the build tree needs to distinguish between architectures and credit packagers.

Plus, if you have access to one tree, you automatically have access to all the others. There's no way I can stop a malicious packager from pushing virus/trojaned versions of packages into their trees or other trees.

More realistically, I can't stop a packager's accidents from causing widespread harm.

---

### Post by tiiim on 2005-01-06
[QUOTE=jdong]I know I can find people who are willing to maintain ppc and amd64 builds. However, the build tree needs to distinguish between architectures and credit packagers.

Plus, if you have access to one tree, you automatically have access to all the others. There's no way I can stop a malicious packager from pushing virus/trojaned versions of packages into their trees or other trees.

More realistically, I can't stop a packager's accidents from causing widespread harm.[/QUOTE]
 how may create an Ubuntu PPC source project under a different project? I know its a diff project but then there more control? maybe... dont know.. or just have a big disclaimer like download at ur own risk...

---

### Post by ZakZak on 2005-01-06
I'd also like to see an AMD64 backports repository as I'm preparing to install AMD64 Ubuntu on the Opteron I use as a desktop machine.  My P4 notebook has been running regular Ubuntu great for three months now and I think it's time to ditch Windows on my desktop machine too now.

-Zak

---

### Post by jdong on 2005-01-06
Well, SF.net is going to be giving us a new file release mechanism. Hopefully it'll accomodate these conditions!

---

### Post by cutterjohn on 2005-01-07
...well if we were to start a Ubunto Backports PPC, the first package that I'd like to see would be X.org server for 4.10 ...  (Of course since we can't trust jdong we'd have to start our own system entirely from scratch, oh, and also, each and every one of you would also require at least a top secret security clearance. :)

Seriously, I'd be willing to help compile some packages, once I am comfortable with the debian package system, but nothing too big as I am really averse to large downloads over dialup, e.g. X.org source, kernel source(I wish they'd start packaging the kernel as pieces, e.g. common, scripts, etc. plus a specific architecture package, as I saved quite a chunk of space on my old system by blowing away other architecture support files.)

---


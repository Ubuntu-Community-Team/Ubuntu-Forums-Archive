---
title: "Need to add a folder in the root directory"
date: 2009-09-10
forum: Security
---

### Post by onespeedbiker on 2009-09-10
I need to fix a problem by adding the folder "kubuntu" at the end of /usr/share/doc/kde/en/HTML/(kubuntu); as a patch. Without enabling the root account, is there a sudo command that will let me do this? I have tried "sudo mkdir /usr/share/doc/kde/en/HTML/kubuntu" and it tells there is no such directory; duh

---

### Post by Whiffle on 2009-09-10
sudo mkdir /usr/share/doc/kde/en/HTML/kubuntu

---

### Post by onespeedbiker on 2009-09-10
> **Whiffle said:**
> sudo mkdir /usr/share/doc/kde/en/HTML/kubuntu

Yeah, that is the command. The person who wrote the patch reversed folders. should have been /usr/share/doc/kde/HTML/en/kubuntu and I didn't catch it at first. Thanks

---


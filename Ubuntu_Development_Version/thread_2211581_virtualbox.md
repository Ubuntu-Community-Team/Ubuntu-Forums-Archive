---
title: "virtualbox"
date: 2014-03-16
forum: Ubuntu Development Version
---

### Post by cybergalvez on 2014-03-16
Hi I am trying to test out Ubuntu Gnome 14.01 in Virtualbox 4.8.3 with the guest addons installed and gnomeshell is crashing quite a bit, also gdm takes a very long time to pop up. Has anyone else seen this? what can send to whom to help out if this is a but. When it does load and it reports a crash, it says some packages are out of date and won't send the crash report.

---

### Post by tfrue on 2014-03-17
How much memory, space, processors, video memory have you given the VM?

---

### Post by cybergalvez on 2014-03-17
memory: 2048MB
processors 2
space 20GB

---

### Post by tfrue on 2014-03-18
What version are you running? Type:
```
 vboxmanage -v
```

Also, keep in mind that 14.04 is still in development, there may still be some bugs that exist with 14.04 working with VirtualBox.

---

### Post by cybergalvez on 2014-03-18
4.3.8r92456

I know it's still in dev, just wondering if the issues are real or vbox related, and if there was anything useful that I could send that would be helpful. if the issues are plurly vbox then there's little reason to send bug reports at this time, if they're real, its a different issues.

---

### Post by cybergalvez on 2014-03-23
looks like most of the issues are getting resolved with the latest daily builds

---


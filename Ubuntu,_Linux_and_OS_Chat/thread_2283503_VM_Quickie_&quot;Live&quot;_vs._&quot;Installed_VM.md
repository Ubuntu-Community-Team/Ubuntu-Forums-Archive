---
title: "VM Quickie: &quot;Live&quot; vs. &quot;Installed VM&quot;"
date: 2015-06-22
forum: Ubuntu, Linux and OS Chat
---

### Post by Kurt_Alan on 2015-06-22
I'm looking at Lubuntu 15.04 (Sweet!) as a VM but the view is the same as "live cd" and all my config changes and saves disappear with that session.

But then I have the option to "install."  I'm afraid to press that button. But the install to my SSD will remain, actually, not on my SSD, but in a folder for vm created on my SSD, right? So no harm in doing a complete install on VM? And then my config changes will save?

What is CLI syntax for finding all my vm folders?

---

### Post by sudodus on 2015-06-22
As long as you run in the virtual machine, you will not damage your host system in the real computer.

You can use the same tools as in a real machine to find the available drives, partitions, file systems and folders inside the virtual machine.

Depending on which virtual machine system you are using, there are different ways to find your 'vm folders' from outside (in your host system). For example VirtualBox has a self-explaining GUI, that you learn by using it (trial and error).

---

### Post by wildmanne39 on 2015-06-22
This will tell you what you need to know to setup and use virtualbox.
[https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by pretty_whistle on 2015-06-22
I've used virtualbox and can choose "save state" which saves any changes made so I don't know what you've encountered with this.  Maybe you didn't know you could choose "save state". ??

---


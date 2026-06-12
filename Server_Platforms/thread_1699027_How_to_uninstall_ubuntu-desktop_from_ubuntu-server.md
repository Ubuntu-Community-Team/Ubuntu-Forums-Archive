---
title: "How to uninstall ubuntu-desktop from ubuntu-server"
date: 2011-03-03
forum: Server Platforms
---

### Post by adriancs on 2011-03-03
Hi, I have install ubuntu server on the computer.
after few days, I type this to install ubuntu-desktop:

```
sudo apt-get install ubuntu-desktop
```

Everytime the computer startup the system will automatic boot into Desktop GNOME environment.

How to uninstall the ubuntu-desktop?

any clue? thanks

---

### Post by James78 on 2011-03-03
[COLOR=Red]**Keep in mind bug [#574287]("https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/574287")! Use these steps cautiously!! Read the bug report first, and test this out first, as it may wreck your system!**[/COLOR]

You could use tasksel to remove the package. E.g.
```
sudo tasksel
*Deselect ubuntu-desktop*
*Press Ok button*
```If tasksel doesn't exist, just install it first.
```
sudo apt-get install tasksel
```Not tested, but this command might also do the job. You can change the 'remove' to a 'purge' if you want more of the package debris to be gotten rid of.
```
sudo apt-get remove ubuntu-desktop^
```

An alternative could be start a LiveCD/VirtualMachine and install ubuntu-desktop in there, then make a note of the packages it installs, then create an apt-get remove/purge command.

Another alternative. Download the [ubuntu-desktop]("http://packages.ubuntu.com/lucid/ubuntu-desktop") package, decompress it, pick it apart, find the control list, then find the depends section, copy it, and make an apt-get remove/purge command.

---


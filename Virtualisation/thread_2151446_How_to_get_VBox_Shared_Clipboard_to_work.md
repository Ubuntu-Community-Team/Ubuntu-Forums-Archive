---
title: "How to get VBox Shared Clipboard to work?"
date: 2013-06-04
forum: Virtualisation
---

### Post by dragonfly41 on 2013-06-04
I have VirtualBox 4.2.12 installed manually on Ubuntu 12.04.

I created a VM of headless ubuntu-12.04 server and that has worked fine using PuTTY session between host and guest.

But I hit problems in trying to copy/paste text in the PuTTY session terminal.

I saw that this needed Guest Additions and I managed to install this..

Then in Preferences > General > Advanced
I set ...
[LIST]
[*]Shared Clipboard: Bi-directional
[*]Drag'n'Drop: Disabled
[/LIST]

But I still can't copy text from host clipboard into guest command line session.

What more steps should I take for shared clipboard to work?

I can see from my searches that others have hit the same problem ... but few solutions found ...

[http://ubuntuforums.org/showthread.php?t=2102424&highlight=shared+clipboard](http://ubuntuforums.org/showthread.php?t=2102424&highlight=shared+clipboard)

---

### Post by dragonfly41 on 2013-06-05
I still can't get shared clipboard to work in VirtualBox 4.2.

After reading a number of threads my work around for managing remote instances is  ...


[LIST]
[*]Create and edit a bash script in host ubuntu to run in guest ubuntu instance.
[*]Copy this bash script into guest ubuntu through scp session (or by FileZilla session).
[*]Ensure that copied script in guest is executable and ownership is correct (user not root).
[*]Execute bash script in guest ubuntu from host through ssh session.
[/LIST]

This work flow ensures that all my editing is in host environment (e.g. using GEdit).

My next step will be to write the control scripts I need via PHP front end GUI in host ubuntu.
Similar to CLICompanion GUI but controlling multiple remote headless instances which could be in (local) VirtualBox or in (cloud) AWS.

It would still be interesting to learn why shared clipboard does not work in VirtualBox.

---


---
title: "Chrome Remote Desktop and Encryption"
date: 2015-02-08
forum: Security
---

### Post by farside268 on 2015-02-08
With CRD on a standard installation, you have to choose between encrypting your home folder and being able to remotely reboot your system. I've chosen the latter
, but I hope that someone can tell me how to have the best of both worlds. 

Is there a GUI/noob-friendly way to create an encrypted partition for my important data (I'm a lawyer, so I have obligations), while the CRD session can still start automatically? I don't mind having to manually mount the partition, but  I was hoping for something easier to use than a command line script.

---

### Post by TheFu on 2015-02-10
Why use CRD at all?  I'd lean towards running a remote desktop using security that isn't dependent on some 3rd party. x2go does this, uses NX which is fast, and goes over ssh, which is believed to be secure, especially if authentication is through keys, not passwords.  [https://www.howtoforge.com/how-to-install-x2goserver-on-ubuntu-14.04-as-vnc-alternative](https://www.howtoforge.com/how-to-install-x2goserver-on-ubuntu-14.04-as-vnc-alternative) With x2go, you can reboot the system. Heck, with ssh you can reboot the system too.

There are ways to encrypt 1 file, directories, user HOMEs, and partitions in Linux. It is really up to you to decide which is best.  Just know than with HOME directory encryption, when you are logged in, the data is available based on permissions on the box and root can see everything. Perhaps encrypting per client with different keys would be prudent?  I'd manage key access using a password manager and a hardware device to access that - something like a smartcard or ubikey neo ... be certain if you go HW for this access that you get 2 devices - one for you and one (that is a clone) that is placed in a safe.

Also - don't fear the shell. 90% of the power of Linux happens at the CLI/shell/terminal.

---


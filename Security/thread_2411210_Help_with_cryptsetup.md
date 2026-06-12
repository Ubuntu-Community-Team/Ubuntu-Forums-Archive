---
title: "Help with cryptsetup"
date: 2019-01-26
forum: Security
---

### Post by apol1 on 2019-01-26
Ive successfully installed cryptsetup via terminal yet when I go to encrypt an external device I see no option for encryption, merely the options before installation.

What might be happening here?

Thanks for your input

---

### Post by TheFu on 2019-01-27
If you want to encrypt a storage device, then cryptsetup is the command line tool to use. It isn't a GUI tool.

[https://www.cyberciti.biz/hardware/howto-linux-hard-disk-encryption-with-luks-cryptsetup-command/](https://www.cyberciti.biz/hardware/howto-linux-hard-disk-encryption-with-luks-cryptsetup-command/) explains how to do it. The installation commands they show are for RPM, which you can ignore. However, the steps to format and setup an encrypted partition/LV are correct.

---

### Post by apol1 on 2019-01-27
Nevermind I found it, just had to switch the format in the Gui

---


---
title: "keyboard frosen in VirtualBox"
date: 2008-07-09
forum: Virtualisation
---

### Post by Barmaleychik on 2008-07-09
I am trying ti install the first Windows XP pro virtual machine in VBox under Ubuntu 8.04.

Installation starts but at the point I am asked to click enter to install Win PX the virtual machine captures my keyboard and then I am stuck. Computer does not respond to any key and mouse and right control key does not help. As the result I can not install the virtual machine.

Please, help!

---

### Post by fairisle on 2008-07-10
I got the same trable...

Do you use SCIM for Multi-langage?
(I use SCIM for Korean and Japanese...)

If so, try this...

You need to install "scim-bridge-client-qt" and "scim-bridge-client-qt4"
and for safty, choose keyboard, same your ubuntu system , in your scim setup Frontend global.

Last, You MUST reboot Your system!!
(It doesn't work just logout and login...in my case...)

Maybe you can get keyboard in your virtualbox..

Good Luck!

---


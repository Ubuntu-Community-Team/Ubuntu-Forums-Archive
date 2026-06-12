---
title: "Activated usb2.0 on virtualbox to share usb with virtual machinne"
date: 2017-07-31
forum: Virtualisation
---

### Post by sed_faster on 2017-07-31
Hello folks,

I am trying activated usb2.0 on virtualbox. But I haven't sucess on this task. My system is:
```

eno@pcwork:~$ uname -a
Linux pcwork 4.4.0-87-generic #110-Ubuntu SMP Tue Jul 18 12:55:35 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
eno@pcwork:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial
eno@pcwork:~$ VBoxManage --version
5.0.40_Ubuntur115130

```

When I try activated usb2.0 appear a warning message advice which I didn't activate this option because I need install Oracle VM VirtualBox Extension Pack. When I download 
and run the program with extension .vbox-extpack - (Oracle_VM_VirtualBox_Extension_Pack-5.1.26-117224.vbox-extpack), only appear/open the screen referent the program virtualbox.

Please see this picture where you can see warning message referent the activate usb2.0: [http://imgur.com/a/TL7pc](http://imgur.com/a/TL7pc)
How can I handle this?

Thanks

[UPDATE]
I run this command
```

sudo apt-get install virtualbox-ext-pack

```
But I still can't handle usb on virtual machine.

---

### Post by Bucky Ball on 2017-07-31
Tip: The extension pack needs to match your version of Virtualbox from memory. That is possibly why it is not working.

Check and then, if wrong, [have a look here]("https://www.virtualbox.org/wiki/Downloads") for the other and get the correct one for your install.

You should be able to double-click the .extpack extensions file to install, then open Virtualbox. If I remember correctly (haven't done this in awhile) you don't need VBox open to install the extension pack.

You might also find [this of interest]("https://www.virtualbox.org/manual/ch01.html#intro-installing").

---


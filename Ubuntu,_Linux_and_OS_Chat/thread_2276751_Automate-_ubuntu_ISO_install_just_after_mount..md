---
title: "Automate- ubuntu ISO install just after mount."
date: 2015-05-04
forum: Ubuntu, Linux and OS Chat
---

### Post by neel5 on 2015-05-04
Iam Installing my customised Ubuntu ISO/CDROM with the following steps.

[LIST=1]
[*]Mount an ISO, Reboot the system, press F2 get on to boot sequence change to CDROM. So it will boot from ISO.
[*]I can see install(CD/DVD)icon on desktop where i double click to start installation which uses my preseed/custom_seed file or launch terminal, type ubiquity --automatic for successfull instllation

[*]Install some more packages e.g  sudo co_setup -f Co_Setup.conf thorugh terminal

[/LIST]
Now i want to automate all the above steps into single step for headless server.

Which file to change in ISO? so that it would start installing automatically while it boot from ISO.
I have access to ISO contents after unsquashfs and successfully able to squashfs and create fresh ISO.

I tried changing append line in iso/isolinux/isolinux.cfg Label install:append line where ubiquity --automatic doesnot start installation automatically.

Pls help.

---


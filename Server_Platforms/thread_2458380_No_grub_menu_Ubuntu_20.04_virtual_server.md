---
title: "No grub menu Ubuntu 20.04 virtual server"
date: 2021-02-23
forum: Server Platforms
---

### Post by deepakdeshp on 2021-02-23
Hello,
I dont get the grub menu.
I changed parameter in [COLOR=var(--black-800)][FONT=Consolas]/etc/default/grub [/FONT][/COLOR]GRUB_TIMEOUT=15
Holding **** key as the server boots doesnt help too.

---

### Post by oldfred on 2021-02-23
If it is UEFI, you have to press Escape key between UEFI screen & when grub will (should) appear.
If you have UEFI fast boot on, you may not have any time to press a key as it immediately boots. You then can try "cold" full power down boot & press correct key to get into UEFI/BIOS.

If BIOS you hold shift key from UEFI/BIOS screen until grub menu appears.

If only one install in grub menu, it does not normally show menu as you only have one system to boot.

With 18.04 or later to always see menu
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT_STYLE=menu

---

### Post by deepakdeshp on 2021-02-23
I ran update-grub after the suggested change, dont know if it was required.





It is a virtual machine hence I cant get into BIOS or UEFI








export GRUB_MENU_PICTURE="/usr/share/backgrounds/linuxmint-ulyana/calinstan_kyoto.jpg"


[/CODE]

---


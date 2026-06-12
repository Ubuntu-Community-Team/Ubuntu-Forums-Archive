---
title: "installing ubuntu on mac osx in virtual box"
date: 2013-02-22
forum: Virtualisation
---

### Post by vikceo on 2013-02-22
i am trying to install 32 bit latest version of ubuntu on latest version of virtual box 4.2.6 on mountain lion 10.8.2 

on clicking the start for the first time in virtual box it asks me the iso location of ubnutu. On providing that it shows me a black screen with message

UEFI Interative shell v2.0  Revision 1.02
Mapping Table
blaw blaw....

2.0 Shell> 

So I was actually expecting a UI option to install ubuntu rather this shell. Please advise

---

### Post by varunendra on 2013-02-24
*Thread moved to **Virtualisation**.*
------------------

Can you post the exact link of the iso you downloaded?
To check integrity of the downloaded iso : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also, since you seem to install Ubuntu for testing/experimenting purpose, I'd recommend 12.04 (32 or 64 bit), not 12.10 which is latest stable or 13.04 which is still under development.

If you happen to download an iso again, I'd further recommend to download via torrent to ensure integrity of the downloaded image.

Some settings in VBox to check -
[list]
[*]Make sure 'EFI' is NOT enabled in VBox Settings > System > Motherboard tab.
[*]Make sure the chipset is selected to PIIX3 in the same tab.
[*]RAM assigned to the VM is recommended to be at least 1 GB.
[/list]

Please confirm if these are okay.

---


---
title: "Installing VirtualBox extension pack through GUI fails"
date: 2016-12-10
forum: Virtualisation
---

### Post by &amp;KyT$0P# on 2016-12-10
Not really sure if this is a good sub-forum to post a solved problem.  Please move if needed.

I just upgraded VirtualBox to 5.0.30.  Purged the old VirtualBox package, then installed the new one.  I tried to install the new extension pack through the GUI...and it failed.

Initially I thought the problem was my AppArmor profile, so I set that to complain mode and tried again.  But that wasn't the only issue, as now it fails with a different error -
```
Failed to install the Extension Pack /home/.../Oracle_VM_VirtualBox_Extension_Pack-5.0.30-112061.vbox-extpack.

The installer failed with exit code 1: .

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ExtPackManagerWrap
Interface: IExtPackManager {edba9d10-45d8-b440-1712-46ac0c9bc4c5}
```
Reinstalling the VirtualBox package didn't help.  Rebooting the computer didn't help.  Search results suggest to delete a directory in [FONT=Courier New]/usr/lib/virtualbox/ExtensionPacks[/FONT], but that folder was empty.

So I tried using VBoxManage from the command line -
```
VBoxManage extpack install /home/.../Oracle_VM_VirtualBox_Extension_Pack-5.0.30-112061.vbox-extpack
```
... and it worked fine. :KS


Posting this in case I'm not alone having this problem and it helps someone else.  This is not the first time I've successfully used VBoxManage to work around problems doing stuff in the GUI.

---


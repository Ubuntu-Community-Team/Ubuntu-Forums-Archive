---
title: "VirtualBox: Can't find UnattendedTemplates after install"
date: 2020-01-25
forum: Virtualisation
---

### Post by sharku on 2020-01-25
I've installed VirtualBox on a system with brand new installation of 19.04 and want to use the VBoxManage tool to do an unattended install. But when I perform the install command I get the following error message:

    VBoxManage: error: Failed to open '/usr/share/virtualbox/UnattendedTemplates/ubuntu_preseed.cfg' (VERR_FILE_NOT_FOUND)
    VBoxManage: error: Details: code VBOX_E_OBJECT_NOT_FOUND (0x80bb0001), component UnattendedWrap, interface IUnattended, 

I looked in /usr/share/virtualbox and the UnattendedTemplates directory was not there. Just in case I searched is several other places and could not find the missing files. I also looked through the list of files of other virtualbox related packages listed in packages.ubuntu.com and did not see it listed anywhere.

Is there another package I need to install, or is there some other procedure needed to add the templates when installing on Ubuntu?

I have following virtualbox packages installed:

    virtualbox-dkms/disco,disco,now 6.0.6-dfsg-1 all [installed]
    virtualbox-ext-pack/disco-updates,disco-updates,now 6.0.6-1ubuntu1.19.04.1 all [installed]
    virtualbox-guest-additions-iso/disco,disco,now 6.0.6-1 all [installed]
    virtualbox-guest-dkms/disco,disco,now 6.0.6-dfsg-1 all [installed]
    virtualbox-guest-utils/disco,now 6.0.6-dfsg-1 amd64 [installed]
    virtualbox-qt/disco,now 6.0.6-dfsg-1 amd64 [installed,automatic]
    virtualbox/disco,now 6.0.6-dfsg-1 amd64 [installed]

Thanks!

---

### Post by TheFu on 2020-01-25
Support for 19.04 ended recently, Jan 23rd.  Move to 19.10.
[https://www.omgubuntu.co.uk/2020/01/ubuntu-19-04-end-of-life](https://www.omgubuntu.co.uk/2020/01/ubuntu-19-04-end-of-life)

---

### Post by sharku on 2020-01-29
I worked around this problem by copying the UnattendedTemplates folder from a Windows machine where virtual box was installed. Ideally though Id like to find a way to install on Linux via apt rather than patching it up.

---


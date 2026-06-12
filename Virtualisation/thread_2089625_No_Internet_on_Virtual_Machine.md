---
title: "No Internet on Virtual Machine"
date: 2012-11-29
forum: Virtualisation
---

### Post by Hillvz on 2012-11-29
Hello everyone, I'm -fairly- new to Ubuntu and the Linux distro's themselves, and I recently swapped over because of a faulty Windows HDD (don't ask). When I try to run Windows 7 on VirtualBox, I can get logged in and everything, everything works except for the Internet. It only shows me a LAN connection that has network access but no Internet access. Can anyone help me? Would be greatly appreciated. Thanks!

---

### Post by efflandt on 2012-11-29
Does **groups** typed in an Ubuntu terminal show you being a member of **vboxusers** group? If not, maybe you need to add yourself to that group for networking to work from a guest OS.

```
sudo gpasswd -a your_ubuntu_username vboxusers
```Use your normal password (no characters will appear) when sudo asks for it.  You may have to log out of X and back in for the added group to take effect.

If it is not that, not sure why internet would not be working.  Normally virtualbox does NAT for your guest OS, so any networking outside would appear to come from your Ubuntu host IP.  Can you ping anything on your LAN (like your router) from the Windows guest?

---


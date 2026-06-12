---
title: "how to do clean uninstallation of virtualbox-ose?"
date: 2008-07-16
forum: Virtualisation
---

### Post by chrex on 2008-07-16
On Ubuntu 7.10. 
Successfully nstalled virtualbox-ose 1.5.0 following [https://help.ubuntu.com/community/VirtualBox#Support](https://help.ubuntu.com/community/VirtualBox#Support). All the thing I did is:

```
sudo apt-get install virtualbox-ose virtualbox-ose-source
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant unpack virtualbox-ose
sudo module-assistant auto-install virtualbox-ose

sudo gpasswd -a `whoami` vboxusers

echo "vboxdrv" | sudo tee -a /etc/modules
```


Now I want to uninstall it completely. I know how to reverse the last 2 commands and of course also the apt-get one. But I don't know what to do with the 4 module-assistant commands. What are the reverses for them? I've googled and read something on kernel module but still not sure:(. 

Thanks for your help.

---


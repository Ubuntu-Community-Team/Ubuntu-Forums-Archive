---
title: "Cannot upgrade Azure VM running Ubuntu Pro v20.04 to v22.04"
date: 2024-03-03
forum: Ubuntu Cloud and Juju
---

### Post by thangvq8429 on 2024-03-03
Hi All,

Initially I purchased Ubuntu Pro license for an Azure VM running a production website and performed in-place upgrade from v18.04 to v20.04 successfully. Unfortunately, after that, there has been an issue when performing in-place upgrade from v20.04 to v22.04 until now.

I have already run the necessary commands:
sudo apt update && sudo apt upgrade
sudo apt dist-upgrade
sudo reboot
sudo apt install update-manager-core
sudo do-release-upgrade

However, there always is a warning message with the last command as follows:
##
messervn@Messer-VM-WebsiteVN:~$ sudo do-release-upgrade
Checking for a new Ubuntu release Please install all available updates for your release before upgrading.
##

Pls share to me the next-steps for furthur checking. Thanks so much!

---


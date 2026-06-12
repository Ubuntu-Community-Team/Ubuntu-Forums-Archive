---
title: "Upgrade from 8.04 to 10.04 fails"
date: 2012-10-15
forum: Server Platforms
---

### Post by johanbarelds on 2012-10-15
Hi all,

I am trying to upgrade an server running LTS 8.04 to 10.04 but it fails. I do get the following error messages:

------------------------------------------------
root@server1:~# do-release-upgrade
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg'
exception from gpg: GnuPG exited non-zero, with code 131072
Debug information:


gpg: can't open `/tmp/tmpbhlhFU/lucid.tar.gz.gpg'
gpg: verify signatures failed: file open error

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server.
-----------------------------------------------------

I can do normal upgrades with:

apt-get update
apt-get dist-upgrade

I did a lot of googling, but couldn't find any solution.
Anyone any clues?
Thanks!

Gr Johan

---

### Post by johanbarelds on 2012-10-15
Hi all,

I am trying to upgrade an server running LTS 8.04 to 10.04 but it fails. I do get the following error messages:

------------------------------------------------
root@server1:~# do-release-upgrade
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg'
exception from gpg: GnuPG exited non-zero, with code 131072
Debug information:


gpg: can't open `/tmp/tmpbhlhFU/lucid.tar.gz.gpg'
gpg: verify signatures failed: file open error

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server.
-----------------------------------------------------

I can do normal upgrades with:

apt-get update
apt-get dist-upgrade

I did a lot of googling, but couldn't find any solution.
Anyone any clues?
Thanks!

Gr Johan

---

### Post by TheFu on 2012-10-15
[https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/156070](https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/156070) seems similar. Perhaps the comments and links there will help.

---

### Post by johanbarelds on 2012-10-15
Thanks for your reply TheFu!
I also found that article and went trough the solutions mentioned there.
Unfortunatly no one seems to be applicable...:-(

---

### Post by grahammechanical on 2012-10-15
This might help

[https://help.ubuntu.com/community/LucidUpgrades]("https://help.ubuntu.com/community/LucidUpgrades")

Regards

---

### Post by johanbarelds on 2012-10-15
Thanks, but i already tried the instruction from that article.
Still got the error message.
It looks like the server can't download the lucid tar file.
But it's not a network problem since i can download normal upgrades just fine.

---

### Post by coffeecat on 2012-10-15
Threads merged. Please do not post duplicates in different parts of the forum. This dilutes community effort.

---


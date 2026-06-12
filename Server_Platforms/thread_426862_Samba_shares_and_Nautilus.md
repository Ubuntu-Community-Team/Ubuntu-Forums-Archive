---
title: "Samba shares and Nautilus"
date: 2007-04-28
forum: Server Platforms
---

### Post by GeorgeST on 2007-04-28
Hi,

If I enter a share via smb://server/share in Nautilus, I can launch some files fine.  Others do nothing such as *.zip or *.chm.  Locally everything is fine and dandy.  MS and Apple access these files fine.  Any ideas as to why?

server - ubuntu-server 7.04
client - ubuntu-desktop 7.04

Thanks for reading!

---

### Post by misconfiguration on 2007-04-30
sudo apt-get install smbfs

EDIT: Maybe I should explain myself.

I was having the same issue accessing my public SMB share hosted by my slack-box. It seems that the smb front-end software isn't installed, I installed smbfs and all is well now. Give that a shot and see if it works.

---


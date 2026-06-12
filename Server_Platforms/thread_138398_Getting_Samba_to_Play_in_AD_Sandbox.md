---
title: "Getting Samba to Play in AD Sandbox"
date: 2006-03-01
forum: Server Platforms
---

### Post by SuperMike on 2006-03-01
I finally got Samba to work in workgroup mode. Hurray! However, now I want to make it play in the AD domain.

Does anyone have a quick tutorial to show me how to get my Ubuntu 5.10 to act like a member server in an AD domain, letting Windows XP users use their AD logons to authenticate to my member server? Note also that I'm hoping to not have an admin chore to keep adding accounts to my Ubuntu 5.10 -- I want to just say, "Whatever is allowed in the domain to login, is allowed read/write on my share."

I also don't know what ports it requires, so temporarily I had to bring down my firewall (iptables -F) in order to get going for this test.

Here's my smb.conf file as it stands now. Note I had to use smbpasswd command before I could get it to use my local Linux user account to authenticate.

[global]
workgroup = WORKGROUP
netbios name = %h
server string = %h
passdb backend = tdbsam
security = user
domain logons = no
preferred master = no
wins support = no
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
passwd chat debug = yes
unix password sync = no
log level = 3

[public]
path = /tmp/public
available = yes
browseable = yes
public = yes
writable = yes
create mode = 0755
directory mode = 0755
read only = no

---


---
title: "SSH Host based authentication from windows to linux computer"
date: 2020-01-11
forum: Server Platforms
---

### Post by robcorsi2b on 2020-01-11
hi,

I would like to use hostbasedauthentication from Windows to a Linux computer.
  I have generated public / private key with help of putty.
  Linux side conf in /etc/ssh/sshd_config :
  > HostbasedAuthentication yes
IgnoreRhosts no 
  I added windows host in : /etc/hosts.equiv 
  I added windows public key in /etc/ssh/ssh_known_hosts
  Windows side :
  > ssh -i mykey.pub -l mylongon@linuxmachine -o HostbasedAthentication=yes -o EnableSSHKeysign=yes
  but it asks for password I would like that it doesn't request  password. In sshd log I see that it doesn't check the public key given  by windows client...
  Any help please

---

### Post by aljames2 on 2020-01-11
Have you turned off password authentication in sshd_config?  You have to restart the SSH service after editing the config.  With this setting the SSH server won’t ask for a password.

[ https://help.ubuntu.com/community/SSH/OpenSSH/Configuring]( https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by robcorsi2b on 2020-01-12
> **aljames2 said:**
> Have you turned off password authentication in sshd_config?  You have to restart the SSH service after editing the config.  With this setting the SSH server won&#8217;t ask for a password.

[ https://help.ubuntu.com/community/SSH/OpenSSH/Configuring]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")


I would like to keep both password and key authentication.

---


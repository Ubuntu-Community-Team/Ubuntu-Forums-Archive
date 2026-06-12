---
title: "Cannot ssh in a folder"
date: 2011-12-20
forum: Server Platforms
---

### Post by Azathoth_ on 2011-12-20
Hi,

I cannot enter in a different folder in ssh.
I am trying to nackup the full server (/ directory) using root user.

Everytime I try to ssh to a different folder it does not work.

For example:

```
ssh root@myserver.com
ssh root@IP
```
works

but
```
ssh root@myserver.com:/
ssh root@myserver.com:$HOME
ssh root@IP:/home
```
does not work

My server /etc/ssh/ssh_config is

```
# Host *
#   ForwardAgent no
#   ForwardX11 no
#   RhostsRSAAuthentication no
RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
IdentityFile ~/.ssh/identity
IdentityFile ~/.ssh/id_rsa
IdentityFile ~/.ssh/id_dsa
Port 22
#Protocol 2,1
PubkeyAuthentication yes
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   EscapeChar ~
```

How can I make ssh to a different folder than the default one?
Thanks in advance.

---

### Post by matt_symes on 2011-12-20
Hi

This is one way to do it..

```
ssh -t user@ip "cd /; bash"
```

Kind regards

---

### Post by Azathoth_ on 2011-12-20
It worked, thanks!

---


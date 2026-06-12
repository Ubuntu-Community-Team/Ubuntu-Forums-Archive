---
title: "LTSP - Persistent home directories on server"
date: 2010-02-24
forum: Server Platforms
---

### Post by _Morpheus_ on 2010-02-24
Hi Forum!

I'm new to the LTSP topic and I don't know whether I've misunderstood
parts of the key concept.

I've setup an LTSP server using Ubuntu 9.10 64 Bit on VMware ESXi 4 Update 1
according to this article [http://wiki.ubuntuusers.de/LTSP](http://wiki.ubuntuusers.de/LTSP).

Basically the setup works but I would like to know how I can achieve persistent
home directories for the users on the server. Right now Firefox (installed as local
app) does not even save the proxy settings - on the next reboot the clients boot a
fresh blank desktop. Folders, files and everything I put somewhere in the home directory
are lost after rebooting.

Here's what I did so far:

- Installed Ubuntu 9.10, One network card, DHCP on a separate server
- Installed the following packages on the server
  - ltsp-server
  - nbd-server
  - ltspfs
  - ltspfsd
- Added two new user accounts on the server

- Created the client using the command
```

ltsp-build-client --arch i386 \ 
--http-proxy http://internal-apt-cache.domain.local:3142 \ 
--locale de_DE.UTF-8 \ 
--late-packages ubuntu-desktop
```- Executed the command ```
ltsp-update-sshkeys
```- Chrooted into the client jail via ```
chroot /opt/ltsp/i386/
```- Installed Firefox
- Created the ltsp.conf file in ```
/var/lib/tftpboot/ltsp/i386/lts.conf
``` with the following content

```
[Default] 
LDM_DIRECTX = true 
LOCALDEV = True 
SOUND = True 
XKBLAYOUT = de 
LDM_LANGUAGE = de_DE.UTF-8 
LOCAL_APPS = True 
LOCAL_APPS_MENU = True 
LOCAL_APPS_MENU_ITEMS = firefox 
SEARCH_DOMAIN = nr.domain.local 
DNS_SERVER = 192.168.200.201 
```According to the wiki article mentioned above Ubuntu LTSP switched from NFS to nbd starting with Ubuntu Hardy.
If I get this right the clients boot a read only image from the server, right?

What's the main concept then to have persistent settings for the users? What comes to my mind as solution is
to set up and configure NFS, chroot into the client jail and temper the ```
/etc/fstab
```Rebuild the client image afterwards and mount the home directories using NFS.

Is this the way to go for the solution or did I simply misconfigure something?

Looking forward to your replies.

_Morpheus_

---

### Post by _Morpheus_ on 2010-02-25
Wrong forum?

---


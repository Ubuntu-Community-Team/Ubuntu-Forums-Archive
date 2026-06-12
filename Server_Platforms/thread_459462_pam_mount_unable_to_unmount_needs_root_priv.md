---
title: "pam_mount unable to unmount needs root priv"
date: 2007-05-30
forum: Server Platforms
---

### Post by kalisto on 2007-05-30
From pam_mount developer Jan Engelhard sourceforge mailing list:
> "pam_mount *needs* the root privileges, but Ubuntu's PAM configuration
decided to throw them away after the login sequence completed."

From Ubuntu Feisty Fawn user Kalisto:

"When using loopback encrypted file systems this is a security issue, user logs out but the device is not umounted!!
Without pam_mount debug option set this is not immediately apparent to the user!

I have followed the instructions on: [http://felipe-alfaro.org/blog/2006/08/19/encrypted-home-on-ubuntu-using-cryptoloop/](http://felipe-alfaro.org/blog/2006/08/19/encrypted-home-on-ubuntu-using-cryptoloop/)

To create a loopback encrypted home directory with pam_mount.
The dir mounts ok and seemes to work however on logout I get > " error setting uid to 0"
lsof -n | grep /home/crypto comes up empty.

I have included a pam_mount debug output for the login and logout process:
For easier viewing: [http://rafb.net/p/HLVzwm40.nln.html](http://rafb.net/p/HLVzwm40.nln.html)

> user@trinity:su crypto
pam_mount(pam_mount.c:461) pam_sm_open_session: real uid/gid=0:1001, effective uid/gid=0:1001
pam_mount(readconfig.c:418) checking sanity of volume record (/home/crypto.img)
pam_mount(pam_mount.c:476) about to perform mount operations

pam_mount(mount.c:368) information for mount:
pam_mount(mount.c:369) ----------------------
pam_mount(mount.c:370) (defined by globalconf)
pam_mount(mount.c:373) user: crypto
pam_mount(mount.c:374) server:

pam_mount(mount.c:375) volume: /home/crypto.img
pam_mount(mount.c:376) mountpoint: /home/crypto
pam_mount(mount.c:377) options: loop,user,exec,encryption=aes,keybits=128
pam_mount(mount.c:378) fs_key_cipher: aes-128-ecb

pam_mount(mount.c:379) fs_key_path: /home/crypto.key
pam_mount(mount.c:380) use_fstab: 0
pam_mount(mount.c:381) ----------------------
pam_mount(mount.c:177) realpath of volume "/home/crypto" is "/home/crypto"

pam_mount(mount.c:182) checking to see if /home/crypto.img is already mounted at /home/crypto
pam_mount(mount.c:755) /home/crypto.img already seems to be mounted at /home/crypto, skipping
pam_mount(pam_mount.c:123) clean system authtok (0)

pam_mount(misc.c:264) command: /usr/sbin/pmvarrun [-u] [crypto] [-o] [1]
pam_mount(misc.c:341) set_myuid(pre): real uid/gid=0:1001, effective uid/gid=0:1001
pam_mount(misc.c:376) set_myuid(post): real uid/gid=0:1001, effective uid/gid=0:1001

pam_mount(pam_mount.c:360) pmvarrun says login count is 3
pam_mount(pam_mount.c:493) done opening session
pam_mount(pam_mount.c:106) Clean global config (0)

===========================================================================

> crypto@trinity:exit

exit
pam_mount(pam_mount.c:535) received order to close things
pam_mount(pam_mount.c:536) real and effective user ID are 1001 and 1001.
pam_mount(misc.c:264) command: /usr/sbin/pmvarrun [-u] [crypto] [-o] [-1]

pam_mount(misc.c:341) set_myuid(pre): real uid/gid=1001:1001, effective uid/gid=1001:1001
pam_mount(misc.c:346) error setting uid to 0
pam_mount(pam_mount.c:360) pmvarrun says login count is 2
pam_mount(pam_mount.c:564) crypto seems to have other remaining open sessions

pam_mount(pam_mount.c:569) pam_mount execution complete
pam_mount(pam_mount.c:535) received order to close things
pam_mount(pam_mount.c:536) real and effective user ID are 1001 and 1001.
pam_mount(misc.c:264) command: /usr/sbin/pmvarrun [-u] [crypto] [-o] [-1]

pam_mount(misc.c:341) set_myuid(pre): real uid/gid=1001:1001, effective uid/gid=1001:1001
pam_mount(misc.c:346) error setting uid to 0
pam_mount(pam_mount.c:360) pmvarrun says login count is 1
pam_mount(pam_mount.c:564) crypto seems to have other remaining open sessions

pam_mount(pam_mount.c:569) pam_mount execution complete
pam_mount(pam_mount.c:106) Clean global config (0)

===========================================================================
Entry in /etc/security/pam_mount.conf
> 
volume crypto auto - /home/crypto.img /home/crypto loop,user,exec,encryption=aes,keybits=128 aes-128-ecb /home/crypto.key

/Kalisto"

I have also added this as a bug repot: [https://bugs.launchpad.net/ubuntu/+source/libpam-mount/+bug/117736]("https://bugs.launchpad.net/ubuntu/+source/libpam-mount/+bug/117736")

---


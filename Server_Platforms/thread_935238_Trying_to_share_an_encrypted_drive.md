---
title: "Trying to share an encrypted drive"
date: 2008-10-01
forum: Server Platforms
---

### Post by Run Seven on 2008-10-01
Hello all,

I am currently trying to set up a fileserver based on Ubuntu. I installed Ubuntu on a flash drive, and sharing normals folders on the flash drive works just fine. 

Encouraged by the description of pam_mount - " This module is aimed at environments with SMB (Samba or Windows NT) or NCP (Netware or Mars-NWE) servers that Unix users wish to access transparently. It facilitates access to private volumes of these types well. The module also supports mounting  home directories using loopback encrypted filesystems." - I tried to encrypt a hard disk I added and share it with samba. The idea was to use the same password for the encryption of the hard drive and for the user account in samba. So, I encrypted the hard disk /dev/sda1 with luksFormat, added the user "ntheis" to samba and used the same password for both, then trying to make samba mount the hard drive once the user "ntheis" connects to the server.

My pam_mount.conf.xml looks like this:

```
<pam_mount>
    <volume
        user="ntheis"
        fstype="crypt"
        server="j1112801"
        path="/dev/sda1"
        mountpoint="/home/ntheis/crypt"
	options="loop,user,exec,encryption=aes,keybits=256"
    />
-->
<!--
NOTE: Special characters like < > and & require escaping them to &lt; &gt;
and &amp; according to the XML standard. Though, you really should not use
them in pathnames.

Do not use comments inside tags like <lsof></lsof> - the case is not
handled by the parser.
-->


<!-- Turn on if you want to debug why some volume cannot be mounted etc.
This can be overriden by user's local configuration. This will also affect
the pmvarrun helper program. To disable, use enable="0" or comment it out
entirely. -->
<debug enable="1" />


<!--
Create mountpoint if it does not exist yet. This is a good thing.

If enabled, and a mountpoint was created by pam_mount, the mountpoint will
be removed again on logout. To disable this behavior, use remove="false".
-->
<mkmountpoint enable="1" remove="true" />


<!-- Loopback device to use to run fsck on loopback filesystems. -->
<fsckloop device="/dev/loop7" />


<!--
Users' local configuration file (if there is none, comment this parameter
out). Will be read as ~/<file>.

Note: you must include either options_allow or options_deny to use this
directive. I recommend also including options_require.

Individual users may define additional volumes to mount if allowed by
pam_mount.conf.xml (usually ~/.pam_mount.conf.xml). The volume keyword is
the only valid keyword in these per-user configuration files. If the
luserconf parameter is set in pam_mount.conf.xml, allowing user-defined
volumes, users may mount and unmount any volumes they specify. The mount
operation is executed under the user account, not with root permissions.

<luserconf name=".pam_mount.conf.xml" />
-->
<luserconf name="pam_mount.conf.xml" />

<!--
These directives determine which options may be specified in a user config
file (luserconf). You must include one of these directives if you have a
luserconf directive. You may not include both directives.

If you have an options_allow directive, then the options listed in that
directive wil be allowed, and all others rejected. If you have an
options_deny directive, then the options listed will be denied, and all
others permitted.

You may use the wildcard '*' to match all options. I recommend not
permitting the suid and dev options.
-->

<mntoptions allow="*" />
<!--
<mntoptions deny="suid,dev" />
<mntoptions allow="*" />
<mntoptions deny="*" />
-->


<!--
The options listed in this directive are required for all volumes from a
user config file. That is, any volume specified in a user config file that
does not include these options will be ignored.

Note: you must make sure that a required option is permitted (either by
including it in options_allow, or by not including it in options_deny).

I recommend requiring at least nosuid and nodev.

This is ignored completely if the volume is configured to get its options
and mount point from /etc/fstab.
-->
<mntoptions require="nosuid" />


<!--
Commands to mount/unmount volumes. They can take parameters, as shown.

If you change the -p0 argument for lclmount, you'll need to modify the
source in mount.c (it sends the password to the stdin file descriptor of
the child process - look for STDIN_FILENO).

You can specify either absolute paths, or relative ones, in which case
$PATH will be searched. Since some login programs really behave
antisocial, pam_mount will always set its own $PATH.
-->

<path>/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin:/dev/sda1:</path>

<lsof>lsof %(MNTPT)</lsof>

<fsck>fsck -p %(FSCKTARGET)</fsck>

<losetup>losetup -p0 "%(before=\"-e\" CIPHER)"
    "%(before=\"-k\" KEYBITS)" %(FSCKLOOP) %(VOLUME)</losetup>

<unlosetup>losetup -d %(FSCKLOOP)</unlosetup>

<cifsmount>mount -t cifs //%(SERVER)/%(VOLUME) %(MNTPT) -o
    "user=%(USER),uid=%(USERUID),gid=%(USERGID)%(before=\",\" OPTIONS)"</cifsmount>

<davmount>mount -t davfs %(SERVER)/%(VOLUME) %(MNTPT) -o
	"username=%(USER),uid=%(USERUID),gid=%(USERGID)%(before=\",\"
	OPTIONS)"</davmount>

<smbmount>smbmount //%(SERVER)/%(VOLUME) %(MNTPT) -o
    "username=%(USER),uid=%(USERUID),gid=%(USERGID)%(before=\",\" OPTIONS)"</smbmount>

<smbumount>smbumount %(MNTPT)</smbumount>

<ncpmount>ncpmount %(SERVER)/%(USER) %(MNTPT) -o
    "pass-fd=0,volume=%(VOLUME)%(before=\",\" OPTIONS)"</ncpmount>

<ncpumount>ncpumount %(MNTPT)</ncpumount>

<fusemount>mount.fuse %(VOLUME) %(MNTPT) "%(before=\"-o \" OPTIONS)"</fusemount>

<fuseumount>fusermount -u %(MNTPT)</fuseumount>

<!--<truecryptmount>truecrypt %(VOLUME) %(MNTPT)</truecryptmount> <truecryptumount>truecrypt -d %(MNTPT)</truecryptumount>-->

<!-- Linux supports lazy unmounting (-l). May be dangerous for encrypted
volumes. May also break loopback mounts because loopback devices are not
freed. Need to unmount mount point (not volume!) to support SMB mounts,
etc. -->
<umount>umount %(MNTPT)</umount>


<!-- On OpenBSD try "/usr/local/bin/mount_ehd" (included in pam_mount
package). -->
<lclmount>mount -p0 -t %(FSTYPE) %(VOLUME) %(MNTPT)
	"%(before=\"-o\" OPTIONS)"</lclmount>

<cryptmount>mount -t crypt "%(before=\"-o \" OPTIONS)"
	%(VOLUME) %(MNTPT)</cryptmount>

<nfsmount>mount %(SERVER):%(VOLUME) %(MNTPT)
	"%(before=\"-o\" OPTIONS)"</nfsmount>

<!-- mntcheck utility for BSDs which lack /etc/mtab -->
<mntcheck>mount</mntcheck>

<pmvarrun>pmvarrun -u %(USER) -o %(OPERATION)</pmvarrun>

<!--
Volumes that will be mounted when user triggers the pam_mount module
(usually at login).

    <volume
        user="*" | pgrp="foo" | sgrp="bar"
        invert="1"
        fstype="auto"
        server="..."
        path="..."
        mountpoint="..."
        options="..."
        fskeycipher="..."
        fskeypath="..."
    />


USER is a user for which a volume rule applies, "*" selects all users.

A volume with PGRP attribute will be mounted when a user has that
particular group as its primary group. A volume with SGRP attribute will
be mounted when the user has the group as either primary or secondary.

USER, PGRP and SGRP are mutually exclusive. If neither is present,
USER="*" is assumed.

INVERT will invert the sense of the USER, PGRP or SGRP selector, thereby
making it possible to specify, e.g. "all users not in group xyz".


FSTYPE can be any filesystem type. If /bin/mount or the kernel does not
support it, you will get an error. You can use the special keyword "auto"
which automatically lets the kernel choose a matching filesystem. Note
that the kernel's auto feature only works with currently loaded
filesystems (listed in /proc/filesystem), so you will have to load the
necessary modules _first_ for them to be recognized with "auto". If this
attribute is not present, "auto" is assumed.

The "cifs", "davfs", "smbfs", "ncpfs", "fuse" and "truecrypt" types
override the identically-named kernel filesystems and use the
helper programs as defined above.


SERVER defines the server from which to source. The exact volume path
depends on the filesystem type. SMB uses //SERVER/VOLUME, NFS uses
SERVER:VOLUME. davfs uses SERVER/VOLUME. The attribute may be absent.


PATH specifies the location of the volume, locally or on the server (if
applies), respectively. This attribute is mandatory.


MOUNTPOINT specifies the destination directory onto which the volume is
mounted. '~' expands to the user's home directory as present in the passwd
database, according to sh semantics. "~name" is not supported. If this
attribute is omitted, the location is read from /etc/fstab, which also
requires PATH to be the device of an fstab entry.


OPTIONS specifies mount options. If omitted, and /etc/fstab is used (see
MOUNTPOINT), then the options are also sourced from fstab.


Note that if the mount command has specified an option, e.g. %(KEYBITS)
and you do not specify a value, a warning is printed in the log. The
warning can usually be ignored, except when the option is mandatory.

SMB mounts require the `smbmount` and `smbumount` programs, NCP `ncpmount`
and `ncpumount`. Both SMB and NCP work in ~/.pam_mount.conf.xml.


General examples:

    <volume user="user" fstype="smbfs" server="krueger" path="public"
        mountpoint="/home/user/krueger" />

    <volume user="user" fstype="ncpfs" server="krueger" path="public"
        mountpoint="/home/user/krueger" options="user=user.context" />

    <volume fstype="smbfs" server="krueger" path="homes"
        mountpoint="/home/%(USER)/remote" options="dmask=0711" />

    <volume fstype="davfs" server="https://dev.computergmbh.de/"
        path="/svn/libHX/trunk" mountpoint="/projects/libHX" />

You can use ~ to use whatever home directory the user has (therefore you
can distribute home directories along more than one location. This is
useful for pam_chroot:

    <volume path="/bin" mountpoint="~/bin" options="bind" />

For FUSE mounts, use something like this:

    <volume fstype="fuse" path="sshfs#%(USER)@fileserver:"
        mountpoint="~" />

    <volume fstype="nfs" server="fileserver" path="/home/%(USER)"
        mountpoint="~" />

Some more examples:

    <volume path="/home/%(USER).img" mountpoint="~" fskeycipher="aes-256-ecb"
        fskeypath="/etc/ehd/%(USER)" />

Windows 2000, which requires a domain specified (does it really? works for
me without -jengelh), example (thanks John Knox):

    <volume fstype="smbfs" server="viper" path="%(USER)"
        mountpoint="~" options="dmask=0751,workgroup=WINDOWS_DOMAIN" />

-->


<!--
Linux encrypted home directory examples, using dm_crypt:

crypt mounts require a kernel with CONFIG_BLK_DEV_DM and CONFIG_DM_CRYPT
enabled as well as all the used ciphers (e.g. CONFIG_CRYPTO_AES_586,
CONFIG_CRYPTO_TWOFISH, etc.). crypt mounts must be in the global config
file /etc/security/pam_mount.conf.xml.

Linux encrypted home directory examples, using dm_crypt:

    <volume fstype="crypt" path="/dev/sda2" mountpoint="/home/user"
        options="cipher=aes" fskeycipher="aes-256-ecb"
        fskeypath="/home/user.key" />

cryptoloop mounts require a kernel with CONFIG_BLK_DEV_CRYPTOLOOP enabled.
cryptoloop mounts must be in the global config
/etc/security/pam_mount.conf.xml. Linux encrypted home directory examples,
using cryptoloop:

    <volume path="/dev/hda123" mountpoint="/home/user"
        options="loop,encryption=aes" />

    <volume path="/home/user.img" mountpoint="/home/user"
        options="loop,user,exec,encryption=aes,keybits=256" />

    <volume path="/home/user.img" />

    <volume path="/home/user.img" fskeycipher="aes-256-ecb"
        fskeypath="/home/user4.key" />

The last two examples (^^) need a line like the following in /etc/fstab:

    /home/user4.img /home/user4 xfs user,loop,encryption=aes,keybits=256,noauto 0 0

OpenBSD encrypted home directory example (see also lclmount above):

    <volume path="/home/user.img" mountpoint="/home/user"
        options="svnd0" />

Volatile tmpfs mount with restricted size (thanks to Mike Hommey for this
example):

    <volume user="test" fstype="tmpfs" path="none" mountpoint="/home/test"
        options="size=10M,uid=test,gid=users,mode=0700" />

See http://www.tldp.org/HOWTO/Loopback-Encrypted-Filesystem-HOWTO.html to
learn how to create a encrypted loopback filesystem.

If the volume's password is different than the user's login password, the
following technique may be used (see also README):

{...} are placeholders, insert the proper value there!

1.  Create a file containing the volume's password (FS key). If you are
    using pam_mount to mount an loopback encrypted volume, this password
    should be generated with /dev/urandom.

    Simple example:
    echo {volume password} | openssl enc -aes-256-ecb >/home/user.key
    Encrypt this file using the user's login password as the key.

    Verbose loopback encrypted volume example:
    a.  dd if=/dev/urandom of=/home/user.img bs=1M count={image size in MB}
    b.  dd if=/dev/urandom bs=1c count={keysize/8} | \
        openssl enc -{fs key cipher} >/home/user.key
        Encrypt this file using the user's login password as the key.
    c.  modprobe -q cryptoloop
    d.  openssl enc -d -{fs key cipher} -in /home/user.key | \
        losetup -e aes -k {keysize} -p0 /dev/loop0 /home/user.img
    e.  mkfs -t ext2 /dev/loop0
    f.  losetup -d /dev/loop0

3.  In pam_mount.conf.xml:
        a.  Set the fs key cipher variable to the cipher used
            (ie: aes-256-ecb).
        b.  Set the fs key path variable to the key's path
            (ie: /home/user.key)

4.  If a user changes his login password, regenerate the efsk that was
    created in step 1b.  A script named passwdehd is provided to do this.

If FSKEYCIPHER is empty, then the user's login password is also the
volume's password.
-->

<!--
When pam_mount is not used with "use_first_pass" or "try_first_pass" in
the PAM configuration files (/etc/pam.d/), it will have to ask for a
password. This is also the case if pam_mount is the first auth module
in the block.
-->
<msg-authpw>pam_mount password:</msg-authpw>

<!--
In case the 'session' PAM block does not have the password (e.g. on su
from root to user), it will ask again.
-->
<msg-sessionpw>reenter password for pam_mount:</msg-sessionpw>

</pam_mount>
```

common_auth (which is included in the samba file in /etc/pam.d) looks like this:

```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth	optional	pam_smbpass.so try_first_pass
auth	requisite	pam_unix.so nullok_secure
#auth	optional	pam_smbpass.so migrate missingok
```

The /var/log/samba for "freakbox" (the machine I am trying to connect to the encrypted hard drive /dev/sda1 with) shows the following log:

```
[2008/10/01 18:51:19, 0] lib/util_sock.c:write_data(562)
  write_data: write failure in writing to client 192.168.0.100. Error Connection reset by peer
[2008/10/01 18:51:19, 0] lib/util_sock.c:send_smb(761)
  Error writing 4 bytes to client. -1. (Connection reset by peer)
pam_mount(rdconf1.c:554) path to luserconf set to /home/ntheis/pam_mount.conf.xml
pam_mount(pam_mount.c:460) Entered pam_mount session stage
pam_mount(pam_mount.c:481) back from global readconfig
pam_mount(pam_mount.c:485) going to readconfig user
pam_mount(rdconf1.c:554) path to luserconf set to /home/ntheis/pam_mount.conf.xml
pam_mount(pam_mount.c:490) back from user readconfig
pam_mount(pam_mount.c:512) error trying to retrieve authtok from auth code
pam_mount(pam_mount.c:202) enter read_password
pam_mount(pam_mount.c:515) error trying to read password
pam_mount(pam_mount.c:548) done opening session (ret=7)
pam_mount(pam_mount.c:116) Clean global config (0)
[2008/10/01 18:51:24, 1] smbd/service.c:make_connection_snum(1033)
  freakbox (192.168.0.100) connect to service crypt initially as user ntheis (uid=1001, gid=1001) (pid 6085)
[2008/10/01 18:51:26, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/sda1 failed. Permission denied
```

Needless to say that /dev/sda1 is not mounted successfully. What can I do to solve the problem? I am quite a linux newbie, and I have spent three evenings now trying to make the hard drive mount, I have to admit. Thanks for any help.

---

### Post by hyper_ch on 2008-10-01
wouldn't a truecrypt container be simpler to use?

---

### Post by Run Seven on 2008-10-01
Well yes, I could run Truecrypt on the clients and create a container on the file server. But this creates problems if I want to access the container with more than one client at a time. And I have to admit that now that I have tried it this way I want to succeed with it ;-)

---

### Post by hyper_ch on 2008-10-01
I don't think multiple people can uncrypt an encrypted partition at the same time...

---

### Post by Run Seven on 2008-10-01
As I understand it, it is the fileserver that uncrypts the partition, and the clients that get unencrypted data. Why shouldn't more than one user be able to access the same partition?

---

### Post by hyper_ch on 2008-10-01
well, no clue :) good luck with it :)

---

### Post by Run Seven on 2008-10-04
Hello all,

I am still trying to make this thing work but I haven't come very far, despite a complete reinstall and long sessions until the early morning.

I have now tried to make this thing work for switching users, and I get this error message:

```
ntheis@j1112801:/home/j1112801$ su ntheis
Passwort: 
pam_mount(mount.c:873) checking for encrypted filesystem key configuration
pam_mount(mount.c:899) about to start building mount command
pam_mount(misc.c:285) command: truecrypt-nl [-t] [/dev/sda1] [/home/ntheis/crypt] 
pam_mount(misc.c:56) set_myuid<pre>: (uid=1000, euid=0, gid=1001, egid=1001)
pam_mount(misc.c:56) set_myuid<post>: (uid=0, euid=0, gid=1001, egid=1001)
pam_mount(mount.c:104) mount errors:
pam_mount(mount.c:107) pam_mount(spawn.c:134) execvp: Permission denied
pam_mount(mount.c:933) waiting for mount
Dateisystem   Typ   1K&#8208;Blöcke   Benutzt Verfügbar Ben% Eingehängt auf
/dev/sdb1     ext3     7387200   2616500   4398396  38% /
proc          proc           0         0         0   -  /proc
/sys         sysfs           0         0         0   -  /sys
varrun       tmpfs      513492       220    513272   1% /var/run
varlock      tmpfs      513492         0    513492   0% /var/lock
udev         tmpfs      513492        48    513444   1% /dev
devshm       tmpfs      513492        12    513480   1% /dev/shm
devpts      devpts           0         0         0   -  /dev/pts
lrm          tmpfs      513492     39760    473732   8% /lib/modules/2.6.24-19-generic/volatile
securityfs
        securityfs           0         0         0   -  /sys/kernel/security
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon           0         0         0   -  /home/j1112801/.gvfs
pam_mount(pam_mount.c:538) mount of /dev/sda1 failed

```

When I try to login via samba, I still get the text in the applicable log file in samba:

```
[2008/10/04 12:18:21, 0] lib/util_sock.c:write_data(562)
  write_data: write failure in writing to client 192.168.0.100. Error Connection reset by peer
[2008/10/04 12:18:21, 0] lib/util_sock.c:send_smb(761)
  Error writing 4 bytes to client. -1. (Connection reset by peer)
pam_mount(pam_mount.c:460) Entered pam_mount session stage
pam_mount(pam_mount.c:481) back from global readconfig
pam_mount(pam_mount.c:483) per-user configurations not allowed by pam_mount.conf.xml
pam_mount(pam_mount.c:512) error trying to retrieve authtok from auth code
pam_mount(pam_mount.c:202) enter read_password
pam_mount(pam_mount.c:515) error trying to read password
pam_mount(pam_mount.c:548) done opening session (ret=7)
pam_mount(pam_mount.c:460) Entered pam_mount session stage
pam_mount(pam_mount.c:481) back from global readconfig
pam_mount(pam_mount.c:483) per-user configurations not allowed by pam_mount.conf.xml
pam_mount(pam_mount.c:512) error trying to retrieve authtok from auth code
pam_mount(pam_mount.c:202) enter read_password
pam_mount(pam_mount.c:515) error trying to read password
pam_mount(pam_mount.c:548) done opening session (ret=7)
pam_mount(pam_mount.c:116) Clean global config (0)
[2008/10/04 12:18:23, 1] smbd/service.c:make_connection_snum(1033)
  freakbox (192.168.0.100) connect to service crypt initially as user ntheis (uid=1001, gid=1001) (pid 6246)
```

For everybody else this seems to work easily, what am I doing wrong? 

Thanks in advance
Run Seven

---

### Post by LongSteve on 2008-11-20
Has anyone managed to get this working yet?  I've been attempting the same thing and haven't had any luck.

I think that it's basically impossible if you have 'encrypted passwords = true' in your Samba config.  Encrypting the passwords means that the server only has a copy of the hashed password, and does not receive the plain text password in order to pass it into PAM and hence pam_mount.  I have tried turning encrypted passwords off, and modifying my Windows XP machine to allow sending plain text passwords, but this doesn't work either.  Although it looks like it should because if you install pam-script you can see that the auth module does get the users plain text password.  pam_mount still fails however!

If you leave encrypted passwords on, it might be possible to add a second LUKS key to your encrypted device that equates to the NT password hash.  Then, assuming this gets passed into PAM by Samba, pam_mount (or a custom script) could use it to open the encrypted drive and mount it.  I have a feeling this won't work either though because I've read that Samba ignores all PAM operations when you enable encrypted passwords.

In my case, I can get around all this by having my users drives mounted by pam_mount when they attach with OpenVPN, since that's going to be the only way to access the box.  I just hope that works with pam_mount!

Cheers,

Steve

---

### Post by fritz276 on 2009-02-16
I just stumbled upon this with via Google; I exactly want the same: Have a Windows User login to a SAMBA share which then automatically mounts his LUKS encrypted HOME.

Any further success?

---


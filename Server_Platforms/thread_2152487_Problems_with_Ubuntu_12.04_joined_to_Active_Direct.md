---
title: "Problems with Ubuntu 12.04 joined to Active Directory"
date: 2013-06-07
forum: Server Platforms
---

### Post by deoren on 2013-06-07
Thanks in advance for reading this. Any tips/tricks you can offer will be most appreciated!

Following various guides:


[LIST]
[*] [https://wiki.umn.edu/Main/UbuntuAndActiveDirectory](https://wiki.umn.edu/Main/UbuntuAndActiveDirectory)
[*] [http://www.stuartellis.eu/articles/linux-with-active-directory/](http://www.stuartellis.eu/articles/linux-with-active-directory/)
[*] [https://www.lib.auburn.edu/staff/syswiki/Clyde#Winbind_Configuration](https://www.lib.auburn.edu/staff/syswiki/Clyde#Winbind_Configuration)
[*][http://ubuntuforums.org/showthread.php?t=91510](http://ubuntuforums.org/showthread.php?t=91510)
[*][http://serverfault.com/questions/135396/](http://serverfault.com/questions/135396/)
[*][https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)
[/LIST]

I've successfully joined a test Ubuntu 10.04.x system to Active Directory and configured PAM to allow AD logins via SSH. I tried the same steps with Ubuntu 12.04 and I'm not getting the same results. I can run **wbinfo -u** and **wbinfo -g** and get back results. I've also managed to run **wbinfo -t**, **net ads testjoin** and gotten back positive results.

However when I try to SSH into the Ubuntu 12.04 server (poetry.example.com) from another Ubuntu box my login is rejected. The "Received disconnect from..." bit is me giving up by pressing Ctrl-C.

Snippet from **/var/log/auth.log**:

```
Jun  7 19:45:05 poetry sshd[4679]: Invalid user bob from 192.168.1.7
Jun  7 19:45:05 poetry sshd[4679]: input_userauth_request: invalid user bob [preauth]
Jun  7 19:45:07 poetry sshd[4679]: pam_unix(sshd:auth): check pass; user unknown
Jun  7 19:45:07 poetry sshd[4679]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=pickles.example.com
Jun  7 19:45:07 poetry sshd[4679]: pam_winbind(sshd:auth): getting password (0x00000388)
Jun  7 19:45:07 poetry sshd[4679]: pam_winbind(sshd:auth): pam_get_item returned a password
Jun  7 19:45:09 poetry sshd[4679]: Failed password for invalid user bob from 192.168.1.7 port 45789 ssh2
Jun  7 19:56:25 poetry sshd[1815]: Received disconnect from 192.168.1.7: 11: disconnected by user
```

```

root@poetry:~# net ads testjoin
Join is OK

```

```

root@poetry:~# wbinfo -t
checking the trust secret for domain EXAMPLE via RPC calls succeeded

```

As I mentioned I've successfully configured a 10.04 LTS box and have it working *mostly* well (if you don't count the long delays on login), so I'm unsure if I should post those configs or post the 12.04 ones. I'm going to assume that the 12.04 ones would be most relevant.

The **/etc/samba/smb.conf** file:

```

# References:

# https://wiki.umn.edu/Main/UbuntuAndActiveDirectory
# http://www.stuartellis.eu/articles/linux-with-active-directory/
# http://ubuntuforums.org/showthread.php?t=91510
# http://serverfault.com/questions/135396/
# https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto

[global]

workgroup = EXAMPLE
realm = EXAMPLE.COM
netbios name = poetry
server string = %h server (Samba %v, Ubuntu)
dns proxy = no
encrypt passwords = true
#log level = 3
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action


# AD Membership pointers
security = ADS

# NTLMv2 Security options
client ntlmv2 auth = yes
ntlm auth = no

idmap backend = rid:EXAMPLE.COM=16777216-33554431
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431

winbind enum groups = yes
winbind enum users = yes
winbind use default domain = yes
winbind refresh tickets = yes
winbind separator = +
winbind nested groups = Yes
winbind normalize names = no

template shell = /bin/bash
template homedir = /home/%D/%U
domain master = no
local master = no
preferred master = no
os level = 0
guest account = nobody
map to guest = Bad User

# Printer options
load printers = no
printable = no

```

The **/etc/krb5.conf** file:

```

# https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto

[logging]
default = FILE:/var/log/krb5libs.log
kdc = FILE:/var/log/krb5kdc.log
admin_server = FILE:/var/log/kadmind.log

[libdefaults]
default_realm = EXAMPLE.COM
dns_lookup_realm = yes
dns_lookup_kdc = yes
ticket_lifetime = 24000

default_tkt_enctypes = aes-256-cts arcfour-hmac-md5
default_tgs_enctypes = aes-256-cts arcfour-hmac-md5

[realms]
EXAMPLE.COM = {
        kdc = kerberos.example.com
        admin_server = kerberos.example.com
        default_domain = EXAMPLE.COM
}

[domain_realm]
.example.com = EXAMPLE.COM
example.com = EXAMPLE.COM

```

The /etc/nsswitch.conf file:
```

# https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto
passwd:         compat  winbind
group:          compat  winbind
shadow:         compat  winbind

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

Then the PAM configuration files, which I suspect is the problem somehow. I've broken out the contents of each, leaving the comments behind. I've then included the contents of the files together without comments:

**/etc/pam.d/common-account**
```

# here are the per-package modules (the "Primary" block)
account    sufficient    pam_unix.so 
account    sufficient    pam_winbind.so 
# here's the fallback if no module succeeds
account    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```

**/etc/pam.d/common-auth**
```

# here are the per-package modules (the "Primary" block)
auth    sufficient    pam_unix.so nullok_secure
auth    sufficient    pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login require_membership_of=Lib_poetry_login try_first_pass
# here's the fallback if no module succeeds
auth    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```

**/etc/pam.d/common-session**
```

# here are the per-package modules (the "Primary" block)
session    [default=1]            pam_permit.so
# here's the fallback if no module succeeds
session    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session    required            pam_permit.so
# The pam_umask module will set the umask according to the system default in
# /etc/login.defs and user settings, solving the problem of different
# umask settings with different shells, display managers, remote sessions etc.
# See "man pam_umask".
session optional            pam_umask.so
# and here are more per-package modules (the "Additional" block)
session    required    pam_unix.so 
session    sufficient            pam_winbind.so 
session    optional            pam_ck_connector.so nox11

# https://help.lib.auburn.edu/redmine/issues/12202
session required    pam_mkhomedir.so umask=0022 skel=/etc/skel
# end of pam-auth-update config

```

**/etc/pam.d/common-password**
```

#
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define the services to be
# used to change user passwords.  The default is pam_unix.

# Explanation of pam_unix options:
#
# The "sha512" option enables salted SHA512 passwords.  Without this option,
# the default is Unix crypt.  Prior releases used the option "md5".
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs.
#
# See the pam_unix manpage for other options.

# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
password        [success=2 default=ignore]      pam_unix.so obscure sha512
password        [success=1 default=ignore]      pam_winbind.so use_authtok try_first_pass
# here's the fallback if no module succeeds
password        requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
password        required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```

Here are all four files listed together without comments:

```

auth    sufficient    pam_unix.so nullok_secure
auth    sufficient    pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login require_membership_of=SRV_poetry_login try_first_pass
auth    requisite            pam_deny.so
auth    required            pam_permit.so

account    sufficient    pam_unix.so 
account    sufficient    pam_winbind.so 
account    requisite            pam_deny.so
account    required            pam_permit.so

session    [default=1]            pam_permit.so
session    requisite            pam_deny.so
session    required            pam_permit.so
session optional            pam_umask.so
session    required    pam_unix.so 
session    sufficient            pam_winbind.so 
session    optional            pam_ck_connector.so nox11
session required    pam_mkhomedir.so umask=0022 skel=/etc/skel

password        [success=2 default=ignore]      pam_unix.so obscure sha512
password        [success=1 default=ignore]      pam_winbind.so use_authtok try_first_pass
password        requisite                       pam_deny.so
password        required                        pam_permit.so

```

Just in case it is relevant, here is the **/etc/pam.d/sshd** file:
```

@include common-auth
account    required     pam_nologin.so
@include common-account
@include common-session
session    required     pam_limits.so
session    required     pam_env.so user_readenv=1 envfile=/etc/default/locale

```

If you can think of any other files I can post please let me know.

---

### Post by deoren on 2013-06-08
After a lot of hair pulling I think I've got it mostly figured out. I'm not sure which change is responsible for the working setup, but I ended up tweaking these files:


[LIST]
[*]/etc/samba/smb.conf
[*]/etc/pam.d/common-password
[*]/etc/pam.d/common-session
[*]/etc/network/interfaces
[*]/etc/resolvconf/resolv.conf.d/tail
[/LIST]

Between /etc/network/interfaces and /etc/resolv... I added **dns-search example.com **and **domain example.com.**

With the /etc/pam.d/* files I made sure the **sufficient** control flag was being used for both _**pam_unix.so**_ and _**pam_winbind.so**_ and moved the _**pam_mkhomedir.so**_ line to the top of the file.

For **/etc/samba/smb.conf** I changed the syntax for **idmap** sections:

```

-idmap backend = rid:EXAMPLE.COM=16777216-33554431
 idmap uid = 16777216-33554431
 idmap gid = 16777216-33554431
+idmap config EXAMPLE:backend = rid
+idmap config EXAMPLE:range = 16777216-33554431

```

**testparm** still complains, but AD logins are working at this point. I'm going to go back and reverse changes until I find the bare minimum that allows logins to still work properly. I'm going to target the network interface and resolv conf files first.

---

### Post by deoren on 2013-06-11
I tinkered some more, and as far as I know I've determined the essential files/config options for joining an Ubuntu 12.04 box to an AD domain. I found the biggest problem was the syntax for **/etc/samba/smb.conf** which I mentioned in my last post. Once that change was made logins worked. Unfortunately I haven't fixed the long delay (up to 2 minutes) when logging in (winbind seems to poll all group ids), but at this point I suspect it is due to either the use of the **rid** backend or using nested AD groups. I don't suspect the latter because I'm allowed to login *prior* to this line in [B]/etc/pam.d/common-auth:
[/B]
```

auth    sufficient    pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login require_membership_of=Lib_poetry_login try_first_pass

```

Go figure.
[HR][/HR]
Now, to the list of files that are required to _join an Ubuntu 12.04 box to the domain_, _allow SSH logins from a specific AD group_ and _auto-create home directories for users logging in for the first time_ (*locking access to **just** them*).

**/etc/network/interfaces**

* static ip
* _dns-nameservers_ list
* _dns-search example.com_ (seems to be optional, but is recommended)

```

# Note: This is a conf file for Ubuntu 12.04 LTS which handles /etc/resolv.conf
#       differently than 10.04 and 11.x systems.


# References:
#  http://askubuntu.com/questions/130452/how-do-i-add-a-dns-server-via-resolv-conf
#  http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/
#  https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/990660

# The loopback network interface
auto lo
iface lo inet loopback


# Specify here instead of /etc/resolv.conf
dns-nameservers 192.168.41.3 192.168.2.10 192.168.10.13
dns-search example.com


# According to bug 990660 'domain example.com' isn't needed in 
# /etc/resolvconf/resolv.conf.d/tail as 'dns-search' is already
#  specified here and is "functionally equivalent"


# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.172.190
netmask 255.255.252.0
gateway 192.168.172.1

```

**/etc/nsswitch.conf**
```

# https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto
passwd:         compat  winbind
group:          compat  winbind
shadow:         compat  winbind


hosts:          files dns
networks:       files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis

```

**/etc/hostname**

This needs to be properly set. In our case, for _poetry.example.com_ we need to use _poetry_ as our hostname:

```

poetry

```

**/etc/hosts**

Format: **ip address** **fqdn** **shortname**

```

192.168.1.190  poetry.example.com  poetry

```

**/etc/krb5.conf**

```

# https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto


[logging]
default = FILE:/var/log/krb5libs.log
kdc = FILE:/var/log/krb5kdc.log
admin_server = FILE:/var/log/kadmind.log


[libdefaults]
default_realm = EXAMPLE.COM
dns_lookup_realm = yes
dns_lookup_kdc = yes
ticket_lifetime = 24000


# I'm noticing that in some examples the ticket encoding type isn't specified
# Perhaps _not_ specify it here for greater compatibility?
default_tkt_enctypes = aes-256-cts arcfour-hmac-md5
default_tgs_enctypes = aes-256-cts arcfour-hmac-md5



[realms]
EXAMPLE.COM = {
        kdc = kerberos.example.com
        admin_server = kerberos.example.com
        default_domain = EXAMPLE.COM
}


[domain_realm]
.example.com = EXAMPLE.COM
example.com = EXAMPLE.COM

```
[B]
/etc/samba/smb.conf[/B]

```

# References:


# https://wiki.umn.edu/Main/UbuntuAndActiveDirectory
# http://www.stuartellis.eu/articles/linux-with-active-directory/
# http://ubuntuforums.org/showthread.php?t=91510
# http://serverfault.com/questions/135396/
# https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto


[global]


workgroup = EXAMPLE
realm = EXAMPLE.COM
netbios name = poetry
server string = %h server (Samba %v, Ubuntu)
dns proxy = no
encrypt passwords = true
log level = 3
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action




####### Authentication #######


   # AD Membership pointers
   security = ADS


   # NTLMv2 Security options
   client ntlmv2 auth = yes
   ntlm auth = no


   # http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#PASSWORDSERVER
   # NOTE: This option is NOT recommended as the default value of '*' SHOULD
   # be sufficient to maintain a dynamic list of servers to verify passwords
   # against. DNS names or IP Addresses can be used
   #password server = svr00.example.com, srv32.example.com, srv31.example.com


   # http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#CLIENTUSESPNEGO
   # This variable controls whether Samba clients will try to use Simple and 
   # Protected NEGOciation (as specified by rfc2478) with supporting servers 
   # (including WindowsXP, Windows2000 and Samba 3.0) to agree upon an 
   # authentication mechanism. This enables Kerberos authentication in 
   # particular.
   # Default: client use spnego = yes 
   
   # Leaving it at the default setting in case we use this same conf with
   # later versions of Samba
   # client use spnego = yes


# Winbind UID and GID mapping.
# Use the RID part of the SID (the last part of the SID) to make an ID, starting
# with the lowest number in the range. Changes to "idmap backend" need to
# be followed by a "net cache flush" command to clear the old tdb database.
# Using RIDs removes the need to keep a separate database (tdb) of SID-to-UID maps!
# RID maps work only on one domain at a time.
# Ref: http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/idmapper.html


# Range should not include low-number UIDs, because those are local users
# to UNIX and UNIX-like systems (Mac OS X).  This should only be a problem
# when client-side permission mapping is not invoked, or on Mac OS X Lion.
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
idmap config EXAMPLE:backend = rid
idmap config EXAMPLE:range = 16777216-33554431


# -----------------------------------------------------------
# http://wiki.samba.org/index.php/Samba_&_Active_Directory
# -----------------------------------------------------------
# winbind enum users and groups should be used with caution in active 
# directories greater than 200 users or groups, as enumeration is an expensive 
# process and likely to timeout and cause login failures. during login, the 
# full passwd and group will be "enumerated" every time from your active 
# directory server. enumeration is not required for a successful login. 
winbind enum groups = no
winbind enum users = no
winbind use default domain = yes
winbind refresh tickets = yes
winbind separator = +
winbind nested groups = Yes


# Do not replace spaces in names with underscores.
winbind normalize names = no


template shell = /bin/bash
template homedir = /home/%D/%U
domain master = no
local master = no
preferred master = no
os level = 0
guest account = nobody
map to guest = Bad User


# Printer options
load printers = no
printable = no

```

**/etc/pam.d/common-auth**

We modify this conf file to lock logins to a specific group, so if you don't care about that then you don't have to modify this file. The _pam_winbind.so_ line is the only one that needs changing, but I'm pasting the entire file to be complete. After the installation of the **winbind** package, make sure to run **pam-auth-update** to update this file with winbind-specific settings (this may be automatic, but in my case it didn't happen as expected).

```

# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.


# here are the per-package modules (the "Primary" block)
auth    [success=2 default=ignore]    pam_unix.so nullok_secure
auth    [success=1 default=ignore]    pam_winbind.so krb5_auth krb5_ccache_type=FILE require_membership_of=Lib_poetry_login cached_login try_first_pass
# here's the fallback if no module succeeds
auth    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config

```
[B]
/etc/pam.d/common-session[/B]

Here is where we enable the _pam_mkhomedir.so_ module so new user logins result in a home directory being automatically created just prior to their receiving a shell. We're specifying a **umask** of **0077** to prevent other _domain users_ from having access to the directory.

```

# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive).
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.


session required    pam_mkhomedir.so umask=0077 skel=/etc/skel


# here are the per-package modules (the "Primary" block)
session    [default=1]            pam_permit.so
# here's the fallback if no module succeeds
session    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session    required            pam_permit.so
# The pam_umask module will set the umask according to the system default in
# /etc/login.defs and user settings, solving the problem of different
# umask settings with different shells, display managers, remote sessions etc.
# See "man pam_umask".
session optional            pam_umask.so
# and here are more per-package modules (the "Additional" block)
session    required    pam_unix.so 
session    optional            pam_winbind.so 
# end of pam-auth-update config

```

[HR][/HR]
An optional step is configuring a group of users to have **sudo** rights. What I did was take the **Lib_poetry_login** AD group and include **lib_server_admin** in that group (nested group). So **Lib_poetry_login** controls logins (admins and non-admins) and the **lib_server_admin **group is used to elevate particular users to "admin" status (figuratively speaking).

**/etc/sudoers**

```


Defaults    env_reset
Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"


# Host alias specification


# User alias specification


# Cmnd alias specification


# User privilege specification
root    ALL=(ALL:ALL) ALL


# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL


# lib_server_admins AD group has full access
%lib_server_admins ALL=(ALL) ALL


# See sudoers(5) for more information on "#include" directives:


#includedir /etc/sudoers.d

```

---


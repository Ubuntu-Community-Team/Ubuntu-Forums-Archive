---
title: "Samba password not working"
date: 2010-10-06
forum: Server Platforms
---

### Post by gnomikos on 2010-10-06
I'm having a problem with samba authentication. I'm trying to implement user authentication, but with different samba passwords from unix(system) passwords for each user. Users are added using 

smbpasswd -a <user>

which prompts for the new samba password. If I enter the same password as the system's password of the user, I am able to connect to the share using 

mount.cifs -o username=<user>, password=<pass>

but even a wrong password connects successfully. 

If I enter a different password in smbpasswd (and having *unix password sync* disabled in smb.conf), I can't connect with mount.cifs no matter what password, not even the user's unix password. Samba's log output is:
```

[2010/10/06 15:36:54,  5] auth/auth_util.c:208(make_user_info_map)
  Mapping user []\[My_User] from workstation [192.168.1.3]
[2010/10/06 15:36:54,  5] auth/auth_util.c:229(make_user_info_map)
  Mapped domain from [] to [COMPUTER-2] for user [My_User] from workstation [192.168.1.3]
[2010/10/06 15:36:54,  5] auth/auth_util.c:120(make_user_info)
  attempting to make a user_info for My_User (My_User)
[2010/10/06 15:36:54,  5] auth/auth_util.c:130(make_user_info)
  making strings for My_User's user_info struct
[2010/10/06 15:36:54,  5] auth/auth_util.c:162(make_user_info)
  making blobs for My_User's user_info struct
[2010/10/06 15:36:54, 10] auth/auth_util.c:180(make_user_info)
  made an encrypted user_info for My_User (My_User)
[2010/10/06 15:36:54,  3] auth/auth.c:222(check_ntlm_password)
  check_ntlm_password:  Checking password for unmapped user []\[My_User]@[192.168.1.3] with the new password interface
[2010/10/06 15:36:54,  3] auth/auth.c:225(check_ntlm_password)
  check_ntlm_password:  mapped user is: [COMPUTER-2]\[My_User]@[192.168.1.3]
[2010/10/06 15:36:54, 10] auth/auth.c:234(check_ntlm_password)
  check_ntlm_password: auth_context challenge created by random
[2010/10/06 15:36:54, 10] auth/auth.c:236(check_ntlm_password)
  challenge is: 
[2010/10/06 15:36:54, 10] auth/auth.c:262(check_ntlm_password)
  check_ntlm_password: guest had nothing to say
[2010/10/06 15:36:54,  5] passdb/pdb_interface.c:1513(lookup_global_sam_rid)
  lookup_global_sam_rid: looking up RID 513.
[2010/10/06 15:36:54,  5] passdb/pdb_tdb.c:609(tdbsam_getsampwrid)
  pdb_getsampwrid (TDB): error looking up RID 513 by key RID_00000201.
[2010/10/06 15:36:54,  5] passdb/pdb_interface.c:1576(lookup_global_sam_rid)
  Can't find a unix id for an unmapped group
[2010/10/06 15:36:54,  4] libsmb/ntlm_check.c:332(ntlm_password_check)
  ntlm_password_check: Checking NT MD4 password
[2010/10/06 15:36:54,  3] libsmb/ntlm_check.c:350(ntlm_password_check)
  ntlm_password_check: NT MD4 password check failed for user My_User
[2010/10/06 15:36:54,  5] passdb/pdb_tdb.c:758(tdb_update_samacct_only)
  Storing account My_User with RID 3000
[2010/10/06 15:36:54,  5] auth/auth.c:274(check_ntlm_password)
  check_ntlm_password: sam authentication for user [My_User] FAILED with error NT_STATUS_WRONG_PASSWORD
[2010/10/06 15:36:54,  2] auth/auth.c:320(check_ntlm_password)
  check_ntlm_password:  Authentication for user [My_User] -> [My_User] FAILED with error NT_STATUS_WRONG_PASSWORD
[2010/10/06 15:36:54,  5] auth/auth_util.c:2114(free_user_info)
  attempting to free (and zero) a user_info structure
[2010/10/06 15:36:54, 10] auth/auth_util.c:2118(free_user_info)
  structure was created for My_User

```

Authentication parameters from smb.conf :
```

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
   passdb backend = tdbsam

   obey pam restrictions = no

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = no

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes

hosts allow = 127.0.0.1 192.168.1.3

```

The passdb database is updated successfully every time I run smbpasswd.
Any ideas?

---


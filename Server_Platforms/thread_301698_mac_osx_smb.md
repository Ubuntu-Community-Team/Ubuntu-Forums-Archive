---
title: "mac osx smb"
date: 2006-11-17
forum: Server Platforms
---

### Post by huggy77 on 2006-11-17
i have been having all sorts of issues with my mac sharing... my smb.conf looks like

```

[global]
  guest account = unknown
  encrypt passwords = yes
  auth methods = guest opendirectory
  passdb backend = opendirectorysam guest
  printer admin = @admin, @staff
  server string = imac
  unix charset = UTF-8-MAC
  display charset = UTF-8-MAC
  dos charset = 437
  use spnego = yes
  client ntlmv2 auth = no
  os level = 8
  defer sharing violations = no
  vfs objects = darwin_acls
  brlm = yes
  workgroup = AERIALPHOTOS
; Using the Computer Name to compute the NetBIOS name.  Remove this comment to override
  netbios name = imac
[homes]
   comment = User Home Directories
   browseable = no
   read only = no

[DROPBOX]
   comment = User Home Directories
   path = /users/chris/Desktop/DROPBOX
   public = yes
   only guest = yes
   writable = yes
   printable = no

[printers]
  path = /tmp
  printable = yes

```

and there is no smbpasswd command... WHAT A BUMMER... has anyone changed the mac version of samba successfuly

---


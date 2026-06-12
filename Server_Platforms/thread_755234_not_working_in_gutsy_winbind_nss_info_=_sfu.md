---
title: "not working in gutsy: winbind nss info = sfu"
date: 2008-04-14
forum: Server Platforms
---

### Post by jodeet on 2008-04-14
On servers running feisty, I successfully use winbind to get uid/gid/homedir/login-shell info from sfu (Services For Unix) from Microsoft Active Directory.  However, the same configuration does not work on server running gutsy:

       names can be turned into sids, and sids into names, but sids cannot be turned into unix uids/gids.

Here is a snippet from the file /var/log/samba/log.wb-DOMAINNAME :
-----------BEGIN snippet -------------
[2008/04/14 14:33:16, 5] lib/module.c:smb_probe_module(119)
  Probing module 'sfu': Trying to load from /usr/lib/samba/nss_info/sfu.so
[2008/04/14 14:33:16, 3] lib/module.c:do_smb_load_module(49)
  Error loading module '/usr/lib/samba/nss_info/sfu.so': /usr/lib/samba/nss_info/sfu.so: cannot open shared object file: No such file or directory
[2008/04/14 14:33:16, 3] nsswitch/nss_info.c:nss_init(209)
  nss_init: no nss backends configured.  Defaulting to "template".
----------END snippet ----------------------

Was the gutsy winbind built w.o. sfu support?

Here are the relevant config lines I'm using for winbind:
----------- BEGIN snippet ------------------
workgroup = MYGROUPNAME
realm = MY.DOMAIN.NAME
security = ADS
winbind enum groups = yes
winbind enum users = yes
winbind nested groups = yes
winbind nss info = sfu
winbind separator = +
winbind use default domain = yes

idmap gid = 500-45000
idmap uid = 500-45000
idmap backend = ad
-------------END snippet --------------------

Thanks

---

### Post by jodeet on 2008-04-17
Following the tips of people on the samba mailing list, I've changed my smb.conf slightly, and now, winbind successfully gets a users' uid and gid from msad sfu, but for unknown reasons, does not get the user's homedir or loginshell from sfu.

In other words, via the sfu schema extension to MsA.D., each user in msad has unix attributes like so:

msSFU30GidNumber
msSFU30HomeDirectory
msSFU30LoginShell
msSFU30UidNumber

However, winbind is only finding the msSFU30GidNumber and msSFU30UidNumber.  It uses the default value for 'template homedir' as the user's homdir, and /bin/false as the user's loginshell, even if those are defined otherwise in the msad attributes msSFU30HomeDirectory and msSFU30LoginShell.

winbind on feisty was able to get all the attributes from sfu.

What happened?

Here's is what the logfile named 'log.wb-MYDOMAIN' has to say:
[2008/04/17 16:46:04, 5] nsswitch/nss_info.c:smb_register_idmap_nss(79)
  smb_register_idmap_nss: Successfully added idmap nss backend 'template'
[2008/04/17 16:46:04, 5] lib/module.c:smb_probe_module(108)
  Probing module 'sfu'
[2008/04/17 16:46:04, 5] lib/module.c:smb_probe_module(119)
  Probing module 'sfu': Trying to load from /usr/lib/samba/nss_info/sfu.so
[2008/04/17 16:46:04, 3] lib/module.c:do_smb_load_module(49)
  Error loading module '/usr/lib/samba/nss_info/sfu.so': /usr/lib/samba/nss_info/sfu.s
o: cannot open shared object file: No such file or directory
[2008/04/17 16:46:04, 3] nsswitch/nss_info.c:nss_init(209)
  nss_init: no nss backends configured.  Defaulting to "template".
[2008/04/17 16:46:04, 4] nsswitch/nss_info.c:nss_get_info(268)
  nss_get_info: Failed to find nss domain pointer for MSOE

the directory '/usr/lib/samba/nss_info' does not exist.  Is this a problem with the winbind or samba-common deb?  Like, was the deb compiled without full 'nss info = sfu' support?

here are the pertinent bits of my smb.conf:
security = ADS
workgroup = MYDOMAIN
realm = mydomain.tld

idmap domains = MYDOMAIN
idmap config MSOE:backend = ad
idmap config MSOE:default = yes
idmap config MSOE:schema_mode = sfu
idmap config MSOE:range    = 500-45000
idmap alloc backend = tdb
idmap alloc config:range   = 45001-60000

winbind cache time = 0
winbind enum groups = yes
winbind enum users = yes
winbind nested groups = yes
winbind nss info = sfu
winbind separator = +
winbind use default domain = yes

Thanks

---


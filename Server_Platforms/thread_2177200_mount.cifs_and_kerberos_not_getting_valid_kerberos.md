---
title: "mount.cifs and kerberos not getting valid kerberos ticket"
date: 2013-09-27
forum: Server Platforms
---

### Post by cytan on 2013-09-27
Hi guys,
   This seems to be a well-known problem with mount.cifs on Ubuntu 12.04. Unfortunately, although I have applied the suggestions I found with google, I can't seem to be able to get mount.cifs to work with kerberos. I am trying to use kerberos to mount my Windows shares because this is the only allowed secure way in my company to connect to shares. Before anyone asks, I can successfully use smbclient to connect once I have a valid kerberos ticket either as cytan or as root. 

However with mount.cifs, I get the following message:

(Note I am root when I do this, and yes I have done the following to get a valid kerberos ticket:
 kinit cytan
and /tmp/krb5cc_0 does exist. See below.
)

**************************************
root@ad109688-lt:/home/cytan# mount.cifs -o sec=krb5,user=cytan,domain=ABCDE //beamssrv1.abcd.com/cytan$ ./win --verbose
mount.cifs kernel mount options: ip=xxx.xxx.xxx.xx,unc=\\beamssrv1.abcd.com\cytan$,sec=krb5,ver=1,user=cytan,domain=ABCDE,pass=********
mount error(126): Required key not available
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
*************************************

Here's the dmesg output:
************************************
[16262.785552] /build/buildd/linux-lts-quantal-3.5.0/fs/cifs/cifs_spnego.c: key description = ver=0x2;host=beamssrv1.abcd.com;ip4=xxx.xxx.xxx.xx;sec=krb5;uid=0x0;creduid=0x0;user=cytan;pid=0x155d
[16262.946608] /build/buildd/linux-lts-quantal-3.5.0/fs/cifs/sess.c: ssetup freeing small buf ffff88005772ddc0
[16262.946618] CIFS VFS: Send error in SessSetup = -126
[16262.946627] /build/buildd/linux-lts-quantal-3.5.0/fs/cifs/connect.c: CIFS VFS: leaving cifs_get_smb_ses (xid = 57) rc = -126
[16262.946640] /build/buildd/linux-lts-quantal-3.5.0/fs/cifs/fscache.c: cifs_fscache_release_client_cookie: (0xffff880023277c00/0xffff88005a2ac140)
[16262.946803] /build/buildd/linux-lts-quantal-3.5.0/fs/cifs/connect.c: CIFS VFS: leaving cifs_mount (xid = 56) rc = -126
**************************************

Notice the uid and creduid are both 0x0.

I tried both ways of kinit'ing as myself: cytan and as root. See klist below:
*****************************************
as cytan:

Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: [email]cytan@ABCD.COM[/email]

Valid starting    Expires           Service principal
27/09/2013 09:03  28/09/2013 11:03  krbtgt/ABCD.COM@ABCD.COM
	renew until 04/10/2013 09:03

*******************************************

as root:

Ticket cache: FILE:/tmp/krb5cc_0
Default principal: [email]cytan@ABCD.COM[/email]

Valid starting    Expires           Service principal
27/09/2013 13:42  28/09/2013 15:42  krbtgt/ABCD.COM@ABCD.COM
	renew until 04/10/2013 13:42

*********************************************

Unfortunately, using either uid's always gives me the "Required key not available" problem.


What am I doing wrong? Or is this a bug and is there a workaround?


Thanks!

cytan

---


---
title: "Openafs fileserver with Kerberos"
date: 2008-05-28
forum: Server Platforms
---

### Post by majikins on 2008-05-28
Hi

I have been trawling the net trying to find a howto on openafs with kerberos for Heron.

Please can someone point me in the right direction and/or be kind enough to take me through it?

Thanks

---

### Post by womblet on 2008-07-09
Hi,
I too am looking for this information and wanted to highlight the above post.
I installed openafs 1.4.6 using synaptic but do not know how to run it. I tried typing 'openafs' and some variations in terminal without result.
Thanks

---

### Post by coyled on 2008-07-10
> **majikins said:**
> I have been trawling the net trying to find a howto on openafs with kerberos for Heron.

Please can someone point me in the right direction and/or be kind enough to take me through it?


I don't know of an Ubuntu-specific howto, but could help walk you through the setup.  Are you having a particular problem, or are you unsure where to start?

-Coyle

---

### Post by Robstarusa on 2008-07-10
I'd love to see a guide on this as well.

---

### Post by Mabowle on 2008-07-21
AFAIK there is no guide specifically for Ubuntu. However, there is this guide for Gentoo and Debian [http://de.gentoo-wiki.com/OpenAFS_mit_MIT-Kerberos5]("http://de.gentoo-wiki.com/OpenAFS_mit_MIT-Kerberos5") (german) or [http://en.gentoo-wiki.com/HOWTO_OpenAFS_with_MIT-KRB5]("http://en.gentoo-wiki.com/HOWTO_OpenAFS_with_MIT-KRB5") (english). The Debian-specific commands for installation should also work for Ubuntu.

---

### Post by iLoveRuby on 2008-08-27
This link may also help:

[http://www.eos.ncsu.edu/remoteaccess/linuxopenafs.html]("http://www.eos.ncsu.edu/remoteaccess/linuxopenafs.html")

---

### Post by WatsonJX on 2009-05-01
The guide for Debian is here. I tried to follow it on Karmic and I _do_ got problems and need help. Hope there are more people interested in this and help each other.

[http://www.debian-administration.org/article/OpenAFS_installation_on_Debian](http://www.debian-administration.org/article/OpenAFS_installation_on_Debian)

I managed to pass the "Creating a new cell" section but was stuck at this step:
kinit root/admin; aklog

# aklog -d
Authenticating to cell mytv (server mytv).
Trying to authenticate to user's realm MYTV.HOME.
Getting tickets: afs/mytv@MYTV.HOME
We've deduced that we need to authenticate using referrals.
Getting tickets: afs/mytv@
We've deduced that we need to authenticate to realm MYTV.
Getting tickets: afs/mytv@MYTV
Getting tickets: afs@MYTV
Kerberos error code returned by get_cred : -1765328377
aklog: Couldn't get mytv AFS tickets:
aklog: unknown RPC error (-1765328377) while getting AFS tickets

The principals I have are:
root@mytv:/etc/openafs# kadmin.local
Authenticating as principal root/admin@MYTV.HOME with password.
kadmin.local:  listprincs
K/M@MYTV.HOME
[email]afs@MYTV.HOME[/email]
[email]jxiong@MYTV.HOME[/email]
kadmin/admin@MYTV.HOME
kadmin/changepw@MYTV.HOME
kadmin/history@MYTV.HOME
krbtgt/MYTV.HOME@MYTV.HOME
root/admin@MYTV.HOME

---

### Post by WatsonJX on 2009-05-02
Finally it worked! Based on this:
[http://www.debian-administration.org/article/OpenAFS_installation_on_Debian](http://www.debian-administration.org/article/OpenAFS_installation_on_Debian)

Make sure the cell name matches and server IP is correct in following files:
/etc/openafs/ThisCell
/etc/openafs/CellServDB
/etc/openafs/server/ThisCell
/etc/openafs/server/CellServDB


and couple of things to change:

Kerberos principals
-------------------
sudo rm -f /tmp/afs.keytab
sudo kadmin.local
Authenticating as principal root/admin@SPINLOCK.HR with password.

kadmin.local:  addprinc -policy service -randkey -e des-cbc-crc:v4 afs/spinlock.hr
Principal "afs/spinlock.hr@SPINLOCK.HR" created.

kadmin.local:  ktadd -k /tmp/afs.keytab -e des-cbc-crc:v4 afs/spinlock.hr
Entry for principal afs with kvno 3, encryption type DES cbc mode with
CRC-32 added to keytab WRFILE:/tmp/afs.keytab.

sudo asetkey add 3 /tmp/afs.keytab afs/spinlock.hr

AFS Partitions
--------------
Run this command to touch a file in it:
touch /vicepa/AlwaysAttach

Otherwise the fileserver will not list the partition.

Have fun and enjoy!

---


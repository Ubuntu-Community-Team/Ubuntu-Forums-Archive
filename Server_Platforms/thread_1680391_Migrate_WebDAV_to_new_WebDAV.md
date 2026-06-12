---
title: "Migrate WebDAV to new WebDAV"
date: 2011-02-02
forum: Server Platforms
---

### Post by Saorex on 2011-02-02
Hi guys. I have a WebDAV folder (complete folder hierarchy in fact) currently managed by SAP's KM module. Long story short: it's in Windows, it's slow, I hate it.

I want to migrate the hole tree to my brand new Ubuntu Server 10.04 with a functional WebDAV server I just finished configuring. It connects to LDAP for user authentication, it's fast, it works like a charm.

Do you guys know any way I can transfer/migrate files from the Windows WebDAV to to Ubuntu WebDAV? The only thing that is important to keep is file security properties. Both WebDAVs have the same user database: our corporate Active Directory.

Any help, cue, or comment is welcome.

Thanks a lot!

---

### Post by gordintoronto on 2011-02-02
Where are the file security properties stored in WebDAV? 

Could you temporarily create a Share on the Ubuntu server where you want the WebDav folder, then simply copy/paste the folder over? Then remove the Share.

---


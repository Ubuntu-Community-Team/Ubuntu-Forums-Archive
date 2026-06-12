---
title: "How to stop samba from automatically authenticating"
date: 2011-12-12
forum: Server Platforms
---

### Post by sdmike6 on 2011-12-12
So I have a mac and my user name and system name are the same being foobar.

I'm connecting to an ubuntu 11.04 server running samba and the root user has the same user name as my mac. Also the server externally authenticates with OpenLDAP.

So when I connect with my mac to the samba fileshare it logs me in and I don't enter in my credentials. I looked in my keychain and those credentials are not stored.

I looked at the server logs and I found this:
[2011/12/12 14:42:53.246707,  1] smbd/service.c:1070(make_connection_snum)
  workstation (10.12.22.120) connect to service Fileshare initially as user foobar (uid=1003, gid=100) (pid 20539)
[2011/12/12 14:42:54.282792,  0] passdb/passdb.c:627(lookup_global_sam_name)
  User foobar with invalid SID S-1-5-21-1713727836-2215038221-1160323130-3064 in passdb
[2011/12/12 14:42:54.289256,  0] passdb/passdb.c:627(lookup_global_sam_name)
  User foobar with invalid SID S-1-5-21-1713727836-2215038221-1160323130-3064 in passdb

How can I stop this server from logging me into the samba share automatically? 

I also have guest login turned off.

---

### Post by opensourceofwin on 2011-12-15
On your server, do you have a line in your /etc/samba/smb.conf
that says 

security=user?

---


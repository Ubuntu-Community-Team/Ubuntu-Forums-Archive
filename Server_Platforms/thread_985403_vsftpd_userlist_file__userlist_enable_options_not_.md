---
title: "vsftpd userlist_file / userlist_enable options not working in Hardy"
date: 2008-11-17
forum: Server Platforms
---

### Post by Smatchimo on 2008-11-17
Hi,

Does anyone know why the userlist options don't work in Hardy but they work ok in Dapper and Gutsy? I have not tried in 8.10 as we only use LTS versions ideally.

The stock /etc/vsftpd.conf does not contain any userlist settings at all at first. Adding these in under Dapper and Gutsy works, then any users defined in the user_list file can't FTP in while other users can:

userlist_file=/etc/vsftpd.user_list
userlist_enable=YES

Then I put a test user in /etc/vsftpd.user_list and restart the vsftpd service, but the test user can still FTP in ok. In Hardy it doesn't complain about setting those options, but they just don't seem to have any effect. 

Also throwing in a "userlist_disable=NO" does not have any effect (even though that shouldn't be needed since it works w/o that option in the other OS versions).

Yes I am restarting the vsftpd service after making changes to the vsftpd.conf.

Thanks for any insight!

---

### Post by ace201 on 2009-06-15
i misread this post and wrote a reply, but i can't seem to delete it, sorry!

---


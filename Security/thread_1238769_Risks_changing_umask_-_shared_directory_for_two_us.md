---
title: "Risks changing umask - shared directory for two users"
date: 2009-08-12
forum: Security
---

### Post by plo on 2009-08-12
Hi!

Questions in short: 
1.Could changing umask in /etc/profile to 007  (default 0022) cause any problems? 
2.Would it possibly break something in the system "structure" or cause security risks?
3.Why is default umask 0022  (giving default file permission to "others" to read files in the home directory?
4. The system lists 4 digits in umask but I can only find reference to 3 digits?

One of the reference links in the sticky Ubuntu:Security says at the bottom that it's OK with umask 002 if you maintain a strict group handling, but ...

Background: I am setting up a new system at home. Me and my girlfriend will share it with separate user accounts.
I have mounted a separate disk under /mnt/Shared for us to store shared data (photos, economy...).

First I created a new group with both of us as members and then:
chgrp -R newgroup /mnt/Shared
chmod -R 770 /mnt/Shared
chmod -R g+s /mnt/Shared

this basically works but when adding new files the other user does not get write rights to the new files.
Then I discovered the umask command.
Changing the default to 007 would fix this (right?) and also keeping the home-directory private
(not that that's needed in this specific case, but for reference).

Thanks  /Lars

---

### Post by bodhi.zazen on 2009-08-13
There are several ways of making a shared directory. IMO acl are best.

Share directory : [http://hep.pa.msu.edu/user/groups.html](http://hep.pa.msu.edu/user/groups.html) 
    Set Group ID : chmod g+s dirname 
 
    OR (ACL works better) 
 
    ACL : [http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741) 
      or [http://ubuntuforums.org/showpost.php?p=1193555&postcount=13](http://ubuntuforums.org/showpost.php?p=1193555&postcount=13)

---

### Post by plo on 2009-08-13
Thanks for the input. The ACL method sounds good. I had noted that the umask option was not available when mounting ext3/ext2 file systems.

However it still would be nice to get some input on the issue of changing the default umask setting.
Why is the default setting giving read permission to "others" for my homedirectory? 
And would changing the setting to umask 007 have any other impact on the system?

---

### Post by bodhi.zazen on 2009-08-14
Changing your umask value will not affect "the system". umask only affects the permissions of new files you create.

Permissions on your home directory are not related to umask. The permissions on your home directory (world readable) were chosen to facilitate sharing of files. There is no set of defaults that will please everyone, if you do not like the current values, change them.

Otherwise the issues of default permissions of $HOME have been discussed many times on these forums.

---

### Post by plo on 2009-08-15
OK, thanks.

Implemenet second option (ACL), works perfekt.

---

### Post by vjones777 on 2009-11-08
Found this great step-by-step with notes for ACL

[http://en.opensuse.org/How_to_share_directories_between_groups_of_users_using_ACL]("http://en.opensuse.org/How_to_share_directories_between_groups_of_users_using_ACL")

---


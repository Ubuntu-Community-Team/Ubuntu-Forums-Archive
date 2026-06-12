---
title: "Nagios - Unable to write to path - what??"
date: 2015-12-08
forum: Server Platforms
---

### Post by ghughes on 2015-12-08
Good afternoon, all!


I'm running an older version of Nagios Core (3.2.3) on an Ubuntu 12.04 server. After some updates I can't start the nagios3 demon. The preflight all checks until the end. At the end I get the following:


Checking misc settings...
Error: Unable to write to temp_path ('/var/lib/nagios3/spool/checkresults') - Permission denied
Error: Unable to write to check_result_path ('/var/lib/nagios3/spool/checkresults') - Permission denied


Total Warnings: 0
Total Errors: 2


No one changed the owner or permissions on the directory or the files therein. The owner/group on all the files & folders is nagios | www-data. The user is sudo'd to root.


I'm sure it's an ownership issue, but I tried setting the permissions to 777 with no success.  Also checked that an Active Directory user didn't have a profile in /etc/passwd.


Any thoughts from those who have lived in Nagios longer than I?


Thanks!


Gregg



Any thoughts from those who have lived in Nagios longer than I?


Thanks!


Gregg

---

### Post by ghughes on 2015-12-08
Addendum - I have been working on the Nagios server to try and enable SSH with a key - to no avail.  I don't see how that would change the permissions on that checkresults directory, though.

---

### Post by ghughes on 2015-12-09
Found it.

We're using Centrify Express to bind servers to Active Directory.  There is an AD user "nagios" - that user was somehow the owner of /var/lib/nagios3/spool.  Double-checked the UID/GID of the files under that directory, chowned the directory back to the local Nagios user, and it's back online.

I suspect I'll have to make local Nagios users on each remote server to use check_by_ssh.

Thanks to all for looking!

Gregg

---

### Post by Habitual on 2015-12-09
Good job and well done!

---


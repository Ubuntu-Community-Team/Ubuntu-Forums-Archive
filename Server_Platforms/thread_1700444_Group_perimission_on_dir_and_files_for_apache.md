---
title: "Group perimission on dir and files for apache"
date: 2011-03-05
forum: Server Platforms
---

### Post by brentrussell on 2011-03-05
Me and 2 others are working on a website (Bob, Mike, and Joe). We made a group called developers and each of us are in the developers group. The Apache server runs as www-data. When we upload files, the file owner is the users name and the group is "developers".

/etc/group has the following
```
www-data:x:33:
bob:x:1000:
mike:x:1001:
joe:x:1002:
developers:x:1003:bob,mike,joe
```

What should the permissions, owner, and group be for the following files and directories to allow us to upload files and be the owner of the files we edit, and have Apache secure. In addition I want bob to be able to edit a file owned by mike. Also, should I add www-data to the developers group? I am not opposed to completely changing my /etc/group

/var/www/www.site.com/
/var/www/www.site.com/html
/var/www/www.site.com/html/file.php
/var/www/www.site.com/html/directory

I have always just set everything to 775 and just called it good. Well I don't want to wake up to a Russian political message plastered all over the site. It's time I do things properly. As always your help is appreciated a lot.

---

### Post by SeijiSensei on 2011-03-05
The simplest solution is to add the www-data user to the developers group.  Then make sure everything in /var/www and its subdirectories have "developers" as the group.  You can then apply 'chmod o-rwx /var/www -R' to block anyone but the developers from reading or altering the files.

---

### Post by brentrussell on 2011-03-05
I added www-data to the developers group. When I chmod to o-rwx I can no longer access the directories with my username and have to change to root. My username is a part of the developers group too.

Maybe you could tell me the chmod number rather than string. I don't understand chmod strings. I get what rwx is but not 0-rwx. Is that 770?

Thanks cheers
Brent

---

### Post by SeijiSensei on 2011-03-06
> **brentrussell said:**
> I added www-data to the developers group. When I chmod to o-rwx I can no longer access the directories with my username and have to change to root. My username is a part of the developers group too.

Maybe you could tell me the chmod number rather than string. I don't understand chmod strings. I get what rwx is but not 0-rwx. Is that 770?


First, it's the letter "o" not the numeral "0".  So o-rwx turns off all three permissions for "other" users.  (See "man chmod" for details.)  It works better than numeric codes when you're trying to deal with both files and directories at once.

What permissions are on the highest-level directory in the hierarchy, probably /var/www in your case?  What does an "ls -l /var/www" show?  What about "ls -lR /var/www"?  /var/www should be owned by user www-data and group developers, with 0770 permissions.

---


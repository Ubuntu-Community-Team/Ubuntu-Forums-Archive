---
title: "Users, groups n their rights"
date: 2007-12-18
forum: Server Platforms
---

### Post by SoulRaver on 2007-12-18
Maydaymayday... 

The patient:
Ol' x68 machine running 7.10 dektop, installed proftpd, LAMP-stack, joomla!, firestarter.

Symptom:
Adding 'ftpuser' account that has full rights to /var/www, while _not_ limiting group 'www-data' rights. Either LAMP-stack calls are comprimised or FTP access.

Failed Home remedies:
Adding 'ftpuser' to 'www-data'. Both GUI and command promt type. Tried to make 'ftpuser' owner of /var/www ('ftpuser':'www-data') but that again breaks the http rights.


I really am at my vits end here... any clues to as what might be wrong here, except usern00bness?

---

### Post by bodhi.zazen on 2007-12-18
Moved to servers and security.

I use vsftp. This allows users to ftp into their $HOME (which is chroot).

For general ftp (anonymous), use /home/ftp rather then /var/www

---

### Post by SoulRaver on 2007-12-18
Thx bodhi.zazen...

I'm confused now, how does vsftpd differ from any other possible ftp software? What I'm getting at is, dosent the linux core user policies managment overide them all?

---

### Post by bodhi.zazen on 2007-12-18
I am not sure of the differences, I do not run ftp servers all that much.

I have experience only with vsftp as I am paranoid.

---

### Post by SoulRaver on 2007-12-19
Thx for the reply,

Does anyone know of a good online guide to user and group rights, policies and managment? I think better read up instead of asking here :KS


Just incase someone is up for the challenge...
-Which policy has precident? User or Group?

-Can 'UserMemberA' of 'Group1' have rights outside the 'RootUser' defined scope of 'Group1'?

-Can 'UserMemberB' have up tp 777 rights on 'SomeFileX' (Group1:Group1), when said memger is not part of 'Group1'?

-If 'FolderAlpha' is (Group1:Group1) or (root:root), what is the preferred way to ammend rights to 'UserMemberB' and keeping the original rights? Remember 'UserMemberB' is not part of 'Group1' or 'RootUser'.

---

### Post by bodhi.zazen on 2007-12-19
Well, with standard permissions you have only 3 options:

Owner
Group
Other ie global access.

So you would need to either :

1. Add UserMemberB to one of the existing groups
2. Make a new group
3. give global access to the file.

References for permissions:

[http://www.linux-tutorial.info/modules.php?name=MContent&pageid=225](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=225)
[http://dsl.org/cookbook/cookbook_9.html](http://dsl.org/cookbook/cookbook_9.html)

================

The "solution" is acl, or access control lists.

References for ACL liists :

[http://www.debianhelp.co.uk/acl.htm](http://www.debianhelp.co.uk/acl.htm)
[http://www.beginlinux.com/index.php/server_training/acls](http://www.beginlinux.com/index.php/server_training/acls)
[http://www.novell.com/coolsolutions/trench/16418.html](http://www.novell.com/coolsolutions/trench/16418.html)

Edit: This is a very nice tutorial as well : [http://www.onlamp.com/pub/a/bsd/2003/08/14/freebsd_acls.html](http://www.onlamp.com/pub/a/bsd/2003/08/14/freebsd_acls.html)

---


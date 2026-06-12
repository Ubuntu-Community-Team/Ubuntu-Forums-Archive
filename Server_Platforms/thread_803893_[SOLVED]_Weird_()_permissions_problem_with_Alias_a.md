---
title: "[SOLVED] Weird (?) permissions problem with Alias and apache2"
date: 2008-05-22
forum: Server Platforms
---

### Post by ntalamai on 2008-05-22
Hello all, 

I experienced a very weird (?) problem with Alias and apache2. Long story short, I want to alias folder /home/user1/My_docs/Calendar/ to /davhome5/ inside apache. I get a Forbidden 403 message in firefox until I set the permission o+x, not only to /home/user1/My_docs/Calendar/, but also to all parent directories i.e. /home/, /home/user1/, /home/user1/My_docs/. 

Is this what should happen? Even if it is, why should I make all the directories hierarchy executable to others (o+x) while I only need to see the contents of a directory 4 levels down the hierarchy? Details follow.

There are the following directives in /etc/apache2/sites-available/default
```
    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

```
[http://localhost/doc/](http://localhost/doc/) is visible from Firefox.

Then I added the following just below the previous directory by simply copying-pasting and changing the names. 
```
Alias /davhome5/ "/home/user1/My_docs/Calendar/"
    <Directory "/home/user1/My_docs/Calendar/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

```
Permissions of Calendar are set to 777:
$ ls -ld /home/user1/My_docs/Calendar/
drwxrwxrwx 2 root root 4096 2008-01-13 19:04 /home/user1/My_docs/Calendar/

Yet in Firefox I get a forbidden 403 error when trying to view: [http://localhost/davhome5/](http://localhost/davhome5/)

Directories /home/, /home/user1/ have o+rx permissions, but /home/user1/My_docs/ has o-rx. I must set /home/user1/My_docs to o+rx, in order to see from firefox the contents of /home/user/My_docs/Calendar.

Can you explain this please? Does this make sense or is there a security misconfiguration somewhere? Please help!

---

### Post by MJN on 2008-05-22
> **ntalamai said:**
> Is this what should happen? Even if it is, why should I make all the directories hierarchy executable to others (o+x) while I only need to see the contents of a directory 4 levels down the hierarchy? Details follow.

This is indeed correct, albeit a little confusing to many when they first stumble across it.

The bottom line is that Apache needs execute rights to a directory in order to see files within it. However, that's not to say *everyone* needs such access.

Hence, you can either move the web roots to outside of the home directory, or limit access to user/group (not other) where Apache (user 'www-data') is a member of.

Mathew

---

### Post by ntalamai on 2008-05-23
I see MJN... :shock:

Thanks for that. Just a "quick" question in case you are online, or someone else can post a quick reply.

How can I only change the group of a directory/file? 

Now assuming that I changed /home/user1/My_docs/ to group www-data, how can I make user1 belong to two groups? i.e. the default "admin" group and "www-data" group?

Finally, is it possible to have a folder shared by two groups? i.e. can /home/user1/My_docs/ provide g+rwx to both "www-data" and "admin" group? Or is it the case that in Ubuntu (and Unix in general), it has to be exactly one group per file?

Thanks.

---

### Post by samosamo on 2008-05-23
take a look at /etc/group and "man group"

---

### Post by ntalamai on 2008-05-23
Thanks for that - it saved me LOTS of googling. I suppose the answer is that every file is owned by exactly one user and exactly one group. However, a user may belong to many different groups as specified in /etc/group.

1st question: Is manually changing /etc/group enough for adding a user to two or more groups? I mean I don't need to change anything else, right?
Also "cat/etc/group | grep user1" should give all the groups user1 belongs to, right?

2nd question: Group www-data gives no members!:confused:
$ cat /etc/group | grep www-data
www-data: x:33:

However:
$ cat /etc/apache2/envvars 
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid

3rd question: Why not all users/ groups appear in System-->Administration-->Users and Groups?

Thanks in advance.

---

### Post by MJN on 2008-05-23
> **ntalamai said:**
> How can I only change the group of a directory/file?

**chgrp <newgroup> <file/directory>**

> Now assuming that I changed /home/user1/My_docs/ to group www-data, how can I make user1 belong to two groups? i.e. the default "admin" group and "www-data" group?You don't want to do this in your case, but in answer to your question you'd use **usermod -a -G <group> <user>** however you should not be doing this. Remember, your files have separate permissions for the user and group owners of those files and so there's no need to add the owning user to the group. Indeed you specifically don't want to in your case because if you add all users to the www-data group then they will be all able to access each other's files which is what you originally stated you didn't want to happen.

> Finally, is it possible to have a folder shared by two groups? i.e. can /home/user1/My_docs/ provide g+rwx to both "www-data" and "admin" group? Or is it the case that in Ubuntu (and Unix in general), it has to be exactly one group per file?That's right - one group per file (but as mentioned above you've also got separate user control over that file so this shouldn't pose a problem).

> Group www-data gives no members!:confused:
$ cat /etc/group | grep www-data
www-data: x:33:That's correct - the www-data user exists but the www-data group is empty as there's no need for a user to be a member of its own group as it already has its own set of permissions on a given file. Indeed if a user belonged to his own group there could be a conflict of permissions over what they are allowed to do.

Mathew

---

### Post by ntalamai on 2008-05-23
Thank for your replies Matthew. Things start to get more clear.

> That's correct - the www-data user exists but the www-data group is empty as there's no need for a user to be a member of its own group as it already has its own set of permissions on a given file. Indeed if a user belonged to his own group there could be a conflict of permissions over what they are allowed to do.

When you say conflict, do you mean that when for instance group "user1" has no permissions on a file (g-rwx), and the same time the owner "user1" has rwx access to it? In other words:
ls -l someFile
-rwx------ user1 user1 .... someFile

Or even worse:
ls -l someFile
----rwx--- user1 user1 .... someFile

Finally Why not all users/ groups appear in System-->Administration-->Users and Groups?

---

### Post by MJN on 2008-05-23
I think I've made things sound a little more complicated than they actually are. Suffice to say though that you don't need to add a user to its own group of the same name, and you can regard the group permissions of a file as a 'secondary' level of access rights to other users (and hence would typically be either equal to, or less than, those permissions assigned to the owner).

I'm afraid I don't know about the 'Users and Groups' tool as I use KDE myself. What users/groups does it have (or not have)? Perhaps it just shows 'non-system' users/groups?

Mathew

---

### Post by ntalamai on 2008-05-23
Thanks Matthew. Let's don't bother ourselves with "Users and Groups" now. Since you don't have an answer out of you pocket, it is okay. I had a looooooong week setting up SVN+SSL+WebDAV+Apache2 with all my data outside /var/wwww/ and "Users and Groups" seems so secondary. 

Wikipedia also has an excellent article on permissions
[http://en.wikipedia.org/wiki/File_system_permissions#Traditional_Unix_permissions](http://en.wikipedia.org/wiki/File_system_permissions#Traditional_Unix_permissions)
that explains why the we need the "x" flag for the whole directories' hierarchy: traversing. If there is no "r", noone can list my files, and this is enough for me.

Thanks again.

---


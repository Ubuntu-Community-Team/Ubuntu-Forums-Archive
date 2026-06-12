---
title: "Weird Samba Permission issues"
date: 2017-10-03
forum: Server Platforms
---

### Post by shawn-f on 2017-10-03
I'm trying to force 770 for directories and 660 for files in a samba share. When I create files and directories, I am getting 650. I could use some help here.

Ubuntu 16.04 fully updated.

```
# apt policy samba
samba:
  Installed: 2:4.3.11+dfsg-0ubuntu0.16.04.11
  Candidate: 2:4.3.11+dfsg-0ubuntu0.16.04.11
  Version table:
 *** 2:4.3.11+dfsg-0ubuntu0.16.04.11 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2:4.3.8+dfsg-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

```
[admindocstest]
        path = /home/admindocs
        force directory mode = 770
        create mode = 770
        force create mode = 770
        directory mode = 770
        force group = SchoolAdmin
        writeable = yes

```

```
-rwxr-x--- 1 sperry SchoolAdmin    0 Oct  3 20:18 New Bitmap Image.bmp
drwxr-x--- 2 sperry SchoolAdmin 4096 Oct  3 20:18 New folder



```

---

### Post by shawn-f on 2017-10-04
I'm trying to force 770 for directories and 660 for files in a samba share. When I create files and directories, I am getting 650. I could use some help here.

Ubuntu 16.04 fully updated.

```
# apt policy samba
samba:
  Installed: 2:4.3.11+dfsg-0ubuntu0.16.04.11
  Candidate: 2:4.3.11+dfsg-0ubuntu0.16.04.11
  Version table:
 *** 2:4.3.11+dfsg-0ubuntu0.16.04.11 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2:4.3.8+dfsg-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

```
[admindocstest]
        path = /home/admindocs
        force directory mode = 770
        create mode = 770
        force create mode = 770
        directory mode = 770
        force group = SchoolAdmin
        writeable = yes

```

```
-rwxr-x--- 1 sperry SchoolAdmin    0 Oct  3 20:18 New Bitmap Image.bmp
drwxr-x--- 2 sperry SchoolAdmin 4096 Oct  3 20:18 New folder



```

---

### Post by darkod on 2017-10-04
1. According to what you said, shouldn't create mode be 660 in smb.conf? You have it as 770 (same like for directories).

2. Using /home for samba shares is very poor decision. Home folders are designed to be "private" for users, so you might get unexpected results.

I would take the shares outside of /home, and adjust the create mask to 660 in smb.conf.

---

### Post by shawn-f on 2017-10-04
> **darkod said:**
> 1. According to what you said, shouldn't create mode be 660 in smb.conf? You have it as 770 (same like for directories).
Yes, it should be 660 for create mode. That is a test share. Note that the actual permissions created are neither 770 nor 660 for either files or directories. They both end up 750. That is what I'm having trouble with. It is ignoring both create and force create on files and directories.

> **darkod said:**
> 2. Using /home for samba shares is very poor decision. Home folders are designed to be "private" for users, so you might get unexpected results.

I would take the shares outside of /home, and adjust the create mask to 660 in smb.conf.

That wasn't my decision, and I can't change that yet.

---

### Post by darkod on 2017-10-05
Well, if it's only a test share it doesn't hurt creating another test share outside of /home and see if you get the expected results.

As I said, /home is designed to force certain permissions already and when that clashes with samba forcing different ones, I really don't know who will win...

---

### Post by TheFu on 2017-10-05
Did you restart samba after making the changes?

---

### Post by shawn-f on 2017-10-05
Yes, I did.

---

### Post by shawn-f on 2017-10-05
> **darkod said:**
> Well, if it's only a test share it doesn't hurt creating another test share outside of /home and see if you get the expected results.

As I said, /home is designed to force certain permissions already and when that clashes with samba forcing different ones, I really don't know who will win...

New share, same error. what do I need to try next?

```

[admindocstest]
        directory mode = 770
        force create mode = 660
        create mode = 660
        writeable = yes
        force group = SchoolAdmin
        path = /srv/admindocstest
        force directory mode = 770
```

```
root@filestor:/srv/admindocstest/ShawnTesting# pwd
/srv/admindocstest/ShawnTesting
root@filestor:/srv/admindocstest/ShawnTesting# ls -l
total 4
-rw-r----- 1 sperry SchoolAdmin    0 Oct  5 12:45 New Bitmap Image.bmp
drwxr-x--- 2 sperry SchoolAdmin 4096 Oct  5 12:45 New folder
root@filestor:/srv/admindocstest/ShawnTesting#
```

---

### Post by TheFu on 2017-10-05
```
  create mask = 0644
  directory mask = 0755
```
is what I use.

Also - userids and groups are case-insensitive. Best to leave them all lower case to avoid little issues.  I assume the group you are trying to force exists?  I did not look at the other settings.

Where did you setup the valid users?

It would also be smart to use the set-groupid bit (g+s) and make the top level directory 0770.

---

### Post by shawn-f on 2017-10-05
No combination of create mask, directory mask, force create mask, and force directory mask gives me 770 for directories and 660 for files. I'm not having a problem with groups, uids, or gids.

---

### Post by Morbius1 on 2017-10-06
For what it's worth I cannot reproduce your error. I even replicated your share definition with the following exceptions:

** I assumed **admindocs** was a folder name and not a user name.
** I used the group plugdev since it already existed.

By any chance is /home/admindocs a mount point to another partition formatted in NTFS or FAT32?

[COLOR=#0000cd]**EDIT**[/COLOR]: There is another possibility.

Take a look at your smb.conf or even post its entire contents:
```
cat /etc/samba/smb.conf
```
Samba reads smb.conf sequentially from top to bottom and from service declaration - those separated by [something] statements - to service declaration. It's possible that in your testing you have a mask or mode statement past the [admindocstest] share definition that is overriding those in that definition.

---

### Post by shawn-f on 2017-10-06
> **Morbius1 said:**
> For what it's worth I cannot reproduce your error. I even replicated your share definition with the following exceptions:

** I assumed **admindocs** was a folder name and not a user name.
** I used the group plugdev since it already existed.

By any chance is /home/admindocs a mount point to another partition formatted in NTFS or FAT32?

[COLOR=#0000cd]**EDIT**[/COLOR]: There is another possibility.

Take a look at your smb.conf or even post its entire contents:
```
cat /etc/samba/smb.conf
```
Samba reads smb.conf sequentially from top to bottom and from service declaration - those separated by [something] statements - to service declaration. It's possible that in your testing you have a mask or mode statement past the [admindocstest] share definition that is overriding those in that definition.

admindocs is a directory, and is not a user.
Originally it was in /home on ext4. I created a tests share called admindocstest on /srv/admindocstest also on ext4 with the same results.
admindocs is not the last share in the file, but there are no entries that follow until the next share. admindocstest is at the end of the file.

I feel like I've hit a bug, but I can't replicate it anywhere either.

---

### Post by darkod on 2017-10-06
Reading online about the parameters you use, I think that is where the problem lies. Don't use force for the permissions, not needed. Just leave the 'force group'.
For the pdrmission try it with only this:
```
create mask = 660
directory mask = 770
```
Remove or comment out the 'force create mode' and 'force directory mode'. Try it and let us know. You are restarting samba after making changes right?

---

### Post by cariboo on 2017-10-06
Please don't create duplicate threads, as it dilutes the help given, and makes you look in two places for answers to your question.

---

### Post by shawn-f on 2017-10-09
> **darkod said:**
> Reading online about the parameters you use, I think that is where the problem lies. Don't use force for the permissions, not needed. Just leave the 'force group'.
For the pdrmission try it with only this:
```
create mask = 660
directory mask = 770
```
Remove or comment out the 'force create mode' and 'force directory mode'. Try it and let us know. You are restarting samba after making changes right?

No change. Yes, I restarted.

```
[admindocstest]
        path = /srv/admindocstest
#       force directory mode = 770
        directory mode = 770
        create mode = 660
#       force create mode = 660
        writeable = yes
        force group = SchoolAdmin
#       available = no

```

---

### Post by TheFu on 2017-10-09
Appears something else is happening - probably due to other settings in the config file. Please post the entire thing or (better) the output from **testparm**.

---

### Post by shawn-f on 2017-10-09
```
$sudo testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[homes]"
Processing section "[netlogon]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[admindocs]"
Unknown parameter encountered: "force directory mask"
Ignoring unknown parameter "force directory mask"
Unknown parameter encountered: "force create mask"
Ignoring unknown parameter "force create mask"
Processing section "[shared]"
Processing section "[SketchupLic$]"
Processing section "[admindocstest]"
NOTE: Service admindocstest is flagged unavailable.
Loaded services file OK.
Server role: ROLE_STANDALONE


Press enter to see a dump of your service definitions


# Global parameters
[global]
        workgroup = <redacted>
        netbios aliases = <redacted>
        server string = %h server (Samba, Ubuntu)
        server role = standalone server
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = ldapsam:ldap://<redacted>
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        unix extensions = No
        wins support = Yes
        ldap admin dn = <redacted>
        ldap group suffix = ou=Groups
        ldap idmap suffix = ou=Idmap
        ldap machine suffix = ou=Computers
        ldap passwd sync = yes
        ldap suffix = <redacted>
        ldap ssl = no
        ldap user suffix = ou=Users
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        template homedir = /home/%U
        template shell = /bin/bash
        idmap config * : backend = tdb




[homes]
        comment = Home Directories
        read only = No
        create mask = 0600
        directory mask = 0700
        directory mode = 0700
        browseable = No
        root preexec = /usr/local/bin//mksambahomedirs.sh %S




[netlogon]
        comment = Network Logon Service
        path = /home/netlogon
        guest ok = Yes




[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No




[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers




[admindocs]
        path = /home/admindocs
        valid users = @schooladmin
        force group = schooladmin
        group = schooladmin
        read only = No
        map archive = No




[shared]
        path = /home/shared
        read only = No
        create mask = 0644
        map archive = No




[SketchupLic$]
        path = /home/SketchUpLic
        valid users = SketchUp
        read only = No
        create mask = 0776
        directory mask = 0776
        directory mode = 0776
        map archive = No




[admindocstest]
        path = /srv/admindocstest
        force group = SchoolAdmin
        group = SchoolAdmin
        read only = No
        create mask = 0660
        directory mask = 0770
        directory mode = 0770
        available = No

```

Note that [admindocstest] does not actually contain directory mask.
Also, "available = No" is set when I am not working on this problem so as to not mess with users browsing the fileserver.

---

### Post by darkod on 2017-10-09
This definitely looks strange, and unexplained so far. It should work but it doesn't.
I would check permissions and ownership of all parent folders above the share. Don't forget that if you have any specific settings they can propagate if set up like that. Although it doesn't look like that from the info so fat.
I would also create specific folder for the shares data, it doesn't need to be in /srv just in case some umask is forced onto it.
You can create for example /data or /shares and put the test folder inside. That way you don't depend on permissions and ownership of the parent folders because there are no parent folders.

---

### Post by darkod on 2017-10-09
I know this is not a samba related reply, but you can also consider controlling the ownership/permissions/mask through linux filesystem instead of through samba. In fact, using linux filesystem might be cleaner because accessing through samba users still have to comply with both sets of permissions, in linux filesystem and in samba share.

For example, instead of 'force group' on my shares I use the sticky bit which makes all files and folders created to have the group ownership of the main folder (share). Especially if the folder is empty to start with, it is easy to set that up. In your case it would be something like:
```
sudo chgrp SchoolAdmin /srv/admindocstest
sudo chmod g+s /srv/admindocstest
```

After that everything you create in that folder will have the group ownership of SchoolAdmin, regardless whether you do it over samba share or local linux user in ssh session.

On the subject of permissions of the newly created files/folders, it looks like setfacl might help you, although I haven't used it before. I found it looking for a way to control permissions on a folder (what you need).
[https://help.ubuntu.com/community/FilePermissionsACLs](https://help.ubuntu.com/community/FilePermissionsACLs)
[http://manpages.ubuntu.com/manpages/xenial/man1/setfacl.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/setfacl.1.html)

You need user with RW, group with RW and other with nothing. The only thing I am unsure of is whether created files will inherit that, but you can try. If they don't, you will have to play with the mask value for the share folder.
```
sudo setfacl -m u:sperry:rwx /srv/admindocstest
sudo setfacl -m g:ShoolAdmin:rwx /srv/admindocstest
sudo setfacl -m o::--- /srv/admindocstest
```

See if that helps...

PS. After little trial and error, I think I got it. The above setfacl commands will set up the permissions on the folder (which you can also set by chmod). The important then is to use setfacl to set the default permissions for other (using the -d option).
```
sudo setfacl -d -m o::--- /srv/admindocstest
```

After that anything you create inside that folder will have 770 for folders and 660 for files. That should also apply to files created over samba.

---

### Post by shawn-f on 2017-10-09
We are close.

I have this set:

```
# file: .
# owner: sperry
# group: SchoolAdmin
# flags: -s-
user::rwx
group::rwx
other::---
default:user::rwx
default:group::---
default:group:SchoolAdmin:rwx
default:mask::rwx
```

I am getting this:
```
-rw-rw----+ 1 sperry SchoolAdmin    0 Oct  9 16:21 monkey
-rw-rwxr--+ 1 sperry SchoolAdmin    0 Oct  9 16:18 New Bitmap Image.bmp
drwxrwsr-x+ 2 sperry SchoolAdmin 4096 Oct  9 16:18 New folder
```

The file monkey was created by touch. The rest were created via samba.

---

### Post by darkod on 2017-10-10
You are missing the default ACL for other. Did you run the command I put in my PS in the previous post?

That is why files created through samba have R for other. According to the getfacl you have no default setting for other. Run that command above and it should be OK.

---

### Post by shawn-f on 2017-10-10
Yes, it's there.

```
# file: admindocs/
# owner: cburns
# group: SchoolAdmin
# flags: -s-
user::rwx
group::rwx
other::---
default:user::rwx
default:group::---
default:group:SchoolAdmin:rwx
default:mask::rwx
default:other::---
```

---

### Post by darkod on 2017-10-10
Try undoing the default mask. I did my tests since setting default mask because on the other hand it clashes with the other permissions giving rwx.

Or it might be simply that over samba it doesn't work the same. But I would remove the mask and test again.

---

### Post by shawn-f on 2017-10-10
No affect.

```
# file: admindocs/
# owner: cburns
# group: SchoolAdmin
# flags: -s-
user::rwx
group::rwx
other::---
default:user::rwx
default:group::---
default:group:SchoolAdmin:rwx   #effective:---
default:mask::---
default:other::---
```

```

drwxrws---+  3 sperry SchoolAdmin 4096 Oct 10 18:49 .
drwxrws---+ 58 cburns SchoolAdmin 4096 Oct  3 20:11 ..
-rw-rwxr--+  1 sperry SchoolAdmin    0 Oct 10 18:49 New Bitmap Image.bmp
drwxrwsr-x+  2 sperry SchoolAdmin 4096 Oct 10 18:49 New folder
```

---

### Post by darkod on 2017-10-11
I was thinking to remove the default:mask entry, not to change it from rwx to ---. Those two things are different. Was the default:mask already there initially or you put it there with getfacl? Because in my test it didn't exist.

Try removing it with something like:
```
sudo setfacl -d -x m::--- /path/folder
```

If that doesn't work, try putting it back to rwx and then removing it:
```
sudo setfacl -d -m m::rwx /path/folder
sudo setfacl -d -x m::rwx /path/folder
```

I can't be sure if this has any effect on samba, but better to remove the default:mask to be sure it is not getting in the way.

You have also removed all 'force' commands from the samba share and restarted samba, right?

PS. I edited the commands above. Initially I forgot the -d option which specifies to work with the default setting. I have added it now.

---

### Post by darkod on 2017-10-11
Maybe you should also try the following to make samba respect linux ACL on the share: [https://serverfault.com/questions/459479/samba-ignoring-posix-acls](https://serverfault.com/questions/459479/samba-ignoring-posix-acls)

---


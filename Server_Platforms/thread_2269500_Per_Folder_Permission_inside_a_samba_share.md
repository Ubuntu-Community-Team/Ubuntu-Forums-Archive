---
title: "Per Folder Permission inside a samba share"
date: 2015-03-16
forum: Server Platforms
---

### Post by francis8 on 2015-03-16
[COLOR=#141823][FONT=Helvetica]sorry for bothering but i do really need help with my ubuntu file/samba server.. i already tried googling but to no avail..
[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]i have this share/directory
[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]- sharedFolder
-- folderA
-- folderB
-- folderC
[/FONT][/COLOR]
[COLOR=#141823][FONT=Helvetica]"sharedFolder" should be accessible (read only) to all sharedFolderUsers (samba share)
"folderA" should only be accessible (full access) to "groupA"
"folderB" should only be accessible (full access) to "groupB"
"folderC" is accessible (full access) to "groupA" and "groupB"

drwxrwx--- sharedFolder 
drwxrws--- folderA 
drwxrws--- folderB
drwxrws--- folderC

[sharedFolder]
directory mode = 2770
force directory mode = 2770

***also tried:***
[sharedFolder]
directory mode = 4770
force directory mode = 4770
***and***
[sharedFolder]
directory mode = 0770
force directory mode = 0770

your help in doing this one and/or other alternative solution would really be appreciated..


NB: 
- if this post is not allowed.. please let me know and kindly direct me where i could ask this kind of query.. thanks..
- i do have an alternative but it would be not a good idea since i have around 10 sharedFolders and 15 subfolders each sharedFolder with different per user permissions
[/FONT][/COLOR]

---

### Post by volkswagner on 2015-03-16
Greetings. What version of SAMBA are you using?

You will want to look into acl_xattr to have multiple groups enabled on a shared folder.

---

### Post by francis8 on 2015-03-16
> **volkswagner said:**
> Greetings. What version of SAMBA are you using?

4.1.6-Ubuntu

> **volkswagner said:**
> You will want to look into acl_xattr to have multiple groups enabled on a shared folder.

Could you please elaborate or if you have directs links with complete explanation and/or tutorials, it would be much appreciated.

---

### Post by volkswagner on 2015-03-16
Here are some links from google (samba acl_xattr)
[https://www.samba.org/samba/docs/man/manpages/vfs_acl_xattr.8.html](https://www.samba.org/samba/docs/man/manpages/vfs_acl_xattr.8.html)
[https://wiki.samba.org/index.php/Setup_and_configure_file_shares_with_Windows_ACLs](https://wiki.samba.org/index.php/Setup_and_configure_file_shares_with_Windows_ACLs)


Can you post your smb.conf?

---

### Post by francis8 on 2015-03-17
> **volkswagner said:**
> Here are some links from google (samba acl_xattr)
[https://www.samba.org/samba/docs/man/manpages/vfs_acl_xattr.8.html](https://www.samba.org/samba/docs/man/manpages/vfs_acl_xattr.8.html)
[https://wiki.samba.org/index.php/Setup_and_configure_file_shares_with_Windows_ACLs](https://wiki.samba.org/index.php/Setup_and_configure_file_shares_with_Windows_ACLs)


Can you post your smb.conf?


as requested, please find below. hoping that this would be of help to enlighten the issue.

> 
#======================= Global Settings =======================

[global]

## Browsing/Identification ###
    workgroup = WORKGROUP
    server string = %h server (Samba, Ubuntu)
    dns proxy = no

#### Debugging/Accounting ####
    log file = /var/log/samba/log.%m
    max log size = 1000
    syslog = 0
    panic action = /usr/share/samba/panic-action %d

####### Authentication #######
    server role = standalone server
    passdb backend = tdbsam
    obey pam restrictions = yes
    unix password sync = yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    pam password change = yes
    map to guest = bad user


#====================== Share Definitions =======================

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

security = share

[Monthly Attendance]
    write list = administrator,@attendance
    path = /media/Files/0. Monthly Attendance
    force user = administrator
    valid users = administrator,@attendance
    create mode = 770
    directory mode = 770
    writeable = yes
    browsable = yes
    guest ok = no
     
[Projects]
    create mode = 770
    directory mode = 770
    path = /media/Files/1. Projects
    writeable = yes

[Accounts]
    path = /media/Files/2. Accounts

[Procurement]
    path = /media/Files/3. Procurement

[Administration]
    path = /media/Files/4. Administration

[QHSE]
    path = /media/Files/6. QHSE

[Warehouse]
    path = /media/Files/7. Warehouse

[Fuel Expense]
    path = /media/Files/9. Fuel Expense

[Documentation]
    path = /media/Files/11. Documentation

[SAQ]
    path = /media/Files/12. SAQ

[Back-up - Management]
    path = /media/Files/13. Management



---

### Post by volkswagner on 2015-03-17
May I ask why you selected "security = share" vs "security = user"?
If you're not sure, [take a look at the comparison of security and modes for SAMBA]("https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html").

Have you researched acl's?

Since you are running a standalone server with Linux accounts you may simply need to setup
POSIX ACL's.  [Here is some info on acl's]("https://help.ubuntu.com/community/FilePermissionsACLs").

So you will need a combination of share permissions and filesystem permissions to accomplish your goal.

You have not listed yet your specific symptom or problem, only your goal.

---

### Post by francis8 on 2015-03-26
Sorry for the delayed response.

> **volkswagner said:**
> May I ask why you selected "security = share" vs "security = user"?
If you're not sure, [take a look at the comparison of security and modes for SAMBA]("https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html").


Previously, I am using this kind of setting where a group of users could access a certain sharedFolder. I am just trying my luck if this will work or not. :confused:

> **volkswagner said:**
> 
Have you researched acl's?

Since you are running a standalone server with Linux accounts you may simply need to setup
POSIX ACL's.  [Here is some info on acl's]("https://help.ubuntu.com/community/FilePermissionsACLs").

So you will need a combination of share permissions and filesystem permissions to accomplish your goal.


I am kindly asking if you could elaborate this matter since I am a bit confused. I already tried googling but the explainations are still broad for me.

> **volkswagner said:**
> 
You have not listed yet your specific symptom or problem, only your goal.

Apologies.

With the current config, I could create multiple sharedFolders to acheive what I wanted and would have a long list of shared folders.

But it would not be the case since I need to group these multiple sharedFolders into subfolders (with its own permission) under specific department folders.

Currently, if the user is logged in and could access one sharedFolder, he would have full access to all subfolders and files on that sharedFolder.

---

### Post by volkswagner on 2015-03-26
You should find most of what you need in [this article]("http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm"). 

With the above how to you can easily accomplish your goal. You can have one share and set permissions, default permission (for new files
and directories), hide files not readable to underprivileged users, etc.

The how to mentions setting permissions from a windows box, but you'd need domain users for that. You can
substitute those actions and set the permissions via setfacl.

I still think you'll have better results with "security = user".

---

### Post by bab1 on 2015-03-26
> ** francis8 ]With the current config, I could create multiple sharedFolders to acheive what I wanted and would have a long list of shared folders.[/QUOTE]

I would use multiple [s]workgroups[/s] servers with differing workgroups and sort that "long list of shared folders" by workgroup.  The advantages of using **Samba** user security far out ways the your (the admin) convenience.

[COLOR="#0000FF"]**Edit:** It was late and I have misspoken about multiple workgroups.  One workgroup per server is correct.  Multiple workgroups per the network.  Still, I would reevaluate what groups are needed for what shares.[/COLOR]


[QUOTE=volkswagner said:**
> I still think you'll have better results with "security = user".
If the OP elects not to use Samba "security = user" there will be **no Samba authentication at all.**  I believe there will be no Windows style ACL's either.  The entire security capability is limited to the Linux file permissions and POSIX style ACL's.  The Windows POSIX implementation is NOT the same as IEEE (Linux) POSIX.

I would always use *security=user* at minimum for availability security and compatibility between Windows and Linux.  The file system and shares should be configured to that standard.  It is always a tradeoff between security or convenience.  As a systems architect I will take the secure way on behalf of my users.

---


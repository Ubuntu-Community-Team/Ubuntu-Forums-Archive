---
title: "Allow all file-permissions for everyone"
date: 2010-05-11
forum: Server Platforms
---

### Post by stn21 on 2010-05-11
Hi,

on certain folders on a samba-server I would like to allow everyone everything.

(Note: This refers to the filesystem-permissions. External security is cared for by samba. No problem here)

That means: every local user and every remote user should be able to fully create, delete and modify every file in certain folders and all subfolder of these folders. This should include file contents and timestamps and permissions. 

And it should include modifying files owned by someone else, again meaning create/delete/modify/timestamp etc. Here is what happens:

> user1@PC$ dir > testfile 
user1@PC:$ su user2
Passwort: 
user2@PC$ dir > testfile
bash: testfile: Permission denied
user2@PC$ dir -l testfile
-rw-r--r-- 1 user1 user1 2797 2010-05-11 22:36 testfile
This should not happen. User2 should be allowed full access to the file User1 created.

How do I get ubuntu not to enforce any permissions at all and allow everything ?

---

### Post by mhgsys on 2010-05-11
in /etc/samba.smb.conf under #authentication set security to share; and invalid users to root for a little safety

like this
```
section ####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
  security = share
  invalid user = root

```

after that
create a shareable map; 
f.e
```
mkdir map
```
```
chmod 777 map
```

and share it with samba;
f.e
```
[map]
comment = bla
path = /home/mhgsys/Desktop/map
browseable = yes
#read only = no
guest ok = yes
writeable = yes

```

---

### Post by sisco311 on 2010-05-11
> **stn21 said:**
> 
(Note: This refers to the filesystem-permissions. External security is cared for by samba. No problem here)



ACLs or bindfs.

ACL:
[http://www.youtube.com/watch?v=6piQXXHTmqk](http://www.youtube.com/watch?v=6piQXXHTmqk)
[uhelp]community/UbuntuLTSP/ACLSupport[/uhelp]

bindfs:
[http://code.google.com/p/bindfs/](http://code.google.com/p/bindfs/)
[thread]1460472[/thread]

---

### Post by stn21 on 2010-05-12
> **sisco311 said:**
> ACLs or bindfs.
ACL:
[http://www.youtube.com/watch?v=6piQXXHTmqk](http://www.youtube.com/watch?v=6piQXXHTmqk)
[uhelp]community/UbuntuLTSP/ACLSupport[/uhelp]


OK, lets see.

Here are the ACLs for the directory. Looks like everyone can do everything.

```
user1@PC:$ getfacl .
# file: .
# owner: user1
# group: user1
user::rwx
group::rwx
other::rwx

```Other user creates file:

```
user2@PC$ touch zz
user2@PC$ getfacl zz
# file: zz
# owner: user2
# group: user1
user::rw-
group::r--
other::r--
```Now user1 can delete the file but cannot "touch" it. Permission denied. That doesn't make sense. The file should inherit the ACL of the folder. 

If you "chmod a+rwx zz" then user1 can "touch" it too. But chmoding every new file after creation does not seem to be a really elegant way. Certainly I cannot imagine asking my colleague (user2) to do that regularly :)




> 
bindfs:
[http://code.google.com/p/bindfs/](http://code.google.com/p/bindfs/)
[thread]1460472[/thread]I was kind of hoping for a less complicated solution, possibly even with mount-options only.

The mode "everyone can do everything" is the most basic set of permissions that I can think of. Everything else was added years later. So it should be possible to simple leave out everything except the basic mode. Kind of like FAT(32). But with the features of ext3+ like symlinks and journaling.




Edit: removing "acl" from the options in /etc/fstab did not change anything either.

---

### Post by stn21 on 2010-05-12
> **mhgsys said:**
> 
  security = share
...
after that create a shareable map;  ... chmod 777
...
guest ok = yes

chmod 777 : already done

security = share was probably already active, the line "security = user" was commented out. I activated "share" anyway

guest ok = yes: no can do, not everyone should log in, just users with a valid password. But that is not important, with guest ok = yes the same problems occur.


I made the changes but no change. Touching someone else's file from remote (samba-share) still does not work. Deleting works but only with 'rm -f' . 

Different rules everywhere. 
This seems to be a problem with the local permissions. Users logged in locally have the same issues as samba-users.

That's why I want to switch off all ACLs or at least have unconditional rwx for everyone.

---

### Post by sisco311 on 2010-05-12
I don't know much about samba, but to grant read/write permissions for local users, you have to run something like:

```
setfacl -Rdm o:wrx /path/to/dir
setfacl -Rm o:wrx /path/to/dir
```
(ACLs)

or:
```
bindfs -o perms=0777 /path/to/dir /path/to/dir
```
(bindfs)

---

### Post by benderisgreat on 2010-05-12
'chmod 777 <directory>' only changes changes the permissions for the directory.
It sounds like you already have files in the directory you want to share. To also change the permissions of the files contained in the directory recursively run:
```
# chmod -R 777 <directory>
```

Newly created files however won't be affected. To have files be created read/write via your samba share put this in your smbd.conf:```
[share]
..
create mask = 777
```

---

### Post by psusi on 2010-05-12
You didn't set an ACL.  getfacl was just reporting the normal mode mask.

---

### Post by Morbius1 on 2010-05-12
I've never thought of using bindfs with samba together so I figured I'd try a quick experiment:

Created a directory: **/mnt/Common**

Added an entry in fstab to allow all local users to have complete access:
```
bindfs#/mnt/Common /mnt/Common fuse perms=0777 0 0
```Shared the directory ( in this case to allow guests ):
```
[Common]
    path=/mnt/Common
    writeable = yes
    guest ok = yes
```All local login users as well as all remote samba users have full access to every directory and file. All local files will have permissions of 777. All remote files added will have permissions of 777.

The only peculiarity about this is ownership. If local user1 edits and saves a local user2 file, it will retain user2's ownership. A remote guest editing and saving a local user2 file will have ownership changed to "nobody" ( because I'm allowing guest access in this case). It doesn't matter though because all files will have permissions of 777. 

Of course you still have complete control over who has remote access in the samba share definition.

The bindfs statement in fstab can be better tweaked to get you more control if you desire. sisco311 is the expert on these matters :wink:

Does this do what you want?



[COLOR=Blue]BTW, put "security = user" back in smb.conf. [/COLOR]

---

### Post by stn21 on 2010-05-13
@[sisco311]("http://ubuntuforums.org/member.php?u=244665"), [Morbius1]("http://ubuntuforums.org/member.php?u=982144")  
thanks for the infos on bindfs. It seems to be a tool with many  possibilities. I think I will explore it when I have a little more time.

@[benderisgreat]("http://ubuntuforums.org/member.php?u=901212")  
chmod+smb.conf only helps if you access the files via the  samba-share. 

The problem here was that permissions of local  users got in each other's way **and** in the way of samba-users. Any  solution would have to solve the local conflicts first and only after  that the samba-issues.




The different hints on ACLs  helped to find an immediate solution with only very few caveats.

Here  a short summary:

[LIST=1]
[*]sudo apt-get install acl
The  'acl'-package contains getfacl and setfacl

.
[*]Ext2/3/4-volumes  must be mounted with the option 'acl'. In /etc/fstab that would be  something like
'/dev/sda5    /media/mountpoint        auto     defaults,exec,user_xattr,acl      0       0'

.
[*]Current  permissions can be checked with 'getfacl <path-to-directory>' or  getfacl <filespec>

.
[*]Then after remount/reboot there  are many new options for the permissions of files and directories.  Important are the "default"-permissions. These are set for directories,  not for individual files. Any file that is created after that inherits  the 'rw'-part of these default-permissions.
 
Warning: using  setfacl is not as easy as it looks at first. Some caveats are mentioned  below. So do **not** make your first attempts by using setfacl to  recursively go through your whole harddisk. Start with one directory :!:

```
#  Here goes:
$ mkdir test    ## create new directory
$ setfacl -Rdm  o::rwx test
$ setfacl -Rdm g::rwx test
$ setfacl -Rdm u::rwx test
#  check:
$ getfacl test
default:user::rwx
default:group::rwx
default:other::rwx
```The  execute-flat (x) is not inherited by new files. It is inherited by new  directories. It **must** be set in the defaults, otherwise you will  not be able to chdir into new directories.:tongue:

The  '-R'-option of setfacl means "recurse through all subdirectories, '-d'  means "modify default-permissions" and '-m' means "modify" as opposed to  "set".


.
[*]Warning: I recommend starting with an empty  directory, then modify the default-permissions and then put files in it.  

You can of course use setfacl -Rm o::rwx (and then u::rwx and  then g::rwx) to modify all permissions of existing files but you will  set the 'x'-flag for every file. If you leave out the x you will remove  the 'x'-flag meaning you will not have any executable files left. (Have  no idea how to set 'rw' without influencing 'x')
[/LIST]

---

### Post by Gaurav_Ag on 2010-05-14
[ATTACH]156899[/ATTACH]Hi,
I'm new to all this samba server and other configuration. I need all ur help.I made connection ubuntu and windows and is able to tranfer file.
But wht if i want all the user to access automatically their own respective folders without adding each user in smb.conf.

My smb.config file is like this
```

[global]
    ; General server settings
    netbios name = gaurav
    server string =
    workgroup = MQ
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba/
    browseable = no
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = gaurav
    force group = gaurav

[Florian]
path = /home/samba/Florian
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0770
force user = florian
force group = florian



```here at last i'm trying to make add each user.
please help.

---


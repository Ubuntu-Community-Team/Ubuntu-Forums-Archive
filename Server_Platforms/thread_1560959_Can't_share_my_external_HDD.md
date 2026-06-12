---
title: "Can't share my external HDD???"
date: 2010-08-25
forum: Server Platforms
---

### Post by JD32 on 2010-08-25
Im running Ubuntu 10 desktop. Im trying to make it my fileserver for my  windows laptops. The computer im using only has a 40GB HDD so I want to  be able to share my 1TB external HDD. I cant get it to work to save my  life. I read another forum from a guy trying to do something similar but  it still wont work.

I reformatted the drive to ext4, added it to fstab and gave it 777  permission but windows still keeps giving me an error thats saying there  might be a problem with my spelling or a problem with my network?

Any help would be greatly appreciated!

---

### Post by ajgreeny on 2010-08-25
I am not sure about windows shares and all that, but does the fact that the external disk is ext4 have any bearing on this?  Have you tried it formatted as fat32 or ntfs?

I may be totally wrong, as shared folders on a ubuntu server are normally in a linux format I accept, but I wonder if the fact that it is external makes any difference.  I've no idea why it should, but am just thinking of all possibilities.

---

### Post by Morbius1 on 2010-08-25
To be able to help you we need more information:

How are you sharing it - Samba?

What method of Samba - there are 2. To help us find out post the output of the following commands:
```
net usershare info
sudo net usershare info
testparm -s
```Need to see the fstab line you added:
```
cat /etc/fstab
```Need to see the permissions of the 1TB mount point:
```
ls -dl /path_to_mount_point
```And finally post the output of the following command so we can see the status of your shares:
```
smbtree
```

---

### Post by JD32 on 2010-08-25
_1st_

jd@File-Server:~$ net user info

net [<method>] user [misc. options] [targets]
    List users

net [<method>] user DELETE <name> [misc. options] [targets]
    Delete specified user

net [<method>] user INFO <name> [misc. options] [targets]
    List the domain groups of the specified user

net [<method>] user ADD <name> [password] [-c container] [-F user flags] [misc. options] [targets]
    Add specified user

net [<method>] user RENAME <oldusername> <newusername> [targets]
    Rename specified user

Valid methods: (auto-detected if not specified)
    ads                Active Directory (LDAP/Kerberos)
    rpc                DCE-RPC
    rap                RAP (older systems)

Valid targets: choose one (none defaults to localhost)
    -S or --server=<server>        server name
    -I or --ipaddress=<ipaddr>    address of target server
    -w or --workgroup=<wg>        target workgroup or domain

Valid miscellaneous options are:
    -p or --port=<port>        connection port on target
    -W or --myworkgroup=<wg>    client workgroup
    -d or --debuglevel=<level>    debug level (0-10)
    -n or --myname=<name>        client name
    -U or --user=<name>        user name
    -s or --configfile=<path>    pathname of smb.conf file
    -l or --long            Display full information
    -V or --version            Print samba version information
    -P or --machine-pass        Authenticate as machine account
    -e or --encrypt            Encrypt SMB transport (UNIX extended servers only)
    -k or --kerberos        Use kerberos (active directory) authentication
    -C or --comment=<comment>    descriptive comment (for add only)
    -c or --container=<container>    LDAP container, defaults to cn=Users (for add in ADS only)
jd@File-Server:~$ sudo net usershare info
jd@File-Server:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers



_2nd_

I tryed to add " /dev/sbd1  media/fantom   defaults  0    0" but after it wouldnt even let my drive mount. PS- fantom is the volume

but this is what i got.

jd@File-Server:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9f1c8c25-fb5f-4bfd-b2fc-378be2d090da /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c1e800c8-55e9-43ad-b319-3c4a7d0a311c none            swap    sw              0       0



_3rd_

haven't a clue what this means

jd@File-Server:~$ ls -dl /media/fantom
drwx------ 4 jd jd 4096 2010-08-24 18:45 /media/fantom

_4th_ 

jd@File-Server:~$ smbtree
Enter jd's password: 
WORKGROUP
    \\PC                     Desktop
        \\PC\IPC$               Remote IPC
        \\PC\H$                 Default share
        \\PC\Fantom HDD         
        \\PC\C$                 Default share
        \\PC\ADMIN$             Remote Admin
    \\FILE-SERVER            File-Server server (Samba, Ubuntu)
        \\FILE-SERVER\data               
        \\FILE-SERVER\screen shots       
        \\FILE-SERVER\IPC$               IPC Service (File-Server server (Samba, Ubuntu))
        \\FILE-SERVER\print$             Printer Drivers




Thanks for the help!!!

---

### Post by Morbius1 on 2010-08-26
Okey Doke,

_1st_
The usershare command is:
```
net usershare info
```You you did was:
> jd@File-Server:~$ [COLOR=Blue]net user info[/COLOR]
Try it again please.
[U]
2nd[/U]
> I tryed to add " /dev/sbd1  media/fantom   defaults  0    0" but after it wouldnt even let my drive mount. It's the wrong syntax and wouldn't have worked anyway since you left out the filetype in the expression. However since it is an external drive it really doesn't have to automount at boot time anyway.

_3rd_
> jd@File-Server:~$ ls -dl /media/fantom
drwx------ 4 jd jd 4096 2010-08-24 18:45 /media/fantom
What you said you did was this:
> I reformatted the drive to ext4, added it to fstab and gave it 777   permission ....
In reality you either did one of two things:
(1) You may have formatted it to ext4 but you gave it permissions of 700 and you changed ownership from root to "jd"

(2) Or, it's still formatted in NTFS since by default an external NTFS partition will mount with the user as owner and permissions of 700 which is what you have.

If I make some grand assumptions on what I think you've done, the solution to your dilemma is relatively simple. Add the following line to the [global] section of /etc/samba/smb.conf:
```
force user = jd
```But I'd feel more comfortable about that recommendation if I saw the output of :
```
net usershare info
```And another one:
```
sudo blkid -c /dev/null
```

---

### Post by JD32 on 2010-08-26
_1st_

sorry about that 

```
jd@File-Server:~$ net usershare info
info_fn: file /var/lib/samba/usershares/downloads is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/data is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[screen shots]
path=/home/jd/Pictures/Screen Shots
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/movies is not a well formed usershare file.
info_fn: Error was Path is not a directory.
```[U]2nd

[/U]I actually did added the formant, but i prob didnt do it right anyway haha. So your saying thats not needed anyway?

[U]3rd
[/U]I'm kinda lost on this, it was in NTFS when it was on my windows but i just went through the disk utility on ubuntu and reformted it to ext4. Not sure if that what you were asking and i don't really now how the permissions work. But heres that last code....

```
jd@File-Server:~$ sudo blkid -c /dev/null
[sudo] password for jd: 
/dev/sda1: UUID="9f1c8c25-fb5f-4bfd-b2fc-378be2d090da" TYPE="ext4" 
/dev/sda5: UUID="c1e800c8-55e9-43ad-b319-3c4a7d0a311c" TYPE="swap" 
```
PS- I really appreciate the help, im new to linux and was gonna run a windows server but i really wanna learn linux, the command line is just taking some getting used to

---

### Post by Morbius1 on 2010-08-26
Um ......... Is the 1TB drive running?

Plug your 1TB external drive in and turn it on and rerun the following commands:

```
 net usershare info
```
```
 sudo blkid -c /dev/null
```

---

### Post by JD32 on 2010-08-26
haha opps sorry i had it turned off, i'm at school now ill get ya that in a bit

---

### Post by JD32 on 2010-08-26
drive is plugged in and and mounted

net usershare info =

```
jd@File-Server:~$ net usershare info
info_fn: file /var/lib/samba/usershares/downloads is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[data]
path=/media/fantom/Data
comment=
usershare_acl=Everyone:F,
guest_ok=y

[screen shots]
path=/home/jd/Pictures/Screen Shots
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/movies is not a well formed usershare file.
info_fn: Error was Path is not a directory.
```
sudo blkid -c /dev/null  =

```
jd@File-Server:~$ sudo blkid -c /dev/null
[sudo] password for jd: 
/dev/sda1: UUID="9f1c8c25-fb5f-4bfd-b2fc-378be2d090da" TYPE="ext4" 
/dev/sda5: UUID="c1e800c8-55e9-43ad-b319-3c4a7d0a311c" TYPE="swap" 
jd@File-Server:~$ sudo samba
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
jd@File-Server:~$ net usershare info
info_fn: file /var/lib/samba/usershares/downloads is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[data]
path=/media/fantom/Data
comment=
usershare_acl=Everyone:F,
guest_ok=y

[screen shots]
path=/home/jd/Pictures/Screen Shots
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/movies is not a well formed usershare file.
info_fn: Error was Path is not a directory.
jd@File-Server:~$ sudo blkid  -c /dev/null
[sudo] password for jd: 
/dev/sda1: UUID="9f1c8c25-fb5f-4bfd-b2fc-378be2d090da" TYPE="ext4" 
/dev/sda5: UUID="c1e800c8-55e9-43ad-b319-3c4a7d0a311c" TYPE="swap" 
/dev/sdb1: LABEL="fantom" UUID="d23ed25f-7404-4868-8074-934b351ac89b" TYPE="ext4" 
```

---

### Post by Morbius1 on 2010-08-26
Make sure the 1TB drive is turned on.

Open a terminal and type:
```
sudo chmod 777 /media/fantom
```To confirm it successfully modified the permisssions type:
```
ls -dl /media/fantom
```It should come back with this:
> drwxrwxrwx 4 jd jd 4096 .... 

---

### Post by JD32 on 2010-08-26
Yayyyy! it worked. Thanks so much for the help! I cant believe it was that simple!

---

### Post by Vishal Agarwal on 2010-08-26
Pls mark this thread status to solved. It will help others later to get their same type problem solved.

---

### Post by JD32 on 2010-08-27
Quick question tho, could i have left the drive in NTFS format so it would have still worked on my windows machines?

And for future reference is that last code you gave me all you need to do to enable sharing of the drive? just give it 777 permission. I would let to understand what i actually did haha

---

### Post by Morbius1 on 2010-08-27
>          Quick question tho, could i have left the drive in NTFS format so it would have still worked on my windows machines?Yes, but the solution would be different. You can't chmod a windows filesystem ( NTFS or FAT32 ). But you could have achieved the same result using samba itself - it's just a bit more involved.

> And for future reference is that last code you gave me all you need to  do to enable sharing of the drive? just give it 777 permission.Yes and No. You created the share allowing guest access.
Samba determines who MAY access a shared resource but only linux itself determines who CAN access the folder. Nautilus-share insures that the folder permissions and samba authentication are in sync. The problem you had was the 0700 permissions on the parent folder: /media/fantom. There was no way for the remote user to drill down to the "Data" folder because the only user that had access to the parent folder was 'jd".

You needed to allow everyone to at least open the /media/fantom directory so either a 755 or a 777 or I guess even a 711 would have worked.

---

### Post by JD32 on 2010-08-27
sorry for all the questions but what is the difference between all the permission numbers? 

And how much more involved is it to share NTFS? i kinda want to have it work on both machines but if its over my head ill save that for another day

---

### Post by Morbius1 on 2010-08-27
>          sorry for all the questions but what is the difference between all the permission numbers? Each digit represents a different user:
1st digit = owner
2nd digit = group
3rd digit = world

Each number represent a different permission:
4 = read
2 = write
1 = execute  ( on a directory it means open or access )
And their additive, so a 7 allows full access ( 4+2+1), a 5 allows read and for the folder to be opened ( 4+1 ), etc...

So a 777 allows full access to owner, group, and everyone else.
A 755 allows full access to owner but read and open to group and everyone else.

>  And how much more involved is it to share NTFS? i kinda want to have it  work on both machines but if its over my head ill save that for another  day     The easiest way would be to add a line to the [global] section of /etc/samba/smb.conf:
```
force user = jd
```The external NTFS drive will mount with you as the owner and as the only person who can access the drive. The force user will act as a mask and convert the remote user to you for those shares. 

Actually, now that I think about it this would have worked in this situation as well. I'm used to actually fixing permissions on linux filesystems to resolve these types of things but force user would have worked her too.

---


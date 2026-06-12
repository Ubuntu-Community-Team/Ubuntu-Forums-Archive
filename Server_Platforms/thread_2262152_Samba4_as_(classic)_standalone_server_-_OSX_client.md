---
title: "Samba4 as (classic) standalone server - OSX clients cannot delete dirs from others"
date: 2015-01-23
forum: Server Platforms
---

### Post by lptr on 2015-01-23
LTS 14.04.1 this is strictly the ancient Samba config no Domain Server nor ADC - no ACLs active on server machine.  Machines are not joined in any manner just using workgroup WG02. 

With the original config I recognized strange behaviours while using different Windows clients (XP, Win7pro) as also as OS X machine clients (Snow Leopard and Maverics). Sometimes it seemed that especially Maverics looses connects to smbd then there are messages telling of no sufficient access rights. If this happens no machine can access Samba4

What I see in file system rights is following:
If creating a new directory from an OSX machine I getting on any folders created in *public share* directory rigths **drwxrwxr-x** instead of [B]drwxrwxrwx
[/B]
The config below use *unix extension = No* 
so with directory mask that should be rw for others, too. Maybe a bug in Samba4? Anyways...

When creating a new directory from OSX in *office share* the rigths **drwxrwx---** do apply.

For Linux world and Windows world everything is fine. But this does not apply to OSX clients.

The point is something different:
OSX creates hidden files. Namely *.DS_Store* and *._.DS_Store* in every accessed directory (other ._.files will created either but are not important here). In Linux that two files appear to have user and group set to that first accessing user/group hitting the root of where those directories are located. Force group does modified to that one. All fine - right ? No - it is not.

The problem is starting when a _different user_ instead of creator tries deleting dirs from an OSX machine. For same user in share *office* this will always work. However when using a different user that is member of group @samba it does not. It was not obvious what caused the trouble, first. The solution to this will get obvious **ONLY **when using the *terminal* on a Mac (whom Mac users doing this ;) ?). If one changes there into that mounted Samba share (*$ cd /Volumes/sharename*) and doing a *[COLOR=#000000]$ ls -l@eO .DS_Store[/COLOR]* then it will getting visible, that OSX 'thinks' that directory to be deleted is created by another Mac user which has full access rights but all others having none. This informations are stored in those two hidden files. If there are no OS X clients connected to that share, any directories may be deleted by Windows client machines with valid user/pswd and using workgroup *WG02*. But other OSX machines will getting blocked out by OSX itself as they are first looking into those files and detecting there are no access rights.

A solution that is working (with disadvantage that no other OSX machines may visiting that share or directories inside it with Finder or any other prog like MS-Office the same time) to delete directories is to *use delete veto files = yes*. Samba will kill these two files specified every time if OSX client locks on those will disappear. Not elegant but helps with access problems at least in small(er) environments.

```
[global]
    workgroup = WG02
    netbios name = SIMPLE-SMB4
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    unix extensions = No
    os level = 33
    preferred master = Yes
    dns proxy = No
    wins support = Yes
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[public]
    comment = PUBLIC Directory
    path = /home/samba/public
    read only = No
    create mask = 0666
    directory mask = 0777
    guest ok = Yes

[office]
    comment = OFFICE Directory
    path = /home/samba/office
    valid users = @samba
    force group = samba
    veto files = /.DS_Store/._.DS_Store/
    delete veto files = yes
    read only = No
    create mask = 0660
    directory mask = 0770

```

---

### Post by darkod on 2015-01-23
I failed to understand, how are you doing authentication? Local users on the samba server?

---

### Post by lptr on 2015-01-23
Local users (see smb.conf). No Domain nor ADC server role. The stupid simple Samba server standalone. Windows clients just need to use same Workgroup, Mac clients just specifying for example cifs://anysambauser@rttc-test and giving the password that was defined with smbpasswd in password dialog.

Again: Login works like expected, when no error - I originally described - occured. Creating folders, files all fine. One violation and everything sucks!

---

### Post by lptr on 2015-01-29
Ok I found the solution to the problem and why this troubles are with OS X clients.

From here: [http://apple.stackexchange.com/questions/136248/disable-storage-of-invisible-files-on-my-cfs-or-smb-network-storage](http://apple.stackexchange.com/questions/136248/disable-storage-of-invisible-files-on-my-cfs-or-smb-network-storage)
I did learn that OS X does hide ACLs inside this hidden files .DS_Store and ._.DS_Store. If one uses $ ls -l@eO .DS_Store from the OS X machine it will explain why the other machine refuses to kill this directory even it would have unix file rights drwxrwx--- on Samba server. For another OS X client machine it 'seems' is owned by user1 that is member of group 'staff'. user1 has full access rights but 'staff' does not. So the ACLs inside this .DS_Store file simply says the other OS X to prevent deleting the directory. Strangely this is not true for the hidden ._.files inside the share that is generated.

As of this I did add these two lines [office] section:```
[INDENT]veto files = /.DS_Store/._.DS_Store/ 
delete veto files = yes
[/INDENT]

```

I don't know if there are other strange side effects, yet. Will post it here if I find some.

Oh and yes - don't stick with Finder from another machine on that to deleted directory. That will also prevent killing it.

---


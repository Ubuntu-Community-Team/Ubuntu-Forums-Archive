---
title: "Need help to use Local Network Share with Ubuntu 18.04"
date: 2021-07-02
forum: Server Platforms
---

### Post by tryphon2 on 2021-07-02
Hello,

I want to build a Samba share under Ubuntu Server 18.04 and I face a strange error when I try to connect to my shared folder. On the same machine I use the terminal (just to check if I can reach my share on the network using the same computer) :

```
smbclient //10.1.2.3/MyShare -U myname
```

If I enter a wrong password I get : session setup failed: NT_STATUS_LOGON_FAILURE
If I enter the right password I get the smb prompt.
Fine.
When I execute any command as 'ls' I get : NT_STATUS_ACCESS_DENIED \*

I followed this tutorial : [https://www.digitalocean.com/community/tutorials/how-to-set-up-a-samba-share-for-a-small-organization-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-samba-share-for-a-small-organization-on-ubuntu-16-04)
(Yes I used smbpasswd -a command, and Samba application is in the list of the firewall)

Then to understand what's wrong, I try the simplest way to share a folder under Ubuntu 18.04 and 20.04 on 3 different computers on various physical networks. I am following this (creating a folder in my home directory) : [https://ubuntuhandbook.org/index.php/2019/11/share-folder-ubuntu-18-04-step-by-step-guide/](https://ubuntuhandbook.org/index.php/2019/11/share-folder-ubuntu-18-04-step-by-step-guide/)

Quite simple but even with the right username/password the logon window cycle indefinitely as if I entered wrong credentials. Whatever the computer I use, it is the same issue. I am unable to access a shared folder from the same machine (I tried of course to access it from another Ubuntu machine on the network with the same issue).

If I check "Guest access", this is the only way to enter my share. I am really stuck there.

Is there something to do not specified in the tutorials to have this working? Or I am unlucky with 3 Ubuntu computers ...

Thank you for your help.

---

### Post by TheFu on 2021-07-02
Please post the output from 
```
testparm
```
and which file systems are being used by the shared storage.  If the storage is mounted, that can be determined a few different ways:
```
df -hT -x squashfs -x tmpfs -x devtmpfs 
```
or 
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
Native Linux file systems - those that support POSIX permissions - are a little easier to share and provide more options than non-native file systems like NTFS or exFAT or FAT32.

In the smb.conf file, I only modify a few things in the [global] section:
```
   workgroup = MYWORKGRP
   security = user
; This is for the smb server; 
   min protocol = SMB2
; This is for the smb/cifs client connecting to Windows
   client min protocol = SMB2
   server signing = mandatory
```
I leave other lines alone.

In the "share" section to let users access their personal HOME directory, I use:
```
[homes]
  comment = Home Directories
  hosts allow = 127.0.0.1 172.22.22.0/24 172.22.22.27
  hosts deny = 0.0.0.0/0
  browseable = yes
  guest ok = no
  writable = yes
  create mask = 0644
  directory mask = 0755
  valid users = %S
```
 Nothing else.  That's it.  restart the smbd service and use a username created with the **smbpasswd** command.
Bob's your uncle.

For storage that isn't HOME directories, just add a
```
        path = /d
```
which points to the directory you'd like to share. Easy peasy.  Don't forget to restart the smbd service.


However, samba is a worst-case solution for Unix-to-Unix file sharing.  There are more complete implementations that behave like local storage. NFS if the preferred method.  NFS storage acts like local storage with users, groups, POSIX permissions, ACLs and xattrs.  It is usually faster than CIFS too, mainly because NFS is part of the Linux kernel.  Any interest?  You can run both NFS and CIFS sharing on the same storage.

---

### Post by Morbius1 on 2021-07-03
You stated that you are using Ubuntu Server but you reference Local Network Share which is Ubuntu desktop.

Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by tryphon2 on 2021-07-03
I spent more .... more time and get somes results

Ubuntu server 18.04 is installed on a Proliant DL380 machine with pfSense (KVM) running fine as firewall/router to manage a VLAN.

```
testparm -s
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit max (1024) to minimum Windows limit (16384)
Processing section "[Test]"
Loaded services OK.
Server role: ROLE_STANDALONE

```
# Global parameters
[global]
client min protocol = SMB2
disable netbios = Yes
log file = /var/log/samba/smb.log
max log size = 10000
passdb backend = smbpasswd
security = USER
server min protocol = SMB2
server role = standalone server
server signing = required
server string = Ubuntu_server
smb ports= 445
workgroup = LAB.LAN
idmap config * : backend = tbd

[Test]
create mask = 0600
directory mask = 0750
force create mode = 0640
force directory mode = 02770
force user = sudoer2
hosts allow = 127.0.0.1 10.1.2.0/24 10.1.2.3
hosts deny = 0.0.0.0/0
path = /mnt/Storage/Test
read only = no
valid users = @sambashare @admin
```

Note : sudoer2 has sambashare as primary group and admin as secondary group

```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
Filesystem    Type    Size    Use%    Mounted on
/dev/sda5     ext4     78G    18%     /
/dev/sda2     vfat      260M  20%     /boot/efi
/dev/sdb       ext4     7.3T    1%      /mnt/Storage

sdb is a RAID volume

@ TheFu : You suggested to fill the path variable with the storage location. This is what I need (the system disk is SSD where I do not want to share anything).
However, smbclient is not able to access a drive mounted in /mnt ([COLOR=#000000]NT_STATUS_ACCESS_DENIED[/COLOR]). I searched for this situation and found this work around to add in [Test] section :

[HTML]force user = sudoer2[/HTML]

I created sudoer2 which is granted to access Test folder in /mnt/Storage
```
sudo chown :sambashare /mnt/Storage
```

I forced  sudoer2 to have sambashare as primary group :
[HTML]sudo usermod -g sambashare -a -G admin sudoer2[/HTML]

I do not find other way to get an admin user granted to read/write both in Ubuntu file system and in shared folders throughout Samba. If primary group for sudoer2 is not sambashare and is not forced in [Test] section, any normal user created to access shares via Samba cannot access (read/write) mounted drives.

I found this construction somewhat inelegant and complicated to just obtain shares over the network.
Now other computers cannot access the Test share : 
```
smbclient -L //10.1.2.3
```
do_connect : Connection to 10.1.2.3 failed (Error NT_STATUS_IO_TIMEOUT)

and I have no idea why. But I can ping 10.1.2.3 from any machine.

@Moebius1 : I installed Ubuntu desktop then the server stuff via tasksel to keep full desktop functionality.
```
net usershare info --long
```
returned a list of local network shares I tried but I delete them since.

Maybe this page ([https://tecadmin.net/mounting-samba-share-on-ubuntu/](https://tecadmin.net/mounting-samba-share-on-ubuntu/)) could be a simpler solution for mounted drives ... did not tried yet.

Your answers allowed me to reach this point and I thank you for that. As my share is not accessible from other computers in the VLAN, I wonder if you may help more.

---

### Post by MAFoElffen on 2021-07-04
No comment except: My respect to Morbius1 on this. I think it was around 11 years ago when he helped me on this, on a
 hardware network attached storage smb device. He has always lead me to a sound answer concerning network shares and Samba. My many thanks to him.

---

### Post by TheFu on 2021-07-04
> **MAFoElffen said:**
> No comment except: My respect to Morbius1 on this. I think it was around 11 years ago when he helped me on this, on a
 hardware network attached storage smb device. He has always lead me to a sound answer concerning network shares and Samba. My many thanks to him.

Agreed.  When it comes to the many, many, different oddities of Samba, Morbius1 is the best resource here. What for his response.

I don't think samba cares about userids or groups at all.  That is just so that from the Linux side of things, the owner and permissions can make sense, not for Samba's needs. It doesn't care.  That's my impression.

I've never used the point-n-click share methods, so cannot comment about that. Since around 1995, I've always modified the smb.conf.

---

### Post by Morbius1 on 2021-07-04
I really dislike overly convoluted samba HowTo's especially ones that in a few cases are factually incorrect.

It's going to take me a bit to try to reproduce this issue in it's entirety but what I have done so far is:

Recreated your original HowTo smb.conf on a test box - with minor changes:

> [global]
    disable netbios = Yes
    log file = /var/log/samba/smb.log
    max log size = 10000
    passdb backend = smbpasswd
    security = USER
    server role = standalone server
    server string = Ubuntu_server
    smb ports = 445
    workgroup = LAB.LAN
    idmap config * : backend = tbd


[Test]
    create mask = 0600
    directory mask = 0750
    force create mode = 0640
    force directory mode = 02770
    path = /mnt/Storage/Test
    read only = No
    valid users = @sambashare smbuser
And the permissions on /mnt/Stroage/Test is - tester is my main user:
> drwxrws--- 3 tester sambashare 4096 Jul  4 08:14 /mnt/Storage/Test

If I attempt to access the share as smbuser - Samba lets me in because smbuser has a samba password but Linux will not let him do anything:
> tester@vub1804:~$ smbclient //192.168.1.147/Test -U smbuser
Enter LAB.LAN\smbuser's password: 
Try "help" to get a list of possible commands.
smb: \> ls
NT_STATUS_ACCESS_DENIED listing \*

If however I edit the share definition and instead of a "force user" I add the "force group"
> [Test]
    create mask = 0600
    directory mask = 0750
    force create mode = 0640
    force directory mode = 02770
    [COLOR=#ff0000]**force group = sambashare**[/COLOR]
    path = /mnt/Storage/Test
    read only = No
    valid users = @sambashare smbuser
Things work out much better for the smbuser:
> tester@vub1804:~$ smbclient //192.168.1.147/Test -U smbuser
Enter LAB.LAN\smbuser's password: 
Try "help" to get a list of possible commands.
smb: \> ls
  .                                   D        0  Sun Jul  4 08:14:59 2021
  ..                                  D        0  Sun Jul  4 07:26:16 2021
  ABC                                 D        0  Sun Jul  4 08:25:54 2021


Please try this first to see how much if anything it fixes. I dread going trough all the group adds and permissions changes the original HowTo wanted me to do.

*[COLOR=#ff0000]Note[/COLOR]: "force group = sambashare" and "valid users = @sambashare ... " at first glance doesn't seem right since if everyone is forced to that group doesn't that allow all credentialed users access? They are happening at different times in the process. "valid users" happens at the "samba gatekeeper" stage where it determines who to let in. "force group" happens after the client user is allowed access.*

---

### Post by tryphon2 on 2021-07-04
Thank you Morbius1 for your time to try my Samba config. This is really appreciated.
"force group" is not yet working because I discovered that the RAID Storage volume is not accessible to multiple users even if it is set to sambashare group (chown command). I created ubuntu users in sambashare group. They may access to various resource folders set for example purpose but NOT for folders in my RAID volume.
I need to study the getfacl output on Storage volume :
group::---
where I expected rwx (ls shows rwx for the group sambashare).
I don't know yet how to correct that?

---

### Post by TheFu on 2021-07-04
chmod and chgrp are how groups and permissions are modified on the Unix side.

If you post the permissions, we could see them.

```

create mask = 0600
directory mask = 0750
force create mode = 0640
force directory mode = [COLOR="#FF0000"]0[/COLOR]2770
```
seem like they collide. Either members of the group have read or they don't.

If it was me, I'd use:
```

 create mask = 0640
 directory mask = 0750
```
I feel that using ACLs makes for overly complex, hidden, permissions. ACLs aren't easily seen using **ls -l**, whereas Unix permissions are.  If you want to screw with local users, use ACLs. I would clear the ACLs and only use Unix permissions so those  aren't overridden by ACLs.  In over 25 yrs, I've only needed ACLs twice.

Is the goal is for 
[LIST]
[*]one user to have modify (the owner), 
[*]the group members to have read and 
[*]all others to see nothing?
[/LIST]

I've always setup different shares based on the access needed per user as a way to simplify everything.  1 CIFS share for read-write users and another share for read-only users.

---

### Post by tryphon2 on 2021-07-04
Yes, I correct now the create mask.

I agree, I prefer to make it simple.

Ubuntu server is fresh install. I did not realised acl was activated as I did nothing for that. I put **noacl** for Storage volume in fstab and now the _Samba users have access to it_ without confusion.

I plan a quite simple share on Storage volume. One folder per lab in my organisation. Each person in a lab will connect to the lab folder with one account. Other lab, other common account.

Now the Samba server part is done and working : THANK YOU for your huge help.

On the client side (from Ubuntu 20.04), smbclient returns NT_STATUS_IO_TIMEOUT as if there is no communication between Samba server and the client. However ping and ssh to the server IP work fine. Also, in pfSense, there is the rule "Default allow LAN to any rule". If you have a hint ... otherwise, I will open a new threat.

Thank you again to all.

---

### Post by TheFu on 2021-07-04
I wouldn't disable the ACLs in the mount options. Modifying a default for something like that has risks I'd rather avoid.
I'd clear them and use normal POSIX chmod permissions, owner, group, methods.  Some services could expect ACLs to be there for specific files and we don't know because they just work and have always worked silently.

pfSense would be BSD.

---


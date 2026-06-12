---
title: "Samba Not Working with ACL"
date: 2018-06-26
forum: Server Platforms
---

### Post by ancientabysswalker on 2018-06-26
Hi All,

  I'm  trying to set up access control lists on my Ubuntu server box. It comes  with samba pre-installable and I'm trying to use ACL to afford myself  greater control of access than the standard Unix permissions.

  My samba shares already are accessible from both my Win10 and Mint  PCs with unix permissions, but when I switch over to ACL control only the 'owner' of the share  can actually access it (it might be even more restrictive and only be admin, I'll have to re-check). The share filesystem (ZFS) _does _support ACL and does have it  enabled. I have added the three-lines to the samba config and removed  anything from the share samba config except valid users.

  Does anyone have any suggestions for debugging or for steps I might have missed? Any help is appreciated as this is really starting to annoy me. I can't see anything from my searches that indicates I've missed a step...


getfacl output:
  > user::rwx group::r--
group:Scholar:r--
group:Archivist:rw-
mask::rw- other::---
default:user::rwx
default:group::r--
default:group:Scholar:r--
default:group:Archivist:rw-
default:mask::rw-
default:other::---

---

### Post by wildmanne39 on 2018-06-26
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by TheFu on 2018-06-26
I thought ZFS had their own CIFS implementation. Why use samba at all?

Do you have        **inherit acls = yes** in the samba config for that share? Perhaps if you post the output from **testparm**?
[https://wiki.samba.org/index.php/Setting_up_a_Share_Using_POSIX_ACLs](https://wiki.samba.org/index.php/Setting_up_a_Share_Using_POSIX_ACLs)

BTW, in 25 yrs as a Unix admin, I've needed ACLs 1 time.

And I doubt it is an issue, but userids and groupids should be all lowercase on Unix systems to prevent lazy programmers from being case-sensitive and having code not work.

As for troubleshooting, turn up the logging on the server-side and run a console CIFS client with verbosity set "high".

But really, I'd just use the ZFS CIFS implementation to keep things simpler.

---

### Post by volkswagner on 2018-06-26
You didn't include much info. 
You should post output of testparm along with the getfacl command showing if it's against a directory or not.

If I assume the listed getfacl command was ran against a directory, I think you are
missing the execute bit. I don't think a user can navigate the directory tree without the execute bit.

[This article]("http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm") has been my go to reference for file permissions.
Although it's written for active directory, most info should apply to standalone server.

---

### Post by ancientabysswalker on 2018-06-27
> **TheFu said:**
> I thought ZFS had their own CIFS implementation. Why use samba at all?

Do you have        **inherit acls = yes** in the samba config for that share? Perhaps if you post the output from **testparm**?
[https://wiki.samba.org/index.php/Setting_up_a_Share_Using_POSIX_ACLs](https://wiki.samba.org/index.php/Setting_up_a_Share_Using_POSIX_ACLs)

BTW, in 25 yrs as a Unix admin, I've needed ACLs 1 time.

And I doubt it is an issue, but userids and groupids should be all lowercase on Unix systems to prevent lazy programmers from being case-sensitive and having code not work.

As for troubleshooting, turn up the logging on the server-side and run a console CIFS client with verbosity set "high".

But really, I'd just use the ZFS CIFS implementation to keep things simpler.

Funny enough no, but i had **map acl inherit** = yes in [global]. This didn't fix my problem though.

Hmm, perhaps I'm going down the wrong path then? I DID get my samba shares to work just fine with standard permissions, though they couldn't do what I wanted. I want this specific share to have one group have write permissions and one group have read permissions. I originally had this set up under valid users = , but I was having trouble with having ALL added files with 666 permissions so that samba has full control over read/write. This is when someone told me to try ACL. Perhaps you know if there's another way or if there's a way to prevent the mask from setting lower permissions (write permissions always were getting capped).

All my UID are all case-sensitive and all my groups are first-letter capitalized. I don't believe this is the issue as I have done this simply by user instead of group as a test too.

As for why I'm using samba, it comes pre-installed on ubuntu server (version2 or 3 IIRC). Isn't CIFS an older deprecated samba 1 version? I used it on one of my previous servers...


TESTPARM:
# Global parameters
[global]
    dns proxy = No
    log file = /var/log/samba/log.%m
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    syslog = 0
    unix password sync = Yes
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[Astral Clocktower]
    path = /mnt/Hollow/Clocktower
    read only = No
    valid users = maria


[The Grand Archives]
    comment = "A Grand Repository of Ancient Knowledge"
    inherit acls = Yes
    path = /mnt/Hollow/GrandArchive
    valid users = abysswalker @Archivist maria @Scholar

---

### Post by TheFu on 2018-06-27
If I need 2 different groups to use samba with different access rights,  I setup 2 different share-names, pointing at the same storage. ACLs  are always a can of worms and disabling them as a hacker is trivial, so why bother?

And i wouldn't have spaces in share names or directories. I'm old. Learned NOT to do many things to avoid  dumb issues.

And don't get me started about mounted dirs under /mnt/ ... the file system hierarchy standard says how /mnt/ is to be used. This ain't it.

Not a big deal here, but posting text files should be inside "code tags" for better readability in  forums. Please.

---

### Post by Morbius1 on 2018-06-27
This doesn't happen very often but I'm with TheFu.
> I want this specific share to have one group have write permissions and one group have read permissions.
That is trickier than it sounds and it all depends on if you want this one group to be able to edit all the files added by other members of the group.

If they cannot: Create a "read only" share writeable to only one group:
```
[The Grand Archives]
path = /mnt/Hollow/GrandArchive
comment = "A Grand Repository of Ancient Knowledge"
read only = yes
valid users = abysswalker @Archivist maria @Scholar 
write list = @Archivist
```

If they can ... you know ,, there may be a way to do this in one share but it's giving me a headache so I would just create two shares:

One is read only:
```
[The Grand Archives RO]
path = /mnt/Hollow/GrandArchive
comment = "A Grand Repository of Ancient Knowledge"
read only = yes
valid users = abysswalker maria @Scholar 

```
And the other is for the @Archivest group:
```
[The Grand Archives RW]
path = /mnt/Hollow/GrandArchive
comment = "A Grand Repository of Ancient Knowledge"
force group = Archivest
writeable = yes
create mask = 0664
force directory mode = 2775
valid users = @Archivest

```
Just make sure to add the setgid bit to the shared folder:
```
sudo chmod 2775 /mnt/Hollow/GradArchive
```
And make sure the goup is Archivest:
```
sudo chown :Archivest /mnt/Hollow/GradArchive
```

[COLOR=#0000cd]**Note**: This will not work with Ubuntu Desktop 18.04 because Gnome + systemd = totally messed up default umask. Ubuntu Server 18.04 ( as well as Xubuntu 18.04 ) is fine since it has no Gnome.

And on a personal note: All of those spaces in the share names and upper cases in the group names is making that terrible facial tick I used to have come back.
[/COLOR]

---

### Post by volkswagner on 2018-06-27
I'm not sure if you saw my earlier post, but you need the execute bit to 
open a directory and read bit to "see" the directory (you can hide unreadable when 
enabling "access based enumeration" with 'hide unreadable = yes').

Again, I'm still not sure if your getfacl command is for the directory or not, but
I do know acls work perfectly on Ubuntu 14.04.


With the following:
Scholar group will only be able to see the folder exists, but they can't open
the directory to because lack of execute bit.
```
user::rwx group::r--
group:Scholar:r--
group:Archivist:rw-
```



The following only pertains to newly created files ie default setting, 
but neither of your listed groups can navigate into the directory.
```
default:user::rwx
default:group::r--
default:group:Scholar:r--
default:group:Archivist:rw-
default:mask::rw-
defaultther::---
```

You should try:

```
user::rwx group::r-x
group:Scholar:r-x
group:Archivist:rwx
```

Again, all the above assumes your command was run on the directory not a file.

---

### Post by ancientabysswalker on 2018-06-28
Ok. I'm pretty sure I've gone full circle here, but I have gone back to traditional linux permissions. I had them mostly working before and I have them doing what I originally wanted now. Compounding my confusion over the past while is the fact that one of my test laptops for this apparently plays roulette with whether or not it's going to obey reason when trying to access and modify the share. After switching completely to my desktop I'm getting more consistent results... I have the following:

 	 	```
[The Grand Archives]
path = /mnt/Hollow/GrandArchive
comment = "A Grand Repository of Ancient Knowledge"
create mask = 777
directory mask = 777
valid users = @Archivist @Scholar
write list = @Archivist
read list = @Scholar 

```

This works (yes I realize permit 777 is bad but I'm testing), but the issue has always been with this that the permissions ended up being rwxrw-r--, which meant that other 'admins' cannot delete files added by other admins (as files are saved with chown as user:user). This appears to be an unmasking feature (annoy) that I FINALLY found how to disable through /etc/login.defs

My question is then if modifying the umask will create significant security risks.

Now that I found how to modify umask (and since this likely poses a security flaw if set lower) I will probably move over to the suggestion of [**[COLOR=#000000]Morbius1[/COLOR]**]("https://ubuntuforums.org/member.php?u=982144"). I will probably end up mapping two shares to the same directory, wherein on is forced group admin and one is forced used; which allows writing as a constant group while not permitting the entire user base to have that group (my understanding is that force group doesn't force group to saved files only, but also logs you into that group as well).

Let me know if my logic is sound here as I want to make sure my handle on this is good for future, and tired-me sometimes comes up with very weird nonsensical ideas.

Thanks for all the help guys!

---

### Post by Morbius1 on 2018-06-28
> This works (yes I realize permit 777 is bad but I'm testing), but the  issue has always been with this that the permissions ended up being  rwxrw-r--, which meant that other 'admins' cannot delete files added by  other admins (as files are saved with chown as user:user).
That is the reason why I suggested the setgid bit in my post. The setgid bit when applied to the shared folder and in the share definition will force all new files to "inherit" the group of the parent. The files will not save as user:user but as user:Archivest. If your default umask is 002 and not 022 then every every new file will be read / writeable to that group.

---

### Post by TheFu on 2018-06-28
setgid .... chmod g+s file

---

### Post by volkswagner on 2018-06-28
Is this thing on?

LOL

Is anyone going to at least challenge, confirm or laugh at my statements?

:)

---

### Post by TheFu on 2018-06-28
> **volkswagner said:**
> Is this thing on?

LOL

Is anyone going to at least challenge, confirm or laugh at my statements?

:)

I've been waiting for the OP to answer the questions asked.  Plus, between you and Morbius1, I figured the knowledge shared about samba and ACLs was far beyond mine.

Yes, execute permissions are required to access files inside a directory for the owner or group or other permissions bits, based on the uid/gid of the process making the request.

---

### Post by ancientabysswalker on 2018-07-05
Sorry for not responding or thanking you all. It looks like some tinkering got it all to work; I think the setgid bit helped along with finding the location of the umask parameter to allow the group write permission.

[COLOR=#000000][FONT=Arial][The Grand Archives][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]comment = "For Filling the Halls of Advanced Knowledge"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]path = /mnt/Hollow/archive[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]writeable = yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]create mask = 0774[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]directory mask = 0775[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]valid users = @Archivist @Scholar

Cheers! :)
[/FONT][/COLOR]

---

### Post by TheFu on 2018-07-05
The best way to help the community is by marking this thread "solved" ... only the OP can do that.

---


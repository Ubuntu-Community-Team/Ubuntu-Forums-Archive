---
title: "Samba security help"
date: 2013-01-15
forum: Server Platforms
---

### Post by KillerKelvUK on 2013-01-15
New to Ubuntu Server, decided to do a little pet project at home to replace my QNAP NAS so am on a nice little learning curve and loving it.

One question I have is around samba security...so I have my samba share up and running, I can connect from my Win7 desktop and create, execute and delete files/folders etc.

I noticed though on the server itself that a folder created from the Windows client is done so with the ownership "root:kelvin" the later being by account name.  I was thinking this should be more like "kelvin:sambashare"?  Honestly I don't think this will cause me problems but as I'm doing this to learn I wondering if I could get advice on security best practice for samba and what I need to read up on to help me answer the question?  (Attempted to RTFM and went hazy after page 20!)

Was I wrong to expect the file and folder ownership's I was?  Any pointers welcome.

Thanks,

Kelvin

---

### Post by papibe on 2013-01-15
Hi KillerKelvUK.

Could you post the result of this command on the Samba server?
```
testparm
```
Regards.

---

### Post by KillerKelvUK on 2013-01-15
Hi papibe, here's the info...

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
Processing section "[web]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = SLEDGE
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:                    * %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        print ok = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[share]
        comment = BlackServer main file share
        path = /mnt/share/
        admin users = kelvin
        read only = No

[web]
        comment = BlackServer web file share
        path = /mnt/web/
        read only = No

```

---

### Post by papibe on 2013-01-15
Thanks.

The reason user kelvin is creating files as root is because of this setting:
```
admin users = kelvin
```

As for the problem with the Windows 7 machine:

[LIST]
[*]Is the Win7 machine set up as a member of the SLEDGE workgroup?

[*]Does the Win7's user exist as a user on the server as a user?

[*]Have you tried using this username format to connect to the shares?
```
SLEDGE\username
```
(this is what I use from my Win7 machine to be able to connect).
[/LIST]

Let us know how it goes.
Regards.

---

### Post by KillerKelvUK on 2013-01-15
> **papibe said:**
> 
As for the problem with the Windows 7 machine:

[LIST]
[*]Is the Win7 machine set up as a member of the SLEDGE workgroup?

[*]Does the Win7's user exist as a user on the server as a user?

[*]Have you tried using this username format to connect to the shares?
```
SLEDGE\username
```
(this is what I use from my Win7 machine to be able to connect).
[/LIST]

Let us know how it goes.
Regards.

Hi, I'll remove the admin users = syntax and re-test thank you.

Regards your list above, unless I have a problem I don't know about the Win7 machine is working fine, have I confused you or have you seen something else wrong?

I use SLEDGE as my internal workgroup just to tidy up where machines are reported by the network browser (most of my clients are win boxes).  I don't have a DNS server present as yet and so to authentic a windows client against the samba user account I use "IP Address of samba server\username".  This works fine for me although I aim going to attempt internal DNS serving once I've read up on this some more.

---

### Post by KillerKelvUK on 2013-01-16
Okay so I removed the "admin users =" line in my smb.conf, restarted the services and now a directory created from the mapped samba share in windows results in an ownership of 'kelvin:kelvin'...kelvin being me and thus my user account.  How do I default any directories to have the group sambashare so I can allow other users access?

In addition the default file permissions are 755, how can I default these to 770?

Cheers,

K

---

### Post by bab1 on 2013-01-16
> **KillerKelvUK said:**
> ... How do I default any directories to have the group sambashare so I can allow other users access?

In addition the default file permissions are 755, how can I default these to 770?

Cheers,

K
To make the group permissions on a directory inherited (i.e. you want them to be the group *sambashare*), yon need to set the gid bit (sgid) on the root directory of the part of you want this to occur.  

For instance, all my Samba shares are at /smb (i.e. /smb/public or /smb/movies etc).  Then I set the *smb* directory group ownership to sambashare and set the permissions to 2775.  The leading 2 sets the gid bit (see [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") for info).

At this point any data created in the subdirectories will inherit the group ID of samba share.  One caveat is: Ununtu does not standardize the gid for the groups created.  This means that groups created on remote machines may not match the servers gid for sambashare.  I create my own groups with ID numbers well away from the normal user or application groups.There are several ways to set what is essentially a custom *umask*.  Most of what I have is globally set in /etc/profile.  I set mine at 0002 which results in directories created with 0775 permissions (the inheritance is taken care of by the root of the share sgid).  The files created have permissions of 0664.

I also set the create directory and file permissions with ```
create mask = 0664 # for files

directory mask = 0755 # for directories
```

I believe you can also set the umask when mounting shares from the command line of fstab with mount.cifs (mount -t cifs)

What you end up with is a file system (the shares) that inherits the group ID and has the permissions you dictate.  I use this scheme to manage the share access via the group, not the owner (e.g. If the user is in the group they have access).  As always it's good practice to ***not*** have shares under an existing share.

---

### Post by KillerKelvUK on 2013-01-17
Thanks bab1 :-)  Its working as I'd like now, busy reading up more on file permissions.

---


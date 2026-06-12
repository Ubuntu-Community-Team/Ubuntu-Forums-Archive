---
title: "Ubuntu Fileserver problem"
date: 2009-09-18
forum: Server Platforms
---

### Post by sushiguru on 2009-09-18
Hi all,

I'm setting up an older PC I've fallen heir to as a fileserver and am running into a wee problem.

Server setup was fine, with only two components - SSH and Samba.

Server is running fine, and I can successfully log on using putty and administer it remotely.

I have a USB HDD mounting successfully on every boot, and it is shared.

I can create the mapped drive and browse the folder contents fine.

When I reboot the laptop I'm working on, or reboot the server, the laptop (running XP) gives me the 'An error occurred reconnecting to...' and I can't get to the share.  If I disconnect the mapped drive I can re-map it.

Does anyone have any clues why this is happening?  I've spent hours on forums tonight and can't seem to get this wrapped up.

I'm pretty much an Ubuntu n00b.

Cheers,
Gary.

---

### Post by swerdna on 2009-09-18
PLease show us your Samba configuration file, smb.conf, it's located at /etc/samba/smb.conf

---

### Post by ugm6hr on 2009-09-19
Couple of questions / points:

1. Why are you using a USB HD on a file server (which presumably has internal HD adapters)?

2. It is worth considering FreeNAS as an alternative for simplicity.

3. What format is the HD in (i.e. ext3, vfat, ntfs)?

---

### Post by sushiguru on 2009-09-20
> **ugm6hr said:**
> Couple of questions / points:

1. Why are you using a USB HD on a file server (which presumably has internal HD adapters)?

2. It is worth considering FreeNAS as an alternative for simplicity.

3. What format is the HD in (i.e. ext3, vfat, ntfs)?

1 - PC case is a micro tower. No space for extra hdd. Also, USB drive was being used by of and a Mac.

2 - Will look into it...

3 - HDD is ntfs. 

Will post smb.conf when I get a chance. Painting the kitchen just now :|

---

### Post by sushiguru on 2009-09-20
smb.conf:

> [global]
   workgroup = TIS
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[DOCUMENTS]
comment = Public Folder
path = /media/store
browseable = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = gary
force group = gary
available = yes
guest ok = yes

All comments and commented out lines have been deleted, but this was just a modified version of the default smb.conf so they are there and can be un-commented if required.

Cheers.

---

### Post by scorp123 on 2009-09-20
> **sushiguru said:**
> 2 - HDD is ntfs. Why not a Linux-native file system? Accessing Micro$oft NTFS via those various workarounds and compatibility layers that exist (e.g. ntfs-3g, fuse, and what not) is going to be rather slow.

---

### Post by sushiguru on 2009-09-20
> **scorp123 said:**
> Why not a Linux-native file system? Accessing Micro$oft NTFS via those various workarounds and compatibility layers that exist (e.g. ntfs-3g, fuse, and what not) is going to be rather slow.

The HDD has been in use on the XP machine for the last year.  If there's a way to change the file format of the drive without losing data then I'm open to that possibility.  I have 100s of GB of data with no option for temp backup or storage, so a change of format would have to be done with data in-situ.

Cheers,
Gary.

---

### Post by sushiguru on 2009-09-21
OK - so the thick plottens.  The fileserver is always found and available from my household PC (wired ethernet to switch) but the problem persists with the laptop, so I'm guessing this is a problem with the laptop->server networking as opposed to the Samba setup, which seems to be working fine.

The PC and Ubuntu boxes both have static IPs, whereas the laptop's is assigned by DHCP on a wireless AP. [edit] I've also tried the laptop with a static IP and no joy.[/edit]

Any networking experts out there?

Gary.

---

### Post by openfly on 2009-09-21
Just like to remark that your disk should PROBABLY be backed up.  This seems like a perfect opportunity to make that happen.  You know, before it fails.

---

### Post by cteneyck on 2009-09-21
how are you mapping the drive in windows?

a:  \\servername\share
b:  \\ipaddress\share

if you are using A and don't have a dns or wins server, then you will have to wait till your network determines a master browser, and your computers figure out who is who after the reboot.

---

### Post by sushiguru on 2009-09-21
> **cteneyck said:**
> how are you mapping the drive in windows?

a:  \\servername\share
b:  \\ipaddress\share

if you are using A and don't have a dns or wins server, then you will have to wait till your network determines a master browser, and your computers figure out who is who after the reboot.

Actually came back to post that I changed the mapping on the laptop to (b) above, and it found the server after the laptop rebooted.  Still not sure why (a) works on the PC though.

G.

---

### Post by swerdna on 2009-09-21
There may (or may not) be an inconsistency between the Samba setup and the way Linux treats mounted NTFS filesystems.

The Samba setup is this:
```
[DOCUMENTS]
comment = Public Folder
path = /media/store
browseable = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = gary
force group = gary
available = yes
guest ok = yes
```
When a windows user attaches, presumably as "guest", she will auto take on the persona of gary. That's only fine if Gary has read-write access to the mount in a Linux context; i.e. physically log onto the server as gary and check that gary can access and read-write the NTFS drive.

Another thing to check: create masks and directory masks cannot force permissions for new files and folders on an NTFS drive because an NTFS drive is constrained by the Linux operating system to stick strictly with the permissions and ownership mask that it gets at mount time. [Reference here]("http://ubuntu.swerdna.org/ubuntfs.html")

So the share should have the 0777 line removed for consistency.

But all of this might be detail rather than the actual problem. So check it out and see.

---


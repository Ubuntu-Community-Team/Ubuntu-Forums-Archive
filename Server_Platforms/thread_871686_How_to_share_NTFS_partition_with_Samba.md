---
title: "How to share NTFS partition with Samba?"
date: 2008-07-27
forum: Server Platforms
---

### Post by kirandulo on 2008-07-27
I would like to share a folder on an NTFS partition. I would like to configure an anonymous file server (without authentication prompt for windows clients).

smb.conf:
```
[global]
    workgroup = WORKGROUP
    security = share
    guest account = nobody
[mp3]
    comment = music
    path = /media/sda2/mp3
    browsable = yes
    read only = yes
    guest ok = yes
    guest only = yes

```
fstab:
```
# /dev/sda2
UUID=xxxx /media/sda2  ntfs  defaults,umask=007,gid=46  0  1
```
gid=46 group name is 'plugdev' (nobody is not member)
what is user 'sambashare' used for in hardy?

I also cannot share an NTFS folder through Gnome GUI (Nautilus). Error message thrown: "Cannot grant access rights for this folder." I suspect the problem is around 'umask' of /dev/sda2. Have you ever faced a similar situation? Any idea?

---

### Post by yeaitsdark on 2008-07-27
I would just mount as:
/dev/sda2     /media/sda2/mp3    ntfs     defaults,rw 0 0

And in samba check out this link:
[http://www.webmasterworld.com/forum40/349.htm](http://www.webmasterworld.com/forum40/349.htm)

Check also:
[http://ubuntuforums.org/archive/index.php/t-490168.html](http://ubuntuforums.org/archive/index.php/t-490168.html)

Also, sometimes the individual file permissions can get in the way.

You can change them via chmod.
cd /media/sda2/mp3
sudo chmod -R 0755 * 
(R/W Owner R Group R Others)

Check those links. Hope all goes well.

---

### Post by herdivet on 2008-07-30
If I unmount the volumes, then issue the mount command and set up the shares, everything works just like advertised.  This is great, but what happens after a reboot?  When I edit fstab, I don't own the volumes, and cannot set permissions through Nautilus to share them.  

This was working fine about a week ago, now it only shares files on the Linux volumes without all this.  Frustrating...

---

### Post by Antonio Tavares on 2009-10-27
I am able to share the same ntfs partition from Windows and Linux with the same share, transparent to the network user.

I'm using an ntfs partition, because sometimes I still need to reboot in Windows XP to test a corporate application. I could use an ext2 filesystem mount on Windows, but it would cost me more work...

This partition is defined in /etc/fstab like this:
```
# Particao Windows NTFS estava em /dev/sda1
UUID=F2F83FDFF83FA0B1 /windows ntfs uid=1000,gid=1004,nls=iso8859-1,users,umask=000,noatime,nodiratime 0 0
```

User 1000 is (normally) the main user on Ubuntu Linux. On my case user with id 1004 with name"sambadmins" group I set up so a couple of users can access to private folders. With this setup, the Windows partition gets mounted with main user as owner, "sambadmin" group and (just for testing) everyone is accessing (umask=000)

I've added nobody to samba users so guest is allowed:
```
sudo smbpasswd -n nobody
sudo smbpasswd -e nobody
```

My /etc/samba/smb.conf is like this:

```
[global] 
        workgroup = MYWORKGROUP
        server string = 
;        interfaces = eth0 
        bind interfaces only = No 
        security = SERVER 
        map to guest = bad user
	null passwords = yes
        obey pam restrictions = Yes 
        passdb backend = tdbsam 
        pam password change = Yes 
        passwd program = /usr/bin/passwd %u 
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword$ 
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

[print$] 
        comment = Printer Drivers 
        path = /var/lib/samba/printers 
[public] 
        comment = Every soul can read and change 
        path = /windows/i/publico 
        force group = tota 
        read only = No 
        create mask = 0777 
        force create mode = 0777 
        guest ok = Yes
	browseable = Yes
	public= yes
	writable = Yes
[browsable] 
        comment = Common share: sambadmins group can change, others read only 
        path = /windows/i 
        force group = tota
        read only = Yes
	write list = +sambadmins 
        create mask = 0774 
        force create mode = 0774 
        guest ok = Yes
	browseable = Yes

```

To know more sharing options the following article is a good start:
[http://www.devshed.com/c/a/Administration/Authorizing-Users-in-Samba/3/]("http://To know more sharing options the following article is a good start: http://www.devshed.com/c/a/Administration/Authorizing-Users-in-Samba/3/")

I hope it helps someone, as I took about 3 hours to get this working.

Good luck!

---

### Post by Vegan on 2009-10-27
I found using NTFS on Linux troublesome. So I use ext3 for now, and let SAMBA take on the task of naming etc.

I have a second disk on the IBM which is use for backups, storage and the like. Its a kludge file server.

---

### Post by Antonio Tavares on 2009-10-27
> **Vegan said:**
> I found using NTFS on Linux troublesome. So I use ext3 for now, and let SAMBA take on the task of naming etc.
It's the best solution for internal disks, but for external disks that you may also format to ext3, afterwards you cannot read their contents on other operating systems. So, for sharing disks you're stuck with NTFS or FAT.

---

### Post by capscrew on 2009-10-27
> **Antonio Tavares said:**
> It's the best solution for internal disks, but for external disks that you may also format to ext3, afterwards you cannot read their contents on other operating systems. So, for sharing disks you're stuck with NTFS or FAT.


By *other operating systems*, you mean Windows, take a look at [**_http://www.fs-driver.org/index.html_**]("http://www.fs-driver.org/index.html").

This allows Windows systems to recognize ext3/4 formating.

---


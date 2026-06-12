---
title: "username map setting stops Samba from showing in workgroup?"
date: 2014-05-22
forum: Server Platforms
---

### Post by James_Connors on 2014-05-22
Hello all! This is my first post here, so if I'm in the wrong area, I apologize ahead of time... lol

I've been messing with my Samba version 3.6.23 server for 3 nights now with no avail. The issue?
It's  not showing up in my Windows (Windows 7, if it matters) workgroup  (default name WORKGROUP) on any of our computers, yet I can access it  via its IP address and also by its name (MEDIA-SERVER). At first I  thought it may have been a DNS issue, but accessing it by name makes me  believe that's not the case, and I've kinda narrowed it down to this...

I'm  using "passdb backend = tdbsam", and also the "username map" setting to  map Windows users to system users. With how I have it setup right now,  everything works as intended, minus showing up in my workgroup. However,  if I comment out the "username map" setting, it then shows up in my  workgroup just fine yet asks for a user/pass combo when trying to access  any shares that require authentication, and tells me any public shares  aren't accessible, which doesn't work. If I uncomment it, it once again  is gone from my workgroup, yet I can still access it via its IP and  name.

I've tried for hours trying to fix this and don't have too  much Samba experience under my belt, but I've dabbled with it a bit.  Here are my current config files:

smb.conf:
```

[global]
        log level = all:3
        syslog = 0
        netbios name = MEDIA-SERVER
        server string = Samba Media Server
        interfaces = 192.168.1.1/24 127.0.0.1/24
        bind interfaces only = Yes
        workgroup = WORKGROUP
        log file = /opt/var/log/samba/%m.log
        max log size = 1000
        map to guest = Bad User
        guest account = media-guest
        invalid users = root, reboot
        username map = /opt/etc/samba/smbusers
        username map cache time = 60
        passdb backend = tdbsam:/opt/etc/samba/passdb.tdb
        cache directory = /opt/etc/samba/locks/cache
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
        name resolve order = lmhosts wins host bcast
        load printers = Yes
        printing = cups
        printcap name = /opt/etc/samba/locks/printcap
        hide special files = Yes
        hide unreadable = Yes
        dos charset = ASCII
        oplocks = Yes
        obey pam restrictions = Yes
        usershare allow guests = Yes
        encrypt passwords = True
        read raw = Yes
        write raw = Yes
        use sendfile = Yes
        deadtime = 15
        min receivefile size = 16384
        max xmit = 65536
        aio read size = 16384
        aio write size = 16384
        aio write behind = No

        # Domain/Local Master Settings
        local master = Yes
        domain master = Yes
        preferred master = Yes
        wins support = Yes
        dns proxy = Yes
        os level = 255

[Movies]
        comment = Movies folder.
        path = /mnt/movies
        write list = james
        create mask = 0770
        directory mask = 0770
        guest ok = Yes

[TV Shows]
        comment = TV Shows folder.
        path = /mnt/tv-shows
        write list = james
        create mask = 0770
        directory mask = 0770
        guest ok = Yes

[Music]
        comment = Music library.
        path = /mnt/music
        write list = james, mommy
        create mask = 0770
        directory mask = 0770
        guest ok = Yes

[Shared Storage]
        comment = Global shared storage space.
        path = /mnt/storage/global
        valid users = james, mommy
        write list = james, mommy
        read only = No
        create mask = 0770
        directory mask = 0770
        hosts allow = 192.168.1.0/24, 127.0.0.1
        browseable = No

[Personal Storage]
        comment = Your personal user storage space.
        path = /mnt/storage/%u
        valid users = james, mommy
        write list = james, mommy
        read only = No
        create mask = 0700
        directory mask = 0700
        browseable = No

# Must remain last define, as to override any settings with
# the per-user settings defined in smb.conf.<user> files.
[Include]
        available = No
        include = /opt/etc/samba/per-user-config/smb.conf.%U

```

Feel free to laugh at the usernames, haha.
And here is my smbusers file:

```

!james = Chewy
!mommy = DCGibs
media-guest = *

```

I  had it working for quite some time before this just fine, but after doing some "fine  tuning", I guess I tuned something wrong (transfer speeds are faster though!  Lol). smbtree also shows the workgroup as I wish it to be, including the Media Server and our computers...

In short:
If I set the "username map" setting, it works  as I wish it to yet doesn't appear in the workgroup as I also wish it  to. If I remove that setting, it appears in the workgroup yet I can't  access anything. I can only see it there.

Any help/fixes/ideas to  why it's doing this would be awesome! I've been pulling my hair out for  a few nights now over this, so anything is better than nothing!
Thanks :)

---

### Post by dannyboy79 on 2014-05-23
it may have something to do with your bad user mapping and your username map of media-guest. do me favor and remove the media-guest from your username map file and restart the samba server. before testing anything, always wait at least 5 to 10 minutes with samba. have you entered both users james and mommy into smbpasswd? also, why do you have an exclamiation point in front of their username in your map file?

---

### Post by James_Connors on 2014-05-23
Because ! makes it stop reading the file after it finds a correct match, and the mapping of media-guest makes it so that anyone that doesn't match any other users is mapped to media-guest. Without ! in front, it will keep reading the file and thus, everyone is mapped to media-guest. And without the mapping of media-guest, it asks guests for a password as guests aren't mapped to anyone and don't get permissions. Also, smbpasswd? I'm using the tdbsam backend, and all users have been added to the password database with pdbedit and show up when pbdedit -L is used. I'm aware of the timeframe, though if I remove the mapfile line, it does show up immediately, but I do give it time (days technically, as it's not showing. I'm sure it would have by now if that was the case).

I'm kinda confused here. If I'm not using the smbpasswd backend, why would I need this? And as I had said, it had been working for awhile with these settings for awhile, we got mapped to our users while guests got mapped to media-guest.
But alas, I'll give your suggestion a try, but isn't smbpasswd not needed if I'm using tdbsam? I believe those are two completely different backends, and thus wouldn't need to be used together, no? I don't even have an smbpasswd file, just a passdb.tdb and users.map (I changed the name from when I posted that config), and it works if I remove the mapping setting.

EDIT: But alas, you are correct. Removing media-guest did fix the problem it seems. Thank you for the help, such a simple fix! Doh!
EDIT2: But there again, now guests aren't mapped nor allowed to access the folders. But the server does show in the workgroup. They're asked for a password, but because of map to guest, if the just hit okay it lets them. I'd prefer not having it ask for a password, however. But I suppose I'll start googling about that. :)

Resolved. guest ok and changing a few permssion settings and we're good. Thank you for your help! :)

---

### Post by dannyboy79 on 2014-05-24
you're right, you don't need to add them to smbpasswd cause you're using tdbsam.

glad you got it sorted out. if you wouldn't mind mark the "thread as solved" using the thread tools

---

### Post by James_Connors on 2014-05-24
Already done, thanks again for your help :)

---


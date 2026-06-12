---
title: "strange samba permissions question."
date: 2013-10-09
forum: Server Platforms
---

### Post by fallere on 2013-10-09
I have a test server with an slightly annoying problem. I have 6 samba shares, 5 users and one of the shares is not working right.

```
[global]
    log file = /var/log/samba/log.%m
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    obey pam restrictions = yes
    map to guest = bad user
    encrypt passwords = true
    passwd program = /usr/bin/passwd %u
    passdb backend = tdbsam
    dns proxy = no
    netbios name = city fake
    server string = %h server (Samba, Ubuntu)
    unix password sync = yes
    os level = 20
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    usershare allow guests = yes
    max log size = 1000
    pam password change = yes


[Candeloro]
        comment = Miyako
        writeable = yes
        valid users = @Candeloro
        create mode = 770
        path = /home/Candeloro
        directory mode = 770
 
[Ophelia]
        comment = Kafuka
        writeable = yes
        valid users = @Ophelia
        create mode = 770
        path = /home/Ophelia
        directory mode = 770
 
[Kyubey]
        comment = Maayoi
        writeable = yes
        valid users = @Kyubey
        create mode = 770
        path = /home/Kyubey
        directory mode = 770
 
[Oktavia]
        comment = Karen
        writeable = yes
        valid users = @Oktavia
        create mode = 770
        path = /home/Oktavia
        directory mode = 770
 
[Homulilly]
        comment = Hitagi
        valid users = @Homulilly
        writeable = yes
        create mode = 770
        path = /home/Homulilly
        directory mode = 770


[Kriemhild]
    writeable = yes
    path = /home/Kriemhild
    force group = Kriemhild
    valid users = @Kriemhild
    create mode = 770
    directory mode = 770
    directory mask = 0777
    create mask = 0777
```

```

drwxr-xr-x 24 Kyouko    Kyouko    4096 Oct  9 09:19 Kyouko
drwxr-xr-x 23 Homura    Homura    4096 Oct  3 09:16 Homura
drwxrws---  2 root      Kyubey    4096 Oct  3 11:44 Kyubey
drwxrws---  2 root      Oktavia   4096 Oct  3 09:56 Oktavia
drwxrws---  4 root      Candeloro 4096 Oct  3 09:04 Candeloro
drwxrws---  2 root      Ophelia   4096 Oct  3 11:43 Ophelia
drwxrwx---  3 root      Kriemhild 4096 Oct  9 09:22 Kriemhild
drwxr-xr-x 21 Sayaka    Sayaka    4096 Oct  3 08:35 Sayaka
drwxrws---  3 root      Homulilly 4096 Oct  3 09:13 Homulilly
drwxr-xr-x 23 Madoka    Madoka    4096 Oct  3 09:24 Madoka
drwxr-xr-x 28 Mami      Mami      4096 Oct  9 09:19 Mami
```

My 5 users are all in [Kriemhild] group, they can all write to the share, but if Madoka makes a file locally it is in [Madoka] group and not [Kriemhild] group. I can mount the share on a windows machine, login as madoka and make a file that is part of the [Kriemhild] group. All of the other groups/shares are working as they should, remote and local files able to be edited by all who need. I ran```
sudo chmod g+s [share]
``` to get them working. I am hoping there is a way that I can make the share work how I need it to without running extra commands.

---

### Post by volkswagner on 2013-10-13
When writing to the file system locally, it does not obey settings in smb.conf.  You will need to either mount the shares locally using smbclient, or continue
with your additional commands to get the sticky bit set.

---


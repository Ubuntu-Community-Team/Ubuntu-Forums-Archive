---
title: "Browse Nautilus sftp:// mount through terminal"
date: 2010-05-06
forum: Server Platforms
---

### Post by dragos2 on 2010-05-06
I am having an important problem on a  Ubuntu server 8.04 64 bits (with xorg-core, gnome-core, gdm, applied for remote users to work).

I mounted a remote samba (running on another Ubuntu server 8.04) through "Connect to server -> SSH -> etc" and it appears as bookmark in Nautilus.

I can browse that mount through nautilus and it looks like a sftp:// mount since it says
"sftp on samba server" but I can't locate it on the disk! I can't browse it through terminal
since I can't find it.

Also while the nautilus windows is opened with the remote mount this is the content of gvfs:
```

$ ls -al ~/.gvfs
total 8
drwx------  2 user user 4096 2009-07-14 14:30 .
drwxr-x--- 36 user user 4096 2010-05-06 14:07 ..

```

Do I miss something ? What else can I do ? 

This is very important for me and this system to work properly.

---

### Post by ghost_ryder35 on 2010-05-06
> **dragos2 said:**
> I am having an important problem on a  Ubuntu server 8.04 64 bits (with xorg-core, gnome-core, gdm, applied for remote users to work).

I mounted a remote samba (running on another Ubuntu server 8.04) through "Connect to server -> SSH -> etc" and it appears as bookmark in Nautilus.

I can browse that mount through nautilus and it looks like a sftp:// mount since it says
"sftp on samba server" but I can't locate it on the disk! I can't browse it through terminal
since I can't find it.

Also while the nautilus windows is opened with the remote mount this is the content of gvfs:
```

$ ls -al ~/.gvfs
total 8
drwx------  2 user user 4096 2009-07-14 14:30 .
drwxr-x--- 36 user user 4096 2010-05-06 14:07 ..

```

Do I miss something ? What else can I do ? 

This is very important for me and this system to work properly.
you need to make sure the samba server is setup correctly.  then you should be able to do the following.

On samba server
```

foo@sambaserver:~$ less /etc/samba/smb.conf

```
look for 'public'.  You will see something like
```

[public]
        comment = Public Share
        path = /path/to/share/point
        read only = no
        guest only = yes
        guest ok = yes

```
If the above is configured correctly you should be able to do the following.
```

foo@sambaclient:~$  smbclient -L //sambaserver -U foo
foo@sambaclient:~$  smbclient //sambaserver/share_you_want_from_list -U foo
smb: \> help

```

---

### Post by dragos2 on 2010-05-06
> **ghost_ryder35 said:**
> you need to make sure the samba server is setup correctly.  then you should be able to do the following.

On samba server
```

foo@sambaserver:~$ less /etc/samba/smb.conf

```look for 'public'.  You will see something like
```

[public]
        comment = Public Share
        path = /path/to/share/point
        read only = no
        guest only = yes
        guest ok = yes

```If the above is configured correctly you should be able to do the following.
```

foo@sambaclient:~$  smbclient -L //sambaserver -U foo
foo@sambaclient:~$  smbclient //sambaserver/share_you_want_from_list -U foo
smb: \> help

```

I don't think you understood. I can browse samba with no problems either through ssh,
mount.cifs or smbclient. I only want to be able to see where is the nautilus sftp:// mount on the local system.

I have the gnome-open-terminal-here extension installed but when I right click a folder from nautilus on the remote samba it asks for the password but this does not helps me since I want the remote folder mounted locally to be able to pass the files from there as arguments to local programs.

---

### Post by ghost_ryder35 on 2010-05-06
> **dragos2 said:**
> I don't think you understood. I can browse samba with no problems either through ssh,
mount.cifs or smbclient. I only want to be able to see where is the nautilus sftp:// mount on the local system.

I have the gnome-open-terminal-here extension installed but when I right click a folder from nautilus on the remote samba it asks for the password but this does not helps me since I want the remote folder mounted locally to be able to pass the files from there as arguments to local programs.

local system is client or server?

---

### Post by dragos2 on 2010-05-06
> **ghost_ryder35 said:**
> local system is client or server?

Does not helps because I don't know how to mount the remote share with a user and multiple groups (the uids and gids are not the same across the systems). The gvfs from Gnome seems to be able to resolve to the remote groups correctly but it seems that on the newer Gnome the gvfs does not exist on disk anymore - just read that which means a dead end for me with this approach and forces me to synchronized uids and gids and use NFS..

I am pretty pissed right now.

Local system is client.

---

### Post by twisted_steel on 2010-05-06
From what I read, you are trying to connect to your samba server via SSH (SFTP) and mount it in Nautilus.  However, it is not showing up in ~/.gvfs/ despite it actually mounting properly.  This does work for me in 10.04, though there is definitely a possibility that it is an issue with 8.04.  I know several years ago they did a rewrite of gvfs and screwed up some things for a time.

Have you looked into SSHFS?  It allows you to automount the remote location using your fstab and also manually via command-line.  It's not as pretty as using the GUI, but it should at least get you up and running.

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by dragos2 on 2010-05-07
> **twisted_steel said:**
> From what I read, you are trying to connect to your samba server via SSH (SFTP) and mount it in Nautilus.  However, it is not showing up in ~/.gvfs/ despite it actually mounting properly.  This does work for me in 10.04, though there is definitely a possibility that it is an issue with 8.04.  I know several years ago they did a rewrite of gvfs and screwed up some things for a time.

Have you looked into SSHFS?  It allows you to automount the remote location using your fstab and also manually via command-line.  It's not as pretty as using the GUI, but it should at least get you up and running.

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

SSHFS does not work with ACL. 

Have any idea of how to fix that gvfs under 8.04 ? Or whom to talk to? I really want to avoid nfs.

---

### Post by cahalsall on 2011-11-20
You question was never answered here. Did you ever find a solution to this?

Regards

---

### Post by bab1 on 2011-11-20
> **cahalsall said:**
> You question was never answered here. Did you ever find a solution to this?

Regards

What solution are you looking for?  The above (year old) discussion is about something that can't be done.  The protocol SMB (CIFS) is not SSH (sFTP).

---


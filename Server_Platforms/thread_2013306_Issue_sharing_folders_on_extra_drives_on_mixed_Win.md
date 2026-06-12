---
title: "Issue sharing folders on extra drives on mixed Windows / Linux network"
date: 2012-06-30
forum: Server Platforms
---

### Post by Wolfpup on 2012-06-30
Hello,
I'm using Ubuntu 10.04 Deskop as a mixed Web/Torrent/Fileserver and I i have recently added a 1TB HDD to the system but I'm having an issue fully sharing a folder on the new drive with ALL my devices on my network.

Copy of my current smb.conf file:
```

[global]
    ; General server settings
    netbios name = YOUR_HOSTNAME
    server string = 
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
        security = user
        null passwords = true
        username map = /etc/samba/smbusers
        name resolve order = hosts wins bcast

    wins support = yes

;    printing = cups
    printcap name = CUPS

;    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
;    browseable = yes
    guest ok = yes
;    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[Public]
    path = /home/wolfpup/Public
    browseable = yes
    read only = no
    guest only = yes
        guest ok = yes
    create mask = 0644
;    directory mask = 0755

[Torrents]
    path = /media/sdb/torrents
    browseable = yes
    read only = no
    guest only = yes
        guest ok = yes
    create mask = 0644
;    directory mask = 0755

[Web Site]
    path = /home/wolfpup/www
    browseable = yes
    read only = no
    guest only = yes
        guest ok = yes
    create mask = 0644
;    directory mask = 0755


```

With the above setting i can access the Torrents share from my Windows 7 but NOT from my Ubuntu Laptop or from my WD TV Live Plus media player. now if i change the setting to where it is accessible form them then i lose access on my Windows system. Now the folder is seen on my Ubuntu laptop but when i try to access it i get a failure to mount notice.

---

### Post by Morbius1 on 2012-06-30
What's curious about your smb.conf file is that all your shares allow guest access but you have no way of converting a Windows user to a guest because you have a line missing in the [COLOR=Blue][global][/COLOR] section:
```
map to guest = Bad User
```The Windows user automatically passes his user name and local login password when it tries to access a share even though the Samba server isn't asking for one for a guest share. The way you have it the system defaults to:
> map to guest = NeverSo true guest access by a windows user that you have not set up explicitly in the Samba server with a samba password should never have gained access. With "Bad User" Samba will see if the Windows user exists and if has a samba password. If it can't find one the Windows user will be mapped to the guest account and access will be allowed to a guest share.

Anywho, what are the permissions of the target folder:
```
ls -al /media/sdb
```And is this by any chance a mount point of an NTFS partition?

---

### Post by Wolfpup on 2012-07-01
> **Morbius1 said:**
> What's curious about your smb.conf file is that all your shares allow guest access but you have no way of converting a Windows user to a guest because you have a line missing in the [COLOR=Blue][global][/COLOR] section:
```
map to guest = Bad User
```The Windows user automatically passes his user name and local login password when it tries to access a share even though the Samba server isn't asking for one for a guest share. The way you have it the system defaults to:
So true guest access by a windows user that you have not set up explicitly in the Samba server with a samba password should never have gained access. With "Bad User" Samba will see if the Windows user exists and if has a samba password. If it can't find one the Windows user will be mapped to the guest account and access will be allowed to a guest share.
Actually I WANT ALL systems on my network to have FULL guest access to the indicated folders INCLUDING the Torrents folder. My Windows 7 system can access the folders just fine(because i had to use my servers username and pwd) but my issue is my Linux based systems(WD TV Live Plus and Laptop loaded with Ubuntu) CAN NOT access the Torrents folder.
> Anywho, what are the permissions of the target folder:
```
ls -al /media/sdb
```Here is the output:
```

wolfpup@wolfpup-desktop:~$ ls -al /media/sdb
total 28
drwx------ 4 wolfpup wolfpup  4096 2012-06-28 14:34 .
drwxr-xr-x 4 root    root     4096 2012-06-28 15:55 ..
drwx------ 2 root    root    16384 2012-06-28 14:25 lost+found
drwxrwxrwx 3 wolfpup wolfpup  4096 2012-06-28 16:52 torrents
wolfpup@wolfpup-desktop:~$

```> And is this by any chance a mount point of an NTFS partition?No it is not an NTFS it is actually EXT 3(version1.0)

---

### Post by Morbius1 on 2012-07-01
The good news is that /media/sdb/torrents has the correct Linux permissions for what you wish to achieve:
> drwxrwxrwx 3 wolfpup wolfpup  4096 2012-06-28 16:52 torrentsAnd /media has the correct permissions:
> drwxr-xr-x 4 root    root     4096 2012-06-28 15:55 ..Unfortuanltly /media/sdb does not since only wolfpup can traverse the folder:
> drwx------ 4 wolfpup wolfpup  4096 2012-06-28 14:34 .So you have 2 choices:

Change permissions to allow "others" ( i.e., guests ) to gain access:
```
sudo chmod 0755 /media/sdb
```OR modify your share definition to convert all guests to wolfpup:
> [Torrents]
    path = /media/sdb/torrents
    browseable = yes
    read only = no
    guest ok = yes
[COLOR=Blue]**    force user = wolfpup**[/COLOR]Then restart samba:
```
sudo service smbd restart
```*And if you ever plan to add another Windows box to your network you might consider adding "map to guest = Bad User" to the [global] section so you don't have to set up users and samba passwords for guest access by Windows clients.*

---


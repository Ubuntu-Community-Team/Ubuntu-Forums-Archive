---
title: "Samba Shares will not mount on client"
date: 2009-10-24
forum: Server Platforms
---

### Post by snuffy47 on 2009-10-24
I have installed samba on my ubuntu server and tried to set it up to share 2 1T drives in a raid 1 for storage.  I am new to ubuntu

I have the raid mounted /mnt/md0-sda-sdb-1000.2GB-RAID1/  with sub folders Photos, Family Photos, Files, Videos ect

The turtorial I used is here                                   [http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)



When I try to connect with my ubuntu desktop I get this error


Cannot display location "smb://HOME;Smiths@192.168.1.110/myfiles/mnt/md0-sda-sdb-1000.2GB-RAID1
Failed to mount Windows share"

If I use terminal in ubuntu desktop I get 
smiths@smiths-laptop:~$ smbclient //ubuntu//mnt/md0-sda-sdb-1000.2GB-RAID1MyFiles -U Smiths
Enter Smiths's password: 
Domain=[UBUNTU] OS=[Unix] Server=[Samba 3.3.2]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
smiths@smiths-laptop:~$ 

When I try to map the drive on my XP machine I get Extended Error.

Please help 

Here is the config also
[global]
    ; General server settings
    netbios name = ubuntu
    server string =
    workgroup = HOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
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
    browseable = yes
    guest ok = yes
    read only = yes
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

[MyFiles]
    path = /mnt/md0-sda-sdb-1000.2GB-RAID1/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = administrator
    force group = #1admin234

---

### Post by skatinjj on 2009-10-24
Only thing I can think of about this is with the extended error on Windows, make sure that the date and time (more importantly the date) on the server and client match.

---

### Post by snuffy47 on 2009-10-24
Seems like the date and time are the same

Sat Oct 24 12:48:16 2009

Hmmm

---

### Post by snuffy47 on 2009-10-25
I dod finaly get to access the shares

My raid 1 was not mounted for some reason.  After remounting my raid 1 I still could not access the files untill I used chmod a+rwx /mnt/md0-sda-sdb-1000.2GB-RAID1/Videos and created new users for the windows machine.

Can someone please look over my confg and please help me make sure I have it right.

Does the size of the folder name matter? md0-sda-sdb-1000.2GB-RAID1

[global]

; General server settings
        netbios name = ubuntu
        server string = smb
        workgroup = HOME
        announce version = 5.0
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192$

        passdb backend = tdbsam
        security = user
        null passwords = true
        username map = /etc/samba/smbusers
        name resolve order = hosts wins bcast

        log file = /var/log/samba/log.%m
        writeable = yes
        workgroup = HOME
        os level = 20
        comment = Files
        encrypt passwords = true
        public = yes
        max log size = 1000
        wins support = true
        log level = 1

[homes]
    browsable = no
    map archive = yes

[printers]
    path = /var/tmp
    printable = yes
    min print space = 2000

[Family]
        writable = yes
        browsable = yes
        path = /mnt/md0-sda-sdb-1000.2GB-RAID1/Family

[Files]
        writable = yes
        browsable = yes
        path = /mnt/md0-sda-sdb-1000.2GB-RAID1/Files

[Photos]
        comment = Photos
        writable = yes
        browsable = yes
        path = /mnt/md0-sda-sdb-1000.2GB-RAID1/Photos

---

### Post by Vegan on 2009-10-25
Software RAID is problematic, use a hardware card for a better result.

---

### Post by snuffy47 on 2009-10-25
Well thanks for that information
 
From reading I thought that linux raid was actually well proven and for a buget setup a good option.
 
I am a noob to this linux stuff but so far my old laptop loaded with the desktop version of ubuntu is running great except for my old netgear pcmcia wireless card.
 
The server go with only terminal has been a chore and if I chose to start over once again then it will be my 3 atempt
 
After I use webmin and install the right files can I just use it to setup the RAID and SAMBA?
 
If I load the desktop version and set everything up can I copy the fsab, samb.cofg ect and use them on a fresh server load?
 
Just frustrated but learning

---


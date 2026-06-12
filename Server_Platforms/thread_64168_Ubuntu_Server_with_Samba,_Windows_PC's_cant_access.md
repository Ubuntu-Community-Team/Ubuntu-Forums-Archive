---
title: "Ubuntu Server with Samba, Windows PC's cant access server!"
date: 2005-09-10
forum: Server Platforms
---

### Post by ajferrari on 2005-09-10
I have created a RAID 1 array using Ubuntu Linux. I installed a graphical base system (by default) opposed to entering 'server' at the install disc boot prompt. Both my arrays have 160 GB hard drives and are correctly syncing:

    code:

# cat /proc/mdstat


    quote:Personalities : [raid1]
    md0 : active raid1 hdb1[0] hda1[1]
    159332544 blocks [2/2] [UU]

    unused devices: <none>



I then:

    code:

# nmbd
#smbd



I then created my users:

    code:

# adduser bob



I then ran:

    code:

# smbpasswd



I then edited /etc/samba/smb.conf:

(Comments removed for clarity, "Network Data" is the folder I would like to share on the server, as well as the user's respective home's)

    quote:#

    #Global Settings

    [global]
    workgroup = NETWORK
    server string = Network Data
    ; wins support = no
    ; wins server = w.x.y.z
    ; name resolve order = lmhosts host wins bcast

    #### Debugging/Accounting ####

    log file = /var/log/samba/log.%m
    max log size = 1000
    ; syslog only = no
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    ####### Authentication #######

    security = user
    encrypt passwords = true
    passdb backend = tdbsam guest
    obey pam restrictions = yes
    ; guest account = nobody
    invalid users = root
    ; unix password sync = no
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
    ; pam password change = no

    ########## Printing ##########

    ; load printers = yes
    ; printing = bsd
    ; printcap name = /etc/printcap
    ; printing = cups
    ; printcap name = cups
    ; printer admin = @ntadmin

    ######## File sharing ########

    # Name mangling options
    ; preserve case = yes
    ; short preserve case = yes
    wins support = no

    [Network Data]
    public = no
    comment = Data
    path = /home/network
    writable = yes
    printable = no
    valid users = billy bob bart bud
    create mask = 0775
    directory mask = 0775

    ############ Misc ############

    socket options = TCP_NODELAY
    ; message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
    ; domain master = auto
    ; idmap uid = 10000-20000
    ; idmap gid = 10000-20000
    ; template shell = /bin/bash

    #Share Definitions
    available = yes
    browseable = no
    public = yes
    [homes]
    comment = Home Directories
    browseable = yes
    writable = yes
    create mask = 0775
    directory mask = 0775
    [netlogon]
    ; comment = Network Logon Service
    ; path = /home/samba/netlogon
    ; guest ok = yes
    ; writable = no
    ; share modes = no
    [printers]
    comment = All Printers
    browseable = no
    path = /tmp
    printable = yes
    public = no
    writable = no
    create mode = 0700
    [print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    browseable = yes
    read only = yes
    guest ok = no
    ; write list = root, @ntadmin
    [cdrom]
    ; comment = Samba server's CD-ROM
    ; writable = no
    ; locking = no
    ; path = /cdrom
    ; public = yes
    ; preexec = /bin/mount /cdrom
    ; postexec = /bin/umount /cdrom



After editing smb.conf I then restarted samba with:

    code:

sudo /etc/init.d/samba restart



My windows clients can see the server (Samba is running) but no prompt is given for password, I'm just not allowed to use 'this resource'.

Any suggestions?

---

### Post by GTvulse on 2005-09-10
Where is your netmask? I see no "host allow" statement in your smb.conf file. ```
hosts allow = 192.168.0., 127.
``` would cover the case of a small lan behind a NAT and allow access from the localhost as well. I strongly recommend that you install SWAT and use it to configure your server.

---

### Post by LordHunter317 on 2005-09-10
[QUOTE=ajferrari]
    code:

# nmbd
#smbd[/quote]Never, ever do this.  Always use the initscripts to start/stop software.  It's more than possible that you're connecting to the samba daemons you started this way, using the old configuration file.


> # smbpasswdTo give him a smbpasswd, you needed to run:```
sudo smbpasswd -a bob
```


> I then edited /etc/samba/smb.conf:It's invalid (sorta).  You stuck your network data folder in the middle of the [global] section.  Move it to the bottom.

> Any suggestions?Make the share public at least temporarily (I see no reason to hide it) so you can verify things eaiser.

[quote=dradul]Where is your netmask? I see no "host allow" statement in your smb.conf file.[/quote]If it's not there, Samba allows access from everywhere by default.

---


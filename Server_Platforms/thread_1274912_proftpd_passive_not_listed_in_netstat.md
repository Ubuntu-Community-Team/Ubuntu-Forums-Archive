---
title: "proftpd passive not listed in netstat?"
date: 2009-09-25
forum: Server Platforms
---

### Post by 5millp0x on 2009-09-25
Hi, am trying to get my ftp to work in passivemode, but i cant get ubuntu to start listening to the ports, some one know how to do it?

Please help!

```

root@massacserver:~# netstat -an | grep "LISTEN "
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp6       0      0 :::21                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 ::1:631                 :::*                    LISTEN

```

```

ServerName                      "name"
ServerType                      standalone
AllowOverride                   off
DefaultServer                   on
ServerIdent                     off
UseReverseDNS                   off
IdentLookups                    off
DisplayConnect                  /usr/local/etc/issue.ftp
DisplayLogin                    /usr/local/etc/welcome.msg
DisplayChdir                    /usr/local/etc/.message
ScoreboardFile                  /var/run/proftpd.score
ListOptions                      +R strict
TimesGMT                        off
AllowRetrieveRestart            on
ShowSymlinks                    off
DenyFilter                      [^*/A-Za-z0-9_.-]

# Lockdown connections and connection attemps.
MaxClients                      80 "Maximum of %m users are already connected."
MaxInstances                    80
MaxClientsPerUser               80
MaxHostsPerUser                 80
MaxClientsPerHost               80 "Maximum of 80 clients per host allowed."
MaxLoginAttempts                3
RequireValidShell               no

# Lockdown command send/recieve sizes and type.
PassivePorts                    49152 65534
SocketOptions rcvbuf            8192
SocketOptions sndbuf            8192
CommandBufferSize               512

# Limit login times and timeouts to drop dead clients.
TimeoutLogin                    60
TimeoutIdle                     150
TimeoutNoTransfer               150
TimeoutStalled                  150

# Log format and location
TransferLog none

## Normal Mode
LogFormat awstats "%t %h %u %m %f %s %b"
ExtendedLog /var/log/xferlog read,write awstats


# No ftp user ever needs root
RootLogin                       off

# Port 21 and umask 022
Port                            21
Umask                           000

# Set the user and group that the server normally runs at.
User                proftpd
Group              ftpd

# Setup fake properties if needed.
DirFakeGroup                    On
DirFakeUser                     On
DirFakeMode                     0400

# Use this to jail all users in their homes 
#DefaultRoot    ~        
DefaultRoot /home/massac/ distans
DefaultRoot /home/upload/ 6by9

<Global>
  # Limit CHMOD everywhere in the anonymous chroot
        <Limit SITE_CHMOD>
                DenyAll
        </Limit>
        <Limit EPSV EPRT PORT>
                DenyAll
        </Limit>
</Global>

# Normally, we want files to be over write able.
<Directory /*>
  AllowOverwrite                on
</Directory>

# A basic anonymous configuration, no upload directories.
<Anonymous /ftp>
        # Allow logins if they are disabled above.
        <Limit LOGIN>
            AllowAll
        </Limit>

        User            ftp
        Group           ftp
        UserAlias       anonymous ftp
        HideNoAccess    on

        # Limit WRITE everywhere in the anonymous chroot
        <Limit WRITE>
                DenyAll
        </Limit>

        # Drop CHMOD permission
        <Limit SITE_CHMOD>
                DenyAll
        </Limit>
</Anonymous>

```

---

### Post by Bachstelze on 2009-09-25
Your FTP server *is* listening (on port 21, which is the standard port for FTP control connections).

---

### Post by 5millp0x on 2009-09-25
Oki, but i still cant login using passivmode :/ What could be wrong? all my ports are open and my server is a DMZ in the router.

---


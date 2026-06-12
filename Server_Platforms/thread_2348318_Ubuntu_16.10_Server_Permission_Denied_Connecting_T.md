---
title: "Ubuntu 16.10 Server Permission Denied Connecting To Samba Share"
date: 2017-01-02
forum: Server Platforms
---

### Post by elcidsps on 2017-01-02
This shouldn't be a difficult task; however, I have running into the contrary.  I've tried googling an answer to this to no avail.  I am attempting to connect my Linux Mint 18.1 Desktop to a Samba Share located on an Ubuntu 16.10 Server.


My SMB.CONF:


    ```
[global]
           workgroup = WORKGROUP
           netbios name = SAMBA
           guest account = nobody
           log file = /usr/local/samba/var/log.%m
           max log size = 50
           security = user
           map to guest = bad user
           encrypt passwords = no
    [WebApps]
           comment = Web Applications Folder
           path = /server/webapps
           writable = yes
           printable = yes
           guest ok = no
           create mask = 0775
           directory mask = 0775
```
Using the command to connect from the Mint Box:


    ```
sudo mount -t cifs //192.168.1.200/WebApps /mnt/WebApps --verbose -o iocharset=utf8,rw,credentials=~/.smbcreds,sec=ntlmv2
```
And I get:


    ```
mount error(13): Permission denied
```
Taling my syslog shows:


    ```
Jan  2 13:20:17 Shawn-Home kernel: [ 2641.359850] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
    Jan  2 13:20:17 Shawn-Home kernel: [ 2641.359859] CIFS VFS: Send error in SessSetup = -13
    Jan  2 13:20:17 Shawn-Home kernel: [ 2641.359978] CIFS VFS: cifs_mount failed w/return code = -13
```
I've triple checked the username and password on the server and in the credentials file..all checks out.  What am I missing here?  I'm stumped.

---

### Post by TheFu on 2017-01-02
**testparm** output from the samba machine please. Thanks for using code-tags.  Not sure if this matters or not, but SMB.CONF is wrong.  smb.conf is correct.  Don't know what you don't know.

Try spelling out the exact, full, path to the credentials.

Does /mnt/WebApps exist and is it writable by the correct userid?  Permission denied -13 means the userid can't access something, usually a file or a directory.

I have to say this - it is my nature - for Unix to Unix file sharing, NFS is better, more efficient, faster, and provides native permissions.  NFS can be used on the same storage that samba shares too.  NFSv4 can use Kerberos and encryption if you need more security. Anyway, feel free to ignore it.  

We've all been stumped on things like this.

---

### Post by darkod on 2017-01-02
I'm not sure if it applies but I have read cases where recent samba versions show similar error if winbind is not installed. Even if you don't specifically use winbind, try installing it. No need to configure or anything, just add the package.

Although I think it was more related to cases where samba was AD DC, not standalone samba for file sharing... But if you feel like it, give it a shot... I haven't looked in depth for it, but it seems after a certain samba version they made it somehow dependant on winbind.

---


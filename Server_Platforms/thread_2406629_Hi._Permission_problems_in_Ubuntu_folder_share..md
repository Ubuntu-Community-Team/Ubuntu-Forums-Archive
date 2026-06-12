---
title: "Hi. Permission problems in Ubuntu folder share."
date: 2018-11-23
forum: Server Platforms
---

### Post by tjv001 on 2018-11-23
Hi. I'm trying to share a folder on my Ubuntu Server 18.0 and I get the following error message:

net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

I would appreciate any help with this.
Many thanks
Tim.

---

### Post by howefield on 2018-11-23
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2018-11-23
It seems like you are trying to create a new share directly from the client.

Usually you as administrator would create the share on the ubuntu server, and clients would only use that share in accordance with the permissions you assign them.

Also, I wouldn't use the /var/lib/samba location for shares. Create a new folder specifically for your samba shares, like /sambashares or anything similar. This way you can control its permissions without depending on parent folder permissions.

---

### Post by Morbius1 on 2018-11-23
> **tjv001 said:**
> Hi. I'm trying to share a folder on my Ubuntu Server 18.0 and I get the following error message:

net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

I would appreciate any help with this.
Many thanks
Tim.
It looks like you are not a member of the correct group. So add yourself:
```
sudo gpasswd -a your-user-name sambashare
```
Logoff and log on again for the group membership to take affect and create your samba share again.

---

### Post by tjv001 on 2018-11-24
Hi there,
Many thanks for the help but neither method seems to work. Any extra help would be great. Ill keep on googling!

To add, I was creating the shared folder on the Ubuntu Server and I can see the shared folder on my windows 10 machine.
Thanks
Tim.

---

### Post by darkod on 2018-11-24
In that case please post the content of your smb.conf file (in CODE tags). And also the output of the permissions of the folder/path.

---

### Post by Morbius1 on 2018-11-24
Your issue seems to have morphed.

You original post indicated that you could not create the share. Now the problem is either you cannot connect to the server or you you don't have permissions to enter the share - not sure at this point which one it is.

We need a whole lot more information. The output of these commands will give us that:

```
testparm -s
```
```
net usershare info --long
```
```
hostname
```
```
id
```

---

### Post by tjv001 on 2018-11-24
godzukee@ubuntu18:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE

```
# Global parameters
[global]
    dns proxy = No
    log file = /var/log/samba/log.%m
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    syslog = 0
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
godzukee@ubuntu18:~$ 
```




More:
```
godzukee@ubuntu18:~$ net usershare info --long
info_fn: file /var/lib/samba/usershares/home cloud is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[TimCloud]
path=/home/godzukee/TimCloud
comment=
usershare_acl=Everyone:F,
guest_ok=n

godzukee@ubuntu18:~$ 


godzukee@ubuntu18:~$ hostname
ubuntu18

Last bit!godzukee@ubuntu18:~$ id
uid=1000(godzukee) gid=1000(godzukee) groups=1000(godzukee),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lxd),133(sambashare)
godzukee@ubuntu18:~$ 
```

I can share the folder now but cant access it from Win 10 machine.

I hope you can assist!
Thanks Tim.

Im not sure how to get this information, im a bit of a newbieto UIbuntu!
Thanks.
Tim
nb This post was meant for dargod!

---

### Post by Morbius1 on 2018-11-24
> [TimCloud]
path=/home/godzukee/TimCloud
comment=
usershare_acl=Everyone:F,
guest_ok=n
The way your share is defined the Win10 user will have to pass a username and samba password to gain access. If you want to use the godzukee username you have to create his samba password. You do that with this command:
```
sudo smbpasswd -a godzukee
```

---

### Post by garye on 2018-11-24
Have you tried [B]sudo [COLOR=#000000]net usershare


[/COLOR][/B][COLOR=#000000]
Gary[/COLOR]

---

### Post by tjv001 on 2018-11-25
Many thanks. I tried the last suggestion and it works. Thanks for your help.
Kind regards Tim.

---

### Post by tjv001 on 2018-11-25
Many thanks. All fixed!. Thanks for your help.
Kind regards Tim.

---

### Post by sz3bbyla on 2018-11-25
an user shared directory must look like this and can be add before [printer]
all can be made under sudo command
sudo nano /etc/samba/smb.conf
then add this

[folder_name]
        hide dot files = no    #yes/no
        valid users = user_name
        browsable =yes     #yes/no
        writeable = yes     #yes/no
        create mode = 664     #rw-   rw-    r--   for files
        path = /home/user/folder    #replace with exact location folder
#        hide files = /lost+found/   # if folder is partition hdd
        directory mode = 775    #rwx   rwx   r--   for folders

this let you to read and write on folder share
sudo smbpasswd -a user_name     to add user_name to samba

chown -R user_name:user_name /folder/user/folder
chmod -R ug+rw-x,o+r-w-x /folder/user/folder
chmod -R +X /folder/user/folder

the last 3 commandsare only if folder is not located in /home/user/folder_shared

at the end restart samba daemon
sudo /etc/init.d/smbd restart

---


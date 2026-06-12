---
title: "Samba error??"
date: 2013-01-22
forum: Server Platforms
---

### Post by BStrizzy on 2013-01-22
Hey guys,

For some reason when I try to copy something to my server from a windows side I keep getting the error message. I followed [https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html)

and had a question on the part where it is                           workgroup = EXAMPLE    ...    security = user 
i put where it says example workgroup so ... worgroup=workgroup and kept 
security the same way cause I was not sure. other than that this is my share 
```
[share]

        comment = where window files will be stored
        path = /home/bstrizzy/share
        browsable = yes
        guest ok = yes
        read only = no
        create mask = 0755
```


why still error?!

---

### Post by volkswagner on 2013-01-23
What is the error message?

What are the permissions of the folder?

```
ls -al /home/bstrizzy/share
```

---

### Post by BStrizzy on 2013-01-23
> **volkswagner said:**
> What is the error message?

What are the permissions of the folder?

```
ls -al /home/bstrizzy/share
```

bstrizzy@nova:~$ ls -al /home/bstrizzy/share
total 8
drwxr-xr-x  2 nobody   nogroup  4096 2013-01-22 15:35 .
drwxr-xr-x 10 bstrizzy bstrizzy 4096 2013-01-22 15:35 ..

and the error message that comes up says that the file has encountered 1 error and thats it

---

### Post by SeijiSensei on 2013-01-23
Look in /var/log/samba to see the log files.

---

### Post by CharlesA on 2013-01-23
> **BStrizzy said:**
> bstrizzy@nova:~$ ls -al /home/bstrizzy/share
total 8
drwxr-xr-x  2 nobody   nogroup  4096 2013-01-22 15:35 .
drwxr-xr-x 10 bstrizzy bstrizzy 4096 2013-01-22 15:35 ..

and the error message that comes up says that the file has encountered 1 error and thats it

Run this one instead:

```
ls -ld /home/bstrizzy/share
```

The permissions are odd for "." which is the current directory.

> **SeijiSensei said:**
> Look in /var/log/samba to see the log files.

+1.

Also running this helps check for problems:

```
testparm -s
```

---

### Post by BStrizzy on 2013-01-23
> **CharlesA said:**
> Run this one instead:

```
ls -ld /home/bstrizzy/share
```The permissions are odd for "." which is the current directory.



+1.

Also running this helps check for problems:

```
testparm -s
```

bstrizzy@nova:~$ cd /var/log/samba
bstrizzy@nova:/var/log/samba$ ls
cores           log.bstrawt-pc  log.nmbd.4.gz  log.smbd.2.gz
log.192.168.1.101  log.greg-pc       log.nmbd.5.gz  log.smbd.3.gz
log.192.168.1.103  log.jonny-pc    log.nmbd.6.gz  log.smbd.4.gz
log.192.168.1.104  log.nmbd       log.nmbd.7.gz  log.smbd.5.gz
log.192.168.1.107  log.nmbd.1.gz   log.panama      log.smbd.6.gz
log.192.168.1.108  log.nmbd.2.gz   log.smbd      log.smbd.7.gz
log.192.168.1.109  log.nmbd.3.gz   log.smbd.1.gz
bstrizzy@nova:/var/log/samba$ ls -ld /home/bstrizzy/share
drwxr-xr-x 2 nobody nogroup 4096 2013-01-22 15:35 /home/bstrizzy/share
bstrizzy@nova:/var/log/samba$ 

bstrizzy@nova:/var/log/samba$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
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
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[share]
    comment = where window files will be stored
    path = /home/bstrizzy/share
    read only = No
    create mask = 0755
    guest ok = Yes

---

### Post by volkswagner on 2013-01-23
It appears the Ubuntu how to conflicts other Server Docs "[Securing a SAMBA file and print server]("https://help.ubuntu.com/10.04/serverguide/samba-fileprint-security.html")"


According the the link above you should have:
```
security = share
```

When SeijiSensei said "Look in /var/log/samba to see the log files" you were supposed to actually look inside the relevant files not just the directory.  Perhaps reading on of the files matchin the ip address of you client would help.

---

### Post by BStrizzy on 2013-01-24
> **volkswagner said:**
> It appears the Ubuntu how to conflicts other Server Docs "[Securing a SAMBA file and print server]("https://help.ubuntu.com/10.04/serverguide/samba-fileprint-security.html")"


According the the link above you should have:
```
security = share
```When SeijiSensei said "Look in /var/log/samba to see the log files" you were supposed to actually look inside the relevant files not just the directory.  Perhaps reading on of the files matchin the ip address of you client would help.

ok gotchya. I understand what you are trying to say reading one of the files for the matching ip address. I was hoping to make the samba share folder availible for any i.p.
I am really the only one using the home server so I really just need it for me but I also access my server externally. opened up port 22. would making a samba share via webmin be easier for my situation? or it really shouldnt matter right because of the logic behind it all

---

### Post by volkswagner on 2013-01-24
SAMBA is designed for local LAN access and is not secure for exposing to WAN.

If you have opened port 22 on your machine to the outside world, it is best to use key authentication, disable root ssh access and disable password ssh auth.

At the very minimum you should have disabled root ssh access or have a super strong password.


I'm curious if you have samba working locally by changing the security = share?

What type of client are you connecting to the server with?  If you are using a Linux client, you can simply use ssh or sftp for file level access.

Ubuntu desktop has a builtin client to connect via ssh/sftp.  

From Nautilus:
> File > Connect to Server > enter server name or ip address > choose SSH as type (port 22) > leave folder as / or change to /home/shares/documents > enter username and password and connect.

You can use this method from outside you lan by substituting the servers external ip address.

---

### Post by volkswagner on 2013-01-24
If you are the only user that needs access to the SAMBA server why not setup the secure method and add yourself to the samba users, change the folder permissions to owner = yourusername.

To add yourself as a samba user:

```
smbpasswd username
```

If /home/shares/documents is not a separate partition, I'll assume /home has enough available space for your file share.  You can just use the [homes] section of smb.conf which will allow you to share your entire home directory.

---

### Post by CharlesA on 2013-01-24
> **volkswagner said:**
> SAMBA is designed for local LAN access and is not secure for exposing to WAN.

If you have opened port 22 on your machine to the outside world, it is best to use key authentication, disable root ssh access and disable password ssh auth.

At the very minimum you should have disabled root ssh access or have a super strong password.

+1. Another thing that can be done with SSH is enabling two-factor auth by using a Google authenticator. That would allow passwords to be used but also require the input of a unique key.

[http://www.howtogeek.com/121650/how-to-secure-ssh-with-google-authenticators-two-factor-authentication/](http://www.howtogeek.com/121650/how-to-secure-ssh-with-google-authenticators-two-factor-authentication/)

Not really on topic, but maybe it will be helpful to someone. ;)

---

### Post by BStrizzy on 2013-02-10
> **volkswagner said:**
> SAMBA is designed for local LAN access and is not secure for exposing to WAN.

If you have opened port 22 on your machine to the outside world, it is best to use key authentication, disable root ssh access and disable password ssh auth.

At the very minimum you should have disabled root ssh access or have a super strong password.


I'm curious if you have samba working locally by changing the security = share?

What type of client are you connecting to the server with?  If you are using a Linux client, you can simply use ssh or sftp for file level access.

Ubuntu desktop has a builtin client to connect via ssh/sftp.  

From Nautilus:
> File > Connect to Server > enter server name or ip address > choose SSH as type (port 22) > leave folder as / or change to /home/shares/documents > enter username and password and connect.

You can use this method from outside you lan by substituting the servers external ip address.


sorry for the super late response. I have been working on some other things with the server and now the samba is crucially important. the client is my windows side of my laptop. I duel booted it and I would like to run certain programs from my server as well as copy and paste windows documents.

---

### Post by Morbius1 on 2013-02-10
> For some reason when I try to copy something to my server from a windows side I keep getting the error message.
bstrizzy@nova:~$ ls -al /home/bstrizzy/share
total 8
drwxr-xr-x 2 nobody nogroup 4096 2013-01-22 15:35 .
drwxr-xr-x 10 bstrizzy bstrizzy 4096 2013-01-22 15:35 ..
The only user getting write access to that share is "nobody" so you have some options. Here's 2:

** Make it so anybody can write to it:
```
chmod 0777 /home/bstrizzy/share
```** Make all the remote guests look like nobody
> [share]
        comment = where window files will be stored
        path = /home/bstrizzy/share
        browsable = yes
        guest ok = yes
        read only = no
[COLOR=Blue]**        force user = nobody**[/COLOR]
        create mask = 0755[COLOR=Blue][I]BTW, Somebody really needs to take down this HowTo: [https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html)

It's factually incorrect and anyone following it to the letter will not have success.[/I][/COLOR]

---

### Post by BStrizzy on 2013-02-10
> **Morbius1 said:**
> The only user getting write access to that share is "nobody" so you have some options. Here's 2:

** Make it so anybody can write to it:
```
chmod 0777 /home/bstrizzy/share
```** Make all the remote guests look like nobody
[COLOR=Blue][I]BTW, Somebody really needs to take down this HowTo: [https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html)

It's factually incorrect and anyone following it to the letter will not have success.[/I][/COLOR]

thanks, I just changed the settings and will be trying the transfer now

---


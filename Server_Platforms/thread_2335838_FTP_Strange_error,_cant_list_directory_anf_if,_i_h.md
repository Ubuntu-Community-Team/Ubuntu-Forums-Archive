---
title: "FTP Strange error, cant list directory anf if, i have no permissions"
date: 2016-09-01
forum: Server Platforms
---

### Post by raspptoftpd on 2016-09-01
Hello.

Please help me, i have a strange error and i cant get any further.
I konw it is not a complete ubuntu issue. but i have the same running on a ubuntu server correctly.
Maybe you can help me.

I have ProFTPd installed on a Raspberry Pi. It works and is running except to one thing.

I have created a user with GADMIN-proftpd (when you want, i can give special information about the settings, if this is helpful, a bit of information can be found in Part 3)

When  logging in from FileZilla, i get the Error Message that after  succesfully logged, the Connection is refused (like shown in the Part 1  below)

BUT:

When logging in from the terminal, everything  is fine, i can change the directory, i can also list it but when trying  to upload a file, this doesnt work.
I have given the prompt in Part 2 below.

Please help me: How can i handle this?

Thanks for your answers.

Best regards.

 

____________________________________
```
Part 1:

Status:   Verbinde mit 10.0.0.15:21...
Status:   Verbindung hergestellt, warte auf Willkommensnachricht...
Antwort:   220 My FTP Server
Befehl:   USER mont
Antwort:   331 Password required for mont
Befehl:   PASS **********
Antwort:   230 Anonymous access granted, restrictions apply
Befehl:   SYST
Antwort:   215 UNIX Type: L8
Befehl:   FEAT
Antwort:   211-Features:
Antwort:    MDTM
Antwort:    MFMT
Antwort:    TVFS
Antwort:    UTF8
Antwort:    MFF modify;UNIX.group;UNIX.mode;
Antwort:    MLST modify*;perm*;size*;type*;unique*;UNIX.group*;UNIX.mode*;UNIX.owner*;
Antwort:    LANG en-US*
Antwort:    REST STREAM
Antwort:    SIZE
Antwort:   211 End
Befehl:   OPTS UTF8 ON
Antwort:   200 UTF8 set to on
Status:   Verbunden
Status:   Empfange Verzeichnisinhalt...
Befehl:   PWD
Antwort:   257 "/" is the current directory
Befehl:   TYPE I
Antwort:   200 Type set to I
Befehl:   PASV
Antwort:   227 Entering Passive Mode (10,0,0,15,205,27).
Befehl:   MLSD
Fehler:   Could not read from transfer socket: ECONNRESET - Connection reset by peer
Fehler:   Verbindung vom Server geschlossen
Fehler:   Verzeichnisinhalt konnte nicht empfangen werden
____________________________________
Part 2:

desktop@desktop-desktop:~$ ftp
ftp> open
(to) 10.0.0.15
Connected to 10.0.0.15.
220 My FTP Server
Name (10.0.0.15:desktop): mont
331 Password required for mont
Password:
230 Anonymous access granted, restrictions apply
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> put
(local-file) /home/desktop/css.png
(remote-file) css.png
local: /home/desktop/css.png remote: css.png
200 PORT command successful
550 css.png: Operation not permitted
ftp> ls
200 PORT command successful
150 Opening ASCII mode data connection for file list
drwxrwxrwx   2 root     root         4096 Aug 30 22:08 folder1
drwxrwxrwx   2 root     root         4096 Aug 22 14:06 folder2
drwxrwxrwx   4 root     root         4096 Aug 30 22:14 folder3
226 Transfer complete
ftp> 

____________________________________
Part 3:

<Anonymous /var/www/speicher>
User mont
Group root
AnonRequirePassword on
MaxClients 10 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayChdir .msg
<Limit LOGIN>
Allow from All
Deny from all
</Limit>
AllowOverwrite off
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMD$
 DenyAll
</Limit>
</Anonymous>
```

---

### Post by Graham_Willis on 2016-09-02
What's the output of **ls .** ? Anyway, one thing attracting my attention is that all the directories that you listed have the owner and group owner set to root. So perhaps the directory in which you are in immediately after logging to your FTP account also has root as owner and group owner and for this reason you can't write to it. It's also possible that permissions are also wrong. Issue the following commands on the server:

**find [B]/var/www/speicher -mindepth 1 -exec chown -Rh **mont:mont {} \;
**find [B]/var/www/speicher -mindepth 1 -type d -exec chmod -R 750** {} \;[/B]
[/B]**[B]find [B]/var/www/speicher -mindepth 1 -type f -exec chmod -R 640** {} \;
[/B][/B]
Please report back if it helped.

---

### Post by raspptoftpd on 2016-09-02
Hello

Sadly it didnt help.

This was my output.

I added the group mont manually, because i only put it in while creating the virtual user at gadmin proftpd.

Thanks for your advise, what else could i do to solve this?

Best reagrds

```


desktop@desktop-desktop:~$ ftp 
ftp> opwn
?Invalid command
ftp> quit
desktop@desktop-desktop:~$ clear
desktop@desktop-desktop:~$ ftp
ftp> open
(to) 10.0.0.15
Connected to 10.0.0.15.
220 My FTP Server
Name (10.0.0.15:desktop): mont
331 Password required for mont
Password:
230 Anonymous access granted, restrictions apply
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls.
?Invalid command
ftp> ls
200 PORT command successful
150 Opening BINARY mode data connection for file list
drwxrwxrwx   2 root     root         4096 Aug 31 22:23 folder1
drwxrwxrwx   2 root     root         4096 Aug 22 14:06 folder2
drwxrwxrwx   2 root     root         4096 Aug 30 22:33 restricted
drwxrwxrwx   4 root     root         4096 Aug 30 22:14 folder3
226 Transfer complete
ftp> quit
221 Goodbye.
desktop@desktop-desktop:~$ ssh root@10.0.0.15
root@10.0.0.15's password: 
Linux raspberrypi 3.6.11+ #474 PREEMPT Thu Jun 13 17:14:42 BST 2013 armv6l

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Wed Aug 31 22:36:01 2016 from desktop-desktop.lan
root@raspberrypi:~# find /var/www/speicher -mindepth 1 -exec chown -Rh mont:mont {} \;
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
chown: invalid group: `mont:mont'
root@raspberrypi:~# group
groupadd  groupdel  groupmod  groups    
root@raspberrypi:~# group
groupadd  groupdel  groupmod  groups    
root@raspberrypi:~# groupadd mont
root@raspberrypi:~# find /var/www/speicher -mindepth 1 -exec chown -Rh mont:mont {} \;
root@raspberrypi:~# find /var/www/speicher -mindepth 1 -type d -exec chmod -R 750 {} \;
root@raspberrypi:~# find /var/www/speicher -mindepth 1 -type f -exec chmod -R 640 {} \;
root@raspberrypi:~# ftp




```

now the output it this

```


root@raspberrypi:/var/www/speicher# ls
folder1  folder2  restricted  folder3
root@raspberrypi:/var/www/speicher# ls.
-bash: ls.: command not found
root@raspberrypi:/var/www/speicher# ls -l
total 16
drwxr-x--- 2 mont mont 4096 Aug 31 22:23 folder1
drwxr-x--- 2 mont mont 4096 Aug 22 14:06 folder2
drwxr-x--- 2 mont mont 4096 Aug 30 22:33 restricted
drwxr-x--- 4 mont mont 4096 Aug 30 22:14 folder3
root@raspberrypi:/var/www/speicher#


```

---

### Post by Graham_Willis on 2016-09-09
The striking thing about your configuration is this:

```
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<**Limit STOR** STOU  APPE  RNFR RNTO  **DELE**  **MKD** XMKD SITE_MKDIR  RMD XRMD SITE_RMD$
 **DenyAll**
</Limit>

```

I don't remember what all of these stand for, but it seems that your own configuration's blocking the possibility of uploading files over FTP (also deleting them, making directories and so on). Move some of these entries to the **AllowAll** list and check if it works.

---


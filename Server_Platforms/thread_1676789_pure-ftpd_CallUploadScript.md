---
title: "pure-ftpd CallUploadScript"
date: 2011-01-27
forum: Server Platforms
---

### Post by Bob.Davis@wibble.net.nz on 2011-01-27
Hi, 

I am having an issue getting migrating to LTS 10.04 I have previously run this on Fedora. Of course Ubuntu is quite differnet to configure.
 
I have pure-ftpd working but the CallUploadScript is not actually calling the script.

when I start pure-ftpd 

```
/etc/init.d/pure-ftpd-mysql restart
```It starts fine and shows the script as running 

```
Restarting ftp server: Running: /usr/sbin/pure-ftpd-mysql -l mysql:/etc/pure-ftpd/db/mysql.conf -E -O clf:/var/log/pure-ftpd/transfer.log -H -o -d -u 501 -C 4 -S 192.168.9.23,21 -A -c 20 -8 UTF-8 -i -B
Restarting ftp upload handler: pure-uploadscript.
```and when I do a ps-aux i can see the server and the script 

```
root     15545  0.0  0.0  35244  2012 pts/1    T    10:41   0:00 /usr/sbin/pure-uploadscript -r /bin/newfile.sh
root     17138  0.0  0.0  35480   980 ?        Ss   11:07   0:00 pure-ftpd (SERVER)
```so they are both running .. 

but when I upload a file it doesn't run the script,

I have tried running the script which simply has this in it for testing 

```
 echo $(date +%e-%m-%y_%H:%M:%S) "," "$1" | mail -s "New File on FTP02 Server" \ bobd@mhnz.co.nz
```when i run it straight from a shell it sends me an e-mail perfectly, of course without the file name, it has just the date in it, as of course its not run by the ftp server, which is  the result I would expect. and it works fine, but when i ftp up a file nothing happens.

To debug I have tried killing the process started by the server and running the script in a shell as a foreground process and uploaded a file.  It uplaods the file fine but the script is silent does nothing.

when i check the logs i can see the file upload etc in /var/log/messages.log and in /var/log/pure-ftpd/transfer.log,  I  have verbose loging enabled trying to work this out ..

I am at a loss can't see why its not working ?  anyone got any ideas ?? 

Bob

---

### Post by Bob.Davis@wibble.net.nz on 2011-02-01
Hi i have solved this myself.. 

I was missing 

```
#!/bin/sh
```
at the top of the script ..  Fedora doesn't care but Ubuntu does :)

---


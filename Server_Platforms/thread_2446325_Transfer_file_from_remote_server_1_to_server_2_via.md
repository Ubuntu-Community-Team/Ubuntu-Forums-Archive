---
title: "Transfer file from remote server 1 to server 2 via client 3 (GOTO FINAL POST))"
date: 2020-06-28
forum: Server Platforms
---

### Post by makem2 on 2020-06-28
I have a Raspberry Pi4 which I use as a server. I also have a Samsung Galaxy Tab A which I also use as a server (SSHelper app).

I have ssh keys on both and control them via my xubuntu laptop client.

I have files on the Pi4 which I regularly need to view from the Tab A.

When using a terminal on my laptop to access the Pi4 and I attempt to copy the ssh ID from the Pi4 to the Tab A I get the error:

```

u0_a264@localhost:~$ ssh-copy-id pi@192.168.2.73
-bash: /data/user/0/com.arachnoid.sshelper/bin/ssh-copy-id: /data/data/com.arachnoid.sshelper/files/usr/bin/sh: bad interpreter: No such file or directory
u0_a264@localhost:~$

```

When using a terminal on my laptop to access the Tab A and I attempt to copy the ssh ID from the Tab A to the Pi4 I get the error:

```

pi@Pi4:~ $ ssh-copy-id makem@192.168.2.8 -p 2222
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/pi/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
SSHelper Version 13.0 Copyright 2018, P. Lutus
makem@192.168.2.8: Permission denied (publickey,keyboard-interactive).
pi@Pi4:~ $

```

It seems I may need to use a keyboard?

Is it possible to copy an ssh ID manually from machine to machine in my case where one machine is Android?

I used to have a program in Windows which from an ftp client could move files from one server to another which is exactly what I am trying to achieve but I cannot find a suitable program/app to do the job in this case.

---

### Post by HermanAB on 2020-06-29
It is just a file like any other.  You don't have to use the ssh-copy-id script.  You can copy key files with scp or sftp.  The important thing is that you don't accidentally overwrite a file at the destination and the owner and permissions of the key file must be right after you copied and appended to it.  The keys are really just text files that you can edit with vi, or append one key file onto another with 'cat newkey >> oldkeys'.

Also note that with scp, you can send a file from a 2nd machine to a 3rd machine and rename the file all at the same time:
$ scp user2@server2:/filename2 user3@server3:/filename3

---

### Post by ActionParsnip on 2020-06-29
```

cat ~/.ssh/id_rsa.pub | ssh -p 2222 makem@192.168.2.8 "cat >> ~/.ssh/authorized_keys"

```

Something like that?

---

### Post by slickymaster on 2020-06-29
*Thread moved to **Server Platforms**.*

---

### Post by makem2 on 2020-06-29
> **ActionParsnip said:**
> ```

cat ~/.ssh/id_rsa.pub | ssh -p 2222 makem@192.168.2.8 "cat >> ~/.ssh/authorized_keys"

```

Something like that?

From client to Pi4:

```

makem@XPS-13-9300:~$ cat ~/.ssh/id_rsa.pub | ssh makem@192.168.2.73 "cat >> ~/.ssh/authorized_keys"
SSHelper Version 13.0 Copyright 2018, P. Lutus
makem@XPS-13-9300:~$

```

From Tab A:

```

pi@Pi4:~$ cat ~/.ssh/id_rsa.pub | ssh -p 2222 makem@192.168.2.8 "cat >> ~/.ssh/authorized_keys"
SHelper Version 13.0 Copyright 2018, P. Lutus
Enter passphrase for key '/home/pi/.ssh/id_rsa':
bash: warning: setlocale: LC_ALL: cannot change locale (en_GB.UTF-8): No such file or directory
ls -l ~/.ssh/id_*.pub
/home/pi/.ssh/id_rsa  /home/pi/.ssh/id_rsa.pub
pi@Pi4:~$ 

```

The key is there but I don't know about the error reason.

I cannot find a syntax which works with sftp to transfer a file from the Pi4 to the folder:

```

sftp://makem@192.168.2.8:2222/storage/48BE-2703/Movies/PLEX/

```

The address /storage/48BE-2703 is the physical SDcard. I get errors because of the port 2222 I think.

I think I need to investigate the permission methods of Android. I know that when connecting via USB you have to answer, "OK" manually, to a query about allowing data transfer.

---

### Post by makem2 on 2020-06-29
Interaction with Tab A from client (ubuntu laptop)

```

makem@XPS-13-9300:~$ ssh -t -p 2222 makem@192.168.2.8 "cd /storage/48BE-2703; bash --login"
SSHelper Version 13.0 Copyright 2018, P. Lutus
Galaxy_Tab_A_(2018,_10.5):3.18.120-18306396
u0_a264@localhost:48BE-2703$ ls -la
ls: ./.android_secure: Permission denied
total 2176
drwxr-xr-x    7 root     everybod    131072 Jun 29 16:39 .
drwxr-xr-x    6 root     root           120 Jun 29 02:13 ..
drwxr-x---    4 root     everybod    131072 Jan 26 16:11 Android
drwxr-xr-x    3 root     everybod    131072 Feb 10 21:47 Data
-rwxr-xr-x    1 root     everybod    196467 Aug 11  2019 M25.png
drwxr-xr-x    4 root     everybod    131072 Apr 23 14:45 Movies
-rwxr-xr-x    1 root     everybod   1271646 Aug 11  2019 bookmarks.html
drwxr-xr-x    2 root     everybod    131072 Aug 11  2019 expressvpn
u0_a264@localhost:48BE-2703$ mkdir test
mkdir: can't create directory 'test': Permission denied
u0_a264@localhost:48BE-2703$ 

```

I have a feeling the denial is because Android needs manual input from the Tab A user to allow writing.

The, "ls: ./.android_secure: Permission denied" error is caused by the ls -la command where Android does not recognise the "-la". No error with just "ls".

Attempt to change the lack of write permission:

```

u0_a264@localhost:48BE-2703$ chmod 777 Movies
u0_a264@localhost:48BE-2703$ ls -la
ls: ./.android_secure: Permission denied
total 2176
drwxr-xr-x    7 root     everybod    131072 Jun 29 16:39 .
drwxr-xr-x    6 root     root           120 Jun 29 02:13 ..
drwxr-x---    4 root     everybod    131072 Jan 26 16:11 Android
drwxr-xr-x    3 root     everybod    131072 Feb 10 21:47 Data
-rwxr-xr-x    1 root     everybod    196467 Aug 11  2019 M25.png
drwxr-xr-x    4 root     everybod    131072 Apr 23 14:45 Movies
-rwxr-xr-x    1 root     everybod   1271646 Aug 11  2019 bookmarks.html
drwxr-xr-x    2 root     everybod    131072 Aug 11  2019 expressvpn
u0_a264@localhost:48BE-2703$ 

```

Edit: Until I can write it is not possible to act as a conductor and pass files between Pi4 and remote Android.

Until I find something better I will use Method 1 here (assuming it works!):

[URL="https://arachnoid.com/android/SSHelper/index.html#External_Storage_Access"]https://arachnoid.com/android/SSHelper/index.html#External_Storage_Access

[/URL]
Following those instructions I can now connect to and write to the 'special folder' using the following syntax:

```

makem@XPS-13-9300:~$ ssh -t -p 2222 makem@192.168.2.8 "cd SDCard/Android/data/com.arachnoid.sshelper; bash --login"
SSHelper Version 13.0 Copyright 2018, P. Lutus
Galaxy_Tab_A_(2018,_10.5):3.18.120-18306396
u0_a264@localhost:com.arachnoid.sshelper$ ls
test
u0_a264@localhost:com.arachnoid.sshelper$

```

The 'test' folder is one I created previously.

So far so good.


Hopefully will now be able to duplicate this on the Pi4 and be able to copy files to the Tab A remotely from the client laptop.

The downside mentioned in the instructions about losing the data does not affect me as the data is transient anyway.

---

### Post by makem2 on 2020-06-29
[SIZE=2][FONT=arial]Well, as expected, I can access the Tab A from the Pi4.

However, I cannot find the correct syntaxt to copy a file from the Pi4 to the Tab A
 I have tried:

```

pi@Pi4:~ $ scp /media/pi/torrent/data/torrent_downloads/text.txt  -t -p 2222 makem@192.168.2.8 "cd SDCard/Android/data/com.arachnoid.sshelper; bash --login"
cd cd SDCard/Android/data/com.arachnoid.sshelper; bash --login: No such file or directory
scp /media/pi/torrent/data/torrent_downloads/text.txt  -t -p 2222  makem@192.168.2.8:/SDCard/Android/data/com.arachnoid.sshelper
ssh: connect to host 192.168.2.8 port 22: Connection refused

```

[/FONT][/SIZE]```

[SIZE=2][FONT=arial][SIZE=2][FONT=arial]pi@Pi4:~ $ scp -p  2222   /media/pi/torrent/data/torrent_downloads/text.txt   makem@192.168.2.8:/SDCard/Android/data/com.arachnoid.sshelper[/FONT][/SIZE][/FONT][/SIZE]
[SIZE=2][FONT=arial]SHelper Version 13.0 Copyright 2018, P. Lutus [/FONT][/SIZE][SIZE=2][FONT=arial]
Enter passphrase for key '/home/pi/.ssh/id_rsa':[/FONT][/SIZE][SIZE=2][FONT=arial]
bash: warning: setlocale: LC_ALL: cannot change locale (en_GB.UTF-8): No such file or directory
[/FONT][/SIZE]scp: [SIZE=2][FONT=arial]/SDCard/Android/data/com.arachnoid.sshelper: No such file or directory
[/FONT][/SIZE][SIZE=2][FONT=arial]pi@Pi4:~ $ [/FONT][/SIZE]

```

Can anyone suggest the correct syntax?

Edit: It looks like the correct syntax is:

```

[SIZE=2][FONT=arial][SIZE=2][FONT=arial]pi@Pi4:~  $ scp -P 2222 /media/pi/torrent/data/torrent_downloads/text.txt makem@192.168.2.8:SDCard/Android/data/com.arachnoid.sshelper[/FONT][/SIZE][/FONT][/SIZE]

```

as it copied the file to Tab A.

Try a whole directory tomorrow :)
[B]
Copy a File Between Two Remote Systems using the scp Command![/B]

[URL="https://linuxize.com/post/how-to-use-scp-command-to-securely-transfer-files/"]https://linuxize.com/post/how-to-use-scp-command-to-securely-transfer-files/
[/URL]

---

### Post by makem2 on 2020-06-30
Simple solution avoiding using a third machine:

1. Install Total Commander on the Android Samsung Galaxy Tab A
2. Install  a Samba share on the Pi4
3. Create a LAN (Windows share) in Total Commander
4. Access Pi4 files via the samba share

---

### Post by TheFu on 2020-08-15
Unrelated, but I see that expressVPN directory.  That company claims to be in the British VI, but is actually in Hong Kong. It is part of of a parent company which is part of another parent company, both are clearly Chinese. They have Mandarin terms even though locals in Hong Kong speak Cantonese.  [https://www.csoonline.com/article/3335480/china-owns-half-of-all-vpn-services.html](https://www.csoonline.com/article/3335480/china-owns-half-of-all-vpn-services.html)

---


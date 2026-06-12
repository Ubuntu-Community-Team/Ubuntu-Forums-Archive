---
title: "Error while moving - Permission denied"
date: 2011-06-09
forum: Server Platforms
---

### Post by keith_irl on 2011-06-09
Hi everyone,

I am sorry if this has been asked a thousand times I have tried searching but I am not getting any relevant results.

I am running an instance of ubuntu server 10.10. Its headless and I connect to it by ssh.

I am having problems with file permissions on the server while accessing it on ubuntu 11.04.

I use the transmission daemon to download torrent files. 

When I boot up my laptop and mount the server location I can see play and use files but I dont seem to have the permissions to delete or move the files that have been downloaded by the transmission daemon.

I am a noob with linux and hoping someone may be able to offer some easy to digest help.

Here is the samba share in smb.conf on my server.
```
[server]
        guest ok = yes
        comment = shares
        writable = yes
        browseable = yes
        path = /home/administrator/shares

```However when I log into webmin and use the integrated file manager I can do what I like with the files.

Any help would be greatly appreciated. Thanks

---

### Post by ruffEdgz on 2011-06-09
So when you ssh into the server with this problem and run the following command(s):
```

ll -d /home/administrator/shares

ll /home/administrator/shares

```
What is displayed (and post it on here if you can and you can change the name of the files if you like)?

Do you have access to the root account (sudo su -)? If so, do you have the same problem moving/deleting these files?

Who are you logging in as from your laptop to the server?

Cheers!

---

### Post by keith_irl on 2011-06-09
Thanks for your reply

Here are the results of the command 

```
Last login: Thu Jun  9 21:57:02 2011 from 192.168.15.100
administrator@Server:~$ ll -d /home/administrator/shares
drwxrwxrwx 6 administrator administrator 4096 2011-06-09 22:03 /home/administrator/shares/
administrator@Server:~$ 
administrator@Server:~$ ll /home/administrator/shares

```
```
administrator@Server:~$ ll /home/administrator/shares
total 68
drwxrwxrwx  6 administrator administrator  4096 2011-06-09 22:03 ./
drwxr-xr-x 10 administrator administrator  4096 2010-12-20 20:46 ../
drwxrwxrwx 50 administrator administrator 49152 2010-11-22 00:20 itunes_music/
drwxrwxrwx 16 administrator administrator  4096 2011-06-05 12:58 music_downloads/
drwxrwxrwx  6 administrator administrator  4096 2011-01-30 23:02 Pictures-Backups/
drwxrwxrwx  5 administrator administrator  4096 2011-06-09 22:04 video/

```
The problem is when I am accessing the share on my ubuntu laptop and have the share mounted. I have no problem moving the files when I log into the server and mv the files by ssh using the administrator account.

---

### Post by ruffEdgz on 2011-06-09
In thos subdirectories in /home/administrator/shares, how does the permissions look there? Find a file that you have a hard time moving/deleting and run this command:
```

ll /home/administrator/shares/path/to/file

```
And post it back here.

Do you have an administrator account on your laptop which also have a group? If you don't know, run these commands:
```

getent passwd administrator

getent group administrator

```
Thanks.

---

### Post by keith_irl on 2011-06-09
> **ruffEdgz said:**
> In thos subdirectories in /home/administrator/shares, how does the permissions look there? Find a file that you have a hard time moving/deleting and run this command:
```

ll /home/administrator/shares/path/to/file

```And post it back here.

Do you have an administrator account on your laptop which also have a group? If you don't know, run these commands:
```

getent passwd administrator

getent group administrator

```Thanks.

Heres the results.
```
administrator@Server:~$ ll /home/administrator/shares/video
total 28
drwxrwxrwx   5 administrator       administrator        4096 2011-06-09 22:04 ./
drwxrwxrwx   6 administrator       administrator        4096 2011-06-09 22:03 ../
drwxrwxrwx 102 administrator       administrator       12288 2011-06-09 00:32 movies/
drwxr-xr-x   2 debian-transmission debian-transmission  4096 2011-06-09 21:17 Pt.2011.R5.LiNE.AC3.XViD-EP1C/
drwxrwxrwx   3 administrator       administrator        4096 2011-06-09 21:55 tv/

```Nothing happens if I issue the other commands. Sorry
Its the file that owner is debian-transmission that I cannot move and thats where I get the permission denied error.
Thank you very much for your time.

---

### Post by ruffEdgz on 2011-06-10
So if you are talking about this line here:
```

drwxr-xr-x   2 debian-transmission debian-transmission  4096 2011-06-09 21:17 Pt.2011.R5.LiNE.AC3.XViD-EP1C/

```
Can you drill down to where the files are and post back the results (I don't know the full path but the example should help):
```

ll /home/administrator/shares/Pt.2011.R5.LiNE.AC3.XViD-EP1C/path/to/file

```
The directories look fine as you are able to get to the file you want but I will need an actual file that you want to move/delete using the **ll** command. Does that make sense. Also, you don't need to use the actual name of the file when you post back if you don't want. When you post back, change the name of the file from the result (I just need the information to the left of the file name really).

Cheers!

---


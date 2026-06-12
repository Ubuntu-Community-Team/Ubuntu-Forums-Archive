---
title: "Samba File server not allowing me write access on Ubuntu server 10.04?"
date: 2013-01-21
forum: Server Platforms
---

### Post by Jamie_Edwards on 2013-01-21
Hi guys.

Ok, so this is my first attempt at getting a file sharing server running, and although I'm able to mount it, I can't modify or delete or do anything to the existing test file that I created on the server itself.

So my setup is as follows, I have Ubuntu Server 10.04 LTS which has Samba FS running on it ( no problems here ) that's running on a laptop, then I have my client which is Ubuntu 12.04 LTS Desktop Ed.

Now after a few google searches I managed to get Samba running and also being able to mount the share on the desktop. But the problem that I have is that although I can see the test file, I'm unable to do anything with it, i.e. delete it from the share, modify the file, and what's more is, I can't even create a folder or file in the share either.

It comes up with "Permission Denied".

Here's a rough estimate to my smb.conf:

```


...
workgroup = USERS
...
...
security = user
...
...
[Documents]
    comment = Backup files are stored in here.
    path = /home/shares/documents
    valid users = @users
    force group = users
    create mask = 0660
    directory mask = 0771
    writeable = yes
    read only = no
    browsable = yes


```

Any idea's at all?

---

### Post by volkswagner on 2013-01-21
Please post your mount command.

Have you create system user and samba user and added him to the users group?

What are the permissions of your folder.

From the server what is output of:

```
ls -al /home/shares/documents
```

---

### Post by Jamie_Edwards on 2013-01-22
> Please post your mount command.

That is:
```

:~$ sudo mount -t cifs -o username=jamie,password=************* //***.***.*.**/documents /media/samba/

```

> Have you create system user and samba user and added him to the users group?

Umm, yeah... I think :L How can I found out what users I have?

> What are the permissions of your folder.
Although I've used Ubuntu for over a year, I've never really paid attention/understood the whole file permissions stuff :L

As for the output for the command:

```

:~$ ls -al /home/shares/documents
total 12
drwxr-xr-x 2 root users 4096 2013-01-21 19:39 .
drwxr-xr-x 3 root root  4096 2013-01-21 19:16 ..
-rw-r--r-- 1 root root    24 2013-01-21 19:40 test.txt

```

Hope that helps :)

---

### Post by volkswagner on 2013-01-22
> **Jamie_Edwards said:**
> That is:
```

:~$ sudo mount -t cifs -o username=jamie,password=************* //***.***.*.**/documents /media/samba/

```



Umm, yeah... I think :L How can I found out what users I have?


Although I've used Ubuntu for over a year, I've never really paid attention/understood the whole file permissions stuff :L

As for the output for the command:

```

:~$ ls -al /home/shares/documents
total 12
drwxr-xr-x 2 root users 4096 2013-01-21 19:39 .
drwxr-xr-x 3 root root  4096 2013-01-21 19:16 ..
-rw-r--r-- 1 root root    24 2013-01-21 19:40 test.txt

```

Hope that helps :)

Getting acquainted with [file permissions]("http://www.tuxfiles.org/linuxhelp/filepermissions.html") is fairly important for a joyful Linux experience.

The folder you are trying to write to is owned by root with group=users.
The group, users does not have write permissions.  Also your test.txt file is owned by root so you must have sudo touch, or you were logged in as root to create that file.

First you will want to set the permissions for the folder.  Without knowing your situation you can start by making yourself the owner and users as the group.  Make it writeable by users as well.

```
sudo chown jamie:users /home/shares/documents
```

The chown command can change owner and group.

```
sudo chmod 775 /home/shares/documents
```

chmod changes file and folder permissions.   The above command will make the folder writeable for the owner and group.

Hope this helps.

---

### Post by Jamie_Edwards on 2013-01-23
> **volkswagner said:**
> Getting acquainted with [file permissions]("http://www.tuxfiles.org/linuxhelp/filepermissions.html") is fairly important for a joyful Linux experience.

The folder you are trying to write to is owned by root with group=users.
The group, users does not have write permissions.  Also your test.txt file is owned by root so you must have sudo touch, or you were logged in as root to create that file.

First you will want to set the permissions for the folder.  Without knowing your situation you can start by making yourself the owner and users as the group.  Make it writeable by users as well.

```
sudo chown jamie:users /home/shares/documents
```

The chown command can change owner and group.

```
sudo chmod 775 /home/shares/documents
```

chmod changes file and folder permissions.   The above command will make the folder writeable for the owner and group.

Hope this helps.

Thank you for that as doing that has "worked". I say that because although I can add/delete/modify files on the server, I can only do so while in root nautilus on the client. I don't want to have to launch the root manager everytime I want to add something to the server. Any idea's on how that can be achieved?

note: after doing ls -al /home/shares/documents on the server, I get the same output as before but with "jamie:users" instead :)

---

### Post by volkswagner on 2013-01-23
> **Jamie_Edwards said:**
> Thank you for that as doing that has "worked". I say that because although I can add/delete/modify files on the server, I can only do so while in root nautilus on the client. I don't want to have to launch the root manager everytime I want to add something to the server. Any idea's on how that can be achieved?

note: after doing ls -al /home/shares/documents on the server, I get the same output as before but with "jamie:users" instead :)

Did you perform the chmod?  The permissions should be different.

From server please post output:
```
ls -al /home/shares/documents
```


From you client machine please post output:
```
ls -al /media/samba/
```

Can you navigate to the samba server on the client using networks?

I'm not sure what version of desktop you are running but using 12.04 open nautilus > Browse Network > Windows Network >WorkgroupName > SAMBAserverName

Using this method are you able to write?

I don't want to confuse issues here, but if you are using a Linux server and a Linux client SAMBA is not necessarily the best choice.  Unless you have MS Windows machines in the mix it may be easiest to use sftp.

From Nautilus:
> File > Connect to Server > enter server name or ip address > choose SSH as type (port 22) > leave folder as / or change to /home/shares/documents > enter username and password and connect.

Can you write using this method?

---

### Post by Jamie_Edwards on 2013-01-23
> Did you perform the chmod? The permissions should be different.
Yes I had, and when I did it, there were no errors.

> From you client machine please post output:
The output is:
```

:~$ ls -al /media/samba
total 4
drwxrwxr-x 2 1001 users    0 Jan 23 13:26 .
drwxr-xr-x 4 root root  4096 Jan 23 11:14 ..

```

> From server please post output:
```

:~$ ls -al /home/shares/documents
total 8
drwxrwxr-x 2 jamie users 4096 2013-01-23 13:26 .
drwxr-xr-x 3 jamie users 4096 2013-01-21 19:16 ..

```


I'm no expert so I could be wrong but aren't both of those supposed to match up?

---

### Post by volkswagner on 2013-01-23
On the server is jamie part of the users group?

On the server while logged in as jamie run the following command to see if jamie is part of @users.

```
groups
```

Did you try to access the server via "Nautilus > Network"?

---

### Post by Jamie_Edwards on 2013-01-23
> On the server is jamie part of the users group?
Yes, as far as I know, I followed a tutorial which gave out a command saying 
```
sudo adduser jamie users
```

Which didn't actually work until I used
```
sudo adduser jamie 
```
first.

> On the server while logged in as jamie run the following command to see if jamie is part of @users.
The output was:
```
jamie users
```

> Did you try to access the server via "Nautilus > Network"?
Now this. This has made me feel quite stupid, I did this:

Network > Windows Network > USERS > UBUNTU-SVR > Documents.

That took me a little by surprise as it is the directory on the server. I then tried making a test directory named "hello" and inside that I created a text file with some text in it.

Went down stairs to the server and low and behold the directory and file was there. So now I can modify it without being root.

Thank you so much for baring with me and helping through this as I now have control over my server!

---

### Post by volkswagner on 2013-01-23
> **Jamie_Edwards said:**
> 
...
Went down stairs to the server and low and behold the directory and file was there. So now I can modify it without being root.
...



[SSH]("https://help.ubuntu.com/10.04/serverguide/openssh-server.html") is your friend, it can save you from walking down the stairs :p


I'm still not sure why you could not write while using your mount command.  My guess is you need to mount it with user option, or the issue may lie with jamie vs. uid=1001.

---

### Post by Jamie_Edwards on 2013-01-23
> SSH is your friend, it can save you from walking down the stairs 
I did consider using OpenSSH and looked at the tut you posted but there was a warning that scared me off which said about making a mistake to the config file could lock you out of the remote server, but if anything does that apply to me? Seeming as I have access to the server? XD

> I'm still not sure why you could not write while using your mount command. My guess is you need to mount it with user option, or the issue may lie with jamie vs. uid=1001.
I'm not entirely sure with this as I'm very new when it comes to servers and networking etc XD There probably is a very simple explanation like I didn't put the right parameter into the config file, or I didn't add something to the right group etc.

---


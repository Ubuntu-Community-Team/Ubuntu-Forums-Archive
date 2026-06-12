---
title: "ftp permissions issue"
date: 2009-05-07
forum: Server Platforms
---

### Post by bcdudley on 2009-05-07
I am building a proftpd server. This machine will have no other access once it is complete other than ftp.  I am running 9.04 and followed the directions at [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588) to build it. I have 2 usernames that will access it, admin and user. I have 2 directories, download and upload. _Admin_ should have full and unlimited access to read, write, create directories, delete etc both files and directories in both download and upload. _User_ should have view and read access to download and write, create directories only to upload.

My directory permissions are currently:
drwsrwsrwt root:root **[COLOR=Lime]download[/COLOR]**
drwsrwsrwt root:root [COLOR=Lime][B]upload

[/B][COLOR=Black]My relevant proftpd.conf[/COLOR]

[/COLOR][COLOR=Red][I]<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>


<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite on
        <Limit READ RMD DELE>
        AllowAll
        </Limit>

       <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        Order Allow,Deny
        AllowUser admin
        DenyAll
        </Limit>
</Directory>

<Directory /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
        <Limit READ RMD DELE>
        Order Allow,Deny
        AllowUser admin
        DenyAll
        </Limit>

        <Limit STOR CWD MKD>
        AllowAll
        </Limit>
</Directory>

[/I][COLOR=Black]The problem I am running into is when user creates a file or directory in the upload folder, admin is unable to delete that file via ftp. The owner of said file or directory is set to user.[/COLOR]
[/COLOR][COLOR=Lime]
[COLOR=Black]Any suggestions on how to fix this?
Thank you.
[/COLOR][/COLOR]

---

### Post by bcdudley on 2009-05-11
Wow, nobody knows how to set these permissions? Did I not include enough information about what I am trying to do? Somebody please help with this. I need this server up asap and this is the last remaining obstacle.

Thank you,

---

### Post by Alekz_ on 2009-05-11
Try to change the umask...

022 = 755

Only the owner can delete with this sets!

---

### Post by bcdudley on 2009-05-11
Thank you. That fixed part of the problem with the permissions. I set the umask to 002 and I am getting rw-rw-r. I am still unable (as admin) to delete files created in the upload folder by the user account. When the files or directories are created by the user, it shows the owner as user. Is there any way to make all files and directories created with an owner of admin?

---

### Post by Alekz_ on 2009-05-11
Did you set the same group for both users (i.e.: ftpusers)?

If the "group" has r+w permission but the user admin does not belong to that group, it will never work...

---

### Post by bcdudley on 2009-05-11
I had not done that. That may be the issue, but I am not sure. I have been playing around with groups since you suggested that, but I am still getting the same results of 550, Operation not permitted. 

I created a new group called ftpusers and chowned -R both the upload and download directory with root:ftpusers. I also tried chown -R admin:ftpusers download/ and chown -R user:ftpusers upload/. I am getting the same results.

(Edit: I can go in and chown admin:ftpusers the file in upload and I am able to delete it correctly as I should. Would a cron job every minute be the answer? I know absolutely nothing about cron as of now so not sure if that is what I want or not.)

Any other suggestions?

Thank you for the help.

---

### Post by Alekz_ on 2009-05-12
I suppose you add both users to the "ftpusers" group...

If not, you have to do it!

You can use the `usermod` command for that:

```
usermod -g GROUP_ID USERNAME
```

Where:
GROUP_ID = id of ftpusers group
USERNAME = admin and user

You run the command twice!

---

### Post by bcdudley on 2009-05-12
I believe I have them added correctly. Here are the lines from my group file. Could you please confirm.

user:x:1001:ftpusers
admin:x:1002:ftpusers
ftpusers:x:1003:

I ran the command again and nothing appeared to change from what I had.

---

### Post by Alekz_ on 2009-05-12
The commando you supposed to run is:

```
usermod -g 1003 user
usermod -g 1003 admin
```

To verify if the command run succesfuly you can run the command:

```
groups user admin
```

And it must return something like:

```
user : ftpusers
admin : ftpusers
```

---

### Post by bcdudley on 2009-05-12
That is exactly what it returns. 

[COLOR=Silver]I do not understand why it will not let me delete files if both users belong to the same group and the group has rw permissions to the file/directory. Is it possible that the permissions in proftpd.com are set to only allow the owner to delete the file, not the group members?[/COLOR]

Edit: Scratch that. It is working correctly now. I am not sure which command changed it, but I just went back and checked again and it is working. I think it was the command

usermod -g GROUP_ID USERNAME

that did it, but I am not 100% sure. nothing appeared to change in the group file after that was run. I will check out everything to make sure, but it appears to be working correctly now. Thank you AlekZ for sticking with this and helping me.

---

### Post by Alekz_ on 2009-05-12
I'll give one last shot..

```
chown -R root:ftpusers /home/FTP-shared/download /home/FTP-shared/upload
chmod -R 2775 /home/FTP-shared/download /home/FTP-shared/upload
```

You have new permissions set!

Now, edit you proftpd configuration file and replace with these changes:

```
<Directory /home/FTP-shared/download/>
Umask 002
AllowOverwrite on

<Limit ALL>
AllowUser admin
</Limit>

<Limit READ CWD STOR>
AllowUser user
</Limit>
</Directory>

<Directory /home/FTP-shared/upload/>
Umask 002
AllowOverwrite on
<Limit ALL>
AllowGroup ftpusers
</Limit>
```

PS.: Backup you file before doing this! :)

Restart service and do some test!

---

### Post by bcdudley on 2009-05-12
Sorry, You had it on the previous post. I went back and edited it, but maybe you missed it.

Thank you for your help. It is working as it should (As I want it to) now.

---

### Post by Alekz_ on 2009-05-12
No problem! :)

If it's working, it's good! 

[]'s

---


---
title: "Question about folder and file creation"
date: 2010-02-18
forum: Server Platforms
---

### Post by rbalaa on 2010-02-18
Hello,
 
I'm not completely new to Linux, but I consider myself still a newbie. 
 
I'm trying to setup a Samba share for our work. I have it almost complete, however I can't successfully share editable files between users. 
 
The issue I'm having is that say User1 create a file test.txt, because of the 755 permissions, then User2, who has "writable" rights as per the smb.conf file, cannot edit that test.txt file.
 
Whevener I create a file with a user, its locked by that user. Is there a way I can set it that every folder/file a user creates is 777 ? I firgured that there's still security because of the "Valid users = " field in the smb.conf file.
 
Thank you.

---

### Post by Girya on 2010-02-18
> **rbalaa said:**
> Hello,
 
I'm not completely new to Linux, but I consider myself still a newbie. 
 
I'm trying to setup a Samba share for our work. I have it almost complete, however I can't successfully share editable files between users. 
 
The issue I'm having is that say User1 create a file test.txt, because of the 755 permissions, then User2, who has "writable" rights as per the smb.conf file, cannot edit that test.txt file.
 
Whevener I create a file with a user, its locked by that user.  Is there a way I can set it that every folder/file a user creates is 777 ? I firgured that there's still security because of the "Valid users = " field in the smb.conf file.
 
Thank you.

I think 755 gives the owner read (4) write (2) and execute (1) permissions
read/write permissions should be 6 so 666 would give everyone read write and delete permissions. You might want to think about setting the sticky bit that that only lets the person that owns the file delete the file.

you should be able to set the umask to what you need. I **think** you do that in .bashrc

---

### Post by rbalaa on 2010-02-18
> **Girya said:**
> I think 755 gives the owner read (4) write (2) and execute (1) permissions
read/write permissions should be 6 so 666 would give everyone read write and delete permissions. You might want to think about setting the sticky bit that that only lets the person that owns the file delete the file.
 
you should be able to set the umask to what you need. I **think** you do that in .bashrc
 
But since I want to allow all the users in my "valid users" field to be able to edit/create whatever they need in that folder, shouldn't it be 777 ? 
 
umask rings a bell, from my college days, I just want to make sure it only applies to that particular shared folder.
 
Thank you for your help.

---

### Post by Girya on 2010-02-18
> **rbalaa said:**
> But since I want to allow all the users in my "valid users" field to be able to edit/create whatever they need in that folder, shouldn't it be 777 ? 
 
umask rings a bell, from my college days, I just want to make sure it only applies to that particular shared folder.
 
Thank you for your help.

777 will let everyone read, write and execute the file. you want the bits to add up to 6 not 7 or 5 for read + write privileges. check out

```
man chmod
``` 

for a thorough explain 

off to work good luck

---

### Post by amac777 on 2010-02-18
There is a setting in the smb.conf file that allows you to specify what permissions files created through samba will have. 

```
sudo nano /etc/samba/smb.conf
```

Look for this setting and change it to whatever you want. If you want everybody to have read/write permissions, set it to 666.

```
# File creation mask is set to 0700 for security reasons. If  you
want to # create files with group=rw permissions, set next param&#8208;
eter to 0775.
create mask = 0666
```

After it is changed, restart SAMBA to have the changes take effect:

```
sudo /etc/init.d/samba restart
```

Note, this will only effect new files that are created after you make this change. The old ones will still have the old permissions. You can change those manually with the 'chmod' command.

---

### Post by rbalaa on 2010-02-18
> **amac777 said:**
> There is a setting in the smb.conf file that allows you to specify what permissions files created through samba will have. 
 
```
sudo nano /etc/samba/smb.conf
```
 
Look for this setting and change it to whatever you want. If you want everybody to have read/write permissions, set it to 666.
 
```
# File creation mask is set to 0700 for security reasons. If  you
want to # create files with group=rw permissions, set next param&#8208;
eter to 0775.
create mask = 0666
```
 
After it is changed, restart SAMBA to have the changes take effect:
 
```
sudo /etc/init.d/samba restart
```
 
Note, this will only effect new files that are created after you make this change. The old ones will still have the old permissions. You can change those manually with the 'chmod' command.
 
Do I use create mask under thye "Share section" or "global" ? I tried it yesterday under the share section with 0777 but maybe I missed something, I will try it again.
 
I was doing a bit of reading online and other options are available that seem to be related to what I'm doing. Example:
 
force create mode
force directory mode
create mask
directory mask
 
I'm not clear on what's the difference between the two "force" and "mask" and I'm wondering if that's related to what I need done.

---

### Post by amac777 on 2010-02-18
> **rbalaa said:**
> I was doing a bit of reading online and other options are available that seem to be related to what I'm doing. Example:
 
force create mode
force directory mode
create mask
directory mask
 
I'm not clear on what's the difference between the two "force" and "mask" and I'm wondering if that's related to what I need done.

Okay, so I read about those settings in the man page for smb.conf and I learned something new myself. On my system, I used the "create mask" set to 666 and it worked well to allow all SAMBA users to edit files created through samba by other users. However, after reading about "force create mode" I realized that setting should also have worked.

From my understanding:

"force create mode" indicates file permission settings that will be applied even if the original user didn't want them. So if you set this setting to 666, and the user creating the file wants to make a file only readable to themselves, they cannot because the permissions will be at least 666. So these mode bits are logically OR'ed with the desired permissions.

"create mask" indicates file permissions settings that can be controlled by the original user. So for example, if you set this setting to 700, then even if they wanted to give permissions to other users, they can't because those bits were masked out. So these mask bits are logically AND'ed with the desired permissions.

I guess that since, by default, files are at least readable by everyone, using the "create mask" works. At least it does on my end.

> Do I use create mask under thye "Share section" or "global" ? I tried it yesterday under the share section with 0777 but maybe I missed something, I will try it again. 

I have mine in the top section so I guess that's the global section. (It's not specified in the actual [Shared folder] definition at the bottom.)

Also, remember that these settings will only affect new files so you might need to do some tests like creating a file through SAMBA, and then running:

```
ls -l
```

in that directory in the terminal to see exactly what the permissions are.

---

### Post by rbalaa on 2010-02-18
> **amac777 said:**
> Okay, so I read about those settings in the man page for smb.conf and I learned something new myself. On my system, I used the "create mask" set to 666 and it worked well to allow all SAMBA users to edit files created through samba by other users. However, after reading about "force create mode" I realized that setting should also have worked.
 
From my understanding:
 
"force create mode" indicates file permission settings that will be applied even if the original user didn't want them. So if you set this setting to 666, and the user creating the file wants to make a file only readable to themselves, they cannot because the permissions will be at least 666. So these mode bits are logically OR'ed with the desired permissions.
 
"create mask" indicates file permissions settings that can be controlled by the original user. So for example, if you set this setting to 700, then even if they wanted to give permissions to other users, they can't because those bits were masked out. So these mask bits are logically AND'ed with the desired permissions.
 
I guess that since, by default, files are at least readable by everyone, using the "create mask" works. At least it does on my end.
 
 
 
I have mine in the top section so I guess that's the global section. (It's not specified in the actual [Shared folder] definition at the bottom.)
 
Also, remember that these settings will only affect new files so you might need to do some tests like creating a file through SAMBA, and then running:
 
```
ls -l
```
 
in that directory in the terminal to see exactly what the permissions are.
 
 
Great help. Thank you very much. I will test this out later and let you know.

---

### Post by amac777 on 2010-02-18
> **amac777 said:**
> I guess that since, by default, files are at least readable by everyone, using the "create mask" works. At least it does on my end.

Sorry to double post, but now that I think about it, this part of my explanation of why it works on my system doesn't make sense to me. The reason is files created by other users in SAMBA are not just readable by other users, they are also writable.... I did some more remembering of how I set this up and forgot I also have a group and the setgid bit set on the samba shared folder. So that probably explains why using the "create mask" works on my end but not on yours.

Long story short, perhaps you should try using the "force create mode" instead. Don't forget to restart samba after you change the setting and then do some tests.

---

### Post by rbalaa on 2010-02-18
> **amac777 said:**
> Sorry to double post, but now that I think about it, this part of my explanation of why it works on my system doesn't make sense to me. The reason is files created by other users in SAMBA are not just readable by other users, they are also writable.... I did some more remembering of how I set this up and forgot I also have a group and the setgid bit set on the samba shared folder. So that probably explains why using the "create mask" works on my end but not on yours.
 
Long story short, perhaps you should try using the "force create mode" instead. Don't forget to restart samba after you change the setting and then do some tests.
 
 
I was putting it in the wrong spot (Share definitions). As soon as I put it under [global] section it worked.
 
create mask = 0666
directory mask = 0666
 
Appreciate all the help. Thanks.

---

### Post by amac777 on 2010-02-18
Okay, glad it's working. I see you set the directory mask to 0666, which does not include the "execute" bit. For directories, the execute bit allows users to enter into the directory (example using 'cd' command). So if you find users are not able to enter directories created by other users, you may need to change the directory mask to 0777 to fix that.

---

### Post by rbalaa on 2010-02-18
> **amac777 said:**
> Okay, glad it's working. I see you set the directory mask to 0666, which does not include the "execute" bit. For directories, the execute bit allows users to enter into the directory (example using 'cd' command). So if you find users are not able to enter directories created by other users, you may need to change the directory mask to 0777 to fix that.
 
 
Good point. I just changed it back to 0777. I need them to be able to do what they want, but only in that folder and only the users that I allow from the "valid users =" field.
 
I think this solves it well for me. Thanks again. Now I'm thining about authentication ... :)

---


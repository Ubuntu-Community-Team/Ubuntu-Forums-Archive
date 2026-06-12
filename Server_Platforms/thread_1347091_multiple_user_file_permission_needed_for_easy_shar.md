---
title: "multiple user file permission needed for easy sharing via ssh?"
date: 2009-12-05
forum: Server Platforms
---

### Post by bcn17 on 2009-12-05
I have set up a server that I want my entire family to each be able to ssh into. They each have their own home folder that only they can access. And, I created a folder that is owned by me, but the permissions are 770 and the group the folder is owned by is the same group as my family. They can each create files. They can also delete a file made by anyone, or read a file made by anyone. However, they cannot edit a file made by anyone. I want this folder to be completely open to those in the group "family." Is there a way to make files placed in the folder by those in the group completely accessible by the group automatically. I don't want them to have to change permissions. Each file should auto save as 770. Currently they are saving as:   rw-r--r-- 
Also, I am a bit confused as to why they can delete files but not edit. Is this because the folder permissions are 770, and that's what dictates creating, deleting file, but the file  permissions do not give write access(or would it be the execute access?) which is required for editing files. 

Thanks!

---

### Post by brettg on 2009-12-05
Try;

```
chmod g+s public
```

For more information;

[http://tuxnetworks.blogspot.com/2009/12/inheriting-group-ownership-for-shared.html]("http://tuxnetworks.blogspot.com/2009/12/inheriting-group-ownership-for-shared.html")

---

### Post by bcn17 on 2009-12-08
This manages to make all of the files part of the group the directory is part of which is great, however the permission on the files are still:

-rw-r--r--

Therefore, I can't have anyone edit the other files. Now, I have the group problem fixed, how do I make the file permissions:

770 or rwxrwx--- 

Every time a file is saved? 

And thanks brettg!

---

### Post by bcn17 on 2009-12-09
I still can't find anything. I don't think it is going to have anything to do with the:

chmod u+s 
or 
chmod g+s 

commands after doing some googleing and playing with them. Possibly their is some other way to do this. I suppose maybe a script that autmatically changes file permissions as soon as they are created? Although this seems kind of "non-elegant." 

There has to be a way for people to completely share files between each other! I could create a separate 'public' user and give them all the key, but that seems to be cheating....

---

### Post by HighCommander540 on 2009-12-09
Hey, so you need to change is each users default usergroup to your family group.

---

### Post by bcn17 on 2009-12-09
> **HighCommander540 said:**
> Hey, so you need to change is each users default usergroup to your family group.


I have tried this, they still are currently. But the files are still saved as:

-rw-r--r--

Which is only read for group, not write.

---

### Post by HighCommander540 on 2009-12-09
Oh, ok well then you need to change the default umask for each user to 775. It will make it so that all files created by the user are auto 775. Also, if they are using FTP to upload the files there is usually a setting you can add to the config file to auto 775.

If not, at the very least you can make a shell script that will change the files in each users home directory to 775.

---

### Post by bcn17 on 2009-12-13
Thanks HighCommander540! your umask idea was a bump in the correct direction. You can use umask on specific directories thankfully using it as a command rather than editing files.

So that anyone else with the problem can do what I did, here I go. 

Create users with their own group each, or all part of one group.

I have a folder /data3/fam-share/ that I want shared between different users. 

Set permissions for /data3/

```
sudo chmod -R 750 /data3/
```

This will allow the directory owner of data3 to do whatever, and allow the group that owns it to read, and execute. So, see what is in it and execute, open the folders in it, but not write, or edit files. 

Then, lets make this directories group and all subdirectories owned by the group of the users. 

```
sudo chown -R your.sudo.user.name:other.user.group.name /data3/
```

Now, lets open up the permissions for the /data2/fam-share/ directory. 

```
sudo chmod -R 770 /data3/fam-share/
```

also, make sure that fam-share is owned by other.user.group.name, using chown to fix if need be. (It depends if you made the directory before or after changing the parent directories permissions while using the -R)

At this point the other users can all create files in /data3/fam-share/ and read each others, and see files in /data3 and enter the /data3/fam-share/ folder but cannot edit the files no created by themselves in the /fam-share/ folder. 

So, lets change the umask setting for the folder /data3/fam-share/ so that when users create files the permissions are automatically -rw-rw---- or 660. 

```
umask 007 /data3/fam-share/
```

If all the users are part of the same group then your done! 

If they are not, then add them all to another group that is the same( and the owner of the fam-share directory), and to make sure that their files are saved under the group that they all share and  not their own group use the sticky bit for directories. 

```
sudo chmod g+s /data3/fam-share/
```

All done! You should have a folder that the users that are part of the group that owns the folder can edit and delete, rename, write whatever they want to, but not anything else outside of that folder, except see what's in the folder above it. Hope this helps someone.

If anyone finds errors let me know - I typed it up very quickly after figure the whole thing out, but it was from memory.

comptech.org and yolinux.com helped me out quite a bit.

EDIT: Also, as far as the users who can edit in the /data3/fam-share/ folder, everything still works fine if the permissions for the /data3/ folder are such that they do not have read permission. So you can go ahead and do the command ```
sudo chmod g-r /data3/
```

Also, when setting the SGID, with the g+s command, it will apply to all sub directories, do not use -R, it does something different that has a capital S rather than lower case s and it also affects the files.

---

### Post by HighCommander540 on 2009-12-13
Hey, thanks you actually helped me out a bit too. I didn't know that you could do umask per folder. That's awesome.

---

### Post by luddgopelle on 2010-12-29
Hello. I have tried to do this as in post #8 but it does not work for me. I have done this:
```
sudo mkdir -p /var/cache/common
sudo chown pelle:sharegroup /var/cache/common/
sudo chmod -R 770 /var/cache/common/
umask 007 /var/cache/common/
sudo chmod g+s /var/cache/common/

ls-l /var/cache/
...
drwxrws---  2 pelle     sharegroup    4096 2010-12-29 20:20 common
...

touch /var/cache/common/pellesFile
ls -l /var/cache/common/
-rw-r--r-- 1 pelle sharegroup 3 2010-12-29 20:32 pellesFile
```As you can see, the file does not have write-permission for this group, which is what I want. Have I missed something?

---


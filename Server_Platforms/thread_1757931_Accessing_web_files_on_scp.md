---
title: "Accessing web files on scp"
date: 2011-05-14
forum: Server Platforms
---

### Post by joshli on 2011-05-14
Hello.

I am on Ubuntu 10.04.2 on Amazon EC2.

I want to use the Cherokee web server and have it (and php) running under www-data then have the files also owned by www-data. I am only able to ssh and scp into my server using the user ubuntu. This means that I am unable to edit the files.

I want to be able to edit the files owned by www-data through ssh/scp.

Could you assist me in setting my server to allow me to edit the web files through scp?

Thank you very much for helping me

---

### Post by doas777 on 2011-05-14
try adding your 'ubuntu' user to the group www-data (www-data is both a group and a user).
```
sudo useradd -G www-data ubuntu
```then check the permissions on your web folder by running 
```
ls -al <path>
```we need to see what the group permissions are on that folder by default. please post back the output of the ls command and we'll see what we need to do.

---

### Post by joshli on 2011-05-14
Ok, thank you for helping me.

I tried to run this command: ```
sudo useradd -G www-data ubuntu
```
It says:
```
useradd: user 'ubuntu' already exists

```

By default, there is already a user called ubuntu in EC2.

As for the permission settings, I recently changed the user ownership to ubuntu:ubuntu. Is there any difference with having ubuntu owning the web files and server running under the ubuntu user/group compared to www-data?

```

ubuntu@hollowtree-one:/var/www/joshua.li/public_html$ ls -al
total 20
drwxr--r-- 3 ubuntu root   4096 2011-05-13 23:39 .
drwxr-xr-x 3 ubuntu root   4096 2011-05-13 23:05 ..
-r--r--r-- 1 ubuntu ubuntu   35 2011-05-13 23:40 hello.php
-rwxrwxrwx 1 ubuntu ubuntu 1740 2011-05-13 22:54 index.htm

```

Thanks. Also, as a side question, what does the command **ll** really used for. It looks almost identical to ls -al except there is an asterisk by hello.php.

---

### Post by doas777 on 2011-05-14
useradd -G is supposed to add a user to a group. since you may already be a member, the issue is likely with the permissions, as your ll shows. btw ll is just an alias for ls -alf. never looked into the difference. `you can check an alias's command with
```
alias ll
```

it looks like your permissions are pretty messed up at this point. I woudl reset them to www-data as both owner and owner-group starting with the root directory.
```
sudo chown -R www-data:www-data /var/www
```

since you are a member of the www-data group, you need to allow your group write access
```
sudo chmod -R g+rw /var/www
```

that way, you, a member of www-data can now read and write to all files.

---

### Post by joshli on 2011-05-14
Wow, thank you very much, doas777. Works like a charm. I have been at this for over a month. You have helped me solve this big problem (for me) quickly. :)

Also, I figured out why I couldn't add ubuntu to the group. Changing useradd to usermod works.

---

### Post by joshli on 2011-05-14
Wait, I still have a problem here, I thought it would work but unfortunately, I still can't edit files on the user ubuntu.

These are the permissions for my folder.

```
ubuntu@hollowtree-one:/var/www/joshua.li$ ll
total 12
drwxrwxr-x 3 www-data www-data 4096 2011-05-13 23:05 ./
drwxrwxr-x 3 www-data www-data 4096 2011-05-14 09:54 ../
drwxr-xr-x 3 www-data www-data 4096 2011-05-13 23:39 public_html/

```

Well, if I changed the permissions to 775, it would work. Would there be any security issues there?

---

### Post by doas777 on 2011-05-14
> **joshli said:**
> Wait, I still have a problem here, I thought it would work but unfortunately, I still can't edit files on the user ubuntu.

These are the permissions for my folder.

```
ubuntu@hollowtree-one:/var/www/joshua.li$ ll
total 12
drwxrwxr-x 3 www-data www-data 4096 2011-05-13 23:05 ./
drwxrwxr-x 3 www-data www-data 4096 2011-05-14 09:54 ../
drwxr-xr-x 3 www-data www-data 4096 2011-05-13 23:39 public_html/

```Well, if I changed the permissions to 775, it would work. Would there be any security issues there?

in this case, since we are using the owner and the owner group as though they were teh same, having the same permissions on them seems correct. www-data isn't a group with a lot of members. you could probably just as easily use 765 if you wanted.

getting files to automatically assume those permissions upon creation is little harder. I think this thread will set you down the right path:
[http://ubuntuforums.org/showthread.php?t=549457](http://ubuntuforums.org/showthread.php?t=549457)

as for your current public_html/, I would chmod -R them to 775 and see if that doesn't work better.

---

### Post by joshli on 2011-05-15
Ok, I can set as 775. But, the files I create while logged on are under ubuntu:ubuntu, not ubuntu:www-data. How can I fix that? Or all together, just have www-data own the files. Thanks.

---

### Post by doas777 on 2011-05-15
I think the best bet here is the SetGID file permission on the /var/www/ folder, so that all files and folders within it are created with the owner-group from their parent directory. it will also have the desirable effect of running the given file as www-data regardless of the owner-user.

sudo chmod +R 2775 /var/www/

and change the umask in your apache envars to match. 5002.

I do this with samba on occasion so that all files created by a given user are also available to everyone in their group.

---

### Post by joshli on 2011-05-21
How do I set the directory's SetGID.

I am using cherokee, not apache, so I don't have any of that envars thing.

Am I able to set the default umask for a folder.

--------------------------

Or, better yet, how do I give www-data scp access, which would be a lot simpler.

---

### Post by doas777 on 2011-05-21
Ahh, I see I made a typo in the last post. my apologies.
 you can apply setgid to the web-root with:
```
sudo chmod -R 2775 /var/www/
OR
sudo chmod -R g+s /var/www
```if Cherokee does not use /var/www/ as its root, replace the path above with the correct one.

the leading '2' is what turns on setGid. it changes the group Execute bit to s (instead of x). it is case sensitive.
after executing your permissions list should look like:
```
drwxrwsr-x ubuntu:www-data .
```

---


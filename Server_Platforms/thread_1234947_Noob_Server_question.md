---
title: "Noob Server question"
date: 2009-08-08
forum: Server Platforms
---

### Post by accol on 2009-08-08
Hello everyone!

I'm trying to add a user to my ubuntu computer and I want to give the user access only to my music folder (so when they log into the server they start at this folder and cannot go 'back' and see other files/etc).

I've tried this command but its not working for me:

sudo useradd -d /home/mycomp/Music <newuser>

The user gets made, but when I log in as the new user I pretty much begin at the root directory.

Thanks in advance!

---

### Post by cosine352 on 2009-08-08
you can use this 
[http://www.gnu.org/software/gnump3d/](http://www.gnu.org/software/gnump3d/) 

I will ay this will be perfect for your case.

---

### Post by accol on 2009-08-08
Thanks but the location is not just for media files, I just want to know how to set a users root directory

---

### Post by cosine352 on 2009-08-08
create a regular user.
you can then just chnage the permission for all other folders in your home directory and share the Music directory.

> chmod 700 Directory_name
This will give the full permission to you and nobody else can access the Directory.

you can use this calculator if you want
[http://www.javascriptkit.com/script/script2/chmodcal.shtml](http://www.javascriptkit.com/script/script2/chmodcal.shtml)

---

### Post by scorp123 on 2009-08-08
> **accol said:**
>  The user gets made, but when I log in as the new user I pretty much begin at the root directory.  Because that user is not the owner of the directory that is supposed to be his "home" directory.

It would be better if you followed the other suggestions given to you.

Create a regular user in his own home directory. Then you can use commands such as "ln -s" to create a symlink between your directory and their's.

Example:

```
ln -s /home/myusername/Music/FreeMusic /home/mywife/Music/FreeMusic
```

The "FreeMusic" folder should have permissions set to something useful, e.g. ```
chmod 755 /home/myusername/Music/FreeMusic
```

Now, when user "mywife" logs in, they will see a folder called "FreeMusic" in their directory; but that directory is in fact a link back to my own folder of the same name, so the same files don't occupy disk space twice.

---


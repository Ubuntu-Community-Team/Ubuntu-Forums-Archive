---
title: "Consistently having to CHOWN/CHMOD"
date: 2020-08-18
forum: Server Platforms
---

### Post by Dev'olution on 2020-08-18
Hi guys,

So I've just set up my server with a LAMP stack, however, I'm forced to chown every file once I upload it using the following command as despite the -R command, it still comes up as not being owned by www-data.

```
sudo chown www-data -R /var/www
```

I also have the same issue with my samba share, where I am forced to chown to my own account every time I copy files accross.

Does anyone know why this keeps occuring?

---

### Post by slickymaster on 2020-08-18
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2020-08-18
When you copy a file as userA then the owner of that file by default would be userA. So if you want another user to be the owner you either have to copy the file using that username or change ownership/permissions later.

For the group ownership there is something called the sticky bit. It is set with chmod g+s and can be used with -R for recursive effect. If you have this configured the group ownership of any created file should be as the group ownership of the folder where you are creating the file. That could help you little if you set up necessary group ownership and basically can ignore if the user ownership is not identical.

---

### Post by TheFu on 2020-08-18
darkod is mostly correct, except the "sticky bit" isn't the correct term for the "set-group-id" bit, setgid.  Just be aware that it is commonly called the wrong thing, so when someone is talking "sticky bit", they could mean either the real sticky bit or the setgid bit.  It will only work when the userids copy files into a directory - moving a file doesn't do it. There's something about _creating a new file in the location_ that mv doesn't do.

From the chmod manpage:
```
SETUID AND **SETGID BITS**
       chmod clears the set-group-ID bit of a regular file if the  file's
       group  ID  does  not match the user's effective group ID or one of
       the user's supplementary group IDs, unless the user has  appropri&#8208;
       ate privileges.  Additional restrictions may cause the set-user-ID
       and set-group-ID bits of MODE or RFILE to be ignored.  This behav&#8208;
       ior  depends  on  the  policy  and functionality of the underlying
       chmod system call.  When in doubt,  check  the  underlying  system
       behavior.

       chmod  preserves  a  directory's set-user-ID and set-group-ID bits
       unless you explicitly specify otherwise.  You can set or clear the
       bits  with  symbolic  modes like u+s and g-s, and you can set (but
       not clear) the bits with a numeric mode.
...
RESTRICTED DELETION FLAG OR **STICKY BIT**
       The restricted deletion flag or sticky bit is a single bit,  whose
       interpretation depends on the file type.  For directories, it pre&#8208;
       vents unprivileged users from removing or renaming a file  in  the
       directory  unless  they  own  the  file  or the directory; this is
       called the restricted deletion flag for the directory, and is com&#8208;
       monly  found on world-writable directories like /tmp.  For regular
       files on some older systems, the  bit  saves  the  program's  text
       image  on  the  swap device so it will load more quickly when run;
       this is called the **sticky bit**.
```
The sticky bit DOES make since in our heads for the setgid bit, since it will keep the same group, but that isn't really what "sticky" means.  The /tmp/ directory has the "**sticky bit**" set - it shows as a **+t** at the end of a long listing - **ls -al**.
```
/tmp$ ll
total 72
drwxrwxrw**[COLOR="#FF0000"]t[/COLOR]**  9 root root 36864 Aug 18 10:17 ./
drwxr-xr-x 26 root root  4096 Aug 15 08:10 ../

```

The **setgid** bit is seen as an "s" where the "x" for group is usually seen.
```
$ ll
total 100
drwxrw**[COLOR="#FF0000"]s[/COLOR]**r-x  56 tf   plex  4096 Aug 14 19:10 T3/
```

On directories, the setgid bit means this.  On a program, it means the program runs with an effective GID of that group, if possible.  Running processes always have an effective uid/gid which controls access to other files on the system and which userid/groupid any output uses.  Linux, like all Unix-like systems, is multi-user from start to finish. It is at the core of the OS, how processes run and file permissions are how access it granted/prevented, based on the current userid/groupid.  It is really quite elegant and simple, once understood, with just a few exceptions and subtle corner cases deep in the kernel.

---

### Post by LHammonds on 2020-08-18
For websites, I use the group sticky for stuff to just work immediately.  However, everything on my websites are "known" permission sets and I have a bash script that goes through and resets all the permissions so that no matter what was done by end-users, root users, copy vs move, etc., the ownership and permissions will get reset to how they should be.  This script is set to run in crontab.  It is a little bit different for every website but for the most-part it is the same.

I can post a sample if you like.

LHammonds

---

### Post by Dev'olution on 2020-08-19
Ok, so I'm a bit confused.

In the past, I'd just install LAMP, then vsftpd.

From there, after I'd chown'd the directory **OR** Chmod'd to 766/644, I'd be able to consistently post things up with the recursive -R command.

I guess the question I have is - how do I get this to happen again?

---

### Post by TheFu on 2020-08-19
I haven't seen the behavior you describe.  Perhaps the web-app you run is doing it?
Would be helpful to see the permissions when the problem happens and see the exact commands used to copy files into the web-root area.  More facts, less attempted descriptions.  Please.

BTW, 19.04 has been out-of-support since January. Which release are you running?

---

### Post by LHammonds on 2020-08-19
> **Dev'olution said:**
> I'm forced to chown every file once I upload it
Direct upload accounts (outside the web application) can be done with an account that is in the www-data group.  Files uploaded by that account will have the username attached to the file but will have the group permission set that matches the web server's group permission...thus allowing the web app to immediately access the uploaded files.  Or, you set the group sticky bit so that no matter who copies/moves files into the web folder, the group is changed to the web server's group.

> **Dev'olution said:**
> after I'd chown'd the directory **OR** Chmod'd to 766/644, I'd be able to consistently post things up with the recursive -R command.
Now you are confusing me.  In your 1st post, you said your issue is having to correct ownership after uploading.  In your last post, you said things worked by uploading and then changing ownership.  Sounds like the exact same process unless I misunderstand what you are saying (entirely possible).

LHammonds

---


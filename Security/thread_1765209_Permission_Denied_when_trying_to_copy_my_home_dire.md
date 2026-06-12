---
title: "Permission Denied when trying to copy my home directory"
date: 2011-05-22
forum: Security
---

### Post by ClientAlive on 2011-05-22
Running Ubuntu 10.04

I logged into (sudo?) (root?) using:

```
 sudo -s 
```

and then entering my password.

I navigated into the home folder and viewed the long listing of it's contents using:

```

root@host:~# cd /home; ls -l
total 4
drwxr-xr-x 65 uname uname 4096 2011-05-22 17:14 uname

```

I attempted to copy the contents of my home directory named "uname" into a folder on my external usb drive which is located at < /media/Lacie/Backup >

So I'm in my home directory

```
 above 
```

and I run:

```

cp -R uname /media/Lacie/Backup

```

And I got the following response:

```

root@host:/home# cp -R shine /media/Lacie/Backup
cp: cannot stat `uname/.gvfs': Permission denied

```

I was logged in as root. Why would it not allow me to copy the directory?

Any ideas on what I'm doing wrong here and how I can get this done?

Thanks in advance

:confused:

---

### Post by sanderd17 on 2011-05-22
first: copying everything as root will mess up your permissions. You will not be able to put it back in original state. There is some flag you could use with the cp command to keep the owner and permissions, but you should look in the help for it. Anyway, it is better to use a backuptool like Deja-dup.

second: It is possible for a file to have rights like 000. That means nobody can write it, even not the owner. But, the owner and root can always change the rights. It's an extra layer of security, not against attacks, but against the stupidity of the user. Check out the permissions with

```

ls -l blablabla/shine.gvfs

```

and change it with

```

chmod a+x blablabla/shine.gvfs

```

---

### Post by ClientAlive on 2011-05-22
> **sanderd17 said:**
> . . . not against attacks, but against the stupidity of the user.


LMAO

I think I can relate to that one.


> **sanderd17 said:**
> first: copying everything as root will mess up your permissions. You will not be able to put it back in original state. There is some flag you could use with the cp command to keep the owner and permissions, but you should look in the help for it. Anyway, it is better to use a backuptool like Deja-dup.

second: It is possible for a file to have rights like 000. That means nobody can write it, even not the owner. But, the owner and root can always change the rights. It's an extra layer of security, not against attacks, but against the stupidity of the user. Check out the permissions with

```

ls -l blablabla/shine.gvfs

```

and change it with

```

chmod a+x blablabla/shine.gvfs

```


Thanks. I'll look into that. Wish me luck.

:)

---

### Post by ClientAlive on 2011-05-22
ok.

So I navigate back into my home directory; and, logged in as root, I run:

```
 cp -Rpiv uname /media/Lacie/Backup 
```

It copies it over fine; but, after I look at the

```

ls -la

```

in both the original and the copy I see one important different. In the original there is one, single directory named ".." (or "dot dot"), which is owned by root, all the rest are owned by "uname". However, in the copy this is changed to "uname" (both owner and group owner) for that directory. I assume whatever else inside it that was owned by root is also now changed.

Here is what it says in the man page for the -p option with the cp command:

> 
 **-p     same as --preserve=mode,ownership,timestamps**

       --preserve[=ATTR_LIST]
              preserve the specified attributes (default: mode,ownership,time&#8208;
              stamps),  if  possible  additional  attributes:  context, links,
              xattr, all



I would have thought that using that -p option as one of my optoins would have caused the ownerships to stay the same. The only thing I can think of is maybe bash reads these options in a certain order and if I don't list them in the right order they don't get done correctly?

What's going on with this?

---

### Post by Dave_L on 2011-05-23
I normally use the -a (archive) when copying files, whether as root or another user. That preserves permissions and dates.

```
$ cp -a from-path to-path
```

It's normal to get an error when attempting to copy the ~/.gvfs directory. I think it's safe to ignore the error. Or you can use rsync instead of cp, and use the parameter to exclude .gvfs.

---

### Post by ClientAlive on 2011-05-23
> **Dave_L said:**
> I normally use the -a (archive) when copying files, whether as root or another user. That preserves permissions and dates.

```
$ cp -a from-path to-path
```

It's normal to get an error when attempting to copy the ~/.gvfs directory. I think it's safe to ignore the error. Or you can use rsync instead of cp, and use the parameter to exclude .gvfs.


Right on. Just trying to get more comfortable using he command line - doing stuff. I was just reading about rsync. From what I read I thought it was more to do with incremental backups. Maybe I just didn't catch all of what they were talking about. Havta look at it again I guess.

Thanks

---


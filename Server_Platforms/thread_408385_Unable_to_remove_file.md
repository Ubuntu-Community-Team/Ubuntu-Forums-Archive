---
title: "Unable to remove file"
date: 2007-04-13
forum: Server Platforms
---

### Post by Phalanx747 on 2007-04-13
I have a SSH account that I can use (probably not on Ubuntu though). I can login just fine, but I'm seemingly unable to remove a single individual file. I have no problem removing other files, so the problem seems to be specific to this individual file.

The result of "ls -Al":

> total 320800
-rwxrwxrwx   1 MyUserName  MyGroupName  164153519 May 23  2006 install.bin*


Usernames and groupnames have been changed to protect the innocent, but the username is in fact my username. Also, the security rights seem to indicate that *everyone* (and not just me) should be able to remove the file.

Please note the asterix after the filename. I don't know what this means. I've tried to find out, but was unable to find it anywhere (even in the man page of ls). When I attempt to delete the file I get this:

Results of "rm install.bin":

> rm: remove install.bin (yes/no)? yes
rm: install.bin not removed: Permission denied

Results of "rm -f install.bin" are exactly the same. Any ideas to delete this file?

---

### Post by Aberrix on 2007-04-13
try ```
sudo rm
```

the '*' means its executable. (iirc)

---

### Post by ViRMiN on 2007-04-13
To view the file attributes do:

```
lsattr install.bin
```Sounds like it's immutable, if it is try this to remove the immutable attribute:

```
chattr-i install.bin
```Now try deleting it:

```
rm install.bin
```

---

### Post by ViRMiN on 2007-04-13
Here's how an immutable file looks by the way:

```
root:~# lsattr test
----i------------- test
```

---

### Post by ViRMiN on 2007-04-13
Could be worth checking the file ACL's too:

```
getfacl install.bin
```

(this depends on the commands getfacl/setfacl being present)

---

### Post by Phalanx747 on 2007-04-13
> **Aberrix said:**
> try ```
sudo rm
```

the '*' means its executable. (iirc)
I would try to sudo it, but I'm just a measly user on the system and don't have those kinds of rights.

---

### Post by Phalanx747 on 2007-04-13
> **ViRMiN said:**
> To view the file attributes do:

```
lsattr install.bin
```Sounds like it's immutable, if it is try this to remove the immutable attribute:

```
chattr-i install.bin
```Now try deleting it:

```
rm install.bin
```
Neither chattr-i or lsattr works on this account ("Command not found"). Like I said, it isn't necesarily an Ubuntu server. Is there any way to figure out what kind of system it is?

---

### Post by ViRMiN on 2007-04-13
What does the file do?  Your sysadmin must be protecting it for you for a reason?

---

### Post by Phalanx747 on 2007-04-13
> **ViRMiN said:**
> Could be worth checking the file ACL's too:

```
getfacl install.bin
```

(this depends on the commands getfacl/setfacl being present)
This worked:

> # file: install.bin
# owner: MyUserName
# group: MyGroupName
user::rwx
group::rwx              #effective:rwx
mask:rwx
other:rwx


---

### Post by ViRMiN on 2007-04-13
Sorry, there was a typo; should have read:

```
chattr -i install.bin
```

---

### Post by ViRMiN on 2007-04-13
For some system info try:

```
uname -a
```

or:

```
cat /etc/issue
```

---

### Post by ViRMiN on 2007-04-13
Those rights you got with getfacl are just showing the normal rights through the 777 perms and the owner and group; i.e there are no extended ACL's being used.  Have another try with the file attributes (lsattr/chattr).

---

### Post by Phalanx747 on 2007-04-13
> **ViRMiN said:**
> What does the file do?  Your sysadmin must be protecting it for you for a reason?
Well, at the time my account was mounted through Windows (as a network drive) and I tried to copy a file unto it. It was a while ago now, but if I recall correctly Windows crashed during the file transfer, leaving the incompleted install.bin on my account. Could the file still be locked or something, because the transfer wasn't completed neatly?

---

### Post by Phalanx747 on 2007-04-13
Neither chattr or lsattr worked. "uname -a" returned as follows:

> SunOS solost 5.9 Generic_117171-05 sun4u sparc SUNW,Sun-Fire-V210

They should be running Ubuntu instead :)

---

### Post by ViRMiN on 2007-04-13
Ah, Solaris 9!

---

### Post by Phalanx747 on 2007-04-13
> **ViRMiN said:**
> Ah, Solaris 9!
Does that help? Any other thoughts on how to rid my account of this nuisance?

---

### Post by Phalanx747 on 2007-04-18
Well, I found out what the problem was. After some searching I managed to get a hold of the sysadmin. Apparently, deleting a file doesn't require write permissions on the file (at all), but rather write permissions on the directory itself. Now, from a technical perspective this kinda makes sense; after all, removing a file will require you to change the directory structure. Still, I think it's odd that you can actually remove a file that you have no write permissions on.

Hope this tidbit of info helps someone else!

---


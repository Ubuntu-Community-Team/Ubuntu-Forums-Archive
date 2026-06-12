---
title: "CLI - Command to change all 777 privileges to 755"
date: 2009-10-20
forum: Server Platforms
---

### Post by Oceanwatcher on 2009-10-20
I am looking for a command that can change all instances of files and folders with 777 to 755.

I have a server with several things installed and have had to use 777 on a number of files and folders. But after installing suexec and suphp, this is now unnecessary, even unwanted, so I have to change all to 755.

This does not mean I want to change all files and folders to 755. Only those that has 777 privileges... It has to change on subfolders as well as far down as they go.

Any good suggestions for command to run?

---

### Post by scorp123 on 2009-10-20
```
find /path/to/search -perm 777 -print
```

Feel free to consult the manual:
```
man find
```

Once you're sure that the list of files that you got back from above command is what you really really really want to change (e.g. no essential system files got listed !!) you can trigger a slight variation of the above command to do all those changes automatically for you.

```
find /path/to/search -perm 777 -print -exec chmod 755 {} \;
```

---

### Post by Oceanwatcher on 2009-10-20
Fantastic! I knew there was someone out there that knew this!

*Off to fix all* :-)

Thank you very much!!

---

### Post by scorp123 on 2009-10-20
I just found a typo in my posting. I corrected it now.

---

### Post by tr333 on 2009-10-20
If you only wanted to change folders to 755 and change files to 644 then you could run the following:
```
chmod -R u=rwX, g=rX, o=rX
```
The uppercase X character tells it to only set the execute permission on folders and not files.  It won't work for you if you have some binary files in one of the (sub)folders that need 755 for executing as they will all get converted to 644 permissions.

---

### Post by Oceanwatcher on 2009-11-16
Is there a similar command to find files and folders with anything but the logged in user/owner?

I also sometimes have problems with folders and files with the wrong owner.

---

### Post by Vegan on 2009-11-16
chmod is meant for the owner of the item having permissions changed. The su is meant to override this for other purposes.

---

### Post by Lars Noodén on 2009-11-16
> **Oceanwatcher said:**
> Is there a similar command to find files and folders with anything but the logged in user/owner?

I also sometimes have problems with folders and files with the wrong owner.

One way to find the files that *don't* belong to a specific user or group is to use the utility [find](http://linux.die.net/man/1/find)

find /var/www/ ! -user oceanwatcher -print;
find /home/oceanwatcher/ ! -group oceanwatcher -print;

---

### Post by Oceanwatcher on 2009-11-16
> **Vegan said:**
> chmod is meant for the owner of the item having permissions changed. The su is meant to override this for other purposes.

Thank you for answering, but I think you misread my post. I did not write anything about changing. I only wrote about finding.

I know exactly what both chmod and su is. I do not need to override anything. I need a find command that can find all files and folders that is not owned by a specified user. What I will do about it later is a totally different case.

Sorry if my post was that unclear. I will try to do better in the future :-)

---

### Post by Oceanwatcher on 2009-11-16
> **Lars Noodén said:**
> 
find /var/www/ ! -user oceanwatcher -print;
find /home/oceanwatcher/ ! -group oceanwatcher -print;

Thanks! Worked perfect!

---

### Post by Lars Noodén on 2009-11-17
> **Oceanwatcher said:**
> Thanks! Worked perfect!

There are other tricks on that theme:

```

find /var/www/ ! -user oceanwatcher -exec ls -lh {} \;

```

---


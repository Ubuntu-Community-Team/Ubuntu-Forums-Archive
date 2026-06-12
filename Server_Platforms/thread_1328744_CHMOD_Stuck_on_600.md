---
title: "CHMOD Stuck on 600"
date: 2009-11-16
forum: Server Platforms
---

### Post by Netlink on 2009-11-16
I have a server with two hard Drives. The second hard drive 1TB with 2 partitions has nothing on it. I have setup an FTP server and I am testing a single user now accessing a Dir on the second Empty drive. I want the user to be able to read/write to a specified Directory on my second hard drive which is mounted at /media/sdba1

Here is what I have accomplished so far. 
User can access the directory
User can upload to directory
User can create new directories within that single dir they have access to.

One last step and I would be done but that is where I am stuck
User cannot CHMOD any new directories they create or any files they upload.

Tried CHMODing to  777, 644 etc it always just reverts back to 600. Basically the server is not letting this user change any permissions

I have a script that will be using this user ID and it has to CHMOD files and that is why I need this last step to work. any ideas?

---

### Post by Netlink on 2009-11-18
I even tried this on Localhost but still unable to CHMOD

---

### Post by lvlint67 on 2009-11-18
grab a root shell:
chown [username] [directory]
then try the chmod. if it doesn't work I don't know what the problem is but it sounds like something somewhere is enforcing the 644

---

### Post by Netlink on 2009-11-18
The user only exists in ftp so if I try above with that affected 'username" i get invalid user. I installed GUI, went into the second Hard Drive, right Clicked on the Folder I am the "user" is trying to access and pretty much gave everyone includng Owner, Groups and Others create and Delete files permissions. Still did not make any difference. 
 
I see a third option under there where it says "File Access" I see 3 hyphens meaning (---) not sure what kind of permissions that is. 
 
Anyone knows?
 
I tried changing it to "read aand Write" but when I apply changes it just reverts back to the three ---

---

### Post by Vegan on 2009-11-18
Can you post the results of a terminal Window

```
ls -l
```

and post it here

---

### Post by Netlink on 2009-11-19
Sorry for the delay in posting results. 
I decided to go a different route. Installed ehcp and did this instead. 
[http://ehcp.net/?q=node/571](http://ehcp.net/?q=node/571)

Thought I would pots it for the community
Thanks guys

---


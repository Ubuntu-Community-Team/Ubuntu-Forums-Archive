---
title: "User accounts"
date: 2010-12-09
forum: Server Platforms
---

### Post by KayakJim on 2010-12-09
As part of my backup process I include /etc/passwd and /etc/group so that I can restore user accounts in the case of a server failure.

While a failure has never happened, I was wondering what would actually be involved if I had to do a restore. Is it as simple as copying those 2 files into /etc or would I need to view those files and execute adduser for each of the user accounts?

In addition, does adduser do anything aside from adding the appropriate entries to /etc/passwd and /etc/group and creating the home directory?

---

### Post by 3L33T on 2010-12-09
> **KayakJim said:**
> 

While a failure has never happened, I was wondering what would actually be involved if I had to do a restore. Is it as simple as copying those 2 files into /etc


Noooooo!  Doing so will overwrite existing system-level accounts 
(accountid < 500) and existing system-level groups!

Also, add /etc/shadow in your backups.

> 
 or would I need to view those files and execute adduser for each of the user accounts?



Use a script...

```

#!/bin/bash
#Migrate user accounts to new linux box
IFS=":"

cat <passwd file> | while read line

  do
     set $line
     useradd -c $5 -p $2 -s /bin/bash -d /home/$1 -m $1 -n
  done



```


> 
In addition, does adduser do anything aside from adding the appropriate entries to /etc/passwd and /etc/group and creating the home directory?

The script above will do what you've mentioned...

Lastly, edit the /etc/shadow copy and remove system-level accounts.  Append the resulting file to the new /etc/shadown on the new linux machine.

---

### Post by KayakJim on 2010-12-09
Thank you for the response and great information 3L33T.

I'm planning to start learning BASH scripting this weekend but haven't gotten there yet. In the script you provided, can it be used as is or do I need to replace <passwd file> with '/etc/passwd' or something else?

Thank you again for the help. :)

---

### Post by 3L33T on 2010-12-09
> **KayakJim said:**
> In the script you provided, can it be used as is or do I need to replace <passwd file> with '/etc/passwd' or something else?



Replease the <passwd file> with the path of your edited "passwd" file.  So, if your passwd file is in /tmp/, then you would put "/tmp/passwd" in the path.

---

### Post by KayakJim on 2010-12-10
Thank you again for the help and clarification!  :)

---


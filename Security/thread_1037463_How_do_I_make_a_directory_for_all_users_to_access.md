---
title: "How do I make a directory for all users to access?"
date: 2009-01-11
forum: Security
---

### Post by ishkabibble on 2009-01-11
I want to have a place to store all our household files.  I thought I'd done this by creating a new user and making all the permissions on its documents folder "create and delete files" but now I get an error message that says the home directory must be private to that user.  
- What am I doing wrong here?  
- How do I set up this "all users" directory for common files?

---

### Post by adamlau on 2009-01-11
Here is an easy way:

1. Create a directory at /
2. Set 777 permissions on the directory

---

### Post by albinootje on 2009-01-11
> **ishkabibble said:**
> I want to have a place to store all our household files.  I thought I'd done this by creating a new user and making all the permissions on its documents folder "create and delete files" but now I get an error message that says the home directory must be private to that user.  


From which application came that error ?

Likes someone else already posted, you can do this for example :
```

sudo mkdir /data
sudo chmod 1777 /data

```

I wonder whether you want all users to be able to create, edit and delete all the files and directories inside that main directory (/data in the example).
Because chmod 777 and chmod 1777 is not enough for that goal.
You might need to put all users in one group and use chmod g+s on the /data directory so that group permissions are inherited, and even then the default umask creates files with 644 permissions, which is not practical for this...

---


---
title: "could not chdir to home directory error message"
date: 2011-12-21
forum: Server Platforms
---

### Post by herbert tamayo on 2011-12-21
Hi, I'm working with ubuntu server 11.04, I'm using ssh to log in it, I've created another user account in the server, but when I try to use this:

```

ssh user@server

```

i got this error:
```

could not chdir to home directory 

```

Also my prompt is not using bash.

I've tried to create the directory /home/user but still have the problem

so my questions are:
1. how can i fix this problem and get the user's home directory and the bashrc prompt for every new user?

2. i need to create more user's account in the server, but i need that the first time that they log on -using ssh of course-they can change their passwords, how can this be done in ubuntu?

best regards

---

### Post by surfer on 2011-12-21
how did you create the user? normally if you create a user (using adduser or a graphical frontend to that), it gets a home directory. i'm just wondering why you had to create it yourself.

what then is ownership/permsissions of this directory? what is the output of
```
$ ls -l /home/user
```?

---

### Post by surfer on 2011-12-21
oh and:

2. once login works, any user can change his/her password with
```
$ passwd
```

---


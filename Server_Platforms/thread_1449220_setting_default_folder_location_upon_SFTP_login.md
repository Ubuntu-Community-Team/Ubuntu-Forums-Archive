---
title: "setting default folder location upon SFTP login"
date: 2010-04-07
forum: Server Platforms
---

### Post by KnottyMars on 2010-04-07
Hello, 

Ive done some searching on Google and these forums, but I cant find where to set this up. 

So i have a fully functional Ubuntu server 8.04 with virtual hosting setup in Apache2 so that I can serve several domains. The server itself runs great, but Ive setup users that are specific to their domains, so:
domain1 = user1
domain2 = user2
etc... 

Currently when I login via SFTP I was having trouble until I created a home folder for the user, so it defaults to /home/user1 which is normal, but I want the default location to be: 
/var/www/[path to specific domain]

where can i change this default path? 

thanks for your help.

---

### Post by cdenley on 2010-04-07
Why not change their home directory to /var/www/[path to specific domain]? As far as I know, the closest thing to a default initial directory is their home directory, or possibly a ChrootDirectory.
```

man sshd_config

```

---

### Post by KnottyMars on 2010-04-08
> **cdenley said:**
> Why not change their home directory to /var/www/[path to specific domain]? As far as I know, the closest thing to a default initial directory is their home directory, or possibly a ChrootDirectory.
```

man sshd_config

```

Thanks for the info, 

yea, that is exactly what I want to do, since I have several users, this would be set in the users profile info, right? 

How would I edit that? 

I know how to add a user and delete one, but how would i edit an existing users home dir? :confused:

---

### Post by cdenley on 2010-04-08
```

sudo usermod -d /var/www/[path to specific domain] username

```

---

### Post by KnottyMars on 2010-04-08
> **cdenley said:**
> ```

sudo usermod -d /var/www/[path to specific domain] username

```

Thanks so much, new to linux and learning bit by bit. 

I really appreciate the help!!

---


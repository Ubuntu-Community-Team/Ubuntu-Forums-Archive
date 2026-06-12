---
title: "How to login as the user I create an execue a program under it?"
date: 2009-09-05
forum: Security
---

### Post by legolas_w on 2009-09-05
Hi
Thank you for reading my post.
I created a user using 

```
sudo useradd sec -p secpass
```

Now I want to do the following with this user:

- create a directory like /opt/sec and give full permission about that directory to this user.
- copy some files and an executable script into that directory an only allow sec to have access to this directory and also have the permission to execute the script file.
- prevent any user from accessing this directory (except root user)

To accomplish the task I did the following items:
```

sudo mkdir /opt/sec
sudo chown sec /opt/sec

```

And now I am lost and I do not know how to perform other items.

I tried to login as the newly created user and I get an error like:

```
No utmp entry. You must exec "login" from the lowest level "sh"
```

I searched the forum and I find a page containing some information about this problem. the solution was to use

```
sudo su username
```

But that code let the user to have all access that root user  has (doesn't it?) while I want the user to login under its own name and has no permission except what I gave him.

Thanks.

---

### Post by Old_Grey_Wolf on 2009-09-05
**[SIZE="3"]Edit: This doesn't work with Ubuntu for some reason so ignore it[/SIZE]**.

Try these commands
```

> /etc/utmp
> /etc/utmpx
> /etc/wtmp
> /etc/wtmpx

```
with sudo/root privilege.

Then reboot.

---

### Post by Bachstelze on 2009-09-05
> **legolas_w said:**
> 
But that code let the user to have all access that root user  has (doesn't it?)

Of course it doesn't... What would the point of switching to another user be if it gave this user root privileges?

---

### Post by legolas_w on 2009-09-05
> **HymnToLife said:**
> Of course it doesn't... What would the point of switching to another user be if it gave this user root privileges?

Hi
Thank you for replying.

I though that using sudo su username somehow fake the root privileges for it. I get to this idea because when we use sudo.... we are faking the root privileges.

Thanks

---

### Post by legolas_w on 2009-09-05
Can you please also help me with my other questions which I included in the first post? I mean:

> 
- create a directory like /opt/sec and give full permission about that directory to this user.
- copy some files and an executable script into that directory an only allow sec to have access to this directory and also have the permission to execute the script file.
- prevent any user from accessing this directory (except root user)


Thank you.

---

### Post by gombadi on 2009-09-05
> 
- create a directory like /opt/sec and give full permission about that directory to this user.
- prevent any user from accessing this directory (except root user) 

```

sudo mkdir /opt/sec
sudo chown sec /opt/sec
sudo chmod 0700 /opt/sec

```

> 
- copy some files and an executable script into that directory an only allow sec to have access to this directory and also have the permission to execute the script file.

```


Login as the sec user
cp /location/of/files/* /opt/sec
chmod 0755 /opt/sec/scriptyouwant2run.sh

```

---


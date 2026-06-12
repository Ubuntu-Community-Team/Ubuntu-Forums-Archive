---
title: "Multi. servers with same account"
date: 2012-09-25
forum: Server Platforms
---

### Post by jdm2 on 2012-09-25
Hey, I'm not sure if this is the best place for this post, but since it is server related I figured I would ask here.

I'm having to come up with a script that will let me create a user on a linux server, but this script will create a user on two servers at the same time.

For example:

If I have a user name tom I would go through and fill out the username, password, etc., but  it will create this user on server1 and server2.

How would I go about doing this?

I don't want to have to go through and fill out all of the information twice.

Thanks for the help in advance.

Sincerely yours;

jdm2

---

### Post by sandyd on 2012-09-25
Ive never tested this, but use grep to get the username's line from /etc/shadow.

Then, append it to the other server's /etc/shadow.

Something like

```

PASSWORD=$(cat /etc/shadow | grep [username])
ssh root@[host/ip] echo $PASSWORD >> /etc/shadow

```
If you don't want to use root, you just have to have a user that can write to /etc/shadow

---

### Post by lukeiamyourfather on 2012-09-25
Do you mean network authentication? It won't create the accounts on multiple machines but on one centralized machine to which every other machine can look to.

[https://help.ubuntu.com/12.04/serverguide/network-authentication.html](https://help.ubuntu.com/12.04/serverguide/network-authentication.html)

---

### Post by Lars Noodén on 2012-09-25
You could have one machine as master and then rsync the others.  You'd need /etc/passwd, /etc/shadow, /etc/group, /etc/gshadow and /home synced.

---

### Post by jdm2 on 2012-09-27
> **Lars Noodén said:**
> You could have one machine as master and then rsync the others.  You'd need /etc/passwd, /etc/shadow, /etc/group, /etc/gshadow and /home synced.

I think that might be what I have to do.  I'm talking with the person and have to get with them to understand better, but as I understand it there are two servers s1 and s2.  s1 has accounts on it and is where the files are stored and the users can log into it, but everybody logs into s2.  s2 lets the users works with their files on s1 and treats that as there home directory, but if for some reason s2 crashes s1 will be fine (files will be safe).  So I need to be able to create an actual user on s1 with their name and a home directory and just create a user on s2 where it points to the files on s1.

Does this makes since to you?  If so what do I need to do?

Thanks for the help.  I really appreciate it.

Sincerely yours;

jdm2

---

### Post by Lars Noodén on 2012-09-27
Are the home directories NFS mounts from one server to another?  Or are there really separate home directories for the same user on both machines?  If they're editing files on either computer arbitrarily then it's a little harder, I think unison might be what would work there.  But as long as the accounts are centralized on one or the other it should be workable.

---

### Post by jdm2 on 2012-09-27
I'm not sure how it is setup.  Sorry for being vague, but I was just told to do this.  Hopefully I will have more details for you soon.  All I know is both machines are login accessible, but nobody, but a few knows that you can log into s1.  s1 stores all the files and s2 is where everybody logs into and works with the files on s1.  They did it this way so if something happened to s2 while the users were working on it s1 would be fine.  

Until I can talk to the person in charge is there a way to find out how the home directories are hooked up?

Thanks for the help.

Sincerely yours;

jdm2

---


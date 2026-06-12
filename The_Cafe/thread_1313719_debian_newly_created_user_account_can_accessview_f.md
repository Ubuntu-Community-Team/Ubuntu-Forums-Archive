---
title: "debian: newly created user account can access/view files in /home/some1 else' folder"
date: 2009-11-04
forum: The Cafe
---

### Post by hanzj on 2009-11-04
[SIZE=3]i just created a new user account on my debian eeepc running lxde. how come the new user (let's say username is: "frienda") can go to my /home/han/ account and access my files?

How can I fix this?
[/SIZE]

---

### Post by ~sHyLoCk~ on 2009-11-04
> **hanzj said:**
> [SIZE=3]i just created a new user account on my debian eeepc running lxde. how come the new user (let's say username is: "frienda") can go to my /home/han/ account and access my files?

How can I fix this?
[/SIZE]

You will need sudo or root privilege for "frienda" account. Just add "frienda" to /etc/sudoers

---

### Post by hanzj on 2009-11-04
hmmm. doing that will prevent frienda from seeing the /home/han/ folder(s)?

My solution was to go to the file manager (as root) and remove read/write privileges for "groups" and "other users"

---

### Post by snova on 2009-11-04
> **hanzj said:**
> i just created a new user account on my debian eeepc running lxde. how come the new user (let's say username is: "frienda") can go to my /home/han/ account and access my files?

Probably because the permissions on your home directory are too relaxed.

Change them to something more restrictive, such as 700.

```
chmod 700 /home/han
```

Which is read, write, and execute for yourself and nothing for anyone else.

---

### Post by snova on 2009-11-04
> **hanzj said:**
> hmmm. doing that will prevent frienda from seeing the /home/han/ folder(s)?

If you give the account sudo access, there is nowhere it cannot see.

> My solution was to go to the file manager (as root) and remove read/write privileges for "groups" and "other users"

Effectively the same thing I said previously. Though if it's your home directory, root should not be necessary.

---

### Post by cariboo on 2009-11-04
Change each user's home directory permissions to 700, this will prevent other users from accessing each others files:

```
sudo chmod -R 700 /home/<username>
```

There is a fairly long thread about the same problem in Unbuntu (Debian=Ubuntu?) :) in recurring if you are interested.

---

### Post by -grubby on 2009-11-04
> **cariboo907 said:**
> Change each user's home directory permissions to 700, this will prevent other users from accessing each others files:

```
sudo chmod -R 700 /home/<username>
```

There is a fairly long thread about the same problem in Unbuntu (Debian=Ubuntu?) :) in recurring if you are interested.

You don't want that -R option

---

### Post by ad_267 on 2009-11-04
> **-grubby said:**
> You don't want that -R option

Heh, you edited the post. I was going to say yes you want the 700. Another idea would be:
```
sudo chmod -R o-r /home/<username>
```

That way you just remove read privileges for all other users for all files and directories.

---

### Post by snova on 2009-11-04
> **ad_267 said:**
> Heh, you edited the post. I was going to say yes you want the 700. Another idea would be:
```
sudo chmod -R o-r /home/<username>
```

That way you just remove read privileges for all other users for all files and directories.

But it doesn't need to be recursive. As long as nobody can access the home directory itself, you can't access anything underneath it.

---

### Post by ad_267 on 2009-11-04
> **snova said:**
> But it doesn't need to be recursive. As long as nobody can access the home directory itself, you can't access anything underneath it.

Yeah that's what I thought too but I tested it and it's not true. If you know there's a "Pictures" directory you can cd into it and read everything in there even if the home directory itself isn't readable.

---

### Post by ~sHyLoCk~ on 2009-11-04
> **hanzj said:**
> hmmm. doing that will prevent frienda from seeing the /home/han/ folder(s)?

My solution was to go to the file manager (as root) and remove read/write privileges for "groups" and "other users"

Ah damn I was eating while typed that, multi-tasking isn't really my thing. Sorry I thought you meant you want to give "frienda" permission to access the user's /home directory, which can be done by the method I told you. I didn't read properly.

---

### Post by Exodist on 2009-11-04
The default on Lenny is that other users can view your files and access them. But they can not save or delete any data. But that easily fixable.

---

### Post by FuturePilot on 2009-11-04
> **ad_267 said:**
> Yeah that's what I thought too but I tested it and it's not true. If you know there's a "Pictures" directory you can cd into it and read everything in there even if the home directory itself isn't readable.

Doesn't work.

```
$ sudo mkdir -m 700 /tmp/test
$ sudo mkdir /tmp/test/test2
$ sudo ls -l /tmp/test
total 4
drwxr-xr-x 2 root root 4096 2009-11-04 01:49 test2
$ cd /tmp/test/test2
cd: permission denied: /tmp/test/test2
$
```

---

### Post by ad_267 on 2009-11-04
Ahh whoops. I'd removed read permissions but not execute permissions on the parent directory.

---


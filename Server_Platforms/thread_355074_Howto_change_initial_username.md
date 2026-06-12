---
title: "Howto change initial username?"
date: 2007-02-06
forum: Server Platforms
---

### Post by markymarknz on 2007-02-06
Hi everyone,

I have a reasonably simple question but am not quite sure how to go about it.
I have setup an ubuntu server and that's all fine, however after setting it up I would like to change the login name for the server.
I'm talking about changing the initial username you setup when you install the server and it has sudo rights.
I found something about using the command usrmod but just wanted to confirm with someone how to go about this as I don't want to lock myself out of the server.
Also after the name has been changed do I have to change the home folder name & permissions and sudoers list?

Thanks

Mark

---

### Post by p!=f on 2007-02-06
> **markymarknz said:**
> Hi everyone,
Also after the name has been changed do I have to change the home folder name & permissions and sudoers list?

```

sudo usermod -l bar -d /home/bar/ -m foo

```
renames the user "foo" to the user "bar" with the new directory path and moves the home directory to the new location. See usermod --help for all options. 

You may have something like this in your /etc/sudoers (Dapper default),
> 
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

and your user is probably in the admin group so you don't have to change anything.
Don't forget to rename the group too
```

sudo groupmod -n bar foo

```

---

### Post by markymarknz on 2007-02-06
> **p!=f said:**
> ```

sudo usermod -l bar -d /home/bar/ -m foo

```
renames the user "foo" to the user "bar" with the new directory path and moves the home directory to the new location. See usermod --help for all options. 

You may have something like this in your /etc/sudoers (Dapper default),

and your user is probably in the admin group so you don't have to change anything.
Don't forget to rename the group too
```

sudo groupmod -n bar foo

```

Awesome thanks for the fast reply p!=f :)

---


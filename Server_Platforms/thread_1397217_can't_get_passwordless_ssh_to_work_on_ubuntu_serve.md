---
title: "can't get passwordless ssh to work on ubuntu server"
date: 2010-02-03
forum: Server Platforms
---

### Post by nbv4 on 2010-02-03
I followed the steps here: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

It works fine, except every time I try to do something that requires authentication of the key, I have to type in the password in a prompt that looks like this:

```

$ git pull
Enter passphrase for key '/home/<user>/.ssh/id_rsa':
remote: Counting objects: 16, done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 9 (delta 7), reused 0 (delta 0)
...
```

This is very annoying. How can I have it so I don't have to enter my password each time?

On my local machine I followed the same instructions and don't have to enter the password every time...

---

### Post by mgichoga on 2010-02-03
This is indicative that you used a pass phrase when you generated the ssh key in 

> ssh-keygen -t rsa

You could try redoing the steps again, when it prompts for a pass phrase just hit enter

---

### Post by x33a on 2010-02-03
> **mgichoga said:**
> This is indicative that you used a pass phrase when you generated the ssh key in 
You could try redoing the steps again, when it prompts for a pass phrase just hit enter

that's not a very good idea.

take a look here:
[http://wiki.archlinux.org/index.php/Using_SSH_Keys#Remember_key_passphrases](http://wiki.archlinux.org/index.php/Using_SSH_Keys#Remember_key_passphrases)

---

### Post by nbv4 on 2010-02-03
> **mgichoga said:**
> This is indicative that you used a pass phrase when you generated the ssh key in 



You could try redoing the steps again, when it prompts for a pass phrase just hit enter

awesome, that did the trick, thanks

---

### Post by nbv4 on 2010-02-03
> **x33a said:**
> that's not a very good idea.

take a look here:
[http://wiki.archlinux.org/index.php/Using_SSH_Keys#Remember_key_passphrases](http://wiki.archlinux.org/index.php/Using_SSH_Keys#Remember_key_passphrases)

sweet, even better

---


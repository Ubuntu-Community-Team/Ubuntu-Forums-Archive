---
title: "I can do ssh passwordless logins using slogin, but no ssh"
date: 2011-08-11
forum: Security
---

### Post by bobdobbs on 2011-08-11
Hi. I've got an ubuntu laptop and and an ubuntu workstation.

I followed this tut:
[http://blogs.translucentcode.org/mick/archives/000230.html](http://blogs.translucentcode.org/mick/archives/000230.html)

I was then able to achieve passwordless logins from my desktop to my laptop.

I have not been able to do it the other way around. When I am on my laptop, I repeat the process... create the keypair, copy the public key to the remote host and copy it to remotes 'authorized_keys' file. However, I am still asked for a password.

So, this fails:
'ssh me@desktop'.

However, this succeeds:
'slogin -i lappyprivatekey me@desktop'

What's going on here? 

This is very frustating. There are a zillion 'simple, easy ssh passwordless login' tuts on the web. But hardly ever seem to work when I follow them on ubuntu.

---

### Post by jramshu on 2011-08-11
Is your private key in this file "~/.ssh" (without quotes of course)?

This is a good tut for ssh in Ubuntu.
[http://bodhizazen.net/Tutorials/SSH_keys](http://bodhizazen.net/Tutorials/SSH_keys)

Did you try it this way?
```
ssh -i ~/.ssh/keysname yourname@servername.com
```

EDIT: You don't want to disable password authentication until you get your keys working correctly.

EDIT2: You can set up your key with a password, I don't, just my own preference.

---

### Post by bobdobbs on 2011-08-11
Thanks... I'll go through it, and see if I can find a solution.

---

### Post by jramshu on 2011-08-11
No problem. When I set my server up it(bohdi's tuts) helped a lot. I haven't had any problems since.

---


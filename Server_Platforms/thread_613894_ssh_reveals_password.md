---
title: "ssh reveals password"
date: 2007-11-15
forum: Server Platforms
---

### Post by helgman on 2007-11-15
Not sure if this is the right place but since I'm accessing a "server" and I see the problem as security-related I post it here.

I have a few systems (Ubuntu and Debian) that I only access via SSH. This is fine but sometimes you don't want to log in, get a shell and then type in your command, so you head for the *ssh foo "ps -A"* or whatever.

I recently noticed that if you run a command as above but with the sudo-command the sudo password is displayed in plain text like this:

```
$ ssh foo "sudo gnump3d-index"
user@foo's password: 
[sudo] password for user:password-that-I-type
```

Is there anything I can do in my configuration or is this "how it works"?

Regards,
Helgman

---

### Post by doanut on 2007-11-15
Thats how it works.
I think since the release of 7.10

When you type your password nothing is displayed to screen.

---

### Post by MJN on 2007-11-16
It sounds like it was 'fixed' in sudo v1.6.9p6 (it's the same issue as runing sudo in the background) however I think this may mean your example won't work as you won't be prompted for a password (given you're not a connected terminal) hence the remote sudo will fail.
 
Mathew

---


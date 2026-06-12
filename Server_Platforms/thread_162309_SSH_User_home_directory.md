---
title: "SSH User home directory"
date: 2006-04-18
forum: Server Platforms
---

### Post by Coruba67 on 2006-04-18
Hi guys,

Was wondering if anyone knew how to change the home directory of a user from the command line....  instead of it being /home/user I would prefer it to be somewhere in the /var/html directory...

Anyhelp would be awesome.

Cheers

---

### Post by LordHunter317 on 2006-04-18
I can't possibly fathom why you want their home directory there, but use the 'chsh' command or carefully edit /etc/passwd directly.  Note you'll need to copy the contents of /etc/skel over there and set the permissions for them if you want them to have a sane environment.  

usermod may or may not be able to do it for an existing user.  I honsetly don't know, nor have I ever tried it.

---

### Post by Coruba67 on 2006-04-19
Awesome, thanks for the help!

---

### Post by MJN on 2006-04-19
> I can't possibly fathom why you want their home directory there
 
Rather than wanting to change the home directory per se, I think Coruba is more wanting the user to be dropped into /var/html when logging in via SSH as opposed to dropping into their true home directory (as per the default).
 
Mathew

---

### Post by Coruba67 on 2006-04-20
Yes thats exactly it... How do you actually do that??

---

### Post by MJN on 2006-04-20
Ah.. Well I'm afraid whilst I understand the question I don't know the answer...

Looking at the SSHD config directives there appears to be nothing to achieve what you're after so I think you'd have to go with LH's way.

Why do you want to do it? Convenience for the user? If so, could a simple symlink in your home directory to /var/html/whatever suffice?

Mathew

---

### Post by fdoving on 2006-04-20
To change the home directory use:
```

usermod -d /new/home/ username

```

Editing /etc/passwd manually is a bad thing.

- Frode

---

### Post by Coruba67 on 2006-04-20
I guess a symlink could work... but the usermod has worked well for me!

Cheers guys

---


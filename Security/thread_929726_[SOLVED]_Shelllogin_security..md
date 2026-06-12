---
title: "[SOLVED] Shell/login security."
date: 2008-09-25
forum: Security
---

### Post by Nettoyer on 2008-09-25
I tried to look but I couldn't find anything concrete.
If user 'Joe' logs in, he'll be at /home/Joe/
I'm wanting to setup permissions so that he can ONLY see his 
/home/USER/ directory and nothing else.  So if he goes to
/home/, it would deny him. Hopefully this could span (easily) across all accounts.

Also, (I know its the wrong forums, wanted to ask).  
[http://www.ubuntuforums.org](http://www.ubuntuforums.org) is a registered domain website.
What is [http://ubuntuforums.org?](http://ubuntuforums.org?)

Thanks,
Nett.

---

### Post by cdenley on 2008-09-25
> **Nettoyer said:**
> I tried to look but I couldn't find anything concrete.
If user 'Joe' logs in, he'll be at /home/Joe/
I'm wanting to setup permissions so that he can ONLY see his 
/home/USER/ directory and nothing else.  So if he goes to
/home/, it would deny him. Hopefully this could span (easily) across all accounts.

If Joe can't see anything outside of /home/Joe, then how is he supposed to run /bin/bash or /bin/sh? Maybe you can setup a chroot environment for Joe, or give him a restricted shell.

> **Nettoyer said:**
> 
Also, (I know its the wrong forums, wanted to ask).  
[http://www.ubuntuforums.org](http://www.ubuntuforums.org) is a registered domain website.
What is [http://ubuntuforums.org?](http://ubuntuforums.org?)


What?
```

cdenley@ubuntu:~$ host www.ubuntuforums.org
www.ubuntuforums.org has address 91.189.94.12
cdenley@ubuntu:~$ host ubuntuforums.org
ubuntuforums.org has address 91.189.94.12
ubuntuforums.org mail is handled by 10 mail.ubuntuforums.org.

```

---

### Post by Nettoyer on 2008-09-25
> **cdenley said:**
> If Joe can't see anything outside of /home/Joe, then how is he supposed to run /bin/bash or /bin/sh? Maybe you can setup a chroot environment for Joe, or give him a restricted shell.

Oh, I was just speaking in reference to what I could do with my default account.  Thinking that if I setup other users and they login remotely, that they could move outside their home directory. I'll look into chroot environments, thanks!

What?
```

cdenley@ubuntu:~$ host www.ubuntuforums.org
www.ubuntuforums.org has address 91.189.94.12
cdenley@ubuntu:~$ host ubuntuforums.org
ubuntuforums.org has address 91.189.94.12
ubuntuforums.org mail is handled by 10 mail.ubuntuforums.org.

```

For this, I wasn't sure if there was a difference in the two because of the www. not being there.  Guess not, thanks for this as well!

---

### Post by Oldsoldier2003 on 2008-09-25
> **Nettoyer said:**
> For this, I wasn't sure if there was a difference in the two because of the www. not being there.  Guess not, thanks for this as well!

it is very common practice to set a dns "alias" to [www.somedomaain.tld](www.somedomaain.tld) . In this case ubuntuforums.org is the same as [www.ubuntuforums.org](www.ubuntuforums.org). In some sites mail, www, and other services are handled on different servers. DNS allows the flexibility to move servers around to manage the load.

---


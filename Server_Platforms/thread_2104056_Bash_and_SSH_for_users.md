---
title: "Bash and SSH for users"
date: 2013-01-11
forum: Server Platforms
---

### Post by ductiletoaster on 2013-01-11
Ok. I have a new server that is going to be running multiple sites with apache (via Virtual hosts). I would like to setup each site to have both bash and SSH. (test will be the user from here on)

I created a new user...
useradd test
passwd test

I then set a specific location as the users $HOME
/var/www/vhosts/demo.com/ (or something like that)
made sure that both apache and the user had access to the contents within home

However when I went to ssh in to the server using this new user i noticed that the shell was just the default sh.

DISCLAIMER: This is where my suspected noobness came in...
I then changed the users shell to bash using the following cmd
usermod -s bash test

once I did this I was no longer able to get ssh access via this user.
SOOO how can I restore this users SSH access and allow it to use bash as its default shell. 

A secondary question is how can this user also be give SFTP access with out restricting the other two items (not a requirement just wondering if it fits along the same lines)

Thanks!

---

### Post by steeldriver on 2013-01-11
I'm guessing a bit here, but I think your issue may be that you didn't give the absolute path for the new shell i.e.

```
$ sudo usermod -s [COLOR=Red]/bin/[/COLOR]bash *test*
```The ssh login may be failing simply because it can't execute bash without the absolute path

---

### Post by ductiletoaster on 2013-01-11
You are a genius! So simple and I totally didn't think of it...
Problem solved!

---


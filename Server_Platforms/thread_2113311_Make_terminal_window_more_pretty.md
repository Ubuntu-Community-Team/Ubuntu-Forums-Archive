---
title: "Make terminal window more pretty"
date: 2013-02-07
forum: Server Platforms
---

### Post by greytag on 2013-02-07
Hi, 

We just ordered a new virtual server and it is splendid.
However, we don't want to use the standard user setup by our supplier and, fo course, we wand a user each.

The problem is that when I create a new user the terminal is extremely ugly. No colours and keys like tab won't work so we can't really use these users.

I have copied .profile to my new user, but it made no difference.

---

### Post by cj13579 on 2013-02-07
It sounds you might be in another type of shell. From the terminal submit

```
:~$ bash 
```

If that fixes it you can change the default shell to bash. Run the following command to get the location of the bash binary:

```
:~$ which bash
```

Once you have that (something like /bin/bash or /usr/local/bash) then you use that for the next command which changes the default login shell:

```
:~$ chsh -s /bin/bash <user>
```

You will need to enter the password for the user that you want to change the login shell for. Log out and back in again to check that is sorted.

---


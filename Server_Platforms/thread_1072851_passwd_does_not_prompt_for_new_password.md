---
title: "passwd does not prompt for new password"
date: 2009-02-17
forum: Server Platforms
---

### Post by spoffy on 2009-02-17
Hello folks,

For some reason i cannot use passwd to change user passwords-- either on my own account or another user's account (using sudo).  All it does is say "password updated successfully", but it never asks me for the old/new password!  Using sudo to change another user's account prompts for the root password, but the same thing happens there-- it says it's successful, but it doesn't prompt for the new password and nothing changes.

I can delete passwords on an account using passwd -d and log in using a blank password, but then using passwd gets the same thing.  And trying usermod -p gets no error message at all, but it doesn't change anything either.

Where do I look to start? :(

---

### Post by cariboo on 2009-02-17
Are you using:

```
sudo passwd <user>
```

to change the password?

Jim

---

### Post by spoffy on 2009-02-18
Yes, that's exactly what I'm using:

$ sudo passwd username
[sudo] password for adminaccount: *type in password*
passwd: password updated successfully

There's no pause after hitting enter on the password and the response.  The "adminaccount" is the account I made during Ubuntu installation and the password I type in is the one needed to sudo, not the one I want the "username" account to have.

---

### Post by UberGTI on 2009-02-18
I'm following this thread as I have the exact same problem.  I also noticed that if I create a new user and try to change their password using passwd that only response I receive is, passwd: password updated successfully.

---

### Post by UberGTI on 2009-02-18
I found my problem.  Not sure if it applies to you.

I uninstalled likewise-open, and passwd works as expected.  Not sure if it's a bug.  Hope this helps you.

---

### Post by spoffy on 2009-02-18
Hmm, I am running likewise-open on this machine.  So that narrows things down a bit.

In fact, searching some more brought me to this page:

[https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/302026](https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/302026)

I'm going to try installing libpam-cracklib like that thread talks about and see what happens.

---

### Post by spoffy on 2009-02-18
. . . and that fixed it.  So the problem has to do with likewise-open and pam.

---

### Post by zeki893 on 2009-04-10
I ran ```
apt-get remove likewise
``` 
this solved my problem.

---

### Post by GooglieS on 2009-07-09
So what I need to do, if i want to use likewise? passwd command still does not working in 9.04 :(

---

### Post by Ashish_net on 2011-12-17
I found a solltion for problem, and it worked perfectly for me, Everthing what we are facing is due to that cancer software PAM- Face Recognizance, So  Just use following commands sequincially and I am sure it will get solved as same probmem was being faced by me myself, and 1 friend of mine and solution worked for both us as dream world
-
To uninstall follow these commands
 

sudo pam-auth-update --package face_authentication



sudo rm /usr/share/pam-configs/face-authentication



sudo apt-get remove pam-face-authentication
[FONT=Verdana]
[/FONT]
[FONT=Verdana]---[/FONT]

[FONT=Verdana][/FONT]
[FONT=Verdana]Best of luck[/FONT]

---


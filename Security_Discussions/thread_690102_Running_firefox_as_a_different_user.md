---
title: "Running firefox as a different user"
date: 2008-02-07
forum: Security Discussions
---

### Post by gaten on 2008-02-07
I'm trying to run firefox as a different user for security reasons, and I've almost got it except for one fatal snag: I can't get sudo to run without a password. Here's what I'm trying:

I have a user **ff** setup with its own home directory, and my sudoers file looks something like this:
```
gaten   ALL=(ALL) NOPASSWD: /usr/bin/firefox
```This should allow me to run **/usr/bin/firefox** as any user without entering in a password. 

I try the following:
```
sudo -u ff -H /usr/bin/firefox
```But sudo still asks for a password. I've tried these variations to the suoders file above:

```
gaten   ALL=(ff) NOPASSWD: /usr/bin/firefox
gaten   ALL= NOPASSWD: /usr/bin/firefox
```But nothing seems to work. Any ideas? 

To recap, I'm trying to allow my user (gaten) to run /usr/bin/firefox using the command 
> sudo -u ff -H /usr/bin/firefox**without** prompting for a password (as it's in a shell script and I don't want to enter my password everytime I run firefox).

---

### Post by astrotech226 on 2008-02-07
I think your sudoers user entry is mixed up.  All of the examples you gave are giving the user "gaten" permission to run firefox.  But your command line example is trying as user "ff".

Change the sudoers line to:

ff   ALL = NOPASSWD: /usr/bin/firefox

- or -

try this as the command:

sudo -u gaten -H /usr/bin/firefox

---

### Post by gaten on 2008-02-07
```
 ff   ALL = NOPASSWD: /usr/bin/firefox
```

Sorry, forgot to mention this line is already in my sudoers file.

And I don't want to do this:
```
 sudo -u gaten -H /usr/bin/firefox
```

Because that will run the command as the user **gaten**, which is my normal user. I want to run firefox as user **ff**.

---

### Post by astrotech226 on 2008-02-08
I just set up a test and it works for me if I do this, assuming I am logged in as gaten.  Add this line to the /etc/sudoers file:

ff   ALL = NOPASSWD: /usr/bin/firefox

Run this from the command line:

$ sudo -u ff -H /usr/bin/firefox

This works for me with the exception of the of the X security.  As gaten, I need to run:

$ xhost +

---

### Post by gaten on 2008-02-08
Still doesn't work for me. Make sure you issue an ```
sudo -k
```

and try it again. the **-k** switch tells sudo to invalidate your sudo timestamp.

Also, a safer option for xhost would be
```
xhost +local:ff
```

as **xhost +** gives access to anyone from anywhere, while **xhost +local:ff** only gives local access to user **ff**. 

This is really starting to irk me, it should be so simple but it's not working. I'm wondering if I don't have some odd config somewhere.

---

### Post by astrotech226 on 2008-02-08
You are right about the "-k" switch.  When I did that, it must invalidate an older sudo session and forced the password on me.

Check this out.  I've never had to do this on Gentoo or FC, but I found a post on a SUSE board and this works for me!

gaten   ALL = (ff) NOPASSWD: /usr/bin/firefox

This says that "gaten" is allowed to run firefox with no password as user "ff".

Does this work?

---

### Post by gaten on 2008-02-08
Nope, if you look at my first post that's one of the first ones I tried (the first, I think). 

This just seems really odd, as the format for the sudoers file is such
```
user HOST=[RUNAS USER] [OPTIONS] [COMMAND]
```So logically, that should work. It just seems like the NOPASSWD option isn't being invoked. Maybe it has something to do with a paranoid PAM setting? I don't remember changing them, but I've had this desktop a while now do who knows.

---

### Post by astrotech226 on 2008-02-08
I'm at a loss.  Anything of interest in your /var/log/auth.log file?  It might detail what's causing it.

---


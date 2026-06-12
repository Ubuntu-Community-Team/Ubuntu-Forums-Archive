---
title: "Neither GPA or Seahorse works (Gutsy)"
date: 2008-03-25
forum: Security Discussions
---

### Post by spaceboy909 on 2008-03-25
When trying to create a new key (my first one), I get errors in each.

Seahorse:  "...can't communicate with gnome-keyring-daemon..."

GPA: "General Error"


Am I missing a necessary file or something?  I do have gpgv installed.

---

### Post by Dr Small on 2008-03-25
Please try to make a key via the command line to make sure everything is honky dory with GnuPG:

[http://ubuntuforums.org/showthread.php?t=680292](http://ubuntuforums.org/showthread.php?t=680292)

Dr Small

---

### Post by spaceboy909 on 2008-03-25
Ok, now I've tried from the console and am getting errors there as well.

After entering all of the basic info for my key, I get this error:

```
gpg: can't open `/home/mxx/.gnupg/random_seed': Permission denied
```Then I enter the random chars, and then another error:

```
gpg: no writable public keyring found: eof
Key generation failed: eof
gpg: note: random_seed file not updated

```

---

### Post by spaceboy909 on 2008-03-25
Ah, thanks Doc!  We posted about the same time.  Looks like I've definitely got some root issues here.

---

### Post by Dr Small on 2008-03-25
Ok, it looks like a permission problem. Let's see if we can solve this.
First off, here is the set of permissions on my .gnupg directory:
```

drsmall@darkghost:~$ ls -la | grep .gnupg
drwx---rwx   3 drsmall drsmall   4096 2008-03-10 10:01 .gnupg

```

Now, here is my permissions on my random_seed file:
```
-rw----rwx   1 drsmall drsmall   600 2008-03-24 09:43 random_seed
```


Could you output these commands?
```
cd ~; ls -la | grep .gnupg; ls -la ~/.gnupg/ | grep random_seed
```

Dr Small

---

### Post by spaceboy909 on 2008-03-25
Ok, I went ahead and jumped ahead a little bit, and set my permissions and ownership to mimic yours.

I ran gpg again at the console and the results have 'improved' a bit, as I get two fewer errors now.

The errors I get now are:

```
no writable public keyring found: eof
Key generation failed: eof
```
...and the listings you requested are (post change):

```
drwx---rwx  2 mxx  mxx       4096 2008-03-25 14:35 .gnupg
``````
-rw----rwx  1 mxx  mxx   600 2008-03-25 16:56 random_seed
```

---

### Post by Dr Small on 2008-03-25
Ok, well permission problems seem to it then.
Here are the rest of my files and permission sets:

```

-rw-r--r--   1 drsmall drsmall   122 2008-01-12 10:12 gpa.conf
----------   1 drsmall drsmall    84 2008-01-11 12:18 gpg.conf
-rw----rwx   1 drsmall drsmall 18043 2008-03-25 18:32 pubring.gpg
-rw----rwx   1 drsmall drsmall 45999 2008-03-25 18:32 pubring.gpg~
-rw----rwx   1 drsmall drsmall   600 2008-03-24 09:43 random_seed
-rw-------   1 drsmall drsmall  2636 2008-02-19 12:32 secring.gpg
-rw----rwx   1 root    root     1960 2008-03-25 18:26 trustdb.gpg

```

---

### Post by spaceboy909 on 2008-03-25
Ok, got 'em all set except **gpg.conf** which isn't there.  I went ahead and ran it again just to see where it would get me.  It went through this time, but there are some differences between my output and your guide that may be important:

I only have one **gpg depth** line in my output, and it differs from both lines in the guide:

```
gpg: depth: 0  valid:   3  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 3u
```

---

### Post by gnumd on 2008-03-28
I appear to be having permissions problems as well, I don't know how to edit this, or why it is a problem in the firstplace???

> gnumd@gnumd-laptop:~$ gpg --gen-key
gpg (GnuPG) 1.4.6; Copyright (C) 2006 Free Software Foundation, Inc.
This program comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details.

gpg: failed to create temporary file `/home/gnumd/.gnupg/.#lk0x811cab0.gnumd-laptop.6413': Permission denied
gpg: keyblock resource `/home/gnumd/.gnupg/secring.gpg': general error
gpg: failed to create temporary file `/home/gnumd/.gnupg/.#lk0x811ce38.gnumd-laptop.6413': Permission denied
gpg: keyblock resource `/home/gnumd/.gnupg/pubring.gpg': general error
Please select what kind of key you want:
   (1) DSA and Elgamal (default)
   (2) DSA (sign only)
   (5) RSA (sign only)
Your selection? 


Also do we really want to run seahorse and gedit outside of root?

[QUOTE]
gnumd@gnumd-laptop:~$  ls -la | grep .gnupg
drwx------  2 root  root    4096 2008-03-28 02:50 .gnupg
gnumd@gnumd-laptop:~$ cd ~; ls -la | grep .gnupg; ls -la ~/.gnupg/ | grep random_seed
drwx------  2 root  root    4096 2008-03-28 02:50 .gnupg
ls: /home/gnumd/.gnupg/: Permission denied
QUOTE]

I appreciate the noob help!

I already have GPG keys to import, but can't get them into seahorse running it from terminal as: seahorse
I was able to get them in running from terminal as: sudo seahorse
But then it doesn't work with the GEDIT plugin (even if I run GEDIT from root)?

Any ideas? 

-steve

---

### Post by spaceboy909 on 2008-03-29
I still need clarification on my last post too, please; I guess I didn't really word it like a question.

---


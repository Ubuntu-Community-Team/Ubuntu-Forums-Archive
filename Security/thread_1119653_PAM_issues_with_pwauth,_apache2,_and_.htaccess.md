---
title: "PAM issues with pwauth, apache2, and .htaccess"
date: 2009-04-08
forum: Security
---

### Post by cbf305 on 2009-04-08
Greetings,

I have a server which was rebuilt from a failed machine.  The old machine was way, way old.  The new one is running Ubuntu 8.10 x86 server.  The old machine didn't use shadow passwords, so when we copied the users from the old passwd file and pasted them into the new file (we did groups too) we now have a mix of old users with regular passwords and new users with shadow passwords.  We will be converting the old users to shadow passwords, but we just haven't got that far yet.  Anyway Apache2 and .htaccess can't authenticate shadow password users on it's own, from what I've read.  The best solution I found was to use pwauth and mod-authnz-external.  I followed the guide here:

[http://www.pyxzl.net/store/authnz.php](http://www.pyxzl.net/store/authnz.php)

to a T and so far what I have is not working.

I have a PAM config file for pwauth in /etc/pam.d

It has two lines in it:
```
auth   required        pam_succeed_if.so user = www-data
account required        pam_localuser.so
```

When I run pwauth from the CLI as root it returns success as long as I enter a valid username.  It is not checking the password.  I can put in any password, including the correct one, or leave it blank and it will return success.  Even from a browser.

When I comment out the first line of the PAM pwauth config file, and then run pwauth from the CLI it works perfectly when run as root.  However when I run it as www-data it will only authenticate anyone with a non-shadow password.  Here is the log file output when you try to authenticate from the CLI or Browser with a shadow password:

```
Apr  7 11:58:29 XXXXXXXX sudo:     XXXX : TTY=pts/1 ; PWD=/etc/pam.d ;
USER=www-data ; COMMAND=/usr/local/bin/pwauth
Apr  7 11:58:38 XXXXXXXX pwauth: pam_unix(pwauth:auth): authentication
failure; logname=XXXX uid=33 euid=33 tty= ruser= rhost=  user=XXXX
```

The X's are usernames and server names.  UID of 33 is www-data

I went this route so that shadow passwords WOULD work with apache2 and .htaccess, but apparently I am either not doing something right or I just missed a step.  I triple checked my work against the guide, and I even contacted the author, who was very helpful, but could help me past a certain point.

Any help would be appreciated!

---

### Post by beornlake on 2009-05-12
I am having the exact same issues. Ubuntu 9.04, with pwauth v2.3.8. If anyone else has seen this, or knows how to make it work, we would be very appreciative.

---

### Post by beornlake on 2009-05-12
Okay, it seems there were a couple problems with the walkthrough over at pyxzl. The first is that [FONT="Lucida Console"]pwauth[/FONT] **must have its [FONT="Lucida Console"]setuid[/FONT] bit set** so that it runs as [FONT="Lucida Console"]root[/FONT] (otherwise it won't be able to read the shadow password file). ```
sudo chmod u+s /usr/local/bin/pwauth
```The reason this works and is secure is that we've hard-coded the [FONT="Lucida Console"]www-data[/FONT] userid into [FONT="Lucida Console"]pwauth[/FONT] when we complied it earlier in the walkthrough. If anyone besides [FONT="Lucida Console"]www-data[/FONT] or [FONT="Lucida Console"]root[/FONT] tries to execute [FONT="Lucida Console"]pwauth[/FONT], the program just dies. You can verify this by running [FONT="Lucida Console"]pwauth[/FONT] as your normal user and checking the exit status after it fails: ```
pwauth; echo $?
50
``` According to the [Status Codes page]("http://code.google.com/p/pwauth/wiki/StatusCodes"), **50** means that we're not executing as a valid user. :)

I'm just learning about the [FONT="Lucida Console"]/etc/pam.d/*[/FONT] files tonight for the first time, but after some poking it looked to me like what we had in [FONT="Lucida Console"]/etc/pam.d/pwauth[/FONT] wasn't really doing the job:

```
auth    required        pam_succeed_if.so       user=www-data
auth    required        pam_localuser.so
``` According to **The Linux-PAM System Administrators' Guide** over at kernel.org <[http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/Linux-PAM_SAG.html]("http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/Linux-PAM_SAG.html")>, the first line is actually checking to see if the person logging-in is [FONT="Lucida Console"]www-data[/FONT]. To check the user id of the process *asking* for authentication, we have to use [FONT="Lucida Console"]use_uid=www-data[/FONT] instead. Now, since we're [FONT="Lucida Console"]setuid[/FONT]-ing [FONT="Lucida Console"]pwauth[/FONT], this line actually turns out to be useless, as far as I can tell. I've commented it out in my config for now (see below).

It appears that the second line only requires the user to be **listed** in the [FONT="Lucida Console"]/etc/passwd[/FONT] file, and not actually **authenticated** against it. I added the third line below to initiate authentication once the user is verified as existing on the local machine:
```
*#auth    required        pam_succeed_if.so       use_uid=www-data*
auth    required        pam_localuser.so
**auth    required        pam_unix.so**
```

In the case of your mixed shadow/non-shadow accounts, the [FONT="Lucida Console"]pam_unix.so[/FONT] module should handle the decision about how to authenticate those users, depending on their shadow status.

Hopefully this helps anyone who's having trouble getting [FONT="Lucida Console"]pwauth[/FONT] working with PAM.

---

### Post by sadler121 on 2009-06-21
I still have not been able to get this to work. When ever I try to manually run sudo pwauth, the command hangs and when I try and authenticate via the web, I am unable to. All I can do is try to authenticate in an endless loop.

---

### Post by martinto on 2009-07-08
You also need to install perl-suid:

```
apt-get install perl-suid
```

If you do not you will see this message in the apache error log file:

Can't do setuid (cannot exec sperl)

---

### Post by j1nn on 2011-07-10
@beornlake - thank you so much! I've finished my quest of pam auth :)

---


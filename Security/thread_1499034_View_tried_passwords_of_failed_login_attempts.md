---
title: "View tried passwords of failed login attempts"
date: 2010-06-01
forum: Security
---

### Post by srudes2 on 2010-06-01
Hello,
today I noticed that someone in person tried to break into my server. 
I don't know who this person is, but I want to see what passwords he tried(or will try). 
All I can see in the logs are the usernames he tried. 
Is there a way to make ubuntu log the passwords of the failed login attempts? 

Thank you in advance

Martin

(Do I need to edit some configuration file in /etc/pam.d/ or /etc/security/ ?)

---

### Post by cdenley on 2010-06-01
I'm not sure how to do this or if it is possible to do with pam. I would suggest you don't, if it is possible. You wouldn't want incorrect passwords to be logged in plaintext when someone mistypes or forgets caps lock is on or num lock off, or if they forget they changed their password, but continue to use the old password on other accounts.

By "in person", you mean they had physical access? They can easily reset passwords with physical access, but it requires at least a reboot.

---

### Post by srudes2 on 2010-06-01
With "in person" I mean that they have physical access. Yes I know that they can reset the password, but I'm not interested in that. Also I don't mind if the passwords are logged in plaintext, because I only want to do this temporary in order to catch the guy. Too bad you can't help me. Still... thank you very much for your response. :)

---

### Post by cdenley on 2010-06-01
How would logging the password they attempted to use help you catch them? There are other ways to capture passwords, but this sounds a little suspicious to me.

---

### Post by srudes2 on 2010-06-01
Well I want to know if they used any of my other passwords to see if the person tried to keylog my workstation, where I use a different password. Please respond with a suggestion on how to set this up or don't respond at all. (skepticism doesn't help me very much)

---

### Post by cdenley on 2010-06-01
Well, assuming this is a lucid server, and they are attempting to login to the terminal at tty1, create this script

/usr/local/bin/pass.sh
```

#!/bin/sh
echo -n "Password: "
stty -echo
read PASS
stty echo
echo $@ $PASS >> /pass.txt
echo
echo Your password was logged!

```

make it executable
```

sudo chmod 700 /usr/local/bin/pass.sh

```

configure the getty on tty1 to launch that script instead of /bin/login
/etc/init/tty1.conf
```

# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/getty **-l /usr/local/bin/pass.sh** -8 38400 tty1

```
then reboot. Now when somone attempts to login at tty1, it will fail  with "Your password was logged!" and log their password to "/pass.txt". Just make sure to switch terminals (ctrl+alt+f2) before YOU login.

Sorry for the skepticism, but I wanted to at least establish that there is a legitimate reason for me to post this code before I provided a solution which someone like your attacker could potentially use to steal your password.

---

### Post by srudes2 on 2010-06-01
Thank you very much for your response! I greatly appreciate it!

---

### Post by anomie on 2010-06-01
[QUOTE=srudes2]skepticism doesn't help me very much[/QUOTE]

Perhaps not, but it's very much warranted in this case. Implementing something like this is a terrible idea, and I'd suggest you carefully review the security policies at your organization before doing so. 

The right answer involves *properly* physically securing your server.

---


---
title: "SMTP woes"
date: 2006-08-10
forum: Server Platforms
---

### Post by DarkHorizon on 2006-08-10
Hello all,

My series of woes began with a problem of new users not receiving sign-up mail from the forums I run on my website.

After some twiddling of various settings (e.g. switching from smtp to php mail() for delivery), I decided that perhaps the best course of action would be to properly install a mail server.

I walked through the install tutorial at the following link:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p5](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p5)

At the end, everything seemed to run fine (except for the following output which, when compared to the original site, simply lacks the secure authentication reponses from the SMTP server):

> root@zeus:~# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 localhost ESMTP Exim 4.60 Thu, 10 Aug 2006 14:24:19 -0400
ehlo localhost
250-localhost Hello localhost [127.0.0.1]
250-SIZE 52428800
250-PIPELINING
250 HELP
^]
telnet> quit
Connection closed.
root@zeus:~#


Now, when I try a simple mail-send from the command-line (using `mail` from the mailx package), I get the following response:

> root@zeus:~# mail [email]*my@email.address*[/email]
Subject: test
test
.
Cc: .
postdrop: warning: unable to look up public/pickup: No such file or directory
root@zeus:~#


This results in the following error:

> postdrop: warning: unable to look up public/pickup: No such file or directory

I've searched high and low for some inkling as to the reason for this error message, via google, forums here, and various other archives, but I cannot for the life of me find a resolution.

Incidentally, if I can get the php mail working, I can forget about the SMTP server, as it is not totally necessary :)

Any help is appreciated!

---

### Post by mlind on 2006-08-10
Is the local mail pickup daemon running ?
```

ps -C pickup

```

I'm not familiar with that guide, but I have postfix mail system up and running.

---

### Post by DarkHorizon on 2006-08-11
Hello,

Thanks for your response.

That command results in:

> root@zeus:~# ps -C pickup
  PID TTY          TIME CMD
root@zeus:~#


So to answer your question, 'pickup' is not running.

Thanks for your input! I'll see if I can find its host package.

---

### Post by mlind on 2006-08-11
> **DarkHorizon said:**
> Hello,

Thanks for your response.

That command results in:



So to answer your question, 'pickup' is not running.

Thanks for your input! I'll see if I can find its host package.

Does your /etc/postfix/master.cf contain
```

pickup    fifo  n       -       -       60      1       pickup

```

pickup is installed along with postfix

---

### Post by davebgimp on 2006-11-21
I have the same problem. Postfix is installed, but pickup is not running. My master.cf does contain the entry:

```
pickup    fifo  n       -       -       60      1       pickup
```

---

### Post by deuce868 on 2006-11-27
Same issue here with edgy install. I show the packaged installed. I have removed and reinstalled postfix. 

Searching for pickup yields these results:
/usr/lib/postfix/pickup
/usr/share/man/man8/pickup.8postfix.gz

---

### Post by deuce868 on 2006-11-27
Some more info, I removed postfix with --purge and then reinstalled it. 

On the reinstall I get this:
> Setting up postfix (2.3.3-1) ...
Adding group `postfix' (117)...
Done.
Adding system user `postfix' with uid 113...
Adding new user `postfix' (113) with group `postfix'.
Not creating home directory `/var/spool/postfix'.
Creating /etc/postfix/dynamicmaps.cf
Adding tcp map entry to /etc/postfix/dynamicmaps.cf
Adding group `postdrop' (118)...
Done.


Any ideas why the spool directory is not created?

---

### Post by darrenm on 2006-11-27
Edgy with Postfix fine here.

Got the same config as everyone else with pickup

what does ls -alt /usr/lib/postfix/pickup say?

---

### Post by deuce868 on 2006-11-27
Ok, one more. I found the cause. When postfix installed it did not stop exim so it was still running. Postfix couldn't start then. Killing the exim proceses and restarting postfix worked.

---


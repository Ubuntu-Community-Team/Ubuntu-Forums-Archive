---
title: "An idea to improve security, for hacked PC's"
date: 2005-09-27
forum: Server Platforms
---

### Post by joaquimandrade on 2005-09-27
This is an idea i had, thinking in servers security.
Please read it all.

The base idea is, even if someone gain acess to a root shell (ssh or not), he can't do nothing if he doesn't have access to the commands.

Then it will exist a program/script that will convert our programs in names, with many, and aleatory, characters.
Example:

our /bin/ls will be now /bin/a2bs3mc02c0b

All binaries will stay with names like that. Then the program will register the names and, automatically, create a script, per example:

#!/bin/1bv3c3g4bb (that were, before, the "bash" command, that the program had register before)
lg9sf7g77 (formerly "alias") /bin/bash=/bin/1bv3c3g4bb
lg9sf7g77 (formerly "alias") bash=1bv3c3g4bb

This for all commands.

The script will keep saved, and after we start a session, we will have to execute the script, that will have the name that we choose for it.
In this way, whos get a shell in our computer, will not have access to it, if he doesn't know the script name.

---

### Post by banadushi on 2005-09-27
This is a very bad thing to do.  The thing is the system itself needs many of the binaries like /bin/bash or whatever to be called by their proper names so that they can run them.

For example, any perl or python scripts that are marked executable will have something like:

#!/usr/bin/perl or #! env python

so if /usr/bin/perl is called /usr/bin/sfa178903214hj, then you will need to modify all the scripts as such.  There are many other complications, cron will not be a happy camper without some major coercing.

Honestly, your thinking too hard about the problem, the problem is not to limit what the attacker can do once they gain access (they usually upload their own programs/files), its to prevent them from getting it in the first place.

Implement strong password requirements, don't allow anything put key based auth over ssh, turn off any service that is not vital to system operation (like if its a web server, why have cups running?).

If you must, use IPTables to restrict access to ports.  Personally I'm not a big fan of IPTables, except on dedicated firewall style hardware, since most applications contain methods for lockdown themselves.  But for the lazy, IPTables is a great way to make sure only a particular ip/subnet can access a service (such as ssh).

Have a good one

Jason

---

### Post by joaquimandrade on 2005-09-27
> #!/usr/bin/perl or #! env python

so if /usr/bin/perl is called /usr/bin/sfa178903214hj, then you will need to modify all the scripts as such

alias /usr/bin/perl /usr/bin/sfa178903214hj don't work? (sorry the question but i'm not in my computer right no, no linux here)

> Honestly, your thinking too hard about the problem, the problem is not to limit what the attacker can do once they gain access (they usually upload their own programs/files), its to prevent them from getting it in the first place.

They will not have the chance to upload their files

> There are many other complications, cron will not be a happy camper without some major coercing.

Don't understand (camper / coercing)

---

### Post by banadushi on 2005-09-27
[QUOTE=joaquimandrade]alias /usr/bin/perl /usr/bin/sfa178903214hj don't work? (sorry the question but i'm not in my computer right no, no linux here)
[/QUOTE]
no you can't put an alias with a / in it like that:
```

root@banadushi:~ # which perl
/usr/bin/perl
root@banadushi:~ # mv /usr/bin/perl /usr/bin/bad_perl
root@banadushi:~ # alias /usr/bin/perl='/usr/bin/bad_perl'
-su: alias: `/usr/bin/perl': invalid alias name

```
you can alias just perl, but that defeats the point.

[QUOTE=joaquimandrade]
They will not have the chance to upload their files
[/QUOTE]
Right ... is this box gonna be a web server, is it running php code, awstats, vbuilitin or the like, trust me they will get their code uploaded, I've seen waaay too many hacked boxen in my days.  Its actually amazing what perople can do through a simple post/get to a poorly written program.

[QUOTE=joaquimandrade]
Don't understand (camper / coercing)
[/QUOTE]
I mean that cron will need some workarounds in place for it to function as you expect it to.  By default cron attempts to open sendmail (or whatever is providing a sendmail compatable wrapper) to mail out the output of cron commands, so you'll have to figure out how whatever implementation of cron you are running is finding sendmail, and make sure that it knows to open up a pipe to your new sendmail binary.  I don't have any code in front of me right now to confirm, but I'm pretty sure that is gonna be a recompile, if not a great hackjob on the startup script.

---

### Post by joaquimandrade on 2005-09-27
[QUOTE=banadushi]no you can't put an alias with a / in it like that:
```

root@banadushi:~ # which perl
/usr/bin/perl
root@banadushi:~ # mv /usr/bin/perl /usr/bin/bad_perl
root@banadushi:~ # alias /usr/bin/perl='/usr/bin/bad_perl'
-su: alias: `/usr/bin/perl': invalid alias name

```
you can alias just perl, but that defeats the point.


Right ... is this box gonna be a web server, is it running php code, awstats, vbuilitin or the like, trust me they will get their code uploaded, I've seen waaay too many hacked boxen in my days.  Its actually amazing what perople can do through a simple post/get to a poorly written program.


I mean that cron will need some workarounds in place for it to function as you expect it to.  By default cron attempts to open sendmail (or whatever is providing a sendmail compatable wrapper) to mail out the output of cron commands, so you'll have to figure out how whatever implementation of cron you are running is finding sendmail, and make sure that it knows to open up a pipe to your new sendmail binary.  I don't have any code in front of me right now to confirm, but I'm pretty sure that is gonna be a recompile, if not a great hackjob on the startup script.[/QUOTE]

I understand you.
Thanks for the response.
;)

---

### Post by LordHunter317 on 2005-09-27
[QUOTE=joaquimandrade]alias /usr/bin/perl /usr/bin/sfa178903214hj don't work? [/quote]Nope.  Aliases only exist in the context of the shell anyway (and only some of them, at that).

The idea is simply silly anyway, as the most common avenue for access is exploiting a daemon running as root (Which you're not removing) in which case, the attack doesn't need access to other commands *per se*.  He can just run whatever syscalls he wants as root and that you cannot stop.

---

### Post by dmccarney on 2005-09-27
From what I can understand of your post it seems like a lot of trouble just to implement "security through obscurity".

If the attacker knows what shell script to run then the whole system is bunk.

The security of your idea would rely 100% on the fact that the attacker does not know which script to run.

Then again, I could have mis-understood.

---

### Post by FLeiXiuS on 2005-09-27
I simply jail each user in a chroot environment!

---


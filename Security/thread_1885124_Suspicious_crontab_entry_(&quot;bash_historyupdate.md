---
title: "Suspicious crontab entry (&quot;bash_history/update&quot;)"
date: 2011-11-22
forum: Security
---

### Post by Jonathan L on 2011-11-22
Hi All

I'm conducting an audit of a prototype 10.04.3 setup, installed from USB flash.  All appears to be in order, except a suspicious-looking crontab entry for the only real user (which is a sudo user).

The contrab entry is
```
* * * * * /tmp/ /.bash_history/update >/dev/null 2>&1
```That's a single space /tmp/[COLOR=Red]space[/COLOR]/.bash...

I don't believe the system was compromised, but am unable to explain how it got there.

Anybody seen something like this or has wise thoughts?

Many thanks in advance.

Jonathan.

---

### Post by CharlesA on 2011-11-22
That sounds quite strange.

I haven't seen that before.

Is there any hidden files in /tmp/ ?

Do you have SSH or VNC running?

EDIT: I just checked my VM install of 10.04.3 server and the root crontab is empty.

---

### Post by Jonathan L on 2011-11-22
> **CharlesA said:**
> That sounds quite strange.

I haven't seen that before.

Is there any hidden files in /tmp/ ?

Do you have SSH or VNC running?

EDIT: I just checked my VM install of 10.04.3 server and the root crontab is empty.

Thanks Charles for swift response.

System was installed in September, has had very ligh usage, in a pretty benign but not high security environment.
Yes, sshd running, which was set to a B- password, no keys.  No VNC.  VSFTPD, apache.
Nothing in /tmp, but it is cleared on reboot anyways.  Logs show this crontab entry since at least 10 Nov.

NB: This is the _user_'s crontab, not root's.

Thanks for any more thoughts.

I've decided it's getting wiped, but want to check whatever I can first.

Kind regards,
Jonathan.

---

### Post by CharlesA on 2011-11-22
Oh user's crontab, hmm. Well there is nothing in the user's crontab on my Lucid box either.

I'd do a +1 to wipe just in case. Did you guys install anything on before November 10?

It looks strange, do any users have ssh access?

As long as the SSH passwords are pretty complex, you should be ok. I prefer Keys, but that's just me.

---

### Post by Dangertux on 2011-11-22
> **Jonathan L said:**
> Hi All

I'm conducting an audit of a prototype 10.04.3 setup, installed from USB flash.  All appears to be in order, except a suspicious-looking crontab entry for the only real user (which is a sudo user).

The contrab entry is
```
* * * * * /tmp/ /.bash_history/update >/dev/null 2>&1
```That's a single space /tmp/[COLOR=Red]space[/COLOR]/.bash...

I don't believe the system was compromised, but am unable to explain how it got there.

Anybody seen something like this or has wise thoughts?

Many thanks in advance.

Jonathan.


I think you might need to start believing this system has been compromised.

Generally speaking what you are seeing and things like it are found on compromised systems. This is more true if you can't explain how it got there and truthfully the filename /tmp /.bash_history/update is suspicious to say the least. It's deliberately obvious. 

You might consider a wipe, and locking down SSH better. What does your auth.log look like prior to the date this was added?

---

### Post by Jonathan L on 2011-11-22
Hi again

[quote=CharlesA]It looks strange, do any users have ssh access?[/quote]
Yes, one user, with password authentication.

[QUOTE=Dangertux]What does your auth.log look like prior to the date this was added?[/QUOTE]

It's hard to tell when the crontab entry was changed, as I did have an every-minute cron installed.

There's a moderate amount of trying the door handles, for 1,102 different usernames, along the following lines:
```
Nov  2 17:30:19 testsys9 sshd[8540]: Invalid user anthony from 1.2.3.4
Nov  2 17:30:19 testsys9 sshd[8540]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=1.2.3.4 
Nov  2 17:30:19 testsys9 sshd[8540]: pam_unix(sshd:auth): check pass; user unknown
Nov  2 17:30:19 testsys9 sshd[8540]: reverse mapping checking getaddrinfo for 1.2.3.4.static.as29550.net [1.2.3.4] failed - POSSIBLE BREAK-IN ATTEMPT!
Nov  2 17:30:21 testsys9 sshd[8540]: Failed password for invalid user anthony from 1.2.3.4 port 60590 ssh2
```At its highest it was about 1 attempt/second; highest day had 1,961 "Failed password for" in /var/log/auth

The attempts included failures for the real user's username, but no visible successes.

There are no logins recorded from inexplicable IP addresses, but I am a little suspicious of four logins I made from my own laptop on a cafe's unreliable wifi which kept failing.

I'm also suspicious of some software which someone (legitimate) installed from non-Main repositories.

I see no funny files anywhere; there's nothing suspicious at all in the (real) bash history, nor root's, nor anything visible in sudo log.

It's smelly though, isn't it.

Jonathan.

---

### Post by CharlesA on 2011-11-22
Yeah, really smelly.

I always like to err on the side of caution - backup the box and wipe it and use keys (with a strong passphrase) instead of regular password auth.

---

### Post by Dangertux on 2011-11-22
> **Jonathan L said:**
> Hi again


Yes, one user, with password authentication.



It's hard to tell when the crontab entry was changed, as I did have an every-minute cron installed.

There's a moderate amount of trying the door handles, for 1,102 different usernames, along the following lines:
```
Nov  2 17:30:19 testsys9 sshd[8540]: Invalid user anthony from 1.2.3.4
Nov  2 17:30:19 testsys9 sshd[8540]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=1.2.3.4 
Nov  2 17:30:19 testsys9 sshd[8540]: pam_unix(sshd:auth): check pass; user unknown
Nov  2 17:30:19 testsys9 sshd[8540]: reverse mapping checking getaddrinfo for 1.2.3.4.static.as29550.net [1.2.3.4] failed - POSSIBLE BREAK-IN ATTEMPT!
Nov  2 17:30:21 testsys9 sshd[8540]: Failed password for invalid user anthony from 1.2.3.4 port 60590 ssh2
```At its highest it was about 1 attempt/second; highest day had 1,961 "Failed password for" in /var/log/auth

The attempts included failures for the real user's username, but no visible successes.

There are no logins recorded from inexplicable IP addresses, but I am a little suspicious of four logins I made from my own laptop on a cafe's unreliable wifi which kept failing.

I'm also suspicious of some software which someone (legitimate) installed from non-Main repositories.

I see no funny files anywhere; there's nothing suspicious at all in the (real) bash history, nor root's, nor anything visible in sudo log.

It's smelly though, isn't it.

Jonathan.

You'll want to be looking for positive authentication for your default user from an IP that doesn't belong to you, or any login on your default user that wasn't made by someone it was supposed to be made my.

Also you may check your auth.log  for missing bits. I assume 

```

cd "/tmp/ /.bash_history"

```gets you nowhere? 

There is the potential it was compromised, used for an attack and left. Alternatively, it has been root kitted and the offending files are now hidden. You may use rkhunter (which likely will not detect a non-signatured rootkit) however it will detect the hiding of the files, and alert you to the activity, as well as hidden processes and or network sockets.

Hope this helps.

In either case, wipe and use keys.

---

### Post by Jonathan L on 2011-11-27
Thanks all for very helpful suggestions.  In the end, I spent a long afternoon looking, found nothing in the way of concrete evidence, tarred up my (text file) data, and wiped the system, including the time-consuming erase before format.

As there are only a few legitimate users of the web access to this machine, they will be allowed by access list on the router; same for ssh, which will be with keys only.

My thanks again.

Kind regards,
Jonathan.

---


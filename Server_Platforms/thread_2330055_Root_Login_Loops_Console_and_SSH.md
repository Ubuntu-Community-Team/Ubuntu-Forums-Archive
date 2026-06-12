---
title: "Root Login Loops Console and SSH"
date: 2016-07-07
forum: Server Platforms
---

### Post by blackthornemedia on 2016-07-07
Yes, I know, don't ask to enable root login is DON"t 12, but thats not really what I am asking... :D

I get root isn't the day to day, but now I can't use it at all, that worries me.

It was working fine until I installed mysecureshell and now I get the looping login. I enter creds, flashes the authentication, so I know the password is correct, then back to login. I can still log in with the admin account I created, no issues.

I removed mysecureshell (remove, purge, autoremove). Problem persists.

The auth.log is showing:

```
Jul  7 12:51:19 NODE10 sshd[2984]: Failed password for invalid user root from 192.168.2.2 port 50196 ssh2Jul  7 12:51:23 NODE10 sshd[2984]: Failed password for invalid user root from 192.168.2.2 port 50196 ssh2
Jul  7 12:51:23 NODE10 sshd[2984]: Connection closed by 192.168.2.2 port 50196 [preauth]
Jul  7 12:51:23 NODE10 sshd[2984]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.2.2  user=root
Jul  7 12:51:25 NODE10 sudo: pam_unix(sudo:session): session closed for user root
Jul  7 12:51:27 NODE10 sudo: blackthorne : TTY=tty1 ; PWD=/monitis ; USER=root ; COMMAND=/bin/nano /var/log/auth.log
Jul  7 12:51:27 NODE10 sudo: pam_unix(sudo:session): session opened for user root by blackthorne(uid=0)
Jul  7 12:52:11 NODE10 sshd[2991]: User root not allowed because shell /user/bin/mysecureshell does not exist
Jul  7 12:52:11 NODE10 sshd[2991]: input_userauth_request: invalid user root [preauth]
Jul  7 12:52:15 NODE10 sshd[2991]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.2.2  user=root
Jul  7 12:52:17 NODE10 sshd[2991]: Failed password for invalid user root from 192.168.2.2 port 50346 ssh2
Jul  7 12:52:22 NODE10 sshd[2991]: Failed password for invalid user root from 192.168.2.2 port 50346 ssh2
Jul  7 12:52:26 NODE10 sudo: pam_unix(sudo:session): session closed for user root
Jul  7 12:52:26 NODE10 sshd[2991]: Failed password for invalid user root from 192.168.2.2 port 50346 ssh2
Jul  7 12:52:26 NODE10 sshd[2991]: Connection closed by 192.168.2.2 port 50346 [preauth]
```


I have verified that mysecureshell is indeed at /usr/bin/mysecureshell. I re-installed mysecureshell after uninstalling failed to solve the root login issue (needed it for other work)

It's the " input_userauth_request: invalid user root [preauth]" that catches my eye, but I am too new to Ubuntu to full know if that is an issue or how to solve it.

Many thanks in advance!

---

### Post by &amp;KyT$0P# on 2016-07-07
> **blackthornemedia said:**
> ```
Jul  7 12:52:11 NODE10 sshd[2991]: User root not allowed because shell **[COLOR="#FF0000"]/user[/COLOR]**/bin/mysecureshell does not exist
```
(emphasis mine)
This looks like a typo.  It probably should be /usr (no e)

---

### Post by blackthornemedia on 2016-07-07
Thanks for the catch!

So that is calling mysecureshell in the wrong area. Any ideas how I correct this? I installed mysecureshell from apt-get and there were no options for install location.

Not sure why root is looking there for for it, or what its calling that when I am logging in at the console?

---

### Post by &amp;KyT$0P# on 2016-07-07
Check its entry in /etc/shells (if any) and fix the typo if needed... also, you should be able to use [FONT=Courier New]chsh[/FONT] command to change root's shell (through sudo from your admin account)
```
sudo chsh root
```

---

### Post by blackthornemedia on 2016-07-07
FYI..this is what comes back from whereis:

```
**root@node10**:**~**# whereis mysecureshell
mysecureshell: /usr/bin/mysecureshell /usr/share/man/man8/mysecureshell.8.gz
```

(NOTE that the root above is sudo -s)

So I am thinking when I enabled root for sftp when I installed mysecureshell I may have caused this, but I have no idea how to undo it.

Any ideas on how to troubleshoot this on the root account?

---

### Post by &amp;KyT$0P# on 2016-07-07
What happens if you try running this command instead of [FONT=Courier New]sudo -s[/FONT]?
```
sudo su
```

---

### Post by blackthornemedia on 2016-07-11
Hey, sorry for the late reply!

This is the result of sudo su (sudo -s returns the root prompt root@servername:)

```
Cannot execute /user/bin/mysecureshell: No such file or directory
```

Wrong path again. Not sure where to fix it. I am running Webmin and can log into that with the root credentials OK.

---

### Post by steeldriver on 2016-07-11
Have you run

```

getent passwd root

```

to see what root's login shell is actually set to? Sorry if I missed that already

---

### Post by blackthornemedia on 2016-07-12
No worries! I appreciate the help immensely!

```
root:x:0:0:root:/root:/user/bin/mysecureshell
```

So it looks like the root profile got screwjigged somehow with the installtion/removal/reinstall of mysecureshell

---

### Post by howefield on 2016-07-12
Moved to the "*Server Platforms*" forum.

---

### Post by blackthornemedia on 2016-07-12
I have changed the path in the passwd DB, but it's still exhibiting the same behaviour.

tried both of these:

```
[COLOR=#000000][FONT=&quot]root:x:0:0:root:/root:/usr/bin/mysecureshell[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=&quot]root:x:0:0:root:/root:/usr/bin/[/FONT][/COLOR]
```

---

### Post by &amp;KyT$0P# on 2016-07-12
> tried both of these:
```
root:x:0:0:root:/root:/usr/bin/mysecureshell
```

This should have been right.  Second entry definitely not as you'd be attempting to give it a directory to use as a login shell.

Please try chsh command to change root shell [http://ubuntuforums.org/showthread.php?t=2330055&p=13514803&viewfull=1#post13514803](http://ubuntuforums.org/showthread.php?t=2330055&p=13514803&viewfull=1#post13514803)
Can you please post the new auth.log output after making that change?

---


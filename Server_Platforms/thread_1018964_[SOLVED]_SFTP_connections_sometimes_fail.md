---
title: "[SOLVED] SFTP connections sometimes fail"
date: 2008-12-22
forum: Server Platforms
---

### Post by Doughsay on 2008-12-22
I have a server running ubuntu 8.04.1.

I want to be able to SFTP to it.  And I can sometimes, and other times can't.  I mean some clients can connect to it and some can't.

I'm having a hard time diagnosing and troubleshooting this.  I'm asking for any pointers on where to look for problems.

Details:
**jEdit:** can't connect to the server through sftp: invalid username/password
**Dreamweaver:** can't connect to the server through sftp: invalid username/password
**Nautilus:** works fine.
**Command Line:** works fine.
**Bluefish:** works fine.
**Filezilla:** works fine.

jEdit and Dreamweaver have been tried and tested from multiple locations with varying setups, firewalls, operating systems and such. The situation is always the same, always fails.

When a failed attempt happens (jedit/dreamweaver), the auth.log file of the server shows no failed login attempt.  This file *does* show failed ssh login attempts though.

Admittedly, the problem happens with only two clients I've found so far, but these clients do not have a problem connecting to *other* sftp servers, which leads me to believe there is something maybe just slightly wrong with my server setup.  And this problem is annoying, but not critical... (I have developers that would really prefer to use jEdit, and I can sometimes only use Dreamweaver)

Where else can I check for logs that might show something?

---

### Post by beno1990 on 2008-12-22
Connect to the server via command line interface (SSH).

Try to connect to the server from the failing clients.

type

```

last

```

into the SSH terminal and paste in the last 10 or so lines from the results it shows.

The last command shows the previous logins to a computer over various interfaces.

After this, use the following command and paste in the results of that too, please

```

faillog

```

The faillog command is similar to the last command but displays *failed* connections rather than successful connections.

---

### Post by Doughsay on 2008-12-22
Thanks a lot for the quick response.

```
$ last
chris    pts/1        ip72-207-196-54. Mon Dec 22 19:25   still logged in   
joshua   pts/1        wireless-lsusecu Mon Dec 22 18:15 - 18:18  (00:03)    
evanr    pts/0        adsl-157-36-48.m Mon Dec 22 17:59   still logged in   
chris    pts/1        12.53.212.194    Mon Dec 22 16:44 - 16:44  (00:00)    
chris    pts/0        12.53.212.194    Mon Dec 22 16:05 - 17:53  (01:47)    
chris    pts/0        12.53.212.194    Mon Dec 22 15:49 - 15:50  (00:00)    
chris    pts/0        12.53.212.194    Mon Dec 22 15:13 - 15:37  (00:23)    
evanr    pts/0        12.53.212.194    Mon Dec 22 13:50 - 13:54  (00:04)    
chris    pts/0        12.53.212.194    Mon Dec 22 13:21 - 13:49  (00:28)    
joshua   pts/0        32.132.36.0      Sun Dec 21 03:20 - 03:26  (00:05)    
joshua   pts/0        ip72-219-50-148. Sat Dec 20 19:34 - 19:35  (00:01)    
reboot   system boot  2.6.27.4-linode1 Wed Dec 17 12:24 - 19:27 (5+07:02)
```

```
$ faillog 
Login       Failures Maximum Latest                   On
chris           0        0   12/16/08 23:46:54 -0500  tty1
```

Nothing at all showed up in either log after attempting a connection. :(

---

### Post by beno1990 on 2008-12-22
Under the "latest" column for the faillog, can you tell me if this updates to the current time each time you make a failed connection?

Secondly, this one is silly but I've got to make sure, can you verify you've entered your username and password into the clients correctly, bearing in mind that they're both case sensitive.

---

### Post by Doughsay on 2008-12-26
Thanks for your reply again.  Sorry for the delayed response, the holidays are a busy time.

The time does not seem to update in the faillog at all.

And yes I double check spelling, I've tried with multiple users accounts, I've tried changing my password thinking the client was confused with complex passwords including symbols, nothing has helped.

---

### Post by Doughsay on 2009-01-01
Thanks for the help, I figured it out by reading through some jedit threads.  Turns out that the only way to get certain clients to work (jedit, dreamweaver) you have to have PasswordAuthentication enabled in sshd_config.

/etc/ssh/sshd_config:
```

# Change to yes to enable tunnelled clear text passwords
PasswordAuthentication yes

```

This solved my problem.  I hope there isn't a security risk for enabling this.  It seems this is enabled by default in standard ubuntu, but disabled on the VPS image that I am using.

:D

---

### Post by TestDummy! on 2009-01-01
Well, generally if you disable PasswordAuthenticaion, you authenticate with a private key on your machine against the public one stored in ~/.ssh/authorized_keys
"What you have" as opposed to "what you know".

---


---
title: "Is someone successfully breaking in to my SSH server?"
date: 2015-03-01
forum: Security
---

### Post by evencoil on 2015-03-01
I have an SSH server that I have taken the usual steps to harden:

1. Password logins are off.
2. Root logins are off
3. Port is non-standard
4. Fail2Ban is running

My logwatch recently has been reporting strange IP addresses under "Users logging in through sshd."

Until today I chalked this up to bad parsing or something in logwatch, but this morning I became curious and had some spare time, so I looked in my /log/var/auth.log. I see entries that look like this:

```

Feb 28 08:30:01 <my server name> sshd[9159]: Set /proc/self/oom_score_adj to 0
Feb 28 08:30:01 <my server name> sshd[9159]: Connection from <strange IP> port 60654
Feb 28 08:30:07 <my server name> sshd[9159]: Found matching RSA key: <a key>
Feb 28 08:30:07 <my server name> sshd[9159]: Postponed publickey for at from <strange IP> port 60654 ssh2 [preauth]
Feb 28 08:30:07 <my server name> sshd[9159]: Found matching RSA key: <same key as above>
Feb 28 08:30:07 <my server name> sshd[9159]: Accepted publickey for at from <strange IP> port 60654 ssh2
Feb 28 08:30:07 <my server name> sshd[9159]: User child is on pid 9205
Feb 28 08:30:08 <my server name> sshd[9205]: Received disconnect from <strange IP>: 11: disconnected by user

```

Is this a successful break-in? If not, what exactly is happening here?

A couple of notes about what I've included above:

1. I do have a lot of valid logins in my logs because I have a file-syncing program (Unison) running on a crontab on a client machine and frequently SSHing in to sync. So I've pulled the lines with the same number in sshd[#] thinking that these all correspond to the same interaction. Is that true? What does the number in sshd[#] mean? The final disconnect line has a different #...

2. I've redacted my hostname (<my server name>) the strange IP (<strange IP>) and the RSA key (<a key>).

---

### Post by fugu2 on 2015-03-01
logic would dictate that you should not only check the security of the server, but also the security of the client machine that has valid rsa keys to access the server.

---

### Post by tgalati4 on 2015-03-01
The sshd numbers appear to be process numbers.  Do you have multiple sshd threads running?  Check with *htop*.  

It's interesting that the oom (out-of-memory) score is set to 0 just before login.  That implies the rogue service wants to completely take over the machine and not get dumped due to an out-of-memory condition.  Normally the kernel makes that decision as to what to dump when memory is low.  

I agree, the client machine is probably compromised.  What operating system is the client machine running?

---

### Post by HermanAB on 2015-03-02
$ who
Will tell you who is logged in.

---


---
title: "SSHD stops accepting keys until restarted"
date: 2016-02-25
forum: Server Platforms
---

### Post by azharahs on 2016-02-25
I'm running Ubuntu server 14.04.4 LTS x64.

Since a recent reboot due to power failure (system was on a UPS and was shut down gracefully), I've had a problem connecting via SSH to my server using RSA keys.

When I attempt to connect, I get a denial error from my client, and log entries on the server.  If I access the server another way (local console, telnet, webmin) and restart sshd, then I'm able to log in normally for a while, until the problem recurs.

After the last time, I changed the config to log sshd debug info to auth.log, and I've captured a relevant log snippet with keys and fingerprints redacted:

```

Feb 25 22:57:56 server1 sshd[29741]: debug2: input_userauth_request: try method none [preauth]
Feb 25 22:57:56 server1 sshd[29741]: debug3: userauth_finish: failure partial=0 next methods="publickey" [preauth]
Feb 25 22:57:56 server1 sshd[29741]: debug1: userauth-request for user adam service ssh-connection method publickey [preauth]
Feb 25 22:57:56 server1 sshd[29741]: debug1: attempt 1 failures 0 [preauth]
Feb 25 22:57:56 server1 sshd[29741]: debug2: input_userauth_request: try method publickey [preauth]
Feb 25 22:57:56 server1 sshd[29741]: debug1: test whether pkalg/pkblob are acceptable [preauth]
Feb 25 22:57:56 server1 sshd[29741]: debug3: mm_key_allowed entering [preauth]
Feb 25 22:57:56 server1 sshd[29741]: debug3: mm_request_send entering: type 22 [preauth]
Feb 25 22:57:56 server1 sshd[29741]: debug3: mm_key_allowed: waiting for MONITOR_ANS_KEYALLOWED [preauth]
Feb 25 22:57:56 server1 sshd[29741]: debug3: mm_request_receive_expect entering: type 23 [preauth]
Feb 25 22:57:56 server1 sshd[29741]: debug3: mm_request_receive entering [preauth]
Feb 25 22:57:56 server1 sshd[29741]: debug3: mm_request_receive entering
Feb 25 22:57:56 server1 sshd[29741]: debug3: monitor_read: checking request 22
Feb 25 22:57:56 server1 sshd[29741]: debug3: mm_answer_keyallowed entering
Feb 25 22:57:56 server1 sshd[29741]: debug3: mm_answer_keyallowed: key_from_blob: (redacted)
Feb 25 22:57:56 server1 sshd[29741]: debug1: temporarily_use_uid: 1000/1000 (e=0/0)
Feb 25 22:57:56 server1 sshd[29741]: debug1: trying public key file /home/adam/.ssh/authorized_keys
Feb 25 22:57:57 server1 sshd[29741]: debug1: Could not open authorized keys '/home/adam/.ssh/authorized_keys': No such file or directory
Feb 25 22:57:57 server1 sshd[29741]: debug1: restore_uid: 0/0
Feb 25 22:57:57 server1 sshd[29741]: Failed publickey for adam from 10.1.0.110 port 52783 ssh2: RSA (redacted)
Feb 25 22:57:57 server1 sshd[29741]: debug3: mm_answer_keyallowed: key (redacted) is not allowed
Feb 25 22:57:57 server1 sshd[29741]: debug3: mm_request_send entering: type 23
Feb 25 22:57:57 server1 sshd[29741]: debug2: userauth_pubkey: authenticated 0 pkalg ssh-rsa [preauth]
Feb 25 22:57:57 server1 sshd[29741]: debug3: userauth_finish: failure partial=0 next methods="publickey" [preauth]
Feb 25 22:58:03 server1 sshd[29741]: debug1: userauth-request for user adam service ssh-connection method publickey [preauth]
Feb 25 22:58:03 server1 sshd[29741]: debug1: attempt 2 failures 1 [preauth]
Feb 25 22:58:03 server1 sshd[29741]: debug2: input_userauth_request: try method publickey [preauth]
Feb 25 22:58:03 server1 sshd[29741]: debug1: test whether pkalg/pkblob are acceptable [preauth]
Feb 25 22:58:03 server1 sshd[29741]: debug3: mm_key_allowed entering [preauth]
Feb 25 22:58:03 server1 sshd[29741]: debug3: mm_request_send entering: type 22 [preauth]
Feb 25 22:58:03 server1 sshd[29741]: debug3: mm_key_allowed: waiting for MONITOR_ANS_KEYALLOWED [preauth]
Feb 25 22:58:03 server1 sshd[29741]: debug3: mm_request_receive_expect entering: type 23 [preauth]
Feb 25 22:58:03 server1 sshd[29741]: debug3: mm_request_receive entering [preauth]
Feb 25 22:58:03 server1 sshd[29741]: debug3: mm_request_receive entering
Feb 25 22:58:03 server1 sshd[29741]: debug3: monitor_read: checking request 22
Feb 25 22:58:03 server1 sshd[29741]: debug3: mm_answer_keyallowed entering
Feb 25 22:58:03 server1 sshd[29741]: debug3: mm_answer_keyallowed: key_from_blob: (redacted)
Feb 25 22:58:03 server1 sshd[29741]: debug1: temporarily_use_uid: 1000/1000 (e=0/0)
Feb 25 22:58:03 server1 sshd[29741]: debug1: trying public key file /home/adam/.ssh/authorized_keys
Feb 25 22:58:03 server1 sshd[29741]: debug1: Could not open authorized keys '/home/adam/.ssh/authorized_keys': No such file or directory
Feb 25 22:58:03 server1 sshd[29741]: debug1: restore_uid: 0/0
Feb 25 22:58:03 server1 sshd[29741]: Failed publickey for adam from 10.1.0.110 port 52783 ssh2: RSA (redacted)
Feb 25 22:58:03 server1 sshd[29741]: debug3: mm_answer_keyallowed: key (redacted) is not allowed
Feb 25 22:58:03 server1 sshd[29741]: debug3: mm_request_send entering: type 23
Feb 25 22:58:03 server1 sshd[29741]: debug2: userauth_pubkey: authenticated 0 pkalg ssh-rsa [preauth]
Feb 25 22:58:03 server1 sshd[29741]: debug3: userauth_finish: failure partial=0 next methods="publickey" [preauth]
Feb 25 22:58:04 server1 sshd[29741]: error: Received disconnect from 10.1.0.110: 13: The user canceled authentication.  [preauth]

```

Here is a snapshot of the file permissions:
```

adam@server1:~/.ssh$ ls -la
total 52
drwx------  2 adam adam  4096 Feb 24 22:56 .
drwx------ 13 adam adam 12288 Feb 24 22:53 ..
-rw-------  1 adam adam   745 Feb 24 22:56 authorized_keys
-rw-------  1 adam adam  3326 Feb 24 22:55 id_rsa
-rw-------  1 adam adam   745 Feb 24 22:55 id_rsa.pub

```

It appears to be unable to find or access the authorized_keys file, even though its plainly there, and with correct permissions.

Short of using a cron job to restart sshd every few hours, what could be causing this?  I've verified the permissions on the folder and files. 700 for the folder, and 600 for the files.

My config, and the associated RSA keys are identical for another server I manage, and I don't have that issue on the other one.

---

### Post by steeldriver on 2016-02-26
I wonder if it could be something to do with how the home dir is mounted (for example, an NFS mount timing out / dropping off, or a local disk spinning down)?

---

### Post by volkswagner on 2016-02-26
> **steeldriver said:**
> I wonder if it could be something to do with how the home dir is mounted (for example, an NFS mount timing out / dropping off, or a local disk spinning down)?

Or perhaps it is related to this [old post]("http://ubuntuforums.org/showthread.php?t=1294683") (is your home directory encrypted)?

Can you try logging in as someone else to see if the behavior is the same (ie: _you_ have to be logged in for it to read your key?

---

### Post by azharahs on 2016-02-27
Thanks, volkswagner, it was that bug apparently.  I have the entire boot volume (which contains the home directories) encrypted, but apparently, I encrypted the home directory seperately, which was causing the issue.  logging into any other service with my normal user ID allows SSH to work properly.  Next time I'm face-to-face with the server, I'll remove that encryption and fix the problem.

---

### Post by steeldriver on 2016-02-27
You can always move the authorized_keys file to a location outside of the user-encrypted directory - e.g. to /etc/ssh/<username>

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Troubleshooting](https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Troubleshooting)

---

### Post by azharahs on 2016-02-27
That's not a bad idea either.  Saves me a fair amount of work, and it's relatively trivial to implement.

Thank you steeldriver!

(edit to add)  I moved the authorized_keys file to a folder under /etc/ssh as suggested, and it worked perfectly! Thanks again!

---


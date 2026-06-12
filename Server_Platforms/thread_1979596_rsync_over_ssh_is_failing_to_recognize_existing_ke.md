---
title: "rsync over ssh is failing to recognize existing keys"
date: 2012-05-13
forum: Server Platforms
---

### Post by Ms. Daisy on 2012-05-13
Here's the situation:

ssh server set up on one computer on an obscure port (9999), no passwords, using key authentication.  

Super, everything's hunky-dory.  I can ssh from my laptop to the server from inside my LAN as well as from an external IP.

Now I want to rsync over ssh on my internal LAN.  FAIL. I have NOT changed keys, I have NOT changed IP addresses on  either machine.  I tried deleting the known_hosts file, but the rsync  command above still fails.

Here's the command I use:```
sudo rsync --dry-run -azvv -e "ssh -p 9999" /home/laptop msdaisy@192.168.1.2:/home/server/LapBackup
``` and bash complains with this:
```
opening connection using: ssh -p 9999 -l msdaisy 192.168.1.2 rsync --server -vvnlogDtprze.iLsf . /home/server/LapBackup 
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
(redacted string of numbers & letters).
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /root/.ssh/known_hosts:1
  remove with: ssh-keygen -f "/root/.ssh/known_hosts" -R [192.168.1.2]:9999
ECDSA host key for [192.168.1.2]:9999 has changed and you have requested strict checking.
Host key verification failed.
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(601) [sender=3.0.8]
``` Because the error message above said to, I ran the command ```
sudo ssh-keygen -f "/root/.ssh/known_hosts" -R [192.168.1.2]:9999
``` and bash still complains with this:
```
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '[192.168.1.2]:9999' (ECDSA) to the list of known hosts.
Permission denied (publickey).
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(601) [sender=3.0.8]

```I'm at a loss.  Do I need to create a second key for rsync? Is it not possible to use the same key for ssh & for rsync? Do I need to create a new user? Any suggestions would be welcome.

---

### Post by markbl on 2012-05-13
rsync runs over ssh. ssh uses the key not rsync, so it does not make sense to "create a second key for rsync".

You have to get ssh running first before you try rsync. From what you post above it is not clear that you have ssh working for root user to "msdaisy@192.168.1.2". Since you are using sudo for the rsync then it is the root user ssh access you need to test, not your own personal account on the client side. root user needs a private key as well, or copy your own key to root on the client side.

---

### Post by Ms. Daisy on 2012-05-13
Ha. Sometimes the simplest things trip me up.  All I needed to do was remove the "sudo". Thanks for the response- hadn't occurred to me until you said that.

---

### Post by CharlesA on 2012-05-13
Glad you got it working. :)

I ran into problems when I decided to name each of my keys - rsync (ssh in this case) didn't know what key it was supposed to use to connect with. I couldn't get the identityfile option working, so I ended up just adding a config file to ~/.ssh/ with the options I wanted.

Worked like a charm.

I cannot remember the exact page I looked at to set it up, but there is one here:
[http://lookherefirst.wordpress.com/2007/12/17/a-simple-ssh-config-file/](http://lookherefirst.wordpress.com/2007/12/17/a-simple-ssh-config-file/)

---


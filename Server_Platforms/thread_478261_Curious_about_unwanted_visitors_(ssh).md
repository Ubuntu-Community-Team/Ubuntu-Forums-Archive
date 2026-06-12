---
title: "Curious about unwanted visitors (ssh)"
date: 2007-06-19
forum: Server Platforms
---

### Post by thornomad on 2007-06-19
Hi,

I have openssh-server on my ubuntu server.  Last night, I had to turn off the requirement for publickey authentication ("PasswordAuthentication no") because I was adding new keys and then forgot to turn it back on before I went to bed.  Anyway, over the night, there was some interesting activity (at least to me, since this is the first time I have checked /var/log/auth.log, maybe it is common).

I had about one hour's worth of:
```
Jun 19 01:03:41 gaorsk sshd[4953]: Invalid user id from 218.25.161.106
Jun 19 01:03:41 gaorsk sshd[4953]: (pam_unix) check pass; user unknown
Jun 19 01:03:41 gaorsk sshd[4953]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=218.25.161.106
Jun 19 01:03:43 gaorsk sshd[4953]: Failed password for invalid user id from 218.25.161.106 [COLOR="Red"]port 24459[/COLOR] ssh2
``` 

Each time with a different user.  It started around midnight and continued until the one above (last one).  Doesn't look like they ever guessed the correct username but I was wondering: why does it says "port 24459" ?  I have a firewall on my router that only forwards port 22 to my server from the outside world.  Each entry (and there were a lot, sometime a couple each second) has a different port.  Or is that the port established to send the password/publickey enctrypted on ?

Also, the /var/log/auth.log doesn't appear to have let in anyone from anywhere outside my home network (as 218.25.161.106 obviously is, I am on 192.168.0.*) but I am worried -- _should I be_?  I have only had ssh up and running a few days, prior it had required publickey (no passwords).  The morning before I was getting a few of these: 

```
Jun 18 04:55:17 gaorsk sshd[6019]: Invalid user admin from 210.188.206.76
Jun 18 04:56:47 gaorsk sshd[6119]: Invalid user search from 210.188.206.76
Jun 18 04:57:19 gaorsk sshd[6155]: Invalid user halt from 210.188.206.76
```

They don't seem to have gotten very far (I assume it was because passwords weren't allowed). I may look into fail2ban if it keeps up (I know I could change to a non-standard port ... but that doesn't seem to protect me really, just slow people down).

Damon

PS: one user attempt was "fluffy" ... which was darn close to what my real name is!  Dang!

---

### Post by az on 2007-06-19
Denyhosts works well at preventing repeaded attempts.

Just keep a strong password and restrict ssh access as much as you can.  For example, if you only ssh into your box from one or two locations, you can allow them and deny all others.

---

### Post by MJN on 2007-06-19
The port was the clients' ephemeral port that it was connecting *from* - see [http://en.wikipedia.org/wiki/Ephemeral_port](http://en.wikipedia.org/wiki/Ephemeral_port) and [http://www.tcpipguide.com/free/t_TCPIPClientEphemeralPortsandClientServerApplicatio.htm](http://www.tcpipguide.com/free/t_TCPIPClientEphemeralPortsandClientServerApplicatio.htm) for further details.
 
What you are seeing (brute force login attempts) is unfortunately quite common for SSH servers. Mitigation options are many and varied and include strong passwords, restricted logins (specific usernames, source IP etc), disallowing password logins entirely (i.e. only public key authentication as you had), running something like Denyhosts or Fail2ban (having used both I much prefer the latter), moving away from a non-standard port and many more novel and complex methods (an obvious example off the top of my head being port knocking). Thankfully the methods are effective.
 
Plenty of discussion over the years in the archives and if there's one thing in common from all the posts it's that there is no one-size-fits-all solution as it's largely down down to risk management and individual circumstances/preference.
 
Mathew

---

### Post by thornomad on 2007-06-19
Hi,

Thanks for those posts.  Should I keep monitoring the /var/log/auth.log file for attempts ?  Or is there somewhere else I should monitor it ?  I think for now I will just keep an eye on it.  I am pretty secure in the "no password login" bit, since this would mean someone would need the correct privatekey and privatekey passphrase ... which seems unlikely.  

If there number of attempts becomes annoying, I may try fail2ban.

Thanks,
Damon

---

### Post by Gruelius on 2007-06-19
Just install fail2ban, a noob like me managed to do it easily. i dont have global access so i didnt bother but changing the port can also help. Or if you set a port to be forwarded by the router that could also work.

This is the SSH setup for fail2ban's conf file, replace ssh if you change the port number

```
[SSH]
enabled = true
logfile = /var/log/auth.log
port = ssh
timeregex = S{3}s{1,2}d{1,2} d{2}:d{2}:d{2}
timepattern = %%b %%d %%H:%%M:%%S
failregex = : (?:(?:Authentication failure|Failed [-/w+]+) for(?: [iI](?:llegal|nvalid) user)?|[Ii](?:llegal|nvalid) user|ROOT LOGIN REFUSED) .*(?: from|FROM) (?:::f{4,6}:)?(?PS*)
```

---

### Post by MrHorus on 2007-06-19
> **thornomad said:**
> Hi,

Thanks for those posts.  Should I keep monitoring the /var/log/auth.log file for attempts ? 

No - accept it as a fact of life and move on.

If it bothers you either install fail2ban as people suggest or move your SSHd to a non-standard port - mine listens on 2222 now and I never get drive-by attempts on it.

---


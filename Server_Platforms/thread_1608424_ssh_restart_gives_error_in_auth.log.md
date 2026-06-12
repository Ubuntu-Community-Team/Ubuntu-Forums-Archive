---
title: "ssh restart gives error in auth.log"
date: 2010-10-29
forum: Server Platforms
---

### Post by tapas_mishra on 2010-10-29
When ever I restart ssh
> /etc/init.d/ssh restart I see
following line in auth.log
>  sshd[5678]: error: Bind to port 22 on :: failed: Address already in use.That is a headless server.
What does the above line signify or tell and why am I seeing that?
Ubuntu 10.04 64 bit server edition

---

### Post by hawk2010 on 2010-10-29
The error means that a service is already running on port 22 and there for ssh can't use it. 

Do a netstat -a --numeric-ports and see which process is using port 22

Another way to do is configure sshd to run on a different port than 22 and try restarting
/etc/ssh/sshd_config

---

### Post by tapas_mishra on 2010-10-29
```
netstat -plan | grep ssh
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      28576/sshd      
tcp6       0      0 :::22                   :::*                    LISTEN      28576/sshd  
```Well the error I had mentioned is not there right now when I am restarting but it does exist in my log files.I am not at any logical conclusion for this since when before posting here I had checked the netstat output I had same output and restarting ssh was giving the error as I mentioned.
Currently the error is not there in the log /var/log/auth.log
While for previous restarts of ssh the error was there.

---

### Post by CharlesA on 2010-10-29
Does the error occur if you restart ssh like so:

```
sudo service ssh restart
```

---

### Post by tapas_mishra on 2010-10-29
> **CharlesA said:**
> Does the error occur if you restart ssh like so:

```
sudo service ssh restart
```
Yes I had opened the thread for this reason only when I was restarting as you mentioned the error was coming (and it happened more than once which  I had verified) so I opened thread here.
But by the time I posted second reply I do not see this error any more when I restart ssh.
I do not have any logical clue for this.

---

### Post by CharlesA on 2010-10-29
The only real thing I can think of is that ssh wasn't letting go of port 22 when you restarted it before. *shrug*

Did you restart the whole machine between the time when you were getting the original error and when it stopped giving you that error?

---

### Post by aeiah on 2010-10-29
could just be an issue with the way it restarts.. the port might not close on the prior instance before the new instance requests it

---

### Post by jamesbon on 2010-10-29
> **CharlesA said:**
> The only real thing I can think of is that ssh wasn't letting go of port 22 when you restarted it before. *shrug*
Ok this makes sense.

---

### Post by CharlesA on 2010-10-29
> **jamesbon said:**
> Ok this makes sense.
Is there some way I can verify what you said above?

Outside of stopping sshd and seeing if it's still listening on port 22, no.

---

### Post by arrrghhh on 2010-10-29
> **CharlesA said:**
> Outside of stopping sshd and seeing if it's still listening on port 22, no.

Yes, I would do this - you would need physical access to the box to do this, obviously.  So ```
sudo service ssh stop
``` and then ```
netstat -a --numeric-ports |grep :22
``` and see if 22 is in use.

---


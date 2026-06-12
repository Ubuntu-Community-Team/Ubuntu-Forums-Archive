---
title: "my sh file.. Virus? Normal?"
date: 2012-02-07
forum: Security
---

### Post by oklokl on 2012-02-07
Execution
 Are as follows:
 log ..
 I do not command
 Execution ->Red log


#!/bin/bash
gnome-terminal -e "bash -c \"~/home/ufwrun.sh; exec bash\""




#!/bin/bash

## ufw allow out from text

echo "ufw text"
read answer
case $answer in
 yes | y | Yes | YES)
  echo "text"
gksu -- "ufw allow out from 123.0.0.0"
  echo "text";;
  [nN]*)
  echo "text"
gksu -- "ufw delete allow out from 123.0.0.0"
  echo "text";;
  *)
exit 1;;
esac
exit 0

syslog

[COLOR=Red] Feb  7 22:48:51 mypc sudo: pam_ecryptfs: pam_sm_authenticate: /home/mypc2 is already mounted

[/COLOR] 

auth.log

Feb  7 22:52:35 mypc2 sudo: mypc : TTY=unknown ; PWD=/home/mypc ; USER=root ; COMMAND=/usr/bin/x-terminal-emulator
Feb  7 22:57:56 mypc2 sudo: mypc : TTY=pts/0 ; PWD=/home/mypc/desktop ; USER=root ; COMMAND=/usr/sbin/ufw delete allow out from 123.0.0.0
[COLOR=Red]Feb  7 22:58:11 mypc2 sudo: mypc : TTY=pts/0 ; PWD=/home/mypc/desktop ; USER=root ; COMMAND=/bin/bash
Feb  7 23:31:49 mypc2 sudo: pam_unix(sudo:auth): authentication failure; logname= uid=0 euid=0 tty= ruser=mypc rhost=  user=mypc
Feb  7 23:31:52 mypc2 sudo: pam_unix(sudo:auth): conversation failed
Feb  7 23:31:52 mypc2 sudo: pam_unix(sudo:auth): auth could not identify password for [mypc]
Feb  7 23:31:52 mypc2 sudo: pam_unix(sudo:auth): conversation failed
Feb  7 23:31:52 mypc2 sudo: pam_unix(sudo:auth): auth could not identify password for [mypc]

[COLOR=Black] Feb  7 23:31:52 mypc2 sudo: mypc : 3 incorrect password attempts ; TTY=unknown ; PWD=/home/mypc ; USER=root ; COMMAND=/usr/bin/x-terminal-emulator[/COLOR]
Feb  7 23:31:52 mypc2 sudo: cannot execute /usr/sbin/sendmail: &#44536;&#47088; &#54028;&#51068;&#51060;&#45208; &#46356;&#47113;&#53552;&#47532;&#44032; &#50630;&#49845;&#45768;&#45796;


[/COLOR]

---

### Post by CharlesA on 2012-02-07
Where did you get that script?

It looks like an init script that allows traffic out to 123.0.0.0, which is a public IP block.

That isn't something you would normally be running.

Are you running VNC or SSH or something like that?

---

### Post by emiller12345 on 2012-02-07
> **CharlesA said:**
> 
It looks like an init script that allows traffic out to 123.0.0.0, which is a public IP block.


I just tested the command
```

~$ sudo ufw allow out from 123.0.0.0

```
and it's not actually an IP block, but a single address, like this
```

-A ufw-user-output -s 123.0.0.0/32 -j ACCEPT

```

it might be a poorly coded IP block

---

### Post by CharlesA on 2012-02-07
Ah. I was guessing on that bit since a normal IP address wouldn't end in 0, as that is the network address.

Still looks a bit fishy to me.

---

### Post by oklokl on 2012-02-07
> **CharlesA said:**
> Where did you get that script?

It looks like an init script that allows traffic out to 123.0.0.0, which is a public IP block.

That isn't something you would normally be running.

Are you running VNC or SSH or something like that?


 ip 123, is not a ... My house is ip. xxx.xxx.xxx.xxx
Changed 
   In order to release  (my ip Hiding) 



 
I made a
but 
Produce strange results





Infection?
this file  were manipulated?


 I VNC, ssh does not use.
Did not do anything T^T..

---

### Post by CharlesA on 2012-02-07
I don't know if it was manipulated or not without knowing the source.

It just seems like an odd script to run. Is there a reason you are running it?

Is VNC accessible from the internet?

As a general rule, you shouldn't run a script unless you know exactly what it does.

---

### Post by oklokl on 2012-02-07
> **CharlesA said:**
> I don't know if it was manipulated or not without knowing the source.

It just seems like an odd script to run. Is there a reason you are running it?

Is VNC accessible from the internet?

As a general rule, you shouldn't run a script unless you know exactly what it does.

when I will need p2p.  ->qbittorrent
Before use
out allow ufw..

no vnc
 Does not have


add ufw my ip 

Design simplicity


yes -> add my ip out open

no -> delete my ip..
several times
register

---

### Post by CharlesA on 2012-02-07
By default, ufw allows all outbound traffic, so you wouldn't need to allow it out to specific IP addresses.

I don't think your external IP is 123.0.0.0, in any case, as that is not a valid IP address.

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by oklokl on 2012-02-07
> **CharlesA said:**
> By default, ufw allows all outbound traffic, so you wouldn't need to allow it out to specific IP addresses.

I don't think your external IP is 123.0.0.0, in any case, as that is not a valid IP address.

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

temporarily ip..
view..

my ip .. hidden
txt...Report

ex>
123.123.123.123
111.111.111.111

---


---
title: "Kubuntu Natty Finding What Programs Have Open Ports"
date: 2011-06-25
forum: Security
---

### Post by amnite on 2011-06-25
Well I'm kinda a paranoid person, and got bored and ran a port scan from 0 to 500000 and turned up some interesting results, I was wondering how I find the programs tied to each open port. Its my computer and I'd like to very well know what programs are needing these ports and for what usage. THX

---

### Post by Zorael on 2011-06-25
Try '**netstat -tawp**'.

---

### Post by amnite on 2011-06-25
My scanner brought up 14 open port connections, while netstat gave me 5....

---

### Post by The Cog on 2011-06-26
"netstat -tawp" will not show the listening porst which is what I think Zorael is wanting. "netstat -lntuw" will show the listening ports only. Adding -p will also name the process that owns that port, but you will need admin rights to see that info, so use "sudo netstat -lntuwp".

---

### Post by amnite on 2011-06-26
TY that is exactly what im looking for.

---

### Post by amnite on 2011-06-26
Anywhere u no that i can learn more bout netstat or a similar program using python?

---

### Post by The Cog on 2011-06-26
I picked them up mostly from hanging around these forums. Once you hear about any command, you can use the man command to learn more about it. For instance, "man netstat" will give the manual page for netstat that lists all the options etc. Use "q" to quit when you've finished reading.

---

### Post by Bachstelze on 2011-06-27
To identify the process listening on a given port:

```
sudo fuser -n tcp PORT
```

Then note the PID of the process and do

```
ps aux | grep PID
```

For example:

```
firas@wakaba ~ % sudo fuser -n tcp 22                           
22/tcp:               1187
firas@wakaba ~ % ps aux | grep 1187  
root      1187  0.0  0.0  49312  2656 ?        Ss   06:20   0:00 /usr/sbin/sshd -D
firas     2883  0.0  0.0   9940   844 pts/1    S+   06:56   0:00 grep --color=auto 1187

```

---


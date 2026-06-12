---
title: "Command not found"
date: 2010-12-10
forum: Server Platforms
---

### Post by wwoollff on 2010-12-10
Hi,

I found a strange behaviour on a Ubuntu 10.04. Here are a couple of commands and their output:
```
sudo su
sudo: parse error in /etc/sudoers near line 24
sudo: no valid sudoers sources found, quitting
top
File "/usr/lib/command-not-found", line 10, in <module>
    import CommandNotFound
ImportError: No module named CommandNotFound
reboot
 File "/usr/lib/command-not-found", line 10, in <module>
    import CommandNotFound
ImportError: No module named CommandNotFound
```

Same for reboot, init 6, vim, iptables -nvL etc. When I do a ls in /, it doesn't show anything. When I issue a ls-la /, is says: total 0. 
Here is my env:
```
SHELL=/bin/bash
TERM=xterm
SSH_CLIENT=... 4213 22
SSH_TTY=/dev/pts/0
USER=...
LS_COLORS=...
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
MAIL=/var/mail/...
PWD=/
LANG=en_US.UTF-8
HOME=/home/...
SHLVL=2
LOGNAME=...
SSH_CONNECTION=... 4213 78.97.94.12 22
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=localhost:10.0
LESSCLOSE=/usr/bin/lesspipe %s %s
_=/usr/bin/env
OLDPWD=/usr/bin
```

Maybe you could point me in the right direction to solve this problem. Thx.

P.S. no, I cannot gain root privileges, and I can restart it in safe mode only next week, because the server is in a different location.

---

### Post by ajgreeny on 2010-12-10
Sounds as if your /etc/sudoers file has gone awry in some way at line 24, which in my system is ```
#includedir /etc/sudoers.d
```
My whole file is ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset
# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```which may be useful to you if you need a default version to replace yours.

Make sure you edit the file with ```
sudo visudo
```

---

### Post by wwoollff on 2010-12-10
I would happily do that, but I cannot do "sudo visudo", because it says "sudo: parse error in /etc/sudoers near line 24", or "visudo" ( File "/usr/lib/command-not-found", line 10, in <module> ...). Also, this doesn't explain the behaveur of ls and the other commands(expecialy the error regarding the command-not-found).

Thx for the quick reply.

---

### Post by elico on 2010-12-10
dont use vi...

u can try two things.
one is to boot in level 1 using the "single" added to your kernel line in grub and then just use
cat /etc/sudoers 
or just 
cat /etc/sudoers 

im working as root all the time so i dont really care about this sudo stuff.

i really  dont like the sudo idea of ubuntu that you dont need root access...

---

### Post by wwoollff on 2010-12-11
True. In my experience, sudo generates only problems, and this issue is an example. I cannot gain root priviledges on my server, because of Ubuntu sudo policies. 

I'll make this thread resolved. My solution: change the OS to Debian.

---

### Post by ingeva on 2010-12-11
> **wwoollff said:**
> True. In my experience, sudo generates only problems, and this issue is an example. I cannot gain root priviledges on my server, because of Ubuntu sudo policies. 

I'll make this thread resolved. My solution: change the OS to Debian.
I have NEVER experienced any problems with sudo. IMHO the ubuntu people have made a wise decision here. Besides, Ubuntu is based on Debian, and developed further than Debian. Honestly I haven't tried it, but how can it be better? :)

---

### Post by wwoollff on 2010-12-11
Comparing Debian and Ubuntu is like comparing apples with peaches.(they are different OSs with different policies).Saying that one is better then other is so..Window-ish, and it's not fare to the linux community. If you want a linux distribution for you desktop, you use Ubuntu. If you want to build a web farm, you use Debian. If you want to build a massive SAN, you use Solaris. If you want to shoot yourself in the foot, and become a guru, you use Slackware. It's simple.

But, this is not about Debian and Ubuntu. It's about a faulted server.

---


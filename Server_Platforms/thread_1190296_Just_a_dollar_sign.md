---
title: "Just a dollar sign"
date: 2009-06-17
forum: Server Platforms
---

### Post by Xen0n on 2009-06-17
Hello. i just bought a VPS with ubuntu on it. but when i add a new user like

useradd -d /home/timmi -m timmi
passwd timmi

then when i log into it, it just shows a dollar sign

lalalala
lalalalalalalala
alalalla
laalallalalala
$

but when i log in as root it shows root@host:~#

i can fine ls, and stuff like that when i got the dollar sign but i can't use tab or see any "username@host" how do i add this to a user?

---

### Post by estyles on 2009-06-17
I'm pretty sure that it's just a question of your user's default shell.  You want to use bash, I assume.  Try typing "bash" at the dollar sign prompt, and see if that gets you what you want.

If so, then you just have to find out how to change your user's default shell.  You'll need to log in as root to do it.  And you'll probably have to do a quick search on changing default shell, because I don't know off hand how to do that.  Shouldn't be too difficult.

---

### Post by zharmad on 2009-06-17
You may have to specify /bin/bash since $PATH is (if I recall correctly) a bash-shell variable that isn't set without bash running.

---

### Post by Xen0n on 2009-06-17
hey, i solved it. thanks for the reply where i just should write bash, it worked. and i found the solution. just edit /etc/passwd and make sure the last thing in your userline is /bin/bash and not /bin/sh like this

timmi: x:1001:1001::/home/timmi:/bin/bash

not

timmi: x:1001:1001::/home/timmi:/bin/sh

(without the spaces between : and x)

---

### Post by swisstone198 on 2009-06-17
You can see what shell a user is using by looking in /etc/passwd, its at the end. 

You can change a users shell by 

chmod -s shell user

But you get a # prompt at the root terminal to signify a superuser. ($ is normal user)

---

### Post by estyles on 2009-06-17
Yeah, sh sucks.  I guess maybe it's the default because it's lightweight(?), but on a modern machine, bash or zsh don't take up anything even remotely noticeable in terms of cpu time or RAM.

---

### Post by terazen on 2009-06-17
Oddly if you run `ls -la /bin/sh` it's just a symbolic link to /bin/dash.  I have no idea what the motivation was for this setup.

---

### Post by dfreer on 2009-06-18
You could also have just used adduser instead of useradd, which should set the default shell to bash IIRC. Much easier IMO.

---


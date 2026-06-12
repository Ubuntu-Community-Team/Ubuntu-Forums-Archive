---
title: "sudo without password - security issues ?"
date: 2006-04-29
forum: Server Platforms
---

### Post by kabus on 2006-04-29
I am running Ubuntu on a single user desktop system at home and, try as I might, I can't think of any compelling reason why sudo should ask me for my password (I am already logged in, after all).
But before I just disable the password protection I'd like to ask if this is a bad idea, and why ?

---

### Post by codejunkie on 2006-04-29
[quote=kabus]I am running Ubuntu on a single user desktop system at home and, try as I might, I can't think of any compelling reason why sudo should ask me for my password (I am already logged in, after all).
But before I just disable the password protection I'd like to ask if this is a bad idea, and why ?[/quote]
yes it's a bad idea, if you haven't enabled the root account. ubuntu uses sudo to preform actions as root, if you disable sudo, you can't preform any administraton tasks that requires root access like synaptic.

---

### Post by kabus on 2006-04-29
I am not talking about disabling sudo. 
I just don't want it to ask for my password anymore.

---

### Post by codejunkie on 2006-04-29
[quote=kabus]I am not talking about disabling sudo. 
I just don't want it to ask for my password anymore.[/quote]
yeah i noticed that after i re-read your post sorry about that 
yes it does pose some risks by disabling the prompt for passwords. for instance if you run a malicious script or enter a command wrong in the command line, it can cause you problems. but i disable it myself, because i can't stand to be asked for the password over and over, and i haven't had any problems. just never run any shell scripts without looking them over first  or just copy and paste commands into the terminal without knowing what they do first.

---

### Post by kabus on 2006-04-29
Ah, so it doesn't really make a difference.
Thanks !

---


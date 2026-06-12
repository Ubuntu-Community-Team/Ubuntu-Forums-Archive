---
title: "Make a program work like a service?"
date: 2009-11-03
forum: Server Platforms
---

### Post by rocky5051 on 2009-11-03
First off, I'd like to say that I'm pretty new to Ubuntu server and working with SSH, so if what I'm asking is absurd, I'd appreciate not getting flamed for it. :)

Anyway, I purchased a VPS so I could run an AssaultCube server. So far, it works. I can login via SSH, start the run script that I created and have the server going no problem.

However, my laptop with it's baked hardware (including the wireless adapter) and less-than-satisfactory wireless stability causes SSH to drop it's connection, or even worse, my laptop deadlocks, killing SSH and thus killing the AssaultCube server I started! I don't have any other option as far as internet connectivity goes, nor a "better" machine to use, unfortunately.

What I would like to know, is if there is any way to make this run script get initialized automatically whenever Ubuntu server is booted up? That is, make it do it's thing without me starting manually, and not have to worry about it stopping because my SSH connection dies.

Thanks in advance. ):P

---

### Post by KeLa on 2009-11-03
You can try following with ssh

nohup yourcommand &

That will start process and it will keep running even after ssh connection is lost.
Look also "man nohup"

---

### Post by rocky5051 on 2009-11-03
Yep that did the trick. What I'm curious about, however, is if I reconnect and login, will the process keep running for the game server or will it be terminated?

The reason I don't dare do it myself is there's people playing on it now and I don't want to make them suffer through more instability. lol

---

### Post by KeLa on 2009-11-03
It will keep running until reboot of server or program terminated with kill command
Other way to do it is
ssh into your host:

#screen bash
#yourcommand.sh &
#screen -d 
#exit
#exit

And it will continue to run.

Run:
#screen -r

-d = detach
-r = reattach

(I have not tried this myself but the first i have used many times and that first you
can also put to cron if process must run again on regular base)

---

### Post by rocky5051 on 2009-11-03
Well, unless something goes horribly, horribly wrong or I need to inspect something, it's going to run 24/7. I'll keep that second method in mind, though.

Thanks again. :KS

---

### Post by Sporkman on 2009-11-05
There's a script - /etc/rc.local - which gets executed on startup. You can put the command to start your service there.

---


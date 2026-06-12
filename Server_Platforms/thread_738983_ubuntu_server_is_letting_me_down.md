---
title: "ubuntu server is letting me down"
date: 2008-03-29
forum: Server Platforms
---

### Post by johnman145 on 2008-03-29
I have installed ubuntu server edition on a computer about a year ago and although it was a tough start i finally managed to let everything run smooth. Now i have to install a server again, so i downloaded and installed ubuntu 7.1  without a problem.  After the install i logged in and did a apt upgrade.

The thing is however,  when i wanted to install webmin, which is really a must if you cant remember all those little commands, it was unavailable. Tried it again 3 times, just out of frustration, but same result. Then i just turned it of with a sudo shutdown now and even that didn't work anymore. 

Well i did find some tips, i could use sudo poweroff (worked) and i could manually download the webmin from the original site. 

But being a kind of linux noob i am wondering:
- why did some guy removed webmin from the repo? Wasn't it enoughto give a warning? I mean some guys actually need stuff like that just to get every nicely configged

- why do i have to use poweroff now instead of shutdown? can't it figure out by itself if i tell it to shutdown now i want to shutdown now? I kind of have the feeling if the system cant even properly shutdown... well, thats a bad omen isn't it ?!.

---

### Post by faulkes on 2008-03-29
> **johnman145 said:**
> - why did some guy removed webmin from the repo? Wasn't it enoughto give a warning? I mean some guys actually need stuff like that just to get every nicely configged


There was significant discussion within the community and upstream 
about the removal of webmin from the repositories.  
I will not open the can of worms which is that discussion here.

The replacement for webmin on Ubuntu is the eBox set of 
packages.  These are currently in the repositories.

> 
- why do i have to use poweroff now instead of shutdown? can't it figure out by itself if i tell it to shutdown now i want to shutdown now? I kind of have the feeling if the system cant even properly shutdown... well, thats a bad omen isn't it ?!.


The 'shutdown' command is used by Sys V based systems,
Ubuntu has switched to Upstart (which has no concept of 
run-levels).  The 'shutdown' command which is provided emulates
the former ability, some changes in it's use may have occurred.

I believe the command you want to issue is:

```

sudo shutdown -P

```

Thanks,

Faulkes

---

### Post by kerry_s on 2008-03-29
did you turn on all the repo's in /etc/apt/sources.list?

shutdown command is->
sudo shutdown -h now

"-h" for halt
"-r" for reboot

you can also use the commands straight
sudo halt
sudo reboot

debian is much better as a server.
net installer-> [http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

for newer stuff, i recommend adding the lenny repo's.

---

### Post by Mithrilhall on 2008-03-29
I agree...Debian is a much better choice for server projects.

[http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

I run webmin on Debian and it works great.

---

### Post by tmillic on 2008-03-29
That's odd. I'm using Ubuntu 7.1 server edition, and the shutdown command works fine. I once installed it with the wrong ACPI settings, and it wouldn't shutdown. That was my fault.
What's webmin?
Even if you do install a gui, you might try keeping a small notebook at hand that you can write notes into about commands and how to use them. None of us can remember all the "little commands", but once you're familiar enough with them, you'll find you have much more control over your machine with or without a gui.

---

### Post by tmillic on 2008-03-29
Oops. I was posting before having coffee again. The other guy had the question about the gui. My apologies.

---

### Post by johnman145 on 2008-03-29
Thanks guys for the advise, but i think ill just switch. I already had an centos dvd and now im downloading debian if centos will disappoint me to much since im used to debian and ubuntu. I dont want to start i riot here, but to just throw away something like webmin is stupid from my point of view. I was happily using the terminal, learning ubuntu and linux as a went along and using webmin when i got stuck i slowly but surely was getting into it. And now its removed cause somebody thought that a v0.1 program is better or safer?

I dont want to wine, but i am genuinely disappointed by this. I was just getting the hang of it...

---

### Post by kerry_s on 2008-03-29
i hate to tell you this, but it's not in the debian repos either. a quick look at there site says you need to add the repo or download it.

 [http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

---

### Post by Metro_Dan on 2008-03-29
Just download the Webmin .deb from there site and install it on Ubuntu works just fine. Who gives a hell if its in the repos or not

---

### Post by netlogic on 2008-03-29
I'm sorry, but you are letting me down. You should spend time understanding how repos work before blaming on others.

---

### Post by jorge.maravi on 2008-06-26
Hi
I have a weird problem. I have installed ubuntu server 7.0 in a compaq server it works fine and i have installed also proftpd, ssh server and samba server. Today i shutdown the server using "init 0" as root, and it went down. But after a couple hours the server was up and running!!!! Have you had a case like this before?

---


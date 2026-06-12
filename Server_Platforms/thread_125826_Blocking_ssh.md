---
title: "Blocking ssh"
date: 2006-02-04
forum: Server Platforms
---

### Post by caffinide on 2006-02-04
I need help on how to block ssh. At school, everyone knows the password for root and Mr. Elkner doesn't want us to change it. If I keep going like this, I won't get any work done, because i have to have the network cable unplugged and if i don't stop them they will all get A's and credit only for stealing my work. So, I need to stop ssh into my computer but still allow ssh into others computers.

---

### Post by awi on 2006-02-04
Take a look at this thread: 
[http://ubuntuforums.org/showthread.php?t=57111&](http://ubuntuforums.org/showthread.php?t=57111&)

---

### Post by imagine on 2006-02-05
```
sudo /etc/init.d/ssh stop
```
That will stop the SSH daemon.

To start it again:
```
sudo /etc/init.d/ssh start
```

---

### Post by Greyice on 2006-02-05
1. Change the port from 22 to something above 1024 and less than 65535.
2. Disable root from logging in.

Both options are available in /etc/ssh/sshd_config

---

### Post by LordHunter317 on 2006-02-05
[QUOTE=Greyice]1. Change the port from 22 to something above 1024 and less than 65535.[/quote]No, this doesn't do a thing.  Even tools like DenyHosts are better in poor reactionary countermeasures.

---

### Post by steve.horsley on 2006-02-08
Have a look at System->Administration->Services. 

You can also disallow root login by ssh by editing /etc/ssh/sshd-config. You may need to restart sshd after changing the config file though.

---

### Post by MJN on 2006-02-08
That won't stop someone taking root privileges with 'su' once they're in though...

Why won't Mr Elkner change the root password? And why does everyone know it? Does he have an account on the server? If so, a quick **rm -fr ~mrelkner** (optionally taking a backup first...) might make him reassess his somewhat laid-back security policy... ;)

Mathew

---

### Post by caffinide on 2006-02-09
Elkner, while awesome, kinda made a mistake in telling everyone the root password. however, the tip that imagine solved my problem

---

### Post by caffinide on 2006-02-09
I also am not dealing with what you would call "geniuses"... actually, i am the genius of them...

---


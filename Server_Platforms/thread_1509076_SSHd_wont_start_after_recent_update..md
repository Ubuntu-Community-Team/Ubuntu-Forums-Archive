---
title: "SSHd wont start after recent update."
date: 2010-06-13
forum: Server Platforms
---

### Post by Chaosratt on 2010-06-13
Updated two SSH packages today and now SSHd wont start.
Worked fine an hour ago, and I'm still logged onto the server via pre-existing SSH sessions, but now I obviously cannot start new ones.
```

paine@pandora:~$ sudo /etc/init.d/ssh start
 * /dev/null is not a character device!
paine@pandora:~$
```

---

### Post by CharlesA on 2010-06-13
Try this:

```
sudo service ssh start
```

---

### Post by Chaosratt on 2010-06-13
```
paine@pandora:~$ sudo service ssh start
ssh stop/pre-start, process 15726
paine@pandora:~$
```

But I get "connection refused" from my clients (putty, filezilla, etc)

---

### Post by CharlesA on 2010-06-13
If you have console access, see if you can stop it then start it back up.

---

### Post by Chaosratt on 2010-06-13
A reboot seems to have solved the issue, but I just neutered a pretty good uptime :(

---

### Post by CharlesA on 2010-06-13
Been there, done that, got a t-shirt. :(

---

### Post by Chaosratt on 2010-07-03
This problem cropped back up again. I really wish I didn't have to restart the system every time I make an SSH config change, does anyone know whats going on here?

---

### Post by Chaosratt on 2010-07-03
Ok, I've logged in via console and completely purged ssh via "sudo apt-get --purge remove openssh-server" and then reinstalling it, same deal.

Looks like seting up permanent console access via my host isnt the nightmare I thoguht it was going to be, and I can even ssh into the console. I'll just do that for now.

---

### Post by CharlesA on 2010-07-03
After you purge SSH, can you make sure that there is no directory here:

```
ls -ld /etc/ssh/
```

I haven't had any problems with SSH and my system is up-to-date.

Which version of Ubuntu are you using?

---

### Post by Chaosratt on 2010-07-03
There were files in /etc/ssh after purging. I deleted them and reinstalled, to no effect.

---

### Post by CharlesA on 2010-07-03
Hrm wonder what the problem is. :(

---

### Post by inphektion on 2010-07-04
> **Chaosratt said:**
> This problem cropped back up again. I really wish I didn't have to restart the system every time I make an SSH config change, does anyone know whats going on here?
get console access:

run ps aux | grep ssh
to make sure its all stopped. then try starting it...
run tail -n 50 /var/log/auth.log
anything there?

if not then again make sure all stopped and run sshd -t
does everything validate fine?

if so run ssd -d -e

then try to ssh in.
anything throw up on the screen?  if so save to a text file and paste in here.

---


---
title: "How to stop clamav?"
date: 2012-01-11
forum: Server Platforms
---

### Post by o0TarZan0o on 2012-01-11
Hi, my virtual machine ubuntu only have 64mb ram, I try install clamav (clamav-daemon clamav-freshclam) to scan virus for mail service but it can't operate normally (lag), i want stop it to do other things, you know how to ... ?

---

### Post by jonobr on 2012-01-11
Im guessing there is a stop start in init.d

so if you

```
sudo /etc/init.d/clamav-daemon stop
```

then 


```
sudo /etc/init.d/clamav-daemon status
```

to ensure its stopped,
same with the other one.
Theres a lot of FaQs on the ineterweb about this 

[Heres an old post]("http://www.howtoforge.com/forums/archive/index.php/t-44443.html") on uninstalling

googling around may find newer material

---

### Post by o0TarZan0o on 2012-01-11
First time, i used command:

```
/etc/init.d/clamav-daemon stop
```

After that, i test processes in system:

```

ps aux
```

It still display (clamav). I was thought command didn't get efficient. Maybe antivirus of linux operate same as Windows (we must reboot)

Anyway, thanks :)

---

### Post by jonobr on 2012-01-11
Hey

Did you  try stopping clamav-freshclam also?

Maybe start both again and compare ps when started and stopped.

Lastly if 

```
sudo /etc/init.d/clamav-freshclam status
and 
sudo /etc/init.d/clamav-daemon 
```

status say stopped, maybe their are other things you need to look for

---

### Post by o0TarZan0o on 2012-01-11
When I stopped both daemon, freshclam services and test again (ps aux), I didn't see any "track" of clamav. Thanks so much :D

---

### Post by jonobr on 2012-01-11
Excellent,

Nice guess by me eh?

Recommend you mark as solved in thread tools for anyone searching for information

---


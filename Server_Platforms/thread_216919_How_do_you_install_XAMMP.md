---
title: "How do you install XAMMP?"
date: 2006-07-16
forum: Server Platforms
---

### Post by khaledaboualfa on 2006-07-16
I'm trying to setup a local testing server. I've just migrated from WIndows and I used to use XAMMP for all my needs. I've done all the requirements on the XAMMP website:
[http://www.apachefriends.org/en/xampp-linux.html#374](http://www.apachefriends.org/en/xampp-linux.html#374)

The problem is that when I run the command to run XAMMP, or LAMP in this case:

```
/opt/lampp/lampp start
```

I get an message that tells me to start XAMMP from root. Is there a way to get around this and just have an icon for me to just run XAMMP from? I'm a newbie at all this, but I checked out the forums first but didn't find an suitable thread, if you can post it that would be great. THanks a bundle.

---

### Post by DoorGunner on 2006-07-16
you can try 

$sudo su
it will give you
root$ prompt.....then use /opt/lampp/lampp start

but you may have to add yourself to the lamp group. you will have to research that part.

---

### Post by khaledaboualfa on 2006-07-16
Thanks DoorGunner, seems to work fine now. 

On a sidenote: This whole root business is a bit annoying for the home user. I can understand it's need for multiple users, but for the lone user, really annoying. I'm going to try and see if there's anyway around that.

---

### Post by Kurt` on 2006-07-16
You could simply run everything as root, but then you have all the security of Windows (i.e. none).

After your initial setup, 99% of your time spent on the system doesn't require root access, so sudo is fine for most users (that I have come across anyways). Being prompted occasionally for your password for certain things (installing updates, changing system time, etc.) is worth far more than the trouble it requires in terms of security.

---


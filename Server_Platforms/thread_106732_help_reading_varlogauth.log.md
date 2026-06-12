---
title: "help reading /var/log/auth.log"
date: 2005-12-21
forum: Server Platforms
---

### Post by davebradford on 2005-12-21
i am having some problems reading my log file.. problem being i dont know what i am looking for! my log has enties for every mintue of every hour.. it's getting very confusing.. does this mean i am being hacked all the time!

---

### Post by localzuk on 2005-12-21
Don't worry too much. There are a lot of SSH bots out there that try to connect to ssh servers by trying many different usernames and passwords.

As long as you use a decent password (alpha numeric, caps and special characters) you should be fine. 

I am guessing you have lines like:

```

Dec 18 12:20:18 blah sshd[30294]: Failed password for invalid user postmaster from ::ffff:218.206.92.226 port 60532 ssh2

```

or 

```

Dec 20 19:54:50 blah sshd[1045]: reverse mapping checking getaddrinfo for 100.158.93.212.in-addr.arpa.cluj.rdsnet.ro failed - POSSIBLE BREAKIN ATTEMPT!

```

These are failed connections of 2 types. Personally, I have taken to ignoring them... Most admins do IME.

---

### Post by davebradford on 2005-12-22
on closer inspection i can see that they are just cron jobs that need root permission! not to worry.. thanks..

---


---
title: "Server suddenly hangs"
date: 2011-08-30
forum: Server Platforms
---

### Post by inbreed on 2011-08-30
Hi there,

i am currently facing the problem that one of my servers suddenly hangs.

with hangs i mean, that it does not respond to any port anymore, and via serial console, all i see is:


```
Press any key to continue..
Press any key to continue..
Press any key to continue..
Press any key to cont
```

end thats it..

So this messages actually only appear when grub is waiting for eventual user actions.

However, so i restart the server an voila, working again as it should.

Logs: /var/log/syslog, searched fot the time it crashed, not message that differs.
df -h -> on each partition i have more than 30% free, no partition < 400GB.
munin-logs: nothing special either. no high IO, no full ram, no high/low anything.
memtest86 -> 0 errors


Due to this i really have no clue what to search for, i would love to ask google - but what?
"Badass sysadmin in server-room presses random reset button" will propably not fit ;)

The server is running a mySQL, nginx, some rails apps. nothing special at all, important to work though.


So anyone any idea what i could analyze? what i could measure?


Best Regards and Thanks
Daniel

---


---
title: "Shutdown a Dapper server remotely via ssh"
date: 2007-03-23
forum: Server Platforms
---

### Post by timmbob on 2007-03-23
Hi,

my problem is that when i use ssh to connect remotely to my server and then try to shut it down (sudo shutdown -h now), i will not halt properly like a system that i am locally on but just go into some state of "hibernation".
That is, it will be up and running in as soon as i reconnect via ssh or call the webserver running on the machine etc.

But what i want it to do is to shutdown and stay down until someone hits the powerswitch locally.

Any suggestions what i am missing or what to configure to get this working?

Regards,
timmbob

---

### Post by dv5237 on 2007-03-23
```
sudo shutdown -hP now
```

---

### Post by timmbob on 2007-03-23
Thanks that works.
Maybe a rude RTFM would have also been appropriate ;-)

---

### Post by Aberrix on 2007-03-23
I didn't know this either... good info ;)

---


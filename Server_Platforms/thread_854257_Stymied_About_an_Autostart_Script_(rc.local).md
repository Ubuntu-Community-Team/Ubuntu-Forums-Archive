---
title: "Stymied About an Autostart Script (rc.local)"
date: 2008-07-09
forum: Server Platforms
---

### Post by Mysterious Error on 2008-07-09
Hi, this is my first post, so I'd like to express my gratitude to all Ubuntu and FOSS contributors for making the world a better place.

Anyway, I'm trying to get my server (8.04 LTS) to execute [museekd]("http://packages.ubuntu.com/feisty/museekd") (<-link) on boot, and have it run until server shutdown/restart. I've tried using this rc.local script to accomplish my goal but it's not working:


/etc/rc.local
(And yes, I set it's executable privileges)
```
#!/bin/sh -e
# ...snip...

# store nohup.out in /var/logs/mu
cd /var/log/mu
nohup museekd &

exit 0
```

**A Note About nohup:**
I decided to use nohup, because I want to be able to store the messages that museekd would otherwise print to console for later debugging. I could use the log in ~/.museekd/logs/syslog exlusively, but it doesn't log what is shown in console. This is how I found the proceeding error.

My problem starts after rc.local loads.  Museekd doesn't load, and it prints this arcane error into /var/logs/mu/nohup.out:

```

terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
```

I'm pretty sure that this bug is specific to museekd. It will be ideal if I can get it loaded automatically on boot, because I wont have to manually start museekd after every system load.

Hopefully some Linux gurus here can help me find a workaround.

Thanks!

---

### Post by windependence on 2008-07-09
Does it start ok from the command line and run in the background?

What does this software do?

-Tim

---

### Post by Mysterious Error on 2008-07-09
windependence:

Yes and yes.

See my link in the first post for the description & package listing.

I'm pretty certain the error is being caused by museekd itself. I probably should file a bug report to the dev(s) involved.

I'm wondering if there's another logical way to automatically start museekd without using init.d or rc.local.

---

### Post by Mysterious Error on 2008-07-10
Bump

---

### Post by highonv8splash on 2008-07-10
is the nohup really required just to generate a log output?

Would

```

#!/bin/sh
museekd > /var/log/mu.log &

```

work for the same end here?

---

### Post by windependence on 2008-07-11
He doesn't even need to make it a script for just one command. he can just execute it directly in the startup file.

-Tim

---


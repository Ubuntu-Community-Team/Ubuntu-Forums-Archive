---
title: "Both file sync and control panel not working"
date: 2011-07-03
forum: Ubuntu One (CLOSED)
---

### Post by mogray5 on 2011-07-03
Hi,

File sync doesn't not appear to be working and my logs are filled with this error:

**"Connection to the other side was lost in a non-clean fashion."**

The sync daemon after awhile will take up 1.3gb of memory and will peg one of the processors.

I also get connection errors for the control panel app.

I'm on Ubuntu 11.04 64bit.

Anyone have any suggestions?

---

### Post by duanedesign on 2011-07-06
Can you check the file ~/.cache/ubuntuone/log/syncdaemon-exceptions.log to see if it contains anything. You can access it with the following command run in a Terminal.

```
gedit ~/.cache/ubuntuone/log/syncdaemon-exceptions.log

```

If their is nothing in that file you can look in ~/.cache/ubuntuone/log/syncdaemon.log for any errors. If you would like help deciphering the log file you can post it in this thread (please use the CODE tags). The log does contain file names. If that is an issue you can send the log to me as a Private Message and I will look at it for you.

You may need to increase the logging level in order to get more information. You can do that with the following steps.

1. Open Applications->Accessories->Terminal 

2. Run this command:
```
 echo -e "[logging]\nlevel = DEBUG" > ~/.config/ubuntuone/logging.conf; u1sdtool -q; u1sdtool -c
```

This will add more information to the syncdaemon.log.

thank you,
duanedesign

---


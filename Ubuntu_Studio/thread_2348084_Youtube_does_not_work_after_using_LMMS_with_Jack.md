---
title: "Youtube does not work after using LMMS with Jack"
date: 2016-12-31
forum: Ubuntu Studio
---

### Post by jjaakkol on 2016-12-31
1. Ubuntu Studio running (Jack not running)
2. Firefox and youtube works fine
3. LMMS started  
4. LMMS stopped
5. Jack stopped also
6. Youtube does not work

I have searched from WWW and got more confused. Some page say that Jack and Youtube can not work same time. So why youtube is not working even Jack is stopped.

From syslog when trying youtube video after LMMS:

pulseaudio[2082]: [alsa-sink-AD1984 Analog] alsa-sink.c: Error opening PCM device front:0: Device or resource busy

ThinkPad-T61 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

---

### Post by jejeman on 2016-12-31
There is your answer.
Are you sure JACK is really dead?
The only way is to kill it yourself.

---

### Post by jjaakkol on 2017-01-01
```
jack_control status
``` shows that it is stopped.
 
BUT ```
ps -A | grep jack
``` shows that jackdbus is still there. 

```
jack_control exit
``` does not kill jackdbus process.

After killing it by ```
sudo killall -9 jackdbus
``` youtube works again.

---


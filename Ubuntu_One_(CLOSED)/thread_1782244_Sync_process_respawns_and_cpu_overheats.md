---
title: "Sync process respawns and cpu overheats"
date: 2011-06-14
forum: Ubuntu One (CLOSED)
---

### Post by JoakimP on 2011-06-14
I have experienced this problem a couple of days now.
The ubuntu-syncd process seems to create a ubuntuone-sync-<user> process. This restarts in an infinite loop and creates overload and the cpu to overheat.

I have stopped the ubuntuone-launch process in the Startup Applications, but this is not really what I want.

Any ideas?

---

### Post by duanedesign on 2011-06-20
Sorry to hear Ubuntu One is not working as expected. Could you please check the following file to see if it contains anything.

~/.cache/ubuntuone/log

You may need to type Ctrl + h or View > Show Hidden Files to see the .cache folder in Nautilus. You can also use the following command in a Terminal to view the file.

```
gedit ~/.cache/ubuntuone/log
```

thank you,
duanedesign

---

### Post by duanedesign on 2011-06-20
Sorry to hear Ubuntu One is not working as expected. Could you please check the following file to see if it contains anything.

~/.cache/ubuntuone/log/syncdaemon-exceptions.log

You may need to type Ctrl + h or View > Show Hidden Files to see the .cache folder in Nautilus. You can also use the following command in a Terminal to view the file.

```
gedit ~/.cache/ubuntuone/log/syncdaemon-exceptions.log
```

thank you,
duanedesign

---


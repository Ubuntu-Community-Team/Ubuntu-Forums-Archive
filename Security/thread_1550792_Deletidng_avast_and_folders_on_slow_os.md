---
title: "Deletidng avast and folders on slow os"
date: 2010-08-11
forum: Security
---

### Post by wahoobob on 2010-08-11
I installed avast anti-virus on my 10.04 T42p thinkpad.  It immediately slowed to a walk! and the registration number did not work and caused an error message.  I tried to reinstall the program with no improvement/same result.  then tried to remove the program from the machine with dpkg.  Seemed to get rid of it but some of the folders it created are still there and won't let me trash them.  The machine still seems slow, so how do I get rid of all traces of avast?

---

### Post by cdenley on 2010-08-11
Removing a package does not remove configuration files. Purging a package does. It does not remove user-specific configurations the application may have created in home directories, though.
```

sudo dpkg -P avast4workstation
rm -rf ~/.avast

```
Simply having it installed but not running wouldn't affect performance, though. Either it has a process running in the background, or your problem probably isn't related to avast.
```

ps -ef|grep -i '[a]vast'

```

---

### Post by wahoobob on 2010-08-11
I did get it running on the second install, but the update broke it again so I think there might be a process in the background that got started.  Will your suggestion end any process it started?

---

### Post by cdenley on 2010-08-11
> **wahoobob said:**
> I did get it running on the second install, but the update broke it again so I think there might be a process in the background that got started.  Will your suggestion end any process it started?

No. It lists any processes along with with their PID for any process whose command contains the case-insensitive string "avast". If you find any processes, you can use the PID to kill the process if you want. 

How exactly is it broken, anyway? Are you experiencing this common problem?
[http://forum.avast.com/index.php?topic=57775.0](http://forum.avast.com/index.php?topic=57775.0)

---


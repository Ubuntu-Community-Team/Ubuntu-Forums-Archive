---
title: "problems with rc.local"
date: 2009-10-07
forum: Server Platforms
---

### Post by kylegio on 2009-10-07
im having trouble with my rc.local file, it doesnt seem to run on startup. if i manually call it using sudo /etc/rc.local it works just fine, but if i do sudo shutdown -r now, when the server comes back online the commands in rc.local don't seem to have been run (should have started a couple key services) 

1) any suggestions on why this might be, i thought it was a permission error at first because its required to run using sudo, but im pretty sure rc.local is executed as root on boot. 
2)is there an error log for this script anywhere that i might check?


thanks!

---

### Post by gombadi on 2009-10-07
If it works from the command line but not when the system boots then I would guess it is the environment.

Are you using full paths for the commands you run?

May pay to add the following to the start of the file -
```

echo $PATH >>/tmp/path-in-rc.local-during-boot

```

Have a look at the file after the boot to see what it says. 

Logger is also a good tool to use like -
```

logger -t somestring "a syslog message with variables >>$PATH<< if you want"

```

Add that somewhere in the file then look at syslog to see what it tells you.

---


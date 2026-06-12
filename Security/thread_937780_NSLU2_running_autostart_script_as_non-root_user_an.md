---
title: "NSLU2: running autostart script as non-root user and where??"
date: 2008-10-04
forum: Security
---

### Post by Ciesko on 2008-10-04
Hi all, I'm trying to run an autostart script on my NSLU2 unslungged but I have a couple of problems:

-I do not understand, where I have to put the script:
/opt/etc/init.d (at the moment my script is locate here as S80myscript and it works)
/etc/rc.d (someone suggest the folder /etc/rc3.d but it's not present in my NSLU2 and if I try to put the script in /etc/rc.d it doesn't work!)
/unslung? (again someone suggest to put the script in this folder named rc.local)

-how I can execute the script as a non-root user?

I've found on internet this string
 /bin/su - username -c script.sh  where script.sh is the script to execute as non-root

but it doesn't work (if I execute it the TinyLogin help appear)

Thanks!
Ciesko

---

### Post by cariboo on 2008-10-04
If you want to start the script automatically on boot then you would put it in /etc/rc.dX to do this, the easiest way is use update-rc.d eg:

```
sudo update-rc.d myscrip defaults
```

With your script in /opt/etc it will not automagically start, you will have to start and stop it by hand.

The script should be run as root because you can't mount any drives as a regular user.

Jim

---


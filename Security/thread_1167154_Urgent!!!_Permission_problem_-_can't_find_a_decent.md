---
title: "Urgent!!! Permission problem - can't find a decent solution :O"
date: 2009-05-22
forum: Security
---

### Post by zja on 2009-05-22
[I]"On a default Ubuntu system, any task which requires root (or Administrator) privileges runs a program called 'sudo' (or it's graphical equivalent, gksu) to run a helper program in a privileged mode. By default, for security reasons, this program will ask you to input your password. If you make a lot of settings changes on your system (or need to run a lot of programs as root), each password prompt can get rather annoying." ([http://www.ubuntutips.net/node/21](http://www.ubuntutips.net/node/21))

that's **EXACTLY** what I just **LOST** today. now my system asks rarely for my password even when I getting in to **Root Terminal** [gksu /usr/bin/x-terminal-emulator] this is VERY disturbing >:(

how that happened?
I messed a bit with **System > Administration > Login Window** and I ONLY changed the themes under the Local tab & under the Accessibility tab I picked 2 other sounds (which didn't worked at all) for **Login successful** and **Login failed**. that's all

as for _now_, at this very moment, the system DID asked for password for [/I]***System > Administration > Login Window**** and ****Root Terminal****.*

please help. how can I control the system's password request (the more it asks the better)

thanks in advanced!

---

### Post by cdenley on 2009-05-22
By default, once sudo is used, you don't need to enter your password again in that terminal for 15 minutes.
```

sudo EDITOR=gedit visudo

```
change this line, adding the bold red text...
```

Defaults env_reset[COLOR="Red"]**,timestamp_timeout=0**[/COLOR]

```
...then save and close.
That should always require a password. If not, run this command
```

sudo -K

```
That clears out existing timestamps. For more information
```

man sudoers
man sudo

```

---

### Post by The Cog on 2009-05-23
Just to explain teh mail above - sudo normally remembers that you gave a password, and won't bother the same terminal for another password prompt within a 15 minute timeout. This is to prevent the password prompt getting really, REALLY annoying.

---


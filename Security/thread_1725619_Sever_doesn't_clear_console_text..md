---
title: "Sever doesn't clear console text."
date: 2011-04-09
forum: Security
---

### Post by EmilHem on 2011-04-09
When I'm logged in, physically on the server as root and logout the lines doesn't get cleared like when you logout as a normal user.
This could be a bug and if it is, it could be a security problem. The last actions done shows.

I would appreciate any feedback about this issue I'm experiencing.

Additional information:
Ubuntu Server 10.10 (32 bit)
RAM: 1GB
Server used as: webserver, database, gaming server.

---

### Post by RingoFyre on 2011-04-10
Something in .bashrc? Check in both /root & ~/ - 
[http://ubuntuforums.org/showthread.php?t=27892](http://ubuntuforums.org/showthread.php?t=27892)

---

### Post by FuturePilot on 2011-04-10
Make sure you have a ~/.bash_logout. This is what is in it

```
# ~/.bash_logout: executed by bash(1) when login shell exits.

# when leaving the console clear the screen to increase privacy

if [ "$SHLVL" = 1 ]; then
    [ -x /usr/bin/clear_console ] && /usr/bin/clear_console -q
fi
```

---


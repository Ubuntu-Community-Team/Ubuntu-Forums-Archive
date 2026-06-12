---
title: "resolveip 'uname -n' - should return IP??"
date: 2011-10-09
forum: Server Platforms
---

### Post by kpm on 2011-10-09
On Ubuntu 11.04 LAMP server, if I run the command "uname -n", the result is as expected, ie "server.domain.com".  If I run the command "resolveip server.domain.com" the result is expected, ie "IP address of server.domain.com is ###.###.###.###". 
Now the question is, if I run the command "resolveip 'uname -n'", should I expect the same as the returned as with "resolveip server.domain.com"?  What I get is "resolveip: Unable to find hostid for 'uname -n': host not found."

---

### Post by robvas on 2011-10-09
You can use backticks like so:

[FONT="Courier New"]ping `uname -n`[/FONT]

On an American keyboard it is the upper left key:

[IMG]http://i.imgur.com/GksLP.jpg[/IMG]

Not the single-quote or apostrophe key.

Another way to do the same thing is like this:

[FONT="Courier New"]ping $(uname -n)[/FONT]

---

### Post by fdrake on 2011-10-09
+1@robvas
or
```
ping $(uname -n)
```

---

### Post by kpm on 2011-10-09
ahhhh they are back ticks... sigh... i was using single quotes (read that way from a tutorial)...
Thanks!

---


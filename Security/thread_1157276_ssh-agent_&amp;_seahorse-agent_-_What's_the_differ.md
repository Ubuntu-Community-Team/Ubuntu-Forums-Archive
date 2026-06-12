---
title: "ssh-agent &amp; seahorse-agent - What's the differences?"
date: 2009-05-12
forum: Security
---

### Post by pkkid on 2009-05-12
I use ssh-agent a lot while at work to get around all the various test clients we have.  It seems after reinstalling my box to Jaunty my ssh-agent has been acting all funky, and recently its been dieing after a few hours (often during test runs), killing my connection in the middle of using it, as well as killing my productivity.  Looking online for a solution didn't provide much, but a lot of people claim seahorse is unreliable, and disabling it brought back ssh-agent reliability.  However, being a noob, I am now very curious.

What exactly is seahorse-agent in comparison to ssh-agent?
Should I, and How do I disable seahorse-agent from starting?

Running ps ax for seahorse shows ssh-agent is actually using seahorse.
```
 9972 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
 9979 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
10035 ?        Ss     0:00 /usr/bin/seahorse-agent --execute x-session-manager
12025 pts/1    R+     0:00 grep --color --exclude-dir=.svn seahorse
```

---


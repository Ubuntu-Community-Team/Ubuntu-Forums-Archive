---
title: "Server - ssh/telnet into screen"
date: 2012-01-15
forum: Server Platforms
---

### Post by Forecaster71 on 2012-01-15
I'm fairly sure there is a way to ssh/telnet directly into a screen session.

I cannot find any instructions on how to do this though.

Does anyone know where I can find instructions relating to this?

I would also like to prevent a specific user from doing anything outside of this screen.

Any help or tips are appreciated.

---

### Post by Lars Noodén on 2012-01-15
Well you could try something like this:

```

ssh user@example.org "screen -r"

```

And then use [ForceCommand](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html)

```

Match Group *somegroup*
        ForceCommand /usr/bin/screen -r

```

That's just a guess. You'll have to work out the details.

Looking more at it, screen -r won't create a new session so you'll probably have to wrap it in a script and call the script from [font=Courier New]ForceCommand[/font].

e.g. this could be in [font=Courier New]/usr/local/bin/screeners[/font].

```

#!/bin/sh

# try attaching to an existing screen session or,
# or if none exist, make a new screen session

/usr/bin/screen -r || /usr/bin/screen /bin/sh -c "*somecommand*"

```

Then [font=Courier New]sshd_config[/font] could have something like this:

```

Match Group somegroup
        ForceCommand /usr/local/bin/screeners

```

---

### Post by Forecaster71 on 2012-01-16
> **Lars Noodén said:**
> 
Looking more at it, screen -r won't create a new session so you'll probably have to wrap it in a script and call the script from [font=Courier New]ForceCommand[/font].

The screen in question is an already running named session with a single named window.

So the script wouldn't be necessary.

I think I need to learn a bit about user management...

---

### Post by nothingspecial on 2012-01-16
To attach an already running screen session use the -x flag

```
screen -x *session_name*
```

where *session_name* is the actual session name.

---

### Post by Forecaster71 on 2012-01-16
> **nothingspecial said:**
> To attach an already running screen session use the -x flag

```
screen -x *session_name*
```

where *session_name* is the actual session name.

I'm perfectly aware of that. Though I believe that the -x flag is used to attach to a multi-user screen.

The -r flag works just as well to attach to a named screen as far as I know.

I know how my screen works, what I need to do is learn about users it seems.

---

### Post by Lars Noodén on 2012-01-16
Another way would be to set the user's shell (usermod -s) to screen.

---

### Post by Forecaster71 on 2012-01-17
> **Lars Noodén said:**
> Another way would be to set the user's shell (usermod -s) to screen.

But would that limit him to a specific screen or just limit him to screens in general?

---

### Post by Lars Noodén on 2012-01-17
You'll have to add some extra parameters to get it to go to a specific screen.  I'm a novice at screen so can't make a guess.  screen's very flexible, so I expect that the option exists somehow.

---


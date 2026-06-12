---
title: "After log on to SSH, automatically attach (or create) TMUX"
date: 2014-07-29
forum: Server Platforms
---

### Post by smeerbartje on 2014-07-29
I am running a headless Ubuntu server 14.04.1 server. It's great. The last couple of weeks I have discovered tmux: also great! :) Now I want to achieve the following: if I am logging on to the server through SSH (from -for example- my Mac) I am "a user", so I want a possible tmux session to automatically be re-attached to. But when I'm a session (through) ssh which only does file transfer (sftp), then off course, the session should not be re-attached. How can I do this?

In the .bashrc I see the lines:

[FONT=Courier New]# If not running interactively, don't do anything
[ -z "$PS1" ] && return[/FONT]

Is this something which can help me fixing this? How do you guys do this? And is there some kind of script which creates a tmux session if it doesn't exist, but attached to the one IF it does not exist yet?

---

### Post by ian-weisser on 2014-07-29
> **smeerbartje said:**
> if I am logging on to the server through SSH (from -for example- my Mac) I am "a user", so I want a possible tmux session to automatically be re-attached to.

Well, I don't run a lot of needs-a-constantly-active console services from headless servers. So one option is to look for replacement services that don't require tmux. Lots of good daemon software available.

But to actually *answer* your question, I haven't seen any automatically-reconnect-to-tmux applications out there. But I can think of a couple easy ways to do it.

For example, you can place a tmux-is-running/tmux-is-not-running stanza in the login MOTD. Or you can use a different ssh port for tmux logins. Or a different user. Or when you start tmux, place a flag file and subsequent logins a .bashrc script looks for it. Whatever you will find easiest to maintain.


> **smeerbartje said:**
> 
In the .bashrc I see the lines:

[FONT=Courier New]# If not running interactively, don't do anything
[ -z "$PS1" ] && return[/FONT]

Is this something which can help me fixing this? How do you guys do this? And is there some kind of script which creates a tmux session if it doesn't exist, but attached to the one IF it does not exist yet?

A non-interactive ssh session occurs when you use ssh to simply transmit a single command (and perhaps return the output) instead of opening an interactive shell connection. scp is already like that; you get the file transferred instead of a shell prompt.

---

### Post by Lars Noodén on 2014-07-29
You'd have to check the variable $TMUX yourself and go from there in .bashrc.   Use the [logical OR operator](http://www.tldp.org/LDP/abs/html/ops.html#ORREF) to chain together two attempts at starting tmux.  

```

echo Checking for tmux
if [ -z ${TMUX} ]; then
  /usr/bin/tmux attach || /usr/bin/tmux
fi

```

If the first one fails, then bash tries the second one.  And if the first one succeeds in reattaching, then the second one is never tried.

---

### Post by smeerbartje on 2014-07-29
Okay, this works. But what does [ -z ${TMUX} ] do? When is ${TMUX} set? And when is .bashrc evaluated?

---

### Post by Lars Noodén on 2014-07-29
The -z is a [test](http://manpages.ubuntu.com/manpages/trusty/en/man1/test.1.html) to make sure that the variable ${TMUX} is an empty string.  ${TMUX} is about the same as $TMUX but is a safer way to write variables.  tmux sets that variable and uses it for checking if there is already a tmux session running.  I figure if tmux can use it so can we.  

.bashrc gets called by .profile, which gets launched when you run bash.  You can read through .profile to see that it checks for the existence of .bashrc and calls it if it exists.

```

less ~/.profile

```

---


---
title: "non-interactive ssh evironment variables"
date: 2007-01-25
forum: Server Platforms
---

### Post by pjstadig on 2007-01-25
I'm trying to set some environment variables in my ~/.ssh/rc file. Specifically, I'm trying to set up ssh-agent through keychain ([http://www.gentoo.org/proj/en/keychain/)](http://www.gentoo.org/proj/en/keychain/)).

So obviously, given the nature of the environment variables I'm trying to set I can't use ~/.ssh/environment. I'm trying to do something pretty much like this:

[http://www.oreilly.com/catalog/sshtdg/chapter/ch08.html#74105](http://www.oreilly.com/catalog/sshtdg/chapter/ch08.html#74105)

So I think it's possible, but when I add

eval `keychain --eval id_rsa`

to my ~/.ssh/rc file it doesn't modify the environment at all. I've even tried setting env vars directly in the rc file, but it doesn't work. If I do

eval `keychain --eval id_rsa`
env

I can see in the output that the environment variables are getting set, but they are not sticking.

Is there something specific to the default sshd config on Ubuntu that precludes something like this?  Because I'm stumped.


TIA,
Paul

---

### Post by pjstadig on 2007-01-26
Here's what I have in my ~/.ssh/rc on the remote machine:

```
eval `keychain -q --eval id_rsa`
env
echo "*~*~*~*~*~*~*~*~*~*~*~*~*~*"

```

and here's some output:

```
*@*:~$ ssh *@*.*.* env
SSH_AGENT_PID=3215
SHELL=/bin/bash
SSH_CLIENT=*.*.*.* 43336 22
USER=*
SSH_AUTH_SOCK=/tmp/ssh-fbyCuI3214/agent.3214
MAIL=/var/mail/*
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
PWD=/home/*
LANG=en_US.UTF-8
SHLVL=3
HOME=/home/*
LANGUAGE=en
LOGNAME=*
SSH_CONNECTION=*.*.*.* 43336 *.*.*.* 22
_=/usr/bin/env
*~*~*~*~*~*~*~*~*~*~*~*~*~*
SHELL=/bin/bash
SSH_CLIENT=*.*.*.* 43336 22
USER=*
MAIL=/var/mail/*
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
PWD=/home/*
LANG=en_US.UTF-8
SHLVL=1
HOME=/home/*
LANGUAGE=en
LOGNAME=*
SSH_CONNECTION=*.*.*.* 43336 *.*.*.* 22
_=/usr/bin/env

```

As you can see the rc file is getting executed, and the env vars (SSH_AGENT_PID, SSH_AUTH_SOCK) are getting set, but when it gets around to executing my command they're inexplicably gone.  I've looked through everything in the sshd config, and I don't think there are any config directives that are even related to this. I could post my sshd config file, but it is almost exactly the same as the default config. Why? Why is this happening? Some one please rescue me.


Paul

---


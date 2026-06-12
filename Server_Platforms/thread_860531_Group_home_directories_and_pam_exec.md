---
title: "Group home directories and pam_exec"
date: 2008-07-15
forum: Server Platforms
---

### Post by arthurp on 2008-07-15
I'm having a problem with using pam_exec.

My goal is to give users easy access (via FTP and Samba) to group home directories. My idea was to write a script that created symlinks in the user's home directory to the group homes (The script is pasted at the bottom of the message). I could then make the script run whenever anyone logs in (including logins via FTP and Samba). I realized that pam_exec was the correct tool.

However, I cannot figure out how to know which user is logging in from within the script. I want the script to run as that user so I either need to have PAM start it that way in the first place or get the username so I can su to that user. I have seen several places that there should be environment variables like PAM_USER and the like. That would be perfect, but they are not there. Inside the script the environment looks like:

SHELL=/bin/bash
TERM=xterm
USER=root
LS_COLORS=no=00:fi=00:di=01;34:ln=0[...]
SUDO_USER=amp
SUDO_UID=1000
USERNAME=root
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
MAIL=/var/mail/amp
PWD=/
LANG=en_US.UTF-8
TZ=UTC+04:00
HISTCONTROL=ignoreboth
SUDO_COMMAND=/bin/bash
HOME=/root
SHLVL=2
LOGNAME=root
LESSOPEN=| /usr/bin/lesspipe %s
SUDO_GID=1000
LESSCLOSE=/usr/bin/lesspipe %s %s
_=/usr/bin/env

<cut>

Currently my PAM rule is: auth optional pam_exec.so debug log=/tmp/pam.log /usr/local/sbin/create-group-home-links-pam.sh (where /usr/local/sbin/create-group-home-links-pam.sh is a script that prints it's env)

I have also tried putting it in the session stage. The results are the same.

So my question is: How to I find out who is logging in from with a pam_exec script? Or is there a better way to trigger the script to make the symlinks?

Thanks a lot.
-Arthur

Script:
groups_dir=$HOME/groups
mkdir -p $groups_dir

for group in $(groups); do
        gh=/home/$group
        if [ -d $gh ] && [ -r $gh ]; then
                ln -svf $gh $groups_dir
        fi
done

---

### Post by snowboarder04 on 2009-05-20
I'm facing this exact same challenge, trying to get the $USER variable of a connecting user. Did you have any success with this and if so, what did you do to overcome it?

---

### Post by arthurp on 2009-05-20
I never solved the problem. I realized it wasn't all that important and gave up. I'd be interested to know a solution though, so if you find one post it.

Sorry I can't be of more help.

---

### Post by vhex on 2011-01-11
I added the following line to /etc/pam.d/common-session:

```
session optional pam_exec.so debug log=/tmp/pam_exec.log /root/pam-exec.sh
```

This is what I get in /tmp/pam_exec.log:

```
*** Wed Jan 12 04:23:04 2011
PAM_USER=myname
XDG_SESSION_COOKIE=27635bb0d256d895bd49cfc34b5b9fba-1294795384.168724-1231416001
PAM_TYPE=open_session
PAM_RHOST=mv.local
PAM_SERVICE=sshd
PAM_TTY=ssh
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
LANG=ru_RU.UTF-8
PWD=/
*** Wed Jan 12 04:23:36 2011
PAM_USER=myname
XDG_SESSION_COOKIE=27635bb0d256d895bd49cfc34b5b9fba-1294795384.168724-1231416001
PAM_TYPE=close_session
PAM_RHOST=mv.local
PAM_SERVICE=sshd
PAM_TTY=ssh
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
LANG=ru_RU.UTF-8
PWD=/
```

This should help.  Note that I've changed "auth" to "session".  Maybe the way it works changed over time, though.

---


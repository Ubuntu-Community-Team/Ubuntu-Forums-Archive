---
title: "sudo su - versus sudo -i"
date: 2011-08-03
forum: Security
---

### Post by Wim Sturkenboom on 2011-08-03
In a thread I suggested to use *_sudo su -_* to become root temporarily. I was advised that *_sudo -i_* would be a better choice.

I'm very curious why that is the case. Threads that I've found omit the dash from the first command, so don't apply.

```

"var"               |"sudo su -"                                                    |"sudo -i"
--------------------+---------------------------------------------------------------+--------------------------------------------------------------------------
"SHELL"             |"/bin/bash"                                                    |"/bin/bash"
"TERM"              |"linux"                                                        |"linux"
"USER"              |"root"                                                         |"root"
"LS_COLORS"         |                                                               |
"MAIL"              |"/var/mail/[COLOR="Red"]root[/COLOR]"                                               |"/var/mail/[COLOR="Red"]wim[/COLOR]"
"PATH"              |"/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin" |"/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin[COLOR="Red"]:/usr/games[/COLOR]"
"PWD"               |"/root"                                                        |"/root"
"LANG"              |"en_ZA.UTF-8"                                                  |"en_ZA.UTF-8"
"SPEECHD_PORT"      |6560                                                           |6560
"SHLVL"             |1                                                              |1
"HOME"              |"/root"                                                        |"/root"
"LOGNAME"           |"root"                                                         |"root"
"LESSOPEN"          |"| /usr/bin/lesspipe %s"                                       |"| /usr/bin/lesspipe %s"
"LESSCLOSE"         |"/usr/bin/lesspipe %s %s"                                      |"/usr/bin/lesspipe %s %s"
"_"                 |"/usr/bin/env"                                                 |"/usr/bin/env"
--------------------+---------------------------------------------------------------+--------------------------------------------------------------------------
[COLOR="Red"]"XDG_SESSION_COOKIE"|"a7a40db8cf4c937acb049b764d08c288-1312375570.325101-1940988668"|
"SUDO_USER"         |                                                               |"wim"
"SUDO_UID"          |                                                               |1000
"USERNAME"          |                                                               |"root"
"SUDO_GID"          |                                                               |1000[/COLOR]
```

Highlighted in red are the differences in the environment (mail, path and the 5 lines at the end). Please explain to me why *_sudo -i_* is the better choice.

---

### Post by bodhi.zazen on 2011-08-03
You are correct , the difference is with the resulting environmental variables.

sudo -i is "cleaner"

See: [http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

If you have your user environmental variables it can cause either a (minor) security risk or ownership of your files in your home directory owned by root, which from time to time causes breakage, you will see it come up about once a month on these forums.

---

### Post by Wim Sturkenboom on 2011-08-03
That post does not cover the specific command that I use. Note the dash at the end of *_sudo su -_* which (according to *man su*) sets the correct environment.
> 
The optional argument - may be used to provide an environment similar to what the user would expect had the user logged in directly.


And from the results I showed, I don't see root's environmental variables being corrupted.

It sets a cleaner path (;)) as root does not play games :D And one can actually say that *_sudo -i_* corrupts root's mail variable.

But that might be nitpicking (or whatever it is called in english).

---

### Post by sisco311 on 2011-08-03
The behavior of **sudo -i** and **su -** is well documented in **man sudo** and **man su**, respectively. 

When you run **sudo su -**, you use two different setuid root commands. It's much harder to predict which variables will be reset and which will be kept.

---

### Post by sisco311 on 2011-08-03
> **Wim Sturkenboom said:**
> 
It sets a cleaner path (;)) as root does not play games :D And one can actually say that *_sudo -i_* corrupts root's mail variable.

But that might be nitpicking (or whatever it is called in english).

According to the man page **sudo -i** leaves DISPLAY and TERM unchanged and sets HOME, MAIL, SHELL, USER, LOGNAME, and PATH, as well as the contents of /etc/environment on Linux and AIX systems.

In Ubuntu, by default, the PATH is set in /etc/environment.

Not sure why didn't reset MAIL for you, it works here as expected.

---

### Post by bodhi.zazen on 2011-08-03
> **Wim Sturkenboom said:**
> That post does not cover the specific command that I use. Note the dash at the end of *_sudo su -_* which (according to *man su*) sets the correct environment.


And from the results I showed, I don't see root's environmental variables being corrupted.

It sets a cleaner path (;)) as root does not play games :D And one can actually say that *_sudo -i_* corrupts root's mail variable.

But that might be nitpicking (or whatever it is called in english).

You can use what you like. I was merely answering your question 

> **Wim Sturkenboom said:**
> Please explain to me why sudo -i is the better choice.

So while you may agree or disagree, I am not interested in debating the issue, and most (not all) people advise sudo -i for the reasons I cited.

With that, I consider your question asked and answered.

---

### Post by Wim Sturkenboom on 2011-08-03
> **sisco311 said:**
> Not sure why didn't reset MAIL for you, it works here as expected.
Just checked on another system withe the same 64 bit 10.04 LTS). 'mail' is not even set when I use *_sudo -i_* (but is with *_sudo su -_*) ??

Something funny going on.

---

### Post by bodhi.zazen on 2011-08-04
> **Wim Sturkenboom said:**
> Just checked on another system withe the same 64 bit 10.04 LTS). 'mail' is not even set when I use *_sudo -i_* (but is with *_sudo su -_*) ??

Something funny going on.

That is not the way my system works either, sudo -i and sudo su - both set $MAIL.

Check your config files (.bashrc to start with, perhaps /etc/sudoers as well).

---


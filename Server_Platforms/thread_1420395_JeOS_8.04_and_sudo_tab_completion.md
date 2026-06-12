---
title: "JeOS 8.04 and sudo tab completion"
date: 2010-03-03
forum: Server Platforms
---

### Post by jptech on 2010-03-03
Can anyone tell me how to get tab completion working with sudo in JeOS (Ubuntu Hardy) 8.04?  Assuming I have the command '/usr/bin/svnadmin'.  As a normal user I can type:

```
svnad + TAB
```...and it auto-completes as 'svnadmin'.  If I type:

```
sudo svnad + TAB
```...nothing happens.  My 'echo $SHELL' is '/bin/bash'.  I tried enabling the following in '/etc/bash.bashrc':

```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```...but it had no effect (I even tried a reboot to be sure).  It's worth noting that tab completion works as I'd expect if I use absolute paths.  For example:

```
sudo /usr/bin/svnad + TAB
```...auto-completes as I'd expect.  I think I once read that there's some kind of configuration variable for sudo that causes it to use a 'more secure' path rather than the current path in the user's environment.  I can't find any info on it though.  I'm executing the commands from my home directory.

Can anyone help me?

---

### Post by yogesh.girikumar on 2010-03-03
Hi,

Type the following in the terminal.

```
$ complete -c sudo
```

Now see if auto complete works..

Let me know if this helps.
Cheers.

---

### Post by jptech on 2010-03-03
That works!  Is it better for me to add it to ~/.bashrc or /etc/bash.bashrc ?

---

### Post by samosamo on 2010-03-03
You might be interested in "apt-get install ubuntu-standard" to get all those useful apps (bash completion, crontab, logrotate, etc etc) as well as openssh-server.

---

### Post by yogesh.girikumar on 2010-03-04
Hi,

Adding it to ~/.bashrc will enforce it only to the user to which the home folder belongs to. Adding it to the /etc/bash.bashrc file will enforce it to all the users of the machine.

I would suggest you add it to /etc/bash.bashrc . Any user who wish to change it can do that in their own ~/.bashrc file. No harm done here.

see: [http://stefaanlippens.net/bashrc_and_others](http://stefaanlippens.net/bashrc_and_others)

---

### Post by clayg on 2010-08-19
I just spun up a new Ubuntu 10.04 server on slicehost and I couldn't sudo aptit<tab>

Found this post and noted, ubuntu-standard wasn't installed (kinda werid).  Probably would be fine, there's some good stuff in there (telnet, lshw) - but also some stuff I may not need.

```
sudo aptitude install bash-completion
```

was enough to get things working for me.

---


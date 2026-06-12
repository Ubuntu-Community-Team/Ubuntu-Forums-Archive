---
title: "gpg-agent startup options ignored after upgrade to saucy"
date: 2013-11-12
forum: Security
---

### Post by ulrichard on 2013-11-12
Hi, I first posted my question to the gnupg mailing list, but didn't get a response. 
It is more related to ubuntu than gnupg anyway, so I hope for more luck here.

I set up ssh authentication a long time ago according to the second half
of this guide (with smartcard):
[http://www.programmierecke.net/howto/gpg-ssh.html]("http://www.programmierecke.net/howto/gpg-ssh.html")
It worked without an issue until I recently upgraded to Ubuntu 13.10.
After the upgrade I had to disable the gnome-keyring-ssh and
gnome-keyring-gpg as well as ssh-agent again, as I did after previous
upgrades.
The configuration for enable-ssh-support in ~/.gnupg/gpg-agent.conf was
still intact.
On another system where the whole stuff still works, ps aux | grep
gpg-agent shows only one instance with lots of options:
```
$ ps aux | grep gpg-agent
/usr/bin/gpg-agent --daemon --sh
--write-env-file=/home/richi/.gnupg/gpg-agent-info-quadulrich /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch gnome-session --session=ubuntu
```
But on this system, it shows 5 instances 4 with only --daemon and the
fifth with an additional --sh.
If I type "gpg-agent --daemon --enable-ssh-support" and execute the
output in a terminal, I get an instance that works and handles the ssh
key authentication. At the moment I copy the environment variables that this invocation spits out to every terminal session manually. 

Is anybody here aware of some changes in this area, and knows how I need
to configure my system, to have it as seamless as before? More
specifically, what I need to do to have the gpg-agent started with all
these options?

Rgds
Richard

---

### Post by ulrichard on 2013-12-10
Now I performed a fresh install on my new ultrabook. I installed a stock ubuntu, not kubuntu. The behavior is the same. gpg-agent.conf is ignored. I have to start a gpg-agent instance manually to get ssh support.

There is one instance running with only : 
gpg-agent --daemon --sh

With the help of the gpg-agent man page, I could probably bake something together that would work. But I still think it should work automatically as it did with all prior versions of ubuntu.

---

### Post by ulrichard on 2013-12-10
With the help from the gnupg IRC, i baked an  .bashrc file that solves the issue for me:

# If the agent is not already running, start it
if ! ps aux | grep -q [e]nable-ssh-support; then
        /usr/bin/gpg-agent --daemon --enable-ssh-support --write-env-file "${HOME}/.gpg-agent-info"
fi;

#And then read info back
eval $(cat $HOME/.gpg-agent-info) > /dev/null

---

### Post by Bashing-om on 2013-12-10
ulrichard; Hi !

You do good work, Thanks for sharing the solution. 

Please mark this thread as solved to aid others seeking that solution.

[INDENT][INDENT]my best regards
[/INDENT][/INDENT]

---

### Post by ulrichard on 2013-12-10
Actually it only partly solved the problem.
That's good for all the terminal work. 
But programs that were started from the dash or the start menu indicator, don't get the environment vars.
So, I have to close nautilus, evolution and firefox and then launch them from a terminal if I want to acces the gpg smartcard.
It's doable but cumbersome. 
So, where should I put it?  ~/.profile was mentioned before. Are there better places?

---

### Post by Bashing-om on 2013-12-11
ulrichard; Hello .
> 
With the help of the gpg-agent man page, I could probably bake something together that would work. But I still think it should work automatically as it did with all prior versions of ubuntu.


Me to, I should think. This has gone beyond my sphere of knowledge. However, I am more than willing to attend to resolving this situation.
Maybe the requisite files are not in the proper place ?
What returns from the query :
```

gpg --finger

```
and what is in the gpg directory ?
```

ls -la ~/.gnupg

```

So far it seems the the gpg daemon runs on demand>
my return, as far as I know I have no problem with key signing .
```

sysop@1304mini:~$ ps aux | grep gpg
sysop     2000  0.0  0.0   9440   912 pts/0    S+   11:16   0:00 grep --color=auto gpg
sysop@1304mini:~$ 

```
I do not know how one would start the gpg daemon for testing purposes.
This for me, though willing help has become ->
[INDENT][INDENT]a process in learning
[/INDENT][/INDENT]

---

### Post by akwala on 2014-07-14
> **ulrichard said:**
> 
So, where should I put it?  ~/.profile was mentioned before. Are there better places?

gpg-agent needs to be started once per user session, so the "gpg-agent --daemon" command can go either in ~/.profile or ~/.bash_profile. The related environment variables need to be set for every interactive session, so they should go in ~/.bashrc.

An alternate way to do this is to create your own upstart job config file in ~/.config/upstart, see examples in comment 1 & 6 of [https://bugs.launchpad.net/ubuntu/+source/gnupg2/+bug/1257706](https://bugs.launchpad.net/ubuntu/+source/gnupg2/+bug/1257706) -- note that ~/.init, as suggested in the comments, has been deprecated ([http://upstart.ubuntu.com/cookbook/#session-jobs](http://upstart.ubuntu.com/cookbook/#session-jobs) - Section 4.2.3, Session Jobs).

---


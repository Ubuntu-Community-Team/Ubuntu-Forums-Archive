---
title: "keychain/ssh-agent problem: always asked for passphrase when using sudo"
date: 2009-10-14
forum: Security
---

### Post by shinyblue on 2009-10-14
Hi

I'm using keychain so that I only have to enter my passphrase once, at start up. This works fine for ssh from my normal user account.

But I need* it to also work when ssh is run as root (e.g. sudo). This fails in that it **always** asks for my passphrase. i.e. root's id_dsa doees not seem to be being added to the keychain/ssh-agent.

So this works fine:
```
$ ssh rich@server echo blah
blah

```


But this will always ask for my passphrase
```
$ sudo ssh rich@server echo blah
Enter passphrase for key '/root/.ssh/id_dsa': 
blah

```

How can I get it to play ball? I've tried various silly, desperate things like making /root/.ssh and /root/.keychain a symlink to their counter parts in /home/rich/

Thanks.

Rich.


*need: I want to use autofs to automount with sshfs. autofs is happy to launch sshfs, but **as root**. So it fails because that process has no way to ask me for the passphrase (running in a non-interactive environment, as a daemon).

I'm using kubuntu 9.04 but actually running xfce not kde [COLOR="Gray"](because kde4 in IMHO about 3 years away from being anywhere as useful as kde3!)[/COLOR]

---

### Post by Sarmacid on 2009-10-14
You're using sudo on your local machine, try
```
ssh rich@server sudo whoami
```

---

### Post by shinyblue on 2009-10-14
Hi Sarmacid: I know I'm using sudo on my local machine.

I want to log in at "server" with username "rich" (which happens to be the same username on my local machine).

I need to be able to do this as root from my local machine. Another way to express the problem is:

```

rich@local$ sudo bash
root@local$ ssh rich@server echo blah
Enter passphrase for key '/root/.ssh/id_dsa': 
blah

```

Sorry if I wasn't clear first time. Thanks for trying to help.

---

### Post by Lars Noodén on 2009-10-14
> **shinyblue said:**
> Hi Sarmacid: I know I'm using sudo on my local machine.

I want to log in at "server" with username "rich" (which happens to be the same username on my local machine).

I need to be able to do this as root from my local machine. Another way to express the problem is:

```

rich@local$ sudo bash
root@local$ ssh rich@server echo blah
Enter passphrase for key '/root/.ssh/id_dsa': 
blah

```

Sorry if I wasn't clear first time. Thanks for trying to help.

1) Why do you say you need to do that as root?

2) When you run

[INDENT][FONT="Courier New"]sudo ssh rich@server echo blah[/FONT][/INDENT]

You are in effect running 

[INDENT][FONT="Courier New"]sudo ssh -i /root/.ssh/id_dsa rich@server echo blah[/FONT][/INDENT]

The agent was loaded using the user 'rich', I presume.  So you will need:

[INDENT][FONT="Courier New"]sudo ssh -i /home/rich/.ssh/id_dsa rich@server echo blah[/FONT][/INDENT]

You may also need to bind the agent to the correct socket and process. Look around in /tmp/ for ssh-*, find might help: **find /tmp/ -path '*ssh-*' -name '*agent*' -print**

[INDENT][FONT="Courier New"]SSH_AUTH_SOCK=/tmp/ssh-vBdDxM8369/agent.8369; export SSH_AUTH_SOCK;[/FONT][/INDENT]

The process id can be found using **pgrep -l ssh-agent** and then setting and exporting the environment variable SSH_AGENT_PID:

[INDENT][FONT="Courier New"]SSH_AGENT_PID=8370; export SSH_AGENT_PID;[/FONT][/INDENT]

---

### Post by shinyblue on 2009-10-14
Hi Lars, thanks for your post.

> **Lars Noodén said:**
> 1) Why do you say you need to do that as root?


[LIST]
[*] autofs runs as root
[*] autofs therefore calls sshfs as root
[*] the format of autofs map files does not (seem to) allow for anything clever e.g. seems to be limited to something like ```
":sshfs\#rich@server\:"
``` 
[example link 1]("http://www.tjansson.dk/?p=84") | [example link 2]("http://www.mccambridge.org/blog/2007/05/totally-seamless-sshfs-under-linux-using-fuse-and-autofs/")
[/LIST]

> **Lars Noodén said:**
> 2) When you run

[INDENT][FONT="Courier New"]sudo ssh rich@server echo blah[/FONT][/INDENT]

You are in effect running 

[INDENT][FONT="Courier New"]sudo ssh -i /root/.ssh/id_dsa rich@server echo blah[/FONT][/INDENT]


Agreed.

> **Lars Noodén said:**
> 
The agent was loaded using the user 'rich', I presume.  So you will need:

[INDENT][FONT="Courier New"]sudo ssh -i /home/rich/.ssh/id_dsa rich@server echo blah[/FONT][/INDENT]

You may also need to bind the agent to the correct socket and process. Look around in /tmp/ for ssh-*, find might help: **find /tmp/ -path '*ssh-*' -name '*agent*' -print**

[INDENT][FONT="Courier New"]SSH_AUTH_SOCK=/tmp/ssh-vBdDxM8369/agent.8369; export SSH_AUTH_SOCK;[/FONT][/INDENT]

The process id can be found using **pgrep -l ssh-agent** and then setting and exporting the environment variable SSH_AGENT_PID:

[INDENT][FONT="Courier New"]SSH_AGENT_PID=8370; export SSH_AGENT_PID;[/FONT][/INDENT]

Thanks, while I'm sure you're right this sounds like quite a job to automate, and the reason I'm looking into autofs is to save hassle!

Very much appreciate your expertise.

It looks like other people have **[given up on passphrases on their root's id_dsa]("http://russoz.wordpress.com/2007/10/27/how-to-automount-sshfs-filesystems-with-autofs-on-linux/")** to get this to work. But that's not something I really want to risk.

---

### Post by shinyblue on 2009-10-15
Ok, here's what works, and what my logic is. Thanks to all who helped.:)

[SIZE="5"]The problem:[/SIZE]

The autofs daemon is stared by an init script before any ssh-agent processes can have been started. Therefore it runs without SSH_AGENT_PID or SSH_AUTH_SOCK set in its environment vars. Therefore it cannot use ssh-agent, which means that it has no way to ask the user for the passphrase to unlock the ssh key required to make the connection. (assuming you have a passphrase on your root's ssh keys, but if you don't and your PC gets nicked then the thief can easily get your key unless it's on an encrypted filesystem or such). Therefore autofs fails to start the sshfs mount point.

[SIZE="5"]The solution: theory[/SIZE]

Run autofs with SSH_AUTH_SOCK and SSH_AGENT_PID in its environment, pointing to a running ssh-agent that the user has authenticated keys for.

[SIZE="5"]The solution: practice[/SIZE]

Assuming: 

[LIST=1]
[*]You have set up ssh keys for your normal user, and root. (it works to create a symlink at /root/.ssh to /home/you/.ssh if you want to share them).
[*]Root's key is in the authorized_keys file at the server, so that you can authenticate using that key.
[/LIST]

[keychain]("http://www.gentoo.org/proj/en/keychain/") is a program that tries to make sure there's an ssh-agent process running, and to re-use this so you don't have to keep entering your passphrase.

Once installed, put the following line in /etc/bash.bashrc

```

eval `/usr/bin/keychain --eval --nogui`

```

Now start a console. (You should be asked for your passphrase.)

Next stop the useless autofs that init started without access to ssh-agent, and then start bash as root:

```
$ /etc/init.d/autofs stop
$ sudo bash
```

You should again be asked for your passphrase: this is setting up an ssh-agent for **root**, and setting up the important env. vars too.

Next start autofs which will run in our proper environment. Then we can exit that root bash session.

```
$ /etc/init.d/autofs start
$ exit

```

Et Voilá! autofs+sshfs works for me.:) Bit of a faff when you boot up, though. 

Incredible lack of documentation on sshfs/fuse in autofs, mystery how anyone figured it!

---

### Post by Lars Noodén on 2009-10-15
Thanks for posting your solution!

I wonder if you have considered something like this to eliminate the need to jump into bash as root?

```

%autofsusers ALL=(ALL) NOPASSWD: /etc/init.d/autofs start, \
   /etc/init.d/autofs stop, /etc/init.d/autofs restart, \
   /etc/init.d/autofs reload, /etc/init.d/autofs status, \
   /etc/init.d/autofs getmounts, /etc/init.d/autofs active

```

---

### Post by shinyblue on 2009-10-16
**Lars: looks interesting, but I'm afraid I don't recognise what it would do, or where that code belongs?! Could you explain? **:confused:

BTW: turns out I hadn't got it quite fixed :rolleyes:, here's my latest hack in /etc/bash.bashrc:

```
# added by Rich:
# starts keychain (which sets up ~/.keychain/... includes)
# --eval option means keychain outputs the content of the includes
# that set up the environment vars SSH_AUTH_SOCK and SSH_AGENT_PID
#
# In Ubuntu you can only get to a root shell through sudo; root has no 
# password, so you cannot log on as root (e.g. with su )
# This fudge is complicated because ~ is set to the user that called sudo's 
# home, not /root/. So normally you could specify id_dsa and keychain would 
# look in ~/.ssh/id_dsa but this won't help root.
#
# solution (WFM): temporarily change HOME variable around running keychain
HOME1=~
[ `whoami` == 'root' ] && HOME=/root
echo "Home is now $HOME"
eval `/usr/bin/keychain --eval --nogui $HOME/.ssh/id_dsa`
HOME=$HOME1
echo "Home is now $HOME"
```

Obviously the "echo"s are just for my sanity and can be removed.

---

### Post by Lars Noodén on 2009-10-17
@*shinyblue   : it would be a hypothetical excerpt from the sudo configuration file, /etc/sudoers

It would allow any user in the group "autofsusers" to run the script named "/etc/init.d/autofs", but only in conjunction with one of the following options:  start, stop, restart, reload, status, getmounts, active

Otherwise you'd have to log in as root to do that.

---

### Post by shinyblue on 2009-10-19
Thanks Lars, but that won't do the trick (tested). It's starting bash that sets up the all-important environment variables that are necessary for the ssh that is started by sshfs that is started by autofs.

Happy with logging in as bash for now. If autofs had better documentation about the magic :sshfs#... syntax it might be possible to get this done automatically. But with out that, autofs is still good, just not very "auto"!

---

### Post by Lars Noodén on 2009-10-19
sudo allows you to set environment variables.

See SETENV: in sudoers.

$ export FOOBAR='Hello, World!'
$ sudo echo $FOOBAR
Hello, World!

---

### Post by shinyblue on 2009-10-27
> **Lars Noodén said:**
> sudo allows you to set environment variables.


Thanks again Lars, but I need root's vars to be different from mine because a process can only run as one user, so root can't use rich's ssh-agent process, so my env vars are no use to root; must set up its own.

I've just added a line to .bashrc that restarts autofs for root. So I only have one thing to type (+ passphrase).

AND! just upgraded to xubuntu karmic and now autofs springs up a GUI asking for the passphrase, which is much better than flat failing telling noone but syslog!

I'm not checking this thread any more, but thanks for your help!

---


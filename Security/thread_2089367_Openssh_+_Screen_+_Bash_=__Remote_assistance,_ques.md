---
title: "Openssh + Screen + Bash =  Remote assistance, question about local shell switch"
date: 2012-11-29
forum: Security
---

### Post by Rexilion on 2012-11-29
Hello everyone, this is my first post in this section. I hope this question is appropiate.

What I'm doing: Using OpenSSH's remote port forwarding to provide remote assistance to Windows boxes from people I help (you can call them customers if you want). Every now and then, <snip> decides to roll an update that breaks ... random stuff (I unintentionally earn money on this _***insanity***_, really).

My question is regarding the server side OpenSSH setup. I have rules like this in my authorized_keys file (I stripped the public key for your viewing convenience):

```
no-user-rc,no-agent-forwarding,no-pty,
no-X11-forwarding,permitopen="127.255.255.255:65535",
environment="SSH_SIG=customer_name",
command="env PS1=\"$SSH_SIG\"' \t  ' screen -OqxRRS \"$SSH_SIG\" bash -n"
```

My question is specifically about the bash command:

```
bash -n
```

This allows me to abuse bash and use it for chatting. **The '-n' switch (or noexec option) in bash makes bash to not execute anything. Is this safe for using over OpenSSH as a chat mechanism?** The weird thing is, this bash command is an interactive session, and the manual of bash states:

```
    -n      Read commands but do not execute them.  This may be used to check a
    shell  script  for  syntax  errors.  This is ignored by interactive
    shells.

```

Thanks in advance for any tips or remarks.

P.S. As you might have already figured, looking for google for bash + noexec mostly yields results about the noexec mount flag (ugh)...

---

### Post by sudodus on 2012-11-29
I didn't know about ```
bash -n
``` but I see that it works even though I can't find it in man bash.

I don't know enough about internet security to tell how safe it is.

However, I sometimes use the old *write* command. See
```
man write
```
This is an old chat tool, used way back in Unix, but I played with it to teach my daughter some basic command line tools, and it is still there in Ubuntu linux.

You might find this tool convenient :-)

---

### Post by Rexilion on 2012-11-29
> **sudodus said:**
> I didn't know about ```
bash -n
``` but I see that it works even though I can't find it in man bash.

Yes, it's kind of hidden between all the other '-n' 'test' switches. If you search for 'noexec' first and then scroll up to the first instance of '-n' you will find it.

> **sudodus said:**
> I don't know enough about internet security to tell how safe it is.

Yes, this is always hard to asses. I agree.

> **sudodus said:**
> However, I sometimes use the old *write* command. See
```
man write
```
This is an old chat tool, used way back in Unix, but I played with it to teach my daughter some basic command line tools, and it is still there in Ubuntu linux.

You might find this tool convenient :-)

A tool that fits my requirements is better than using an entire shell =) . Thanks I'll try and experiment with this!

---

### Post by Rexilion on 2012-11-29
I gave it a good try (also found the 'who' command), and it has some drawbacks over the old 'bash -n' method:

- It talks to itself if I'm not logged in (the remote user logs in under the same name as the local user)
- Chat history disappears on the other side if the connection breaks

I'm appealed by it's simplicity though. Maybe I have to change some stuff about my setup...

---

### Post by sudodus on 2012-11-29
> **Rexilion said:**
> I gave it a good try (also found the 'who' command), and it has some drawbacks over the old 'bash -n' method:

- It talks to itself if I'm not logged in (the remote user logs in under the same name as the local user)
- Chat history disappears on the other side if the connection breaks

I'm appealed by it's simplicity though. Maybe I have to change some stuff about my setup...

I hope there will also be an answer about the security issue

Good luck :-)

---

### Post by Rexilion on 2012-11-29
> **sudodus said:**
> I hope there will also be an answer about the security issue

Good luck :-)

Again, thank you for your help. I have figured out a secure 'middleground'.

I'm using a seperate user now that starts screen sessions. This user does not have a home directory, but I can specify an alternative screenrc file. This way I can make this screen session 'multiuser' allowing my own user to connect to this.

The reason I did not do this before, is that I assumed that since I blocked a certain range of ports in order to inhibit other users to access someone else his/her remote machine. These ports are only accessible by me.

However, I assumed that *binding* to these ports is also inhibited by other users. This was not the case. 

So, I can keep my firewall simple (and this safe), it doesn't matter now if 'bash -n' is 'safe' since it is ran as an user comparable to 'nobody' and I get to have dedicated screenrc file as a bonus!

However, the 'write' you mentioned might come in handy someday =) Thanks!

---

### Post by Ms. Daisy on 2012-11-29
Do you know if there's a command that will turn off the -n switch? I have no idea but it seems like a crucial thing to know.

You could just use [http://webchat.freenode.net/](http://webchat.freenode.net/) and create your own channel, then give your clients a link to your channel using the "add webchat to your site" feature.
[ATTACH]227930[/ATTACH]

---

### Post by Rexilion on 2012-11-30
> **Ms. Daisy said:**
> Do you know if there's a command that will turn off the -n switch? I have no idea but it seems like a crucial thing to know.

Yes, that is kind of what I'm asking in this thread. However, common sense (to me) says that should not be possible. Because if a command can change this parameter, then it's not suitable for use in scripts.

Furthermore, I looked at other ways of communicating with bash and it seems that signals cannot interfere either...

> **Ms. Daisy said:**
> You could just use [http://webchat.freenode.net/](http://webchat.freenode.net/) and create your own channel, then give your clients a link to your channel using the "add webchat to your site" feature.
[ATTACH]227930[/ATTACH]

I have considered setting up my own IRC chat server for this. But I don't like to involve third parties. This setup (right now) is just me and the other side.

---

### Post by Rexilion on 2012-12-17
I'm not posting what I have and what I use right now. Just to let you know and in case someone else is curious.

- user remote: unix user dedicated for remote control sessions
- user admin: unix user corresponding to an actual uses who manages remote assistance
- env SSH_SIG: environment variable to differentiate between customers, usefull since they all login as user 'remote' so differentiating becames kind of tedious.

[U]There is one caveat to all of this: Remote users can remote forward to any port on my host! I have seen users on OpenSSH mailing lists requesting config settings to limit this, but this has yet to be implemented.

What could happen? Example: You always use 127.0.0.1:80 for a local filtering proxy. Your proxy crashes. A malicious user could attach @ 127.0.0.1:80 and view all your browsing habbits. For me, this is not the case, but a customer that forwards port 5000 for remote assistance could also forward port 5500 and could pretend to be a different person!

However, I can live with this.[/U]

This is in chronological order, containing only relevant snippets:

> **/etc/ssh/authorized_keys/remote]
#Example customer said:**
> 

[QUOTE=/etc/ssh/sshd_config]AllowUsers remote
Protocol 2
ChallengeResponseAuthentication no
PasswordAuthentication no
RSAAuthentication no

AuthorizedKeysFile /etc/ssh/authorized_keys/%u # restricted authorized keys management
PermitUserEnvironment yes # allow environment variable passing
UsePrivilegeSeparation sandbox # not working yet, need seccomp for this

Match user remote # unix user for remote assistance
AllowAgentForwarding no # disabling makes since there is no shell access
PermitOpen none # disable local and dynamic forwarding
ForceCommand screen -c /etc/custom_scripts/remote_screenrc -qxRS "$SSH_SIG" # start screen session

[QUOTE=/etc/custom_scripts/remote_screenrc]multiuser on
acladd admin
bindkey "^D" exec # prevent remote user from shutting down session
screen bash /etc/custom_scripts/remote_bashrc # start new screen with custom start parameters
chacl remote -x ? # disable remote user from doing *anything* (e.g. screen exec can execute commands!)[/QUOTE]

[QUOTE=/etc/custom_scripts/remote_bashrc]echo Dear "$SSH_SIG"
echo Welcome to Remote Assistance
echo Please use this screen to communicate
echo Type short textnotes, end them by pressing [ENTER]
echo
echo
export HISTFILE=~/log_"$SSH_SIG" # set up dedicated logfile
export HISTTIMEFORMAT='%F %T ' # enable history (man bash)
touch "$HISTFILE"
chmod 606 "$HISTFILE" # allow admin to view and modify these files
echo Session started on: "$(date)" >> "$HISTFILE"
export PS1="${SSH_SIG} \t : " # Make PS1 echo customers name and date
exec bash -n # execute dumb and restricted shell for chat only functionality[/QUOTE]

Initial setup:

```
# user: remote
groupadd -g 501 remote
useradd -p "" -M -u 501 -g 501 -d /var/log/remote remote
mkdir -p /var/log/remote
chown remote:admin /var/log/remote
chmod 370 /var/log/remote
```

Cliënt side:

- VNC server attaching to looback only (security).
- PuTTY + private key remote port forwarding VNC to my PC.

One caveat, PuTTY exhibits 'non default window behaviour': Minimizing the PuTTY window, by clicking on the _ symbol of it's window, from within the VNC connection makes the tunnels go down (and thereby hanging your VNC connection indefinitly). I have not found a good way around this (yet). Minimizing from the taskbar works, though...

I think I have it all pretty much under control right now. If anyone has questions/suggestions/critique please do not hesistate to post.

---

### Post by CharlesA on 2012-12-18
TBH, it would be way easier to just use something like gotomeeting or TeamViewer for what you want to do.

---

### Post by Rexilion on 2012-12-18
Gotomeeting involves a third party and TeamViewer is payed.

---


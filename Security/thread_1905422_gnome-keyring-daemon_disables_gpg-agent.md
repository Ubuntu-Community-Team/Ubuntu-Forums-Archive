---
title: "gnome-keyring-daemon disables gpg-agent"
date: 2012-01-06
forum: Security
---

### Post by Yurim on 2012-01-06
Hi,

where is the gnome-keyring-daemon started and how can I configure it to not start the gpg-agent emulation?

Story so far:
I want to use my new Crypto Stick with GnuPG. The basics do work, but I can't use the gpg-agent and therefore Enigmail refuses to encrypt/sign/decrypt mails. 

$ gpg --card-status
gpg: selecting openpgp failed: unknown command
gpg: OpenPGP card not available: general error

$ gpg --no-use-agent --card-status
Application ID ...: D27600012401020000050000115A0000
[...]

My ~/.gnupg/gpg.conf enables the gpg-agent with 
use-agent

/etc/X11/Xsession.d/90x11-common_ssh-agent
checks if gpg.conf has 'use-agent' enabled and sets the STARTUP variable correctly:
STARTUP='/usr/bin/gpg-agent --daemon --sh --write-env-file=/home/user/.gnupg/gpg-agent-info-machine /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session --session=ubuntu-2d'

The file /home/user/.gnupg/gpg-agent-info-machine contains the correct environment settings:
GPG_AGENT_INFO=/tmp/gpg-n8NEBl/S.gpg-agent:9998:1
SSH_AUTH_SOCK=/tmp/gpg-SJd4WP/S.gpg-agent.ssh
SSH_AGENT_PID=9998

With these settings gpg (and Enigmail) can successfully use the smart card.
$ . ~/.gnupg/gpg-agent-info-machine
$ gpg --card-status
Application ID ...: D27600012401020000050000115A0000
[...]

But without manually setting GPG_AGENT_INFO the variable is:
/tmp/keyring-I3X2tC/gpg:0:1
which is AFAIK caused by gnome-keyring-daemon.

So I'm looking for a way to disable the start of the gpg-daemon emulation. gnome-keyring-daemon has the command line option --components, so it should be possible to disable the gpg-agent component.

Now where is the daemon started and how can I configure it? Or am I on the wrong track and everything is dead simple?

Thanks in advance,
Yurim

---


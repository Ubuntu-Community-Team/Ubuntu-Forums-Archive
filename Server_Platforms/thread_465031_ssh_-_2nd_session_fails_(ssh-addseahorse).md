---
title: "ssh - 2nd session fails (ssh-add/seahorse)"
date: 2007-06-05
forum: Server Platforms
---

### Post by bobstro on 2007-06-05
I am running Feisty, and am experiencing a problem with ssh-agent/ssh-add on one machine. I have created ssh keys and applied a passphrase. On another machine also running feisty, everything works properly. I do:

ssh hostname

and ssh-askpass pops up and asks for my passphrase, and I can start additional sessions at whim. However, on this machine, the first session succeeds normally, but any subsequent attempts simply hang. This occurs regardless of the remote host I am attempting to connect to.

If the host is nost already in my ~/.ssh/known_hosts, I am asked to accept the key, but then the second session fails.

If I terminate the original (successful) session, subsequent attempts still fail.

Logging out and back in results in the same sequence.

I see ssh-agent running (ps output):

> /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/seahorse-agent --execute /usr/bin/startkde

I have the following installed:
> $ dpkg -l | grep ssh
ii  denyhosts                                 2.6-1                                      an utility to help sys admins thwart ssh hac
ii  kdessh                                     3.5.6-0ubuntu2                             ssh frontend for KDE
pi  openssh-client                             4.3p2-8ubuntu1                             Secure shell client, an rlogin/rsh/rcp repla
ii  openssh-server                             4.3p2-8ubuntu1                             Secure shell server, an rshd replacement
ii  ssh                                        4.3p2-8ubuntu1                             Secure shell client and server (transitional
ii  ssh-askpass                                1.2.4.1-6.1                                under X, asks user for a passphrase for ssh-
ii  ssh-askpass-fullscreen                     0.3-2                                      Under Gnome2, asks user for a passphrase for
ii  ssh-askpass-gnome                          4.3p2-8ubuntu1                             under X, asks user for a passphrase for ssh-$ dpkg -l | grep seahorse
ii  seahorse                                   1.0.1-0ubuntu1                             A Gnome front end for GnuPG
ii  sshfs                                      1.6-1                                      filesystem client based on SSH File Transfer


I experience the same problem whether using ssh from a terminal prompt, or using putty.

My $HOME is NFS-mounted, and is the same between the two machines (as is ~/.ssh).

If I remove the seahorse package, I am asked for my passphrase at the terminal prompt and can start multiple sessions. However, I have to re-enter my passphrase each time, which is annoying.

I'm stuck at where to proceed. syslog and auth.log don't seem to show any clues.

Any help appreciated!

- Bob

---

### Post by turinglabs on 2007-06-05
X-sessions are started under an ssh-agent by default, so you can just bring up a terminal window once you are logged into your desktop and type 'ssh-add'. Enter your passphrase once, and it wil be added to the agent you are running under, which will be in effect for all X clients started under your curent session.

One thing I noticed that was odd was 'pi openssh-client...' in your dpkg output. This indicates that your ssh client is selected to be purged, even though it is currently installed. Did you abort a package removal attempt?

---

### Post by bobstro on 2007-06-05
Thanks for the tips. I've done a bit more troubleshooting, and it appears seahorse is the culprit. If I remove seahorse, everything works as you described using ssh-add. However, with seahorse reinstalled, ssh-add locks up in the same manner.

I am not certain yet whether this applies only to my user or others as well, but will check that out next. The curious thing is that any preferences in my $HOME are the same between both machines (NFS-mounted /home).

seahorse seems to be the default means of launching ssh-agent for X sessions, so I'm loathe to simply zap it.

I did find the following error messages in /var/log/auth.log:

> Jun  5 10:27:41 PC4 ssh-agent[7432]: error: Unknown message 252
Jun  5 10:28:27 PC4 seahorse-agent[7444]: couldn't communicate with gnome keyri
ng daemon via dbus: The name org.gnome.keyring was not provided by any .service
 files
Jun  5 10:28:27 PC4 seahorse-agent[7444]: couldn't search keyring: (code 2)
Jun  5 10:28:30 PC4 seahorse-agent[7444]: file seahorse-agent-cache.c: line 435
 (seahorse_agent_cache_count): assertion failed: (g_cache != NULL)

I am presently running KDE, but again, this was an issue under gnome as well. I also note that I'm having the same problem using remote ssh mounts via nautilus and konqueror (fish://). Everything just locks up until I abort the process trying to connect.

I'm close, but don't know quite what next step to take! Thanks for any help!

- Bob

---

### Post by turinglabs on 2007-06-05
> **bobstro said:**
> Thanks for the tips. I've done a bit more troubleshooting, and it appears seahorse is the culprit. If I remove seahorse, everything works as you described using ssh-add. However, with seahorse reinstalled, ssh-add locks up in the same manner.
...
seahorse seems to be the default means of launching ssh-agent for X sessions, so I'm loathe to simply zap it.
- Bob

You'll be OK removing seahorse  - it will only be used if it is installed. As an example, I do not have seahorse installed, here is how my X session runs:

/usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session

It looks like seahorse is trying to communicate with the gnome-keyring-daemon, failing, and sending an error code to ssh-agent that the latter does not understand. If you really want to use seahorse, you could make sure that the gnome-keyring-daemon is running (just run it from the command line), it may be that under KDE this is not started by default (seahorse depends on the gnome-keyring package, among others).

---

### Post by bobstro on 2007-06-05
Everything "works" except the automatic launch of gaskpass or equivalent when I haven't run ssh-add yet. It looks like seahorse is somehow tied in with that feature. It isn't a major issue, but I'm disappointed to have a feature that was working drop dead on me like this.

I'll continue tinkering with gnome-keyring-daemon and seahorse.

Thanks for the pointers! They've been useful in getting this far.

- Bob

---


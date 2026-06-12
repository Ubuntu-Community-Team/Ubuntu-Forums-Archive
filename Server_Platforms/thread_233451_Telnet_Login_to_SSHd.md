---
title: "Telnet Login to SSHd"
date: 2006-08-10
forum: Server Platforms
---

### Post by bleh on 2006-08-10
Just a really quick question, I'm testing the SSH daemon on my desktop at the moment so I'll be able to log in remotely... 

There's just minor thing that's bugging me before I let it face the internet, if I telnet onto port 22, it shows straight away what Linux Distro I'm running. Is this output from a text file which I could edit, or could I just switch it off?

Like I say, it's only a minor issue, but generally I think it's best to display as little info as possible

---

### Post by scxtt on 2006-08-10
it's nothing to worry about, as the distro is irrelevant and even if you do have and ssh daemon listening, that's not a clue as to a way to hack into your box ...

i have 2 ports open on my box, ssh and vnc - and i'll be damned if i'm gonna 'close' them entirely out of fear of being hacked ...

if you have a non-root (no root user @ all is a good policy) user name, a decent user username and p/w and a good firewall (i only allow my work IP a.t.m.) you should be fine ...

telneting to a ssh port (i haven't seen telnet (be it a daemon) used in a LONG time) is worthless, even if it does give you a "hey, this box is using ubuntu" response ...

---

### Post by bleh on 2006-08-10
Hey, thanks for the quick response. Yeah I've been using a firewall on the box to control what IP ranges can connect, and am using what I regard as a pretty strong user/pass combination. (I'll live to regret saying that....)

Still though I like the idea of not printing any information besides a password prompt...

---


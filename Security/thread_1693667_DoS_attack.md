---
title: "DoS attack"
date: 2011-02-23
forum: Security
---

### Post by fela on 2011-02-23
While I was away for two weeks, my server (which runs Debian) recieved a denial of service attack and wouldn't respond to ping until my friend (who co-runs the server over SSH) sorted the problem out.

I have no idea what to do about this, because I've never recieved an attack like this before. I'm not sure exactly what it was attacking, but my server runs quite a few services, including an apache web server and postfix email server, as well as an IRC server.

I guess I have to individually go through each service that it runs to the outside world, and protect each against DoS. So how would I protect these:

Apache
SSH (OpenSSH)
Postfix
FTP (vsftpd)
IRC (unrealircd)

I doubt they used SSH as their means, because it's set to run on a non-standard port and so isn't so easily discoverable.
I'm not sure about apache, although I would have thought it would be easy to recognize a DoS on that though (barrage of requests from a single source for example).
Postfix - again not sure.
I doubt they used FTP. I've never heard of a DoS attack exploiting the vsftpd FTP server ;)
IRC sounds quite likely. It's easy to put that under extreme load...although it is supposed to have built-in protection against floods.

Cheers,
Fela

---

### Post by SeijiSensei on 2011-02-24
Personally I wouldn't run an IRC server on any machine in a production environment unless it was heavily firewalled so that inbound connections only came from trusted sources.  The only time I've had a server compromised (about a decade ago now) was when someone exploited a hole in Apache 1.3 and installed an IRC relay on my web server.  There's just too many people in the IRC world out to play these little games.

Have you checked your Apache and Postfix logs?  Do they show the heavy traffic required to bring down your server?  If so, identify the IP addresses involved and block them with iptables.

---

### Post by fela on 2011-02-25
> **SeijiSensei said:**
> Personally I wouldn't run an IRC server on any machine in a production environment unless it was heavily firewalled so that inbound connections only came from trusted sources.  The only time I've had a server compromised (about a decade ago now) was when someone exploited a hole in Apache 1.3 and installed an IRC relay on my web server.  There's just too many people in the IRC world out to play these little games.

Have you checked your Apache and Postfix logs?  Do they show the heavy traffic required to bring down your server?  If so, identify the IP addresses involved and block them with iptables.

Hmm, well the IRC server is actually only run alongside a game server (minecraft), it's not popular with anyone except those playing the game.

I think, unless I get loads of attacks, I won't worry about it for now, but if I do, thanks for your advice :)

---


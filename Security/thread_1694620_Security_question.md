---
title: "Security question"
date: 2011-02-24
forum: Security
---

### Post by Pharnavaziani on 2011-02-24
Hi,
I'm a just-beginning Ubuntu 10.04/Lucid user.  I'm aware of the  excellent safety pedigree Linux has, but I'm worried about keyloggers  and spyware.  On Firestarter, I have a number of connections which are  listed as being from an Unknown service (as opposed to HTTP, HTTPS, FTP,  etc.,) towards various hostnames I do not recognize.  In the past I  haven't had the safest web browsing habits, does my machine have a  security risk?

In the future, prevention is key - I'm a quick  learner - but I want to deal with this now, lest I forget and potential  expose compromising information to a third party.

---

### Post by CharlesA on 2011-02-24
Firestarter lists active connections, which is pretty meaningless. An active connection can be anything from a torrent, to your web browser.

The only thing you need to worry about is if there is a connection to a service you are running, like apache, ftp or ssh.

Also note that firestarter conflicts with ufw (which is installed by default, but not enabled by default)

---

### Post by bodhi.zazen on 2011-02-24
> **Pharnavaziani said:**
> Hi,
I'm a just-beginning Ubuntu 10.04/Lucid user.  I'm aware of the  excellent safety pedigree Linux has, but I'm worried about keyloggers  and spyware.  On Firestarter, I have a number of connections which are  listed as being from an Unknown service (as opposed to HTTP, HTTPS, FTP,  etc.,) towards various hostnames I do not recognize.  In the past I  haven't had the safest web browsing habits, does my machine have a  security risk?

In the future, prevention is key - I'm a quick  learner - but I want to deal with this now, lest I forget and potential  expose compromising information to a third party.

Start with the security sticky.

---


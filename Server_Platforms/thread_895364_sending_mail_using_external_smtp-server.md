---
title: "sending mail using external smtp-server"
date: 2008-08-20
forum: Server Platforms
---

### Post by pascali70 on 2008-08-20
Hi,

Is it possible to send a mail from the terminal using a external smtp-server.  If yes, do you have to install extra software and what are te commands to send the mail ?

thanks in advance,

Pascal.

---

### Post by Ximbiot on 2008-08-20
You can send mail from the command line using mailx:

```
apt-get install mailx
```

That command should install any dependencies as well, but you might consider nullmailer as a simple forwarding mail server - nullmailer can be configured to forward mail to a "smart host" (presumably, your ISP's mail server) if you need to.

```
apt-get install nullmailer
```

---

### Post by Ximbiot on 2008-08-20
There are also some curses-based mail clients that are more interactive than mailx.  mutt and pine come to mind.  Try them both out and uninstall the one you don't like:

```
apt-get install pine mutt
```

---


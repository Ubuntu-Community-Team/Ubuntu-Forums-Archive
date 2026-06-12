---
title: "LAN-only email for home"
date: 2010-06-16
forum: Server Platforms
---

### Post by lykwydchykyn on 2010-06-16
I have a server at home, which I'd like to set up as an email server for my LAN only.  Basically, my kids aren't old enough to need real email addresses, but I want them to have something where they can send and receive email to each other for fun, or where they can get emails from our moodle server (also on the LAN).

I know most Linux systems have some kind of internal mail system set up (for instance I can mail another user on the system with the "mail" command, then read this in mutt), is there an easy way to centralize this and make it accessible from mail clients on the LAN?  Or do I need to set up a full-blown post office?

I've fiddled with postfix a little, but otherwise I'm a bit in the dark on email...

---

### Post by BobVila on 2010-06-16
I'd stick with postfix - an internal setup shouldn't be too bad to set up.

After a quick scan of the interwebs, I came across a little HOWTO:

[http://forums.pcper.com/showthread.php?t=448351](http://forums.pcper.com/showthread.php?t=448351)

It's written for CentOS, but, aside from the yum commands, you should be able to use it verbatim for an Ubuntu setup.

---

### Post by lykwydchykyn on 2010-06-16
Thanks, I'll give that a try.

---


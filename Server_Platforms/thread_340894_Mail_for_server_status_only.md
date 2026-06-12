---
title: "Mail for server status only"
date: 2007-01-17
forum: Server Platforms
---

### Post by chowdah45416 on 2007-01-17
Hey all,

I recently changed some hard drives around on my server and got everything back to normal except for sendmail.  For some reason it doesn't work anymore, so I uninstalled it just to be safe.  I don't need help with that problem because I had way too much on for what I need.  The only reason I need mail on my server is to send an outgoing message everyday to myself about the status of the server.  I was simply using mutt (or mail worked too) on the command line to just send myself the mail.  (`echo "test" | mutt [email]email@address.com[/email])

I would like to know if anyone can tell me how I would go about setting up sendmail or some other program to give me this ability while keeping myself secure by not running a normal mail server.  Thanks.

---

### Post by jtc on 2007-01-18
If I understand thigns correctly, you want a mailserver/mta only only cabable of sending mails? Well, I haven't used sendmail that much, but with Postfix I know it is a really simple matter. When debconfig runs during the installations, all you do is simply to choose to setup Postfix as a satelite-system.

If you want to set up things manually the key setting, with any MTA, is to tell it to only listen to your local network loopback-device. In postfix (/etc/postfix/main.cf) the setting in question looks like this.

```
inet_interfaces = loopback-only
```

---


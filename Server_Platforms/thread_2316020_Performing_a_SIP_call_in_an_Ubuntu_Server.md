---
title: "Performing a SIP call in an Ubuntu Server"
date: 2016-03-04
forum: Server Platforms
---

### Post by sergio38 on 2016-03-04
Hi!

I am in a project where I will be opening/closing doors in a company via Telegram.
The way it works right now it's via telephony. So when you ring a certain number (depending if you're allowed or not) it opens a door.

I would like to build an Ubuntu server to perform a SIP call to an Asterisk VoIP Server, so I can continue to develop the Telegram part. The problem is that I don't find any SIP client without GUI, so I would like to hear what SIP Client have you used in CLI mode.

Thank you!

---

### Post by sergio38 on 2016-03-07
Anyone?

---

### Post by howefield on 2016-03-07
Thread moved to the "*Server Platforms*" forum. You might get more interested traffic here.

---

### Post by volkswagner on 2016-03-07
Have you searched "Command line softphone"?

There are some solutions out there, but the do seem a bit old (perhaps that's a problem)

[pjsua]("http://www.pjsip.org/pjsua.htm") and [sipcmd]("http://sipcmd.sourceforge.net/") may be worth looking into as well as [LinPhone]("https://apps.ubuntu.com/cat/applications/raring/linphone-nogtk/").

What initiates the call if you don't need a gui or hardware device? I ask because phones like Cisco SPA series can accept url directives. For example
There's a [cool browser plugin]("https://chrome.google.com/webstore/detail/cisco-dialer/deelocceageedapbhbdepkcpdmlmoeog?hl=en") that allows a user to click on a phone number in google contacts and it will dial out on the Cisco. I bring this up becuase
perhaps you don't need a softphone, but a device that has a decent api. Perhaps you can do you programming directly in Asterisk/FreePBX with
custom Extension and/or custom destination.

Pardon my simplistic view, as I'm not a developer ;)

---


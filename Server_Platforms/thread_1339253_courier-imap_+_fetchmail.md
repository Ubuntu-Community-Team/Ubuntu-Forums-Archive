---
title: "courier-imap + fetchmail"
date: 2009-11-27
forum: Server Platforms
---

### Post by Dr Small on 2009-11-27
I am looking for a way to invoke the fetchmail script for a specific user, whenever a client connects to the IMAP server to check/download messages.

Like for instance, joe connects from Thunderbird to check his local IMAP mail. When he connects to download any new messages, courier-imap invokes the fetchmail script and downloads any messages from the remote POP3 server, adds them to the maildir, and then the Thunderbird client receives them.

I've been looking around for a way to do this... Is it even possible?

Dr Small

---

### Post by HermanAB on 2009-11-27
You probably could do that, but an easier way is to drop your fetchmail script into /etc/cron.hourly.

---

### Post by Dr Small on 2009-11-27
Yeah, I know how to do that. But see, I was thinking of setting up a local IMAP account on my server for my parents, so whenever they check their IMAP mail, it would poll their POP3 servers, download messages and deliver them to their client.

They probably wouldn't like the idea of having to wait every hour, to check mail. I was just trying to find a way to set it up, so whenever they check their client, it'd be the same as downloading from the POP3 accounts, and yet all of their mail would be storred on my IMAP server for convienance.

Dr Small

---


---
title: "ssh-agent on Ubuntu Server (I need it from cron jobs)"
date: 2009-03-19
forum: Server Platforms
---

### Post by tnek on 2009-03-19
Hi,

I'm planning to use key based login with a passphrase for a bit of increased security. My first question is: Is this a good idea or should I just use a key with a blank passphrase?

My follow-up question. The server will run scripts periodically which uses ssh to access other machines. This should be handled automatically as I can't stay with the server and enter passphrases all day. ;)

I've looked a bit at ssh-agent, and it might be what I need. Will it solve my problem and always (even after a reboot of the server) provide the passphrase automatically?

There seem to be a lot of confusion about when and how to start ssh-agent. There are lot of options out there. In an X Window based system starting it before starting i.e. Gnome seem to be a good idea. But what about a command line based server system? The key issue is that the scripts will be started automatically and need ssh access. It is also possible that two scripts run at the same time. How should I solve it?

---

### Post by HermanAB on 2009-03-19
Save yourself the head-ache and use a blank passphrase.  It is OK if the server is under your control and you run a tight firewall.

Cheers,

Herman

---


---
title: "Execute command when satelliste host receives an email"
date: 2012-09-06
forum: Server Platforms
---

### Post by anXieTyPB on 2012-09-06
Good evening.

I am currently running a satellite postfix-configuration on my ubuntu 12.04 64bit server in order to send emails by using my gmx.net account.

This works fine.

What i need right now is a possibility to execute a command when my gmx.net account receives an email with a specific content, e.g.
"run defaultscript". 

Can I do this with postfix or do I need a POP3-server that fetches mails from my satellite account, processes the fetched mails and then runs a script when an email matches my search-string?


Kind regards!

---

### Post by SeijiSensei on 2012-09-06
Install **procmail**.  You can then write a "recipe" that looks for regular expressions in either the headers or body, or both, and pipes matching messages to a script.

Procmail replaces the usual mail.local delivery agent.  It processes messages after they have arrived.  You can use it in conjunction with **fetchmail** to retrieve a message from the POP3 account and pass it to procmail for delivery.  If you don't want the messages deleted from the POP account you'll need to make sure that you tell fetchmail to leave the messages on the server.  Alternatively you could have fetchmail collect all the mail on the POP account then have procmail pass the ones that match the key text to the script and forward the rest of them to your regular email account.

[http://fetchmail.berlios.de/fetchmail-man.html](http://fetchmail.berlios.de/fetchmail-man.html)
[http://linux.die.net/man/5/procmailrc](http://linux.die.net/man/5/procmailrc)
[http://linux.die.net/man/5/procmailex](http://linux.die.net/man/5/procmailex)

Both procmail and fetchmail are in the repositories.  For some reason that I've never understood procmail does not seem to be the default delivery agent on Ubuntu like it is on RedHat-flavored systems.

---


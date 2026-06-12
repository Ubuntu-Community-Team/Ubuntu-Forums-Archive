---
title: "Dovecot imaps not working"
date: 2011-11-20
forum: Server Platforms
---

### Post by LinuxRocks on 2011-11-20
Hey all,

Been banging my head on this all night... 

Set up dovecot imap so I can have my mail stored on a secure, redundant server.

I am not using postfix, this is simply an imap mail storage server - I have an ISP that I pull mail from.

When I follow all the instructions and set my protocol to imaps, dovecot fails to start.

There are no errors in mail.err or any other log. I have ssl/tls set up properly and have my certs all in place.

If I set the protocol to imap, it works great.

Is there any way to get a secure connection?

BTW, I have set up dovecot 1000 times before on 10.04 and never had a problem, but the devs seems to have split every stanza in dovecot.conf into individual conf files now, so its possible I missed something.

Any ideas? Let me know if you want to see any config files and which ones and I will post.

No firewall is set up and I am running 11.10 64 bit. No encryption on /home

Thanks!

Joe

---

### Post by LinuxRocks on 2011-11-20
BUMP!

Anyone have any ideas why imaps does not work?

Thanks!
Joe

---

### Post by LinuxRocks on 2011-11-21
Ok, I just found out that imaps is deprecated and no longer going to be used.

Developers have implemented SSL/TSL and STARTTSL for clients and there is no need for secure imap or pop connections anymore.

I was surprised by the lack of information about imaps as I have always used it, but apparently, newer imap and pop servers have decided to get rid of it as it hasn't been needed... I guess for some time.

Here is some more information:
[http://wiki2.dovecot.org/SSL](http://wiki2.dovecot.org/SSL)

I tested my server just using imap and I am unable to even log into the server using telnet; even after starttls. Only able to start with a client that initiates tls before login. Kmail is such a client.

After tcpdumping my connection for some time, I am satisfied that imap is now secure... Just make sure you read the docs CAREFULLY and implement ssl and disable_plaintext_auth=yes along with ssl=required.

Surprised that no one else chimed in to this thread - although, I was more surprised about the changes :)

Hope this saves someone else a few days of investigation :).

Joe

---

### Post by SimonSimCity on 2013-02-20
Most of the tutorials out there are written for Dovecot in version 1.x.

As of 2.0, many configuration-options have been rewritten. You may have more deprecated messages in your log-files.
Dovecot provides a tool helping you to migrate your old configuration to Dovecot v2.0. Please read the wiki for further information: [http://wiki2.dovecot.org/Upgrading/2.0](http://wiki2.dovecot.org/Upgrading/2.0)

---


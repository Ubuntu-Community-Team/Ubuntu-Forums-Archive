---
title: "server"
date: 2008-02-10
forum: Server Platforms
---

### Post by clontet on 2008-02-10
how do I install an SMTP server?
i mean
i want to be able to type

echo Sending out to yahoo | mail [email]science90@yahoo.com[/email]

i think i have "sendmail" installed as a mail relay
i can send to science90@localhost
but not to the outside world.

any help on this?

---

### Post by astrotech226 on 2008-02-10
If you are running Gutsy, sendmail is not the default mail program.  Here's what I had to do.  First install the "mailx" package.  That will install the /usr/bin/mail program that allows you to do your echo command.

Next, you'll have to reconfigure exim to allow sending to remote servers.  Your particular set up will vary, but you will most likely want to run the following command and pick "mail sent by smarthost; no local mail".

$ sudo dpkg-reconfigure exim4-config

---


---
title: "Dovecot init.d script"
date: 2006-10-23
forum: Server Platforms
---

### Post by trawler on 2006-10-23
I've recently installed dovecot on my ubuntu edgy, and one of the first things i noticed was that when starting/stopping/restarting the server, there's no output whatsoever to console - which was very annoying since you can't be sure if anything actually happened (if it succeeded loading, or not)

So I added a few lines to the script, and now it works fine :)
I'm attaching the script, in case anybody needs it.

And btw - does anybody know of a good dovecot.conf tutorial?

---

### Post by tstreit on 2006-10-23
This is documentation that I used to set up my email server.  It worked quite well.

[https://help.ubuntu.com/community/MailServer]("https://help.ubuntu.com/community/MailServer")

Can you tell me a little more on how to install the Dovecot script.  I am kind of new to linux, I have played with it for years but just recent got really serious into it.

---

### Post by trawler on 2006-10-23
> **tstreit said:**
> Can you tell me a little more on how to install the Dovecot script.  I am kind of new to linux, I have played with it for years but just recent got really serious into it.


Backup your old configuration first:
```

sudo cp /etc/init.d/dovecot /etc/init.d/dovecot_bak

```

And then just edit /etc/init.d/dovecot with your favorite editor:

```

sudo vi /etc/init.d/dovecot

or

sudo gedit /etc/init.d/dovecot

```

Delete the contents, and paste the contents of my startup scripts.
If it doesn't work for some reason, you can always restore your old startup script.

---

### Post by tstreit on 2006-10-23
Thanks I will give it a try!

---


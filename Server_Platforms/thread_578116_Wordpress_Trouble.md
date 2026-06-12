---
title: "Wordpress Trouble"
date: 2007-10-16
forum: Server Platforms
---

### Post by mattc908 on 2007-10-16
The people at the wordpress forums dont like to help, seriously they tell me not to ask my question there not there for server issues........ Even though its part wordpress. For wordpress when you register on my server, it should kick back and email with an auto generated password to the person it never does any clues.

---

### Post by crouton on 2007-10-17
To be honest, if you don't post any information at all you won't get many responses no matter where you ask for help.

First off, do you have a MTA installed?  Postfix, sendmail, etc.  Anything that would actually do the mail transfer.

Secondly, is Wordpress looking locally for a mail server, or do you have it pointed elsewhere (perhaps your ISP?)

Check those and you'll probably find your issue.

---

### Post by mattc908 on 2007-10-17
Okay well I do not have a mail system set up on the server is there a way to set it up to use a 3rd party system? Like add the server to send email connecting through POP3?

---

### Post by mattc908 on 2007-10-18
Bump

---

### Post by crouton on 2007-10-18
```
sudo apt-get install postfix
```

It should walk you through a menu-based configuration.  I don't remember the exact Site Configuration options that are displayed, but you will likely want the 'forward-to-gateway' or 'send-only' option however they are actually named.

---

### Post by mattc908 on 2007-10-18
Postfix is the only thing?

---


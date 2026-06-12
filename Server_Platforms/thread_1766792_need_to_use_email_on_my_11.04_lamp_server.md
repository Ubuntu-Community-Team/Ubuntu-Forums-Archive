---
title: "need to use email on my 11.04 lamp server"
date: 2011-05-24
forum: Server Platforms
---

### Post by RadarG on 2011-05-24
Hello I'm using ubuntu server 11.04 in a LAMP configuration. I have my login page setup but my php email verification isnt working. I would like to know how can I install a relay that can take the email verifications and send them through a gmail account. any help will be most welcome thanks.

---

### Post by Lars Noodén on 2011-05-25
Do you have postfix, exim or some other mail transfer agent (MTA) installed and configured yet?

---

### Post by brettg on 2011-05-25
The easiest method is to relay mail via another smtp server. You can use a "smarthost" in sendmail but this get's tricky if the upstream server is on another network and won't accept your smtp requests.

Personally I use ssmtp to send via my GMail account for servers that need to email me.

[Instructions here]("http://tuxnetworks.blogspot.com/2009/03/mutt-to-remote-smtp-server.html")

---


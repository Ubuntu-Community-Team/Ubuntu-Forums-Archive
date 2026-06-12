---
title: "Master-Slave Mail Server?"
date: 2011-04-01
forum: Server Platforms
---

### Post by munky99999 on 2011-04-01
So we have mail server(postfix/sendmail) infrastructure already but ideal I would like to see a way of creating a sort of slave mailserver that could be deployed on say a LAN who sends all mail through our current public mail server. Ideally it would be able to be setup such that users would be able to just change their imap-smtp address and nothing else. Then any time they want to send emails which are local to that place. The mail never has to leave the LAN. Also if the public mail server were to go down. The mail just sits on the LAN until it can go out. While local mail still works fine. 

Essentially it would be a Slave server to the Master that already exists. Anyone have a tutorial or something?

---

### Post by HermanAB on 2011-04-02
Howdy,

All mail servers can do that.  On most it is called .smart host'.  postfix calls it something else, but Google will find it anyway of you search for postfix+smart+host.

So pick your poison: Postfix, Citadel, Zimbra, Qmail...

---


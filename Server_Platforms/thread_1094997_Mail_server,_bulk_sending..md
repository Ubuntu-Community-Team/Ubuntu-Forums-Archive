---
title: "Mail server, bulk sending."
date: 2009-03-13
forum: Server Platforms
---

### Post by trstn on 2009-03-13
Hi there, I'm in the process of moving all our servers from windows setups to ubuntu LAMP servers, so far all's going well. The last to move is our mailserver, set up seems easy enough if i follow this guide: [http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/").

But.... We're an email marketing company, currently using [groupmail ]("http://www.group-mail.com/")on windows to send around 50`000 emails each day. 

The server side all sounds good to go, but I'm struggling to find any applications to send large amounts of html emails, does anyone have any ideas?

---

### Post by madverb on 2009-03-13
[mailman]("http://www.gnu.org/software/mailman/index.html")?

---

### Post by BkkBonanza on 2009-03-13
That level of email should be managable easily with any linux mail server. You are more likely worried about "special functions" of group-mail (which I am not familiar with). But certainly sending 50,000 emails/day with any good mail server shouldn't be any sweat. I guess it depends if they are really big too.

---

### Post by trstn on 2009-03-13
Ah yeah definitely, in fact I think linux should be able to send the volume much better than our current windows setup.

I don't really use the special features of group mail, it just happens to be the best program i found for windows, it allows me to create one email that's sent to 50`000 addresses individually, I need to achieve the same in linux for us to move. The only cleverness is it replaces !*NAME*! !*EMAIL*! with stuff from imported lists.

I probably sound like a spammer, so in case you're worried our website is [www.manchesterconfidential.com]("http://www.manchesterconfidential.com"), we send offer emails to opt ins only :)

---


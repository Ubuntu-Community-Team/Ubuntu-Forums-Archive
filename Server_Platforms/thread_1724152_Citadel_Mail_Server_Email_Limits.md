---
title: "Citadel Mail Server Email Limits?"
date: 2011-04-08
forum: Server Platforms
---

### Post by clegends on 2011-04-08
Hi folks, have just run into a really frustrating problem. I run a theatre company, and our address list is over 600 emails. Have just tried to send a group email newsletter out to our list through evolution, and am blocked with the error message:
```
RCPT TO <emailaddress> failed: Too many recipients
```
I run Citadel Mail server on an Ubuntu 10.04 box (server edition). Any help would be really appreciated. I know this isn't an Evolution issue, as before having Citadel I used Postfix flawlessly. For the most part I love Citadel (so easy), but this just sucks. Can someone tell me what's going on, and where to look to disable a limit on the email addresses I can send this to? Thanks

Mitchell

---

### Post by elico on 2011-04-08
i dont know how but if citadel blocked you it means you really tried weird stuff.
how many recipients are we talking about?

---

### Post by HermanAB on 2011-04-08
Howdy,

Citadel can handle massive amounts of mail (256 Terabytes!), so you are somehow doing it wrong.

To send a message to a large number of users, you need to set up a mailing list.  This is basically a special room with all the addresses of the people on the list subscribed to it.  Then you send the message to the room and Citadel will forward the message to each subscriber:

"http://www.citadel.org/doku.php/faq:everydayuse:what_if_someone_wants_to_make_a_room_into_a_mailing_list_can_we_do_that"

"http://www.google.com/search?hl=en&q=citadel+mailing+list+howto"

"http://www.citadel.org/doku.php/documentation:system_administration_manual"

---

### Post by clegends on 2011-06-30
Thanks so much for this! I had forgotten to subscribe to this thread, and hadn't checked back. I will follow up those links. It makes sense I need to create a room. I'm trying to send about 600 emails at a time. Will let you know how I go. Cheers.

---

### Post by clegends on 2011-06-30
I'm getting closer... have made a room, (ridiculously easy), and set it up to receive posts (and thus send emails) from one user only. What's happening now though, is that when I send out an email, it's adding my subject heading, but prefixing it with [0000000019.CuriousViews]

So if my subject heading is: Greeting Everybody!
I get instead: [0000000019.CuriousViews] Greetings Everybody!

The 0000000019.CuriousViews Prefix seems to be the name of my room, even though the name I actually gave it was CuriousViews. So how do I get around this, and either:
1. Edit my room so that the name is only [CuriousViews], rather than [0000000019.CuriousViews], or get rid of the room name all together? There must be a way to do it, but the past hour searching has yielded nothing. Thanks again for your help.

~Clegends

---

### Post by clegends on 2011-09-02
Solved. Needed to make the rooms public. Cheers.

---


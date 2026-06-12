---
title: "Ubuntu bots"
date: 2010-12-16
forum: The Cafe
---

### Post by ki4jgt on 2010-12-16
I would like to host a bot on AIM which could look up phone numbers, prices, weather, sports scores, send out announcements, give daily riddles and a lot of other cool things. Anyone know of any projects currently in the making (All I can find is Windows)?

---

### Post by MattBD on 2010-12-16
Does it specifically have to be on AIM? If Jabber (an open IM protocol which is used by Google Talk, amongst other services) is an acceptable alternative, you might want to check out the Net::Jabber module in Perl, which looks pretty easy to get working.

I have personal experience of using the Net::IRC module (also in Perl) to create an IRC bot, which is pretty easy. Check out [this tutorial]("http://wholok.com/irc/") if you want further details.

---

### Post by donkyhotay on 2010-12-16
The joy of FOSS, uou can just code your own bot! I'm kidding BTW, sorry I don't know of any pre-coded bots myself.

---

### Post by ki4jgt on 2010-12-16
It either has to be AIM or MSN. My messenger Zipit Z2 does AIM, MSN, and Yahoo, but it's not letting me sign into any Yahoo accounts for some reason.

---

### Post by MattBD on 2010-12-16
> **ki4jgt said:**
> It either has to be AIM or MSN. My messenger Zipit Z2 does AIM, MSN, and Yahoo, but it's not letting me sign into any Yahoo accounts for some reason.

Ok, there is apparently a Perl module called Net::AIM that can be used to create a bot, but what I read suggested it may no longer work. Still, it sounds like it's worth investigating.

---

### Post by MattBD on 2010-12-20
OK, after having done some digging I would suggest two options:

One is madcow, a Python bot that's designed for IRC but apparently also supports AIM. Its website is [here]("https://code.google.com/p/madcow/"). Looks like it might be exactly the kind of thing you're after.

Another I stumbled across is [JAIMBot]("http://jaimbot.sourceforge.net/"), which is written in Java so it might work OK on Ubuntu.

If these aren't what you're after, then the only alternative would be to code one yourself. As I mentioned earlier, there is a Perl module called Net::AIM, but it looks like it's been largely replaced by a module called Net::OSCAR (apparently Oscar is the name of the protocol used by both AIM and ICQ).

I think the main reason there aren't too many pre-written bots around might well be that it's actually a pretty trivial task in most scripting languages like Perl or Python. I wrote an IRC bot recently in Perl and it's only a little over 100 lines of code, and that's with quite generous use of whitespace and comments - probably less than 50 lines of actual code.

---

### Post by ki4jgt on 2010-12-20
Thanks very much :-)

---


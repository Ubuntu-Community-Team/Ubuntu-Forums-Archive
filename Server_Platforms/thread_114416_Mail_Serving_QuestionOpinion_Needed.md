---
title: "Mail Serving Question/Opinion Needed"
date: 2006-01-08
forum: Server Platforms
---

### Post by rickyjones on 2006-01-08
Hey everyone, I just have a quick question/scenario that I would like to get some opinions on.

With my new laptop I've decided to take the plunge into an open source environment. I've solved a ton of other issues, but I can't seem to come up with a viable solution for my email.

Currently I have two years of email located in Microsoft Outlook 2003. That is on my desktop computer located in my house. Not that huge of a deal, however I want to have all my email available to me 24/7, no matter my location. This means having it on my notebook under Linux, having it available via Webmail, and being able to access it via a terminal if necessary.

I would like my main server to take care of this for me: I would like to use fetchmail to grab the email from all of my various email accounts, dropping it into Postfix. I would then use Courier IMAP to access it via IMAP and Webmail (Squirrelmail?) Now, that should cover the receiving end. Issues arise when sending, would this be supportive of a configuration where when I send email, postfix will "see" which account it's coming from and forward the message to the correct sending server (like the comcast server) along with my login information to actually make the connection? Is that possible?

Has anyone ever tried a configuration as elaborate as this, and did it work?

Any opinions would be greatly appreciated.

Thanks!

-Richard

---

### Post by Soleil-Raid on 2006-01-09
[QUOTE=rickyjones]
I would like my main server to take care of this for me: I would like to use fetchmail to grab the email from all of my various email accounts, dropping it into Postfix. I would then use Courier IMAP to access it via IMAP and Webmail (Squirrelmail?) Now, that should cover the receiving end. Issues arise when sending, would this be supportive of a configuration where when I send email, postfix will "see" which account it's coming from and forward the message to the correct sending server (like the comcast server) along with my login information to actually make the connection? Is that possible?

Has anyone ever tried a configuration as elaborate as this, and did it work?
[/QUOTE]

Yes. Works fine. :)

On my own server, I replaced squirrelmail with roundcube (Ajax based webmail application) after a few years of solid use. Turned out some of my users liked squirrellmail, so I run them both in parrellel. Works perfectly, same backend. Users can flick back and forth depending on what they prefer.

The trickiest bits will be getting postfix to use Courier's maildir instead of mbox - although this is very well documented - and getting postfix to do SMTP AUTH so you can use it from anywhere - although if you're only doing webmail, you don't need to worry about this, since you can simply set it to trust localhost. Again, I'm pretty sure this will be well documented. (I use exim - mainly because that's what I know, and postfix doesn't offer me any advantage in switching over - but I for what your doing, it's much of a muchness either way, except that the Ubuntu I think ships postfix by default).

---

### Post by rickyjones on 2006-01-09
Thanks! I'm currently following the how-to at:[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

Hopefully it works. :)

-Richard

---


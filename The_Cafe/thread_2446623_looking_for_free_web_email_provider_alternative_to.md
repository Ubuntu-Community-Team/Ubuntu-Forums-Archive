---
title: "looking for free web email provider alternative to gmail"
date: 2020-07-03
forum: The Cafe
---

### Post by Skaperen on 2020-07-03
gmail allows its users to append "+" plus any string of valid characters in email addresses they give out to those that will send email to them, for whatever reason, such as making it easy to identify a folder to deposit incoming email into.  i already do this in my gmail account.

i am looking for another email provider that does the same thing but uses the "-" character instead.  the reason for this is a number of web sites that disallow the "+" character in signup email addresses.  in one case i asked about this and even got a reply from their system administrator who acknowledged that although it was valid in email addresses, it was considered a "security risk" in an old stack exchange thread.

---

### Post by uninvolved on 2020-07-03
My solution:

Get a domain name - they're cheap and there are some free choices out there. Get some free hosting. Put up some silly home page so that it's 'active' and then just use it for mail.

Set up a 'catch-all' email address and then you can just make up email addresses as you go. So, you could have [email]foo1@domain.tld[/email] [email]foo2@domain.tld[/email] [email]foo3@domain.tld[/email] - and they all actually go to [email]catch-all@domain.tld[/email]. You can filter it by inbound email address, you can also set up specific email addresses and those do not go to the catch-all address.

There's ample adequate free hosting for something this trivial. So long as you're not sending out bulk emails, you'll fly under their radar.

It's trivial to set up, even if  you've never done it before. You have control of the emails. You can encrypt your emails if you want, whatever.

---

### Post by Skaperen on 2020-07-03
i want to access the email via a web interface, specifically with firefox.

---

### Post by SeijiSensei on 2020-07-04
The "+" character has a well-defined meaning in mail protocols. The "-" does not.  Since the hyphen is a valid character in domain names, it's unlikely to be offered as an option for IMAP addresses.

---

### Post by uninvolved on 2020-07-04
Your webhosting will come with Squirrel or RoundCube webmail, usually. Those are passable interfaces for webmail. They're straightforward, with sensible layouts and no real learning curve. You'll have it figured out in like five minutes.

---

### Post by Skaperen on 2020-07-04
i still want to not depend on any hosting for email.  that's why i'm using gmail now.

sorry, i wasn't clear about appending the "+" character.  it is to be appended to the username part of the email address, the LHS, before the @.  it has no effect on the domain name at all, whether "+" is used or "-" is used.  in theory, a mail server could be implemented (or hacked) to work with either.  so an email address could look like "skaperen+ubuntu@example.net" or "skaperen-ubuntu@example.net".  it is the latter form i want to use.

---

### Post by Skaperen on 2020-07-04
an alternative would be a free email provider that lets me use my own domain name and anything i want in the LHS (before the @).

---

### Post by mastablasta on 2020-07-05
well you could always set up your own email server. then you can set it up as you like.

---

### Post by Skaperen on 2020-07-06
> **mastablasta said:**
> well you could always set up your own email server. then you can set it up as you like.

yes i can.  but i don't want to deal with that.  i did it as a career.  i am retired, now.  i want to minimize what i am doing.

---

### Post by gairciand on 2020-07-07
You can try Zoho, bluehost.com, or hostgator
I haven't used any of them, to be honest, but they seem to be legitimate options

---

### Post by T6&amp;sfpER35% on 2020-07-07
im using [bluemail](https://www.bluemail.me) atm ,it's nice with no problems

---

### Post by uninvolved on 2020-07-07
If you don't mind the Russians, Yandex has free email hosting for your own domain. It's quite robust and IIRC it's "unlimited" in many ways - like account numbers and disk space.

---

### Post by Chanath on 2020-07-08
Vivaldi has its own free web mail. [https://help.vivaldi.com/article/vivaldi-net-and-its-webmail/](https://help.vivaldi.com/article/vivaldi-net-and-its-webmail/)

---

### Post by Skaperen on 2020-07-08
> **3nd said:**
> im using [bluemail]("https://www.bluemail.me") atm ,it's nice with no problems

can bluemail be used via firefox as a web app or do they require you download a binary?

---

### Post by Skaperen on 2020-07-08
> **Chanath said:**
> Vivaldi has its own free web mail. [https://help.vivaldi.com/article/vivaldi-net-and-its-webmail/](https://help.vivaldi.com/article/vivaldi-net-and-its-webmail/)

will it work in firefox or do they require using their own browser?  can i build their browser from source code anyone can freely download?

---

### Post by Chanath on 2020-07-11
> **Skaperen said:**
> will it work in firefox or do they require using their own browser?  can i build their browser from source code anyone can freely download?

Best to check this at [https://forum.vivaldi.net](https://forum.vivaldi.net)

---

### Post by tomanes on 2021-04-19
I have tried most of the alternatives, but I think your best option here is to get a virtual email address specially if you are the owner of a company.

---

### Post by CharlesA on 2021-04-19
This is an old thread, so I'm closing it.

---


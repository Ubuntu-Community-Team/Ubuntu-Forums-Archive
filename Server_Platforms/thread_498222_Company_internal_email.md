---
title: "Company internal email"
date: 2007-07-11
forum: Server Platforms
---

### Post by jeff on 2007-07-11
I have a bit of an odd one.

I want to set up a email server but does anyone know if it is possible to do the following things?

[LIST]
[*]Only allow certain domains for incoming and out going emails? (I'm sure this one is easy)
[*]Limit users to email only a select few email addresses? But not all users are the same, and have individual limits. It would help if I could group permissions.
[/LIST]

Please tell me what you think
Thanks for your time

---

### Post by kidders on 2007-07-13
Hi there,

The mail server I'm used to dealing with is Postfix, so I hope you don't mind if I write my post in those terms.

Having said that, I imagine every mail server ever written will let you limit what mail domains can be specified in incoming emails ... after all, allowing mails from Yahoo addresses, destined of Gmail addresses (for example) to pass through your mail server would be a major problem.

For outgoing mails, Postfix will let you control what domains you want to let people deliver *to* very easily. You could, for instance, arrange things so that any local attempt to queue a mail to Gmail for delivery would simply fail.

Your second bullet point is more complicated though. Although there may well be a Postfix plugin available already that does exactly what you describe (that I simply don't know about), my first instinct would be something like this...

Postfix will let you pass mail through a script as part of the delivery process. Although the mechanics of what to do vary depending on the ballpark your mail delivery volume is in, the general idea would be something like:
[LIST]
[*]Create a script in any language that you like, eg PHP, a shell script, Python, etc.
[*]For extensibility purposes, you might like have your script talk to some pre-existing service that has some knowledge of what users are allowed to do ... eg an LDAP server or MySQL database.
[*]Your script can use that knowledge to accept or reject emails.
[*]In the future, you could simply alter the information source (rather than the filter script itself) to manipulate what your users are permitted to do with your mail server.[/LIST]The point, I suppose, is that if you use a nice, flexible mail server (eg Postfix), you will find that many of the features you'd like will be built into it already ... and even if they're not, there's almost always a neat way of plugging in the extra functionality.

If you'd like me to try my hand at a less ... well ... vague response to your post, the following information would be useful:
[LIST=1]
[*]Approximately how much mail you intend to process (eg what factor of 10 per hour). 100s? 100,000s?
[*]Roughly how "tailored" you'd like individual users' restrictions to be. For instance, the worst case scenario might be that you would need the ability to explicitly list the individual email addresses a user (or group of users) is entitled to send to.
[*]What kind of authentication/access control services are operating on your network already. It would be ideal if you could use one of them to control the behaviour of your mail server, rather than having to invent something new.[/LIST]

---

### Post by koenn on 2007-07-13
Adding to what kidders said:

1/ controlling/filtering  the sender mail domain is a standard feature on any mail server, for the reasons stated. 

2/ It's probably possible to control outgoing mails by means of whitelists / blacklists, and it's likely there are ways to link withelists/blacklists to users/groups known to the mail server. We use something like that at work. The white/blacklists support wildcards so you can block/allow anything from a specific adres to a part of a domain name. 
Unfortunately, the setup I'm referringh to is hidden behind a web interface and I don't have sufficient access to the underlying system so I can't be more specific as to how it works.

---

### Post by Mr. C. on 2007-07-13
Take a look at policyd:

[http://www.policyd.org/features.html](http://www.policyd.org/features.html)

MrC

---


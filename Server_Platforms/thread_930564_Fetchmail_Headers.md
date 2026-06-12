---
title: "Fetchmail Headers"
date: 2008-09-26
forum: Server Platforms
---

### Post by FiniteRed on 2008-09-26
Hi Everyone

I am using Fetchmail to retrieve e-mails from my ISP and "inject" them into a postmaster account on my e-mail server. The problem i am haveing is that fetchmail does not seem to preserve the headers of the e-mails that are fetched, instead re-writing them to the postmaster. The end result is that all of the mail ends up sitting in the post master account going no where.

Is there an argument that can be passed to fetchmail that will cause it to retrieve from the headers of the message the recipients and inject the message correctly?

This is my fetchmail call:

```
poll mail.MYISP.net with proto pop3
user USER_NAME there with password MY_PASSWORD is postmaster here
```

Many thanks for any advice you can give :)

FR

---

### Post by SeanHodges on 2008-09-26
Perhaps remove the "is postmaster" parameter?

I use the following (ignore the SSL commands for gmail which you probably won't need), my email headers are preserved as they were on the server:

```
poll pop.gmail.com
  with nodns,
  with protocol POP3
  user "myaddress@gmail.com"
  with password mypass,
  with ssl, sslcertck,
  to 'myaddress@gmail.com'='myaddress'
```

---

### Post by FiniteRed on 2008-09-26
My apologies if im being thick, but how will fetchmail know which account to deposit the e-mail into if I do not specify the postmaster? In fact where would it place the gathered e-mails without the postmaster attribute?

Many thanks :)

FR

---

### Post by SeanHodges on 2008-09-26
Well I haven't tested this, but I'd imagine you could modify the "to" attribute:

poll mail.MYISP.net
  with protocol POP3
  user USER_NAME
  with password MY_PASSWORD,
  to 'USER_NAME@MYISP.net'='postmaster'


I'm by no means an expert at fetchmail, but it's worth a try...

---

### Post by FiniteRed on 2008-09-26
Hi

Sadly I have multiple user addresses coming from my ISP that fetchmail picks up:

[email]Bob@address.com[/email]
[email]Tom@address.com[/email]
[email]sam@address.com[/email]

If I used to 'USER_NAME@MYISP.net'='postmaster' would this not direct all e-mails (regardless of address) to [email]USER_NAME@MYISP.net[/email]?

FR

(Sorry to be a pain...)

---

### Post by SeanHodges on 2008-09-26
No problem, assuming my example works for a single account, you should be able to fetch from other accounts as well:

poll mail.MYISP.net
with protocol POP3
user USER_NAME
with password MY_PASSWORD,
to 'Bob@address.com'='postmaster'
to 'Tom@address.com'='postmaster'
to 'sam@address.com'='postmaster'


There may even be some kind of wild-card matching as well, but I don't know about that.

Note this method is fetching FROM "mail.MYISP.net", and placing into the email server's "postmaster" account, not the other way around. I presume this is the functionality you are looking for...

---

### Post by FiniteRed on 2008-09-26
ok, I have tried that and fetchmail complains about multidrop and that envelopes have not been used.

It seems to work with a single e-email address in there, but multiple it complains.

Any ideas :)

FR

---

### Post by SeanHodges on 2008-09-26
Strange this is causing it not to work, I get the envelope warnings as well but fetchmail should still work and fall back on the address header for getting this information. Considering you might be getting emails from any source (the emails I fetch are always from the same server), it may be better for you to use envelope address resolution.

Try adding this to the configuration:

```
envelope Delivered-To
```

This should use the envelope header in the message for multidrop resolution. The actual header to use depends on your email server, "Delivered-To" is the most common, but apparently Postfix uses the alternative "X-Original-To".

The fetchmail man page explains it as this:

> As a better alternative, some SMTP listeners and/or mail servers insert a header in each message containing a copy of the envelope addresses.  This header (when it exists) is often ’X-Original-To’,  ’Delivered-To’  or ’X-Envelope-To’.  Fetchmail’s assumption about this can be changed with the -E or ’envelope’ option.  Note that writing an envelope header of this kind exposes the names of recipients (including blind-copy recipients) to all receivers of the messages, so the upstream must store one copy of the message per recipient  to  avoid  becoming  a  privacy problem.

To be honest I'm getting a little out of my depth here, but I'd be interested to hear how you eventually get it to work. Give the above a try, then maybe ask on the fetchmail users mailing list if you're still stuck: [http://lists.berlios.de/mailman/listinfo/fetchmail-users](http://lists.berlios.de/mailman/listinfo/fetchmail-users)

---


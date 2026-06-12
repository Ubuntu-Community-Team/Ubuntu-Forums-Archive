---
title: "Default Postfix installation - how good is it?"
date: 2012-02-22
forum: Server Platforms
---

### Post by richardgundersen on 2012-02-22
Hi

I recently set up an Ubuntu 10 server for a site I'm working on. I've got Postfix files all over the place, so even though I can't remember installing it, I think I must have selected an option at installation time to set it up (?!).

That's great though, and I can even see in a config file (I forget exactly which file) that my mailname is [email]admin@my-domain.com[/email].

Sooo, I think I already have an SMTP server running, which is brilliant.

But, I'm a total novice in this area so I had a couple of questions about my installation - if anyone could kindly answer them I'd be really grateful. Here they are :)

1) Assuming I've got an out-of-the-box installation already, how secure is it? Can I just leave it running and not worry about it, or should I be learning every aspect of postfix/smtp? Or is it installed with reasonably secure defaults as it is?

2) My app only needs to send emails, not receive them. Assuming I've already got this 'admin' user, is there a default password that I need to know about (my app will need this to send emails I think)? 

I won't get chance to work on my app for a couple of days yet, but wanted to ask these in advance. 

Thanks!

---

### Post by CharlesA on 2012-02-22
I set Postfix to listen on localhost only. Once you have it configured, it should send mail fine without needing a user or password.

I've been using mine as a gmail relay and it works fine so far.

---

### Post by SeijiSensei on 2012-02-22
> **CharlesA said:**
> I set Postfix to listen on localhost only.

I believe that's the default configuration in Ubuntu.

---

### Post by CharlesA on 2012-02-22
> **SeijiSensei said:**
> I believe that's the default configuration in Ubuntu.
Could be. I forgot to check after I installed, but there was an entry in main.cf that mentioned all int interfaces or some such thing. Could be that it was just set up to listen on lo though.

---

### Post by richardgundersen on 2012-02-22
Thanks for the tips guys. Sounds like what I've got by default is fine for what I need then. Plus, port 25 (incoming) is closed, which I'm sure is important. I tested it earlier and it works fine for sending too (from the command line at least).

Thanks again

---


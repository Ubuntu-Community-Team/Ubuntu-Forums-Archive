---
title: "Spam filter"
date: 2012-11-13
forum: Security
---

### Post by geminiscorpio on 2012-11-13
Hello!

Who can recommend me a good and open source or free spam filter?

Thanks

---

### Post by Bucky Ball on 2012-11-13
Depending on your email client, then is generally one built in. I use Thunderbird and that has one already.

---

### Post by geminiscorpio on 2012-11-14
My problem is that I want to filter spam before they reach the e-mail client.I don't want them in my mail queue.One of the good spam filters is Baracuda, but it is not free or open source.

---

### Post by Cheesemill on 2012-11-14
I use SpamAssassin.

---

### Post by Bucky Ball on 2012-11-14
> **geminiscorpio said:**
> My problem is that I want to filter spam before they reach the e-mail client.I don't want them in my mail queue.One of the good spam filters is Baracuda, but it is not free or open source.

In Thunderbird you can set to 'Delete from Server' _*AND*_ 'Delete Mail' so basically it never gets as far as you anyhow ...

---

### Post by geminiscorpio on 2012-11-14
Thank you for all your replies.Already tested SpamAssassin.It's good but I'm looking for better.Any other choices?

---

### Post by SeijiSensei on 2012-11-14
It's just good?  There isn't much out there that is better than SpamAssassin.  You might need to write some of your own rules to handle specific cases, but there isn't anything better than SA as a general anti-spam tool.  Last I looked Barracuda uses SA with proprietary rules.  

I have been scanning mail for years using [MailScanner]("http://www.mailscanner.info/") with ClamAV and SpamAssassin.  I probably catch 95% of the spam arriving at my server.

---

### Post by Cheesemill on 2012-11-14
SpamAssassin is only as good as the rules that you set up for it. A default installation will be good but you can get it much better by tweaking the rules and configuration.

---

### Post by Grenage on 2012-11-14
I'm not aware of any free anti-spam systems that come close to Barracuda in terms of catch-rate (with low/no maintenance).

---


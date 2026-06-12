---
title: "[SOLVED] Gmail forwards spam messages"
date: 2023-03-21
forum: The Cafe
---

### Post by Rooster2000 on 2023-03-21
I have an old Gmail account which has automated forwarding to my other non-Gmail account. Recently I have noticed that Gmail has started to forward messages that it places to Spam -folder. I thought forwarding should happen only for messages that stay on Inbox, but not for spam. Has this changed recently? Where I have set forwarding on in Gmail is

```
Settings > Forwarding and POP/IMAP > Forwarding: (X) Forward a copy of incoming mail to [x@y] and [Keep Gmail's copy in the Inbox]
```

There are no filters that would do any forwarding.

---

### Post by DuckHook on 2023-03-21
I nuked my gmail account some time ago so no longer have a test bed, but I would highly suspect any forwarding feature that withheld any piece of mail. False positives are a real problem, so I wouldn't trust an algorithm to deprive me of a possibly very important piece of email. I imagine that this same consideration is why Google forwards everything.

In my opinion, this is proper behaviour. You should rely on your new e-mail provider to filter for spam. That way, everything remains within your control rather than some bot's no matter how sophisticated its algorithms.

---

### Post by Rooster2000 on 2023-03-22
Maybe so, in any case I think it has been changed to current behavior recently, and was working differently before.

I wonder if there would be a way to make forwarding from Gmail by filters in a way that it would not send any messages categorized as spam forward. In my understanding, Gmail executes filters first and spam detection would come after that. If this is the case then it is not possible.

---

### Post by SeijiSensei on 2023-03-22
You could read your GMail account from Mozilla Thunderbird and apply filters locally.

---

### Post by Rooster2000 on 2023-03-23
> **SeijiSensei said:**
> You could read your GMail account from Mozilla Thunderbird and apply filters locally.

This could be one option, as I am using Thunderbird already for my primary email account. Thanks for suggestion.

---

### Post by DuckHook on 2023-03-23
Another option (and the one I was implying) is to use the spam filter in the service provider to which the gmail is being forwarded. This would seem the logical solution to me as it would take care of spam across all devices yet stil allow you to see and maintain the spam folder.

---

### Post by Rooster2000 on 2023-03-24
> **DuckHook said:**
> Another option (and the one I was implying) is to use the spam filter in the service provider to which the gmail is being forwarded. This would seem the logical solution to me as it would take care of spam across all devices yet stil allow you to see and maintain the spam folder.

Yes, that is a good option also. The reason I have  preferred Gmail's own spam filtering in the past is that in my  experience it seemed to be better than the one of my email provider (SpamAssassin, Rspamd).

---

### Post by Rooster2000 on 2023-04-03
Well, now it seems Gmail has returned into it's old habit of **not** forwarding any emails that are categorized as spam. Maybe this was only temporary error or trial.

---


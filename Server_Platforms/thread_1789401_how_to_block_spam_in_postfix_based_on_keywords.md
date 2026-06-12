---
title: "how to block spam in postfix based on keywords"
date: 2011-06-23
forum: Server Platforms
---

### Post by envis on 2011-06-23
i keep receiving this damn annoying spam:

> No Cost Website Analysis and Ranking Report
Rank mysite.com at the top of the 3 major search engines

Do you want to know why your competitors are showing up at the top of the three major search engines
and how you can rank on top? To increase the number of visitors to your website it is crucial that you have a top search engine position.
If you are like most people, you will spend countless hours trying to get traffic to your website.

Our search engine optimization experts will run a detailed website ranking and analysis report showing you exactly where mysite.com
currently stands in all the major search engines along with the recommendations of how we can increase your ranking on
Google, Yahoo and Bing.

For Your No Cost Analysis Report and More Info  Please Click Here

 

All the Best,
The Spotlights - SEO   Team

____________________________________________________

To be removed from further offers please click here

5201 Great America Pkwy.
Santa Clara, California 95054 


i get about 30 of those a day, everyday, for a long time. ive asked the ISP to stop it (theplanet.com) they are not responding and the spam continues.


i was thinking is there a way that i can tell postfix to reject emails that contain "No Cost Website Analysis and Ranking Report" in their subject? there must be a way but i dont know how.

---

### Post by rudelgurke on 2011-06-24
Well - without external modules or software, Postfix won't do it because that's the content of the mail.
If it's the same IP originating the spam, block this IP. If not, maybe an additional spam filtering module (bogofilter, spamassassin) will do the job or even procmail. :)

And yes - I agree about theplanet - their abuse service or better their non-existing abuse service is a huge shame.

---

### Post by SeijiSensei on 2011-06-24
If you are using procmail as the delivery agent, then you could put this in your $HOME/.procmailrc:

```

:0 B
* No Cost Website Analysis and Ranking Report
/dev/null

```

This checks the body for the "No Cost..." string and delivers the message to /dev/null instead of your inbox.

To see if procmail is active, check /etc/postfix/main.cf and make sure it has the line:

```
mailbox_command = procmail -a "$EXTENSION"
```

---

### Post by envis on 2011-06-24
> **rudelgurke said:**
> Well - without external modules or software, Postfix won't do it because that's the content of the mail.
If it's the same IP originating the spam, block this IP. If not, maybe an additional spam filtering module (bogofilter, spamassassin) will do the job or even procmail. :)

And yes - I agree about theplanet - their abuse service or better their non-existing abuse service is a huge shame.

can you block an ip at the postfix level? how would i do that? i have crawlers that curl wget and fopen stuff online, i wouldnt want to interfere with those (wouldnt want to prevent them to fetch certain ips for their purposes).

any recommendations on what external modules could allow me to block messages based on keywords found in message or subject that isnt too complicated?

---

### Post by envis on 2011-06-24
> **SeijiSensei said:**
> If you are using procmail as the delivery agent, then you could put this in your $HOME/.procmailrc:

```

:0 B
* No Cost Website Analysis and Ranking Report
/dev/null

```

This checks the body for the "No Cost..." string and delivers the message to /dev/null instead of your inbox.

To see if procmail is active, check /etc/postfix/main.cf and make sure it has the line:

```
mailbox_command = procmail -a "$EXTENSION"
```

for the moment i have ```
mailbox_command =
``` yet i toughed i had mbox, or am i confusing somethings.

i guess ill try to install that procmail [https://wiki.ubuntu.com/Procmail](https://wiki.ubuntu.com/Procmail)

---


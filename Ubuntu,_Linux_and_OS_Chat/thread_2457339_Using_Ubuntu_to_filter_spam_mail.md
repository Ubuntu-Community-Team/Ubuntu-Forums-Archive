---
title: "Using Ubuntu to filter spam mail"
date: 2021-01-31
forum: Ubuntu, Linux and OS Chat
---

### Post by petrolhead2 on 2021-01-31
Hi

New Ubunu user hear so be kind :)

I am not sure if this is possible.

I want ubuntu to filter my email forore I get it in my Windows 10 Outlook inbox.

Is this possible and if so what software do I need

Thanks

---

### Post by grahammechanical on 2021-01-31
I have not studied this subject, but I think that I am right. If you want to filter emails before they are downloaded to the operating system and the email client on the operating system then you would have to do it at your email account with your Internet Service Provider (ISP).

The default email client in Ubuntu is Thunderbird Mail. Whatever settings you set in Thunderbird Mail will not affect the default email client in Windows, which is Outlook. The same thing applies the other way around.

> No one likes spam or junk email. The Outlook Junk Email Filter doesn’t  stop delivery of junk email messages, but does the next best thing—it  moves suspected spam to the **Junk Email folder.**

> By default, the Junk Email Filter is turned on and the protection level is set to **No Automatic Filtering. You can make the filter more aggressive by [changing the level of protection]("https://support.microsoft.com/en-us/office/change-the-level-of-protection-in-the-junk-email-filter-e89c12d8-9d61-4320-8c57-d982c8d52f6b") that  it provides. The Junk Email Filter evaluates each incoming message  based on several factors. These can include the time when the message  was sent and the content of the message.**

[https://support.microsoft.com/en-us/office/overview-of-the-junk-email-filter-5ae3ea8e-cf41-4fa0-b02a-3b96e21de089](https://support.microsoft.com/en-us/office/overview-of-the-junk-email-filter-5ae3ea8e-cf41-4fa0-b02a-3b96e21de089)

I do believe a similar practice is followed by Thunderbird Mail.

[https://support.mozilla.org/en-US/kb/thunderbird-and-junk-spam-messages](https://support.mozilla.org/en-US/kb/thunderbird-and-junk-spam-messages)

If you do not want emails downloaded on to the computer, then, maybe, use Web Mail and delete the emails that you do not want on your machine and set your ISP account to filter emails. I would not be surprised if Web Mail also moves junk emails into a separate folder so that the user can decided if junk mail is really junk.

Regards

---

### Post by T6&amp;sfpER35% on 2021-01-31
I'm not a pro ,but just off the top of my head i would think no operating system handles / filters emails. 
That's what a email client is there for. I would think even if your email account is at your ISP, stuff would still get filtered and land in spam. No service is going to decide to delete emails they think you won't want.
So the answer to your question ,in my opinion , is a short *no.*

---

### Post by TheFu on 2021-01-31
For someone new to Linux, email filtering isn't really accessible. There aren't any point-n-click solutions and if you want the email to actually be seen by another machine as the client, then you are in the realm of running an email server of some sort.  That's non-trivial the last 15 yrs, since spam has become the scourge of the internet.

Possible? Yes.
But probably not something you really want to attempt until after you are a good Linux Server admin first.
The tools I use for this are postfix, anvil, postscreen, ipset, iptables, and procmail.

---

### Post by CelticWarrior on 2021-01-31
> **TheFu said:**
> The tools I use for this are postfix, anvil, postscreen, ipset, iptables, and procmail.
It must be stressed this is only applicable to the very unlikely situation of you,@petrolhead2, *running an email server of some sort.*

I suspect you're asking about third-party service like GMail, aren't you? If so I suggest you google IMAP vs. POP3 to start understanding the differences and then, knowing that IMAP is what's used today, adjust your expectations.

---

### Post by SeijiSensei on 2021-02-01
How does the mail arrive in Outlook? Are you accessing a remote server?

To do what you want requires setting up the Ubuntu box as a mail server with spam controls, then having your mail go first to the Ubuntu box. You'd then point Outlook at the Ubuntu box to read your mail.

This is not a project for a new user of Linux. I suggest instead that you look into any anti-spam controls in the software you use to read mail. Mozilla Thunderbird, for instance, has built-in anti-spam controls. Most mail clients also do filtering, so if there are identifiable features in the spam you receive, you can use a filter to send such messages to Trash.

---


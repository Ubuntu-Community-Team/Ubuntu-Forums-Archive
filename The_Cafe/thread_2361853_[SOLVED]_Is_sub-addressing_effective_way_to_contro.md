---
title: "[SOLVED] Is sub-addressing effective way to control spam?"
date: 2017-05-21
forum: The Cafe
---

### Post by Rooster2000 on 2017-05-21
There are many spam-preventing instructions online which guide one to use disposable email addresses for signing to services one doesn't trust. The other option often mentioned is using [sub-addressing]("https://en.wikipedia.org/wiki/Email_address#Sub-addressing") (also known as plus addressing or tagged addressing) if your [email provider]("https://en.wikipedia.org/wiki/Comparison_of_webmail_providers#Features") only supports it. For example address joeuser@example.com could be tagged as joeuser+tag@example.com. This would help - depending on usage - both to identify the source of spam and handle it more effectively with filters.

The costs and benefits of sub-addressing depends on how specifically one is using it. One way would be to categorize tags based on service groups, like[INDENT]joeuser+forums@example.com
joeuser+newsletters@example.com
joeuser+some@example.com
[/INDENT]
 
Better, although more effortful way would be to individualize for each site, so the leakage of the email address can be more precisely known and incoming spam more effectively filtered[INDENT]
joeuser+forum001@example.com
joeuser+forum002@example.com

joeuser+newsletter001@example.com
joeuser+newsletter002@example.com

joeuser+some001@example.com
joeuser+some002@example.com
[/INDENT]
 
This might require maintaining some sheet about which tag is used on which site, especially as many sites use email as login name. Other incoveniences might include sites not accepting '+' at email address or stripping it away silently, or spammers - or anyone who provides emails for them - stripping the tags away.

Is anyone using this kind of sub-addressing in some form? What are your experiences of it, is it worth the costs? Have you received some spam to your non-sub-addressed email anyway?

---

### Post by Rooster2000 on 2017-08-10
Bump.

---

### Post by Rooster2000 on 2017-10-11
Looks like no one has tried it in this sophisticated way. Got to do it myself then.

---

### Post by SeijiSensei on 2017-10-11
Since I own my domain, I created a subdomain which I use when I sign up for sites online.  Suppose I own "example.com".   I would add an MX record to my DNS zone file that points to the subdomain, call it "signup.example.com."  Then if I signed up with Amazon, I could register [email]amazon@signup.example.com[/email].  I point all the mail for that subdomain to my personal account.  If I get spam from one of them, I'll know right away which sender has problems.

I've used this method for years.  My favorite example comes from when my daughter attended Emagination Computer Camps one summer.  I created an [email]emagination@signup.example.com[/email] at the time.  About a year later I started getting spams at that address.  After laughing that an organization which runs computer camps couldn't protect its own email list, I stopped accepting mail sent to that address.  I now block about two dozen such addresses either because they became spam sources or because they kept barraging me with solicitations.

---

### Post by Rooster2000 on 2017-10-15
So this method you use is basically similar to second alternative I presented in my first post; using individual address for each site.

But it seems better for two reasons. Firstly, your real email address cannot be concluded from those addresses by stripping away the tag part. Secondly, they don't have any special characters - namely '+' sign - which is not allowed in email addresses for all sites. Naturally, as you said, it requires that you own your domain - or at least have one subdomain to use.

Glad to hear it has worked.

---


---
title: "Postix w/ Multiple Domains MyOrigan MyHostName and MyConfusion..."
date: 2023-08-22
forum: Server Platforms
---

### Post by glued-2-keyboard on 2023-08-22
Hello.

While trying to setup SPF so that mail can be sent to GMAIL accounts I notice what might be some other issue(s).

The bounced automated email from Google GMAIL shows that MY [COLOR=#000000][FONT=Helvetica]Reporting-MTA: dns;[/FONT][/COLOR][COLOR=#000000][FONT=Helvetica] as[/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]  hostname.domainname.com [/FONT][/COLOR] and not mail.virtualdomain-two.com or mail.virtualdomain-three.com

When sending to non-GMAIL accounts I noticed that mail that I am sending from [EMAIL="johndoe@virtualdomain-two.com"]johndoe@virtualdomain-two.com[/EMAIL] or [EMAIL="janedoe@virtualdomain-three.com"]janedoe@virtualdomain-three.com[/EMAIL] is being seen as being sent from (MyOrigan.MyHostName) aka my mailname and hostname even though the FROM address is correctly showing [EMAIL="johndoe@virtualdomain-two.com"]johndoe@virtualdomain-two.com[/EMAIL] or [EMAIL="janedoe@virtualdomain-three.com"]janedoe@virtualdomain-three.com[/EMAIL] 

How do I correctly setup POSTFIX so that the mail is seen as being sent from the corresponding VIRTUAL DOMAIN and not the HOST machine? 

Not even sure I am asking to correct question.

---

### Post by SeijiSensei on 2023-08-23
Usually I handle all of this in my mail client, Thunderbird. I create multiple "identities" with multiple domains and select the appropriate From: address in the mail client during composition. Whether that solves your problem or not is more complicated. I assume you have SPF set up for all your domains. DKIM also helps. ([http://opendkim.org/](http://opendkim.org/))

Each domain should have an SPF record that points to the external IP address of the sending server as a legitimate sending host.

---


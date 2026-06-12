---
title: "how to redirect an email account in sendmail?"
date: 2009-03-12
forum: Server Platforms
---

### Post by machinakias on 2009-03-12
hi all! need some help with sendmail please...

here it is:
there is a user that left and he has a mail accound (example) [email]user@company.com[/email].

what i need is to receive his emails to my own email in gmail (or elsewhere...yahoo,zimbra or what...)

is there any way to do it?

thank you very much! ;)

---

### Post by machinakias on 2009-03-12
> **Exilim said:**
> There is a tutorial on how to setup redirects in sendmail over here: [http://support.real-time.com/linux/email/server/aliases.html](http://support.real-time.com/linux/email/server/aliases.html)

THANKS DUDE! i'll give it a try....;)

well,it didnt help much....just saw an advert of a company....

anyone else please?

---

### Post by darksideforge on 2009-03-12
Sendmail aliases should allow you to redirect user's emails wherever you want them to go (yahoo/hotmail/gmail) as long as you have POP3 and IMAP installed/activated.

---

### Post by machinakias on 2009-03-12
oh well....and how can i do it? can you please give me some more info?

you see,they set me up in this situation and i'm trying to make up things that i dont really know...

so please everyone,if you could give me some clear instructions....

thank you all for your help! you are really nice guys!:P

(sorry for my poor engish....)

---

### Post by darksideforge on 2009-03-14
You should consider downloading and using Webmin in my opinion. It's much easier to keep track of sendmail that way. Also, it's easier to track dependencies--if any--and resolve issues with Postfix.

Navigating sendmail via CLI is a ***** to say the least. However, find the sendmail directory and then find your aliases subdirectory. CD into your aliases subd and then enter vi or vim (or the command for your editor) to edit the aliases file.

Scroll down until you find this former user's username (ie: user  user@company  com.

Following user@company  com should be the localhost name or the domain name where user's mail is placed. Insert/Edit localhost or domain to reflect *your* email address at another domain, such as yahoo  com. (Remember to pay attention to spacing/space-bar-entries...sendmail uses two spaces of separation I believe).

Unfortunately, unless you're using Webmin to make these changes, I'm not sure whether or not your particular server will allow external routing to a new domain outside of your system's firewall. (In my server, I have to disable a block in order to get sendmail to redirect to an outside domain). If you change your alias file (and don't forget to save the changes prior to exiting!) and your firewall blocks your change, all of "user's" mail will end up in the catchall account.

---

### Post by machinakias on 2009-03-17
thanks again my friend...i didnt remember webmin at all!!!
i'll try it...thank you!

---


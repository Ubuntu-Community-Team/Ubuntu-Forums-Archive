---
title: "Postfix -&gt; One to many email account"
date: 2008-05-02
forum: Server Platforms
---

### Post by lotsofish on 2008-05-02
I have set up a web server which is going to be hosting a few domains on a VPS running Hardy and I set up Postfix (minus the AV so far) according to these directions: [https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

Now I can add email accounts for each of the domains and connect through pop to receive the mail just fine.

What I am going to need to do is set up a one to many email alias. For example:
[email]info@domain.com[/email] gets forwarded to [email]andrew@domain.com[/email], [email]bill@domain.com[/email], [email]charlie@otherdomain.com[/email]

I've tried various changes through /etc/aliases, /etc/postfix/virtual (adding virtual_alias_maps to main.cf) but I can't get it worked out.

Any help would be appreciated!

---

### Post by lotsofish on 2008-05-02
Got it... You have to create the user account first before you can set up the virtual aliases.

So, once I created [email]info@domain.com[/email] adding the following line to the virtual_alias_maps file forwarded the mail correctly.

[email]info@domain.com[/email] [email]andy@otherdomain.com,bob@thirddomain.com[/email]

---


---
title: "Postfix sending to aliases"
date: 2008-09-22
forum: Server Platforms
---

### Post by bp1509 on 2008-09-22
d

---

### Post by MJN on 2008-09-23
It could be because you are not specifying the domain as part of the RCPT TO: address.
 
To experiment further, try adding a domain to the address - ideally one which matches the domains that Postfix is the final destination for (i.e. one that appears in $mydestination).
 
Incidentally, why is t9.com not listed in $mydestination? Do you not accept mail for <someone>@t9.com? The default behaviour of Postfix, for locally submitted mail without a domain portion, is to append $myorigin to the address. In your case this is set to mailname and hence t9.com. However, Postfix does not think it is the final destination for t9.com thus is probably ignoring the alias maps altogether.
 
Mathew

---

### Post by bp1509 on 2008-09-23
d

---

### Post by MJN on 2008-09-23
If Postfix isn't the final destination for this mail then it won't be envoking any of the alias mappings.
 
Try testing as mentioned - sending to, say, [EMAIL="rancid-admin-cisco@localhost.t8.com"]rancid-admin-cisco@localhost.t8.com[/EMAIL] and see if the logged behaviour changes.
 
Mathew

---

### Post by MsTBWx2c on 2008-09-23
**[[color=red]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=red]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[size=3][color=red]Make money online,now![/color][/size]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---


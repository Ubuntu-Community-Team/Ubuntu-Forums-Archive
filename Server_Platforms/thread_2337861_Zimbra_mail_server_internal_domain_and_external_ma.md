---
title: "Zimbra mail server: internal domain and external mail"
date: 2016-09-22
forum: Server Platforms
---

### Post by france68 on 2016-09-22
[COLOR=#141414][FONT=&quot]Hello,[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]I installed Ubuntu 4.14 on a mail server Zimbra 8.7 properly configured to run between the PCs on Lan with an invalid domain on the internet, for example, [/FONT][/COLOR]*mydomain.local*[COLOR=#141414][FONT=&quot].[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]Now I would like, from my address internal [/FONT][/COLOR]*info@mydomain.local*[COLOR=#141414][FONT=&quot], able to send mail outside the local network.[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]Not being able to go out with [/FONT][/COLOR]*mydomain.local*[COLOR=#141414][FONT=&quot] because non-existent on the internet, I wish that, for e-mail and from the internal domain was automatically turned into, for example,[/FONT][/COLOR]*mydomain.com*[COLOR=#141414][FONT=&quot], properly registered on the internet.[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]In short, I would like, at the time the outside, my [/FONT][/COLOR]*info@mydomain.local*[COLOR=#141414][FONT=&quot] internal mail address was transformed into [/FONT][/COLOR]*info@mydomain.com*[COLOR=#141414][FONT=&quot] (domain box existing on the internet managed by ISP).[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]I think this is called [/FONT][/COLOR]**domain masquerading**[COLOR=#141414][FONT=&quot].[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]How you can do all this?[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]Thanks

[/FONT][/COLOR]

---

### Post by TheFu on 2016-09-22
I've been a zimbra admin for about 10 yrs.  Never attempted this.  I do host multiple domains on the same machine, but these are separate.  You can add a domain alias - have you tried that? Think you'd need to change the primary name to be mydomain.com, however. 

You can ask on the zimbra forums, but be very specific and correct with accurate data in the questions.

---


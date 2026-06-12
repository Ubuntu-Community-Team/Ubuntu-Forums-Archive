---
title: "Postifx mail receiving size limit"
date: 2010-04-10
forum: Server Platforms
---

### Post by t_ras on 2010-04-10
using kubuntu 9.04 on AMD 64,working with ISPconfig panel
I have postfix configured and have no problem getting mails with small attachments, but when they pass certain size I don't get them
Where can I configure this?  
thanks

---

### Post by dudumomo on 2010-04-10
Are you using a webmail in php ?
If yes, you have to modify the php.ini file and increase the size limit.

But if not, I don't think modifying the php conf file will helps...

---

### Post by lisati on 2010-04-10
If you've got webmin installed, the relevant page is servers->postfix->general resource control. There's an option, "max size of a message"

---

### Post by t_ras on 2010-04-10
It seems to work from other accounts, it seems the problem was in the source account.
sorry for waisting your time...

---


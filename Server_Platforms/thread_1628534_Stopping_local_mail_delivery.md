---
title: "Stopping local mail delivery"
date: 2010-11-22
forum: Server Platforms
---

### Post by dwessell on 2010-11-22
Hi,

I installed ispcp on top of Ubuntu server.. And than installed drupal. Went to submit a contact form, and email isn't being delivered. The email address is valid from any other machine.

I looked at the logs, and whenever the server tries to deliver mail it says that there is no such address. I'm guessing it's trying to deliver locally.

As far as I can tell it's using postfix.. How can I configure this to never deliver mail locally, and always relay? I ran a sudo dpkg-reconfigure postfix

But didn't see any options like this.

Thanks
David

---

### Post by SeijiSensei on 2010-11-22
[http://embraceubuntu.com/2005/09/07/setting-a-smarthost-in-postfix/](http://embraceubuntu.com/2005/09/07/setting-a-smarthost-in-postfix/)

---


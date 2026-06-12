---
title: "Spammers using my domain"
date: 2007-07-19
forum: Server Platforms
---

### Post by t_ras on 2007-07-19
I have an email server which can not even be used from out side.
The problem is that some one is sending mail identifying his self as my domain (some_fake_mail[at]my_real.domain) and I get all the "undeliverable" messages.
I can also see the IP from which it was sent, which is defenetly not mine.
Any idea how to take care of it?

Thanks

---

### Post by Adnarim on 2007-07-19
You can't stop him spoofing emails, that's a genereal problem of the protocol.

The recieving mail-servers could do this by doing a host-lookup to the mailfrom field and then look if it corresponds to the IP which sends it.

The undeliverable message you can simply filter out by the adress,IP-range the spoofer uses, I think..

---

### Post by koenn on 2007-07-19
technically, there's not much you can do, other than what to previous poster offered. 
You might look up who owns the IP address of the spoofer, and report the abuse.

---

### Post by MJN on 2007-07-19
It's difficult, if not impossible, to filter the bounce messages as these messages are genuine - this backscatter is the result of the spam not the cause (although just as annoying). Furthermore, you don't want to filter all bounces given they could be responses to your own misdelivered mail. See [http://www.postfix.org/BACKSCATTER_README.html](http://www.postfix.org/BACKSCATTER_README.html) for some good tips on what you can reasonably do, along with discussion on the limitations of its effectiveness.

Also investigate adding SPF records to your domain's DNS (see [http://www.openspf.org/](http://www.openspf.org/)). It's not an ultimate solution to the problem, nothing is, but when I had similar problems with my domains a while back it hammered the backscatter down to practically zero. I didn't hold much hope of it working to be honest - mainly as I wasn't sure how many were checking SPF as part of their filtering - but the results have spoken for themselves.

Mathew

---

### Post by t_ras on 2007-07-20
Thanks for the helpful info!

---

### Post by Mr. C. on 2007-07-20
I'm betting you have a catch-all address, and are allowing all such email.

It is no longer consider useful or prudent to use catchall addresses, as they become a dumping ground for spam and backscatter.

Do yourself a favor; reject all unlisted recipeints.  Use + style address extensions if you need customizable email addresses.

Trying to validate the sending server's IP against MAIL FROM will result in many false positive rejections.

MrC

---

### Post by t_ras on 2007-07-20
good idea. I really do nothing about this mails coming to the catch all address any way...

---


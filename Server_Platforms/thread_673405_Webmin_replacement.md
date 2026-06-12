---
title: "Webmin replacement?"
date: 2008-01-20
forum: Server Platforms
---

### Post by superman69 on 2008-01-20
Hi there

Please could you tell me if there is a replacement for webmin, or is  it secure to use webmin?

Many thansk
Superman:)

---

### Post by dasunst3r on 2008-01-20
Webmin is a pretty decent web administration platform, but if you are looking for an alternative, you could try eBox: [www.ebox-platform.com](www.ebox-platform.com)

---

### Post by superman69 on 2008-01-20
Thanks Will have a look at it, I have a few guys saying that Webmin is easy to hack and very unsecured?

---

### Post by HermanAB on 2008-01-20
Cpanel and Plesk.  Both cost money of course, but if you have lots of domains to manage then Plesk is money well spent.

Cheers,

Herman

---

### Post by Maxtorm on 2008-01-20
Also ISPConfig ([http://www.ispconfig.org/](http://www.ispconfig.org/))

---

### Post by sciurus on 2008-01-29
Ebox is Ubuntu's chosen replacement. It should be ready to use for Hardy. For now, you can help test the packages on Feisty; see the [ebox mailing list]("https://lists.warp.es/pipermail/ebox-user/2008-January/000969.html").

---

### Post by perfecttao on 2008-02-01
Webmin is secure.....as long as it isn't visible to untrusted hosts - it's like anything - the second it's visible to the outside world you open yourself up to attack - you can secure it against internal hosts by locking down so it's accessible from the server itself only, or to a specific management machine:

 Webmin configuration -> IP Access Control, check "Only allow from listed addresses", and enter "localhost."

Never ever open up the Webmin port to the outside world....and certainly never run it without SSL support....

---

### Post by rickyjones on 2008-02-01
> **perfecttao said:**
> Webmin is secure.....as long as it isn't visible to untrusted hosts - it's like anything - the second it's visible to the outside world you open yourself up to attack - you can secure it against internal hosts by locking down so it's accessible from the server itself only, or to a specific management machine:

 Webmin configuration -> IP Access Control, check "Only allow from listed addresses", and enter "localhost."

Never ever open up the Webmin port to the outside world....and certainly never run it without SSL support....

I'm quoting this for truth: What he says is correct.

Webmin should be perfectly secure as long as the server has decent passwords and you continue to use SSL which is the default. Don't open the port to the internet. Lock it down so only certain machines can access it.

Beyond that technically everything is insecure in some way. No matter what program you use there will always be a way in if someone wants to get there.

-Richard

---


---
title: "Does maintaining personal webpage adds to security risks of OS?"
date: 2015-02-12
forum: Security
---

### Post by arroy_0209 on 2015-02-12
May be this is a stupid question but I want to get my doubt cleared regarding creating and maintaining personal webpage through either Google or such facilities provided by an organization. In general there may be links to downloadable files (pdf, study purpose), links to email etc. Does such webpages add to security risks of operating system of the user? I still use Ubuntu 12.04 with noscript, adblockplus, click and clean Firefox add-ons and I have ufw enabled. Also apparmor is in enforced mode to protect Firefox. Please give your suggestions.

---

### Post by Habitual on 2015-02-12
If you're the sole maintainer of such a website, I'd say "no worries".
I'd use html code for email addresses on such a website.
```
name&#64;domian.com
```
vs.
the traditional [email]name@domain.com[/email]

Where do these .PDFs originate?

---

### Post by buzzingrobot on 2015-02-12
If you're maintaining pages/sites on servers operated by Google or someone else, then they are responsible for the security of that.  They may or may not allow users to take additional security measure regarding their files. This would have no affect on the OS or other software running on your own system.

If you run a server on your own equipment and open it for access via the internet, then, of course, you are responsible for the security of that system.

It's not entirely clear from your post which approach you're considering.

---

### Post by arroy_0209 on 2015-02-12
Thanks for your replies. Regarding the pdf files, I meant such files created by me and linked to in the webpage. The file would be uploaded to google for example if I use their service to create my webpage. Also in case I provide links to some relevant websites which one can click to visit those pages, then  I guess it should  be done the way shown for email. Finally I don't intend to run a server from my desktop so the first option mentioned by buzzingrobot is what I had in mind.

---


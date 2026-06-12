---
title: "need help setting up mail server"
date: 2009-06-10
forum: Server Platforms
---

### Post by p1nkrubb3rd1ld0 on 2009-06-10
hi there,

i have followed this howto: [link]("http://flurdy.com/docs/postfix/#intro_ego")

I ma having some problems however. I need only the simplest mail server in this configuration. The server sends and receives e-mails ... but ... i cannot log in through my mail client (i receive authorisation failed).

I have noticed that my server is sending me some generic certificate not the one i have generated.

Does anybody have any ide on how to fix this ??

---

### Post by HermanAB on 2009-06-10
Howdy,

If you chose Postfix as a learning exercise, then do go to the postfix web site.  The documentation there is very good.

If you want a mail server for actual use and don't want to waste time on setting it up, then install Citadel.  It only takes about 20 minutes to get a fully working system using their Easy Install script (or download a preconfigured VMware image) with more features that you'll ever need ([http://www.citadel.org](http://www.citadel.org)) or see my web site for Citadel howtos.

---

### Post by p1nkrubb3rd1ld0 on 2009-06-10
thanks for the hint with citadel. works like a charm (almost) ...

how do i set users for different domains ?? eg. i would like to have [EMAIL="info@domain1.com"]info@domain1.com[/EMAIL] and [EMAIL="info@domain2.com"]info@domain2.com[/EMAIL] to be seperate accounts in citadel ... i know how to restrict a login to one domain ... but how do i set the same login for the second domain ? ... i tried to create usser as [EMAIL="info@domain1.com"]info@domain1.com[/EMAIL] ... but it doesnt work ... i can't find the solution :(

---


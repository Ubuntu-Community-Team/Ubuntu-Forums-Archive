---
title: "Getting SASL authentication to work with Postfix"
date: 2010-09-09
forum: Server Platforms
---

### Post by defaria on 2010-09-09
I'm sure there's many threads about this. In fact I've searched many of them - all of them have been dead ends.

It's pretty simple - I want to be able to send email from my cell phone through my email server at home. But my cell phone keeps getting different IP addresses. So I need to set up saslauth authentication. I've followed many guides however when I connect to my server via port 25 and EHLO it does not show me any auth lines. Doing an auth login results in "503 5.5.1 Error: authentication not enabled". I have "smtpd_tls_auth_only = yes" in postfix's main.cf. If I change that to no then my mail server doesn't work at all. 

I'm tired of reading all kinds of fixes, none of which works, hence this post.

How do I get this working!!!!

---


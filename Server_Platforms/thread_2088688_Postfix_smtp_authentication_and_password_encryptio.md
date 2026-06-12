---
title: "Postfix smtp authentication and password encryption"
date: 2012-11-27
forum: Server Platforms
---

### Post by Wombacik on 2012-11-27
Hello.

Im following this guide: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) and im stuck at Authentication step. I did all as described in guide and on telnet connection server return both STARTTLS and AUTH options so according to guide it means all is ok.

But its not. Anyone can connect with smtp and send mail. Server nowhere asks for password. What i did wrong? 

Whats more, i need to use SHA1 to store password in database instead of CRYPT, how i can change it? Ive found a lot of misleading information about that, seriously i have to replace courier with dovecot to just change hash function?

---


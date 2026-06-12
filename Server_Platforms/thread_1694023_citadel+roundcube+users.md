---
title: "citadel+roundcube+users"
date: 2011-02-23
forum: Server Platforms
---

### Post by jenka on 2011-02-23
Hello!

I wonder a bit about how to proceed with having multiple domains and users on a citadel and roundcube system? I want my users to get their own mail accounts.. And now the only way to do that is in citadel.. and then they get an username and password so they can login on roundcube. And thats great!

But I want so they get a mail adress instead. So they login with [email]user@domain.com[/email]. If you understand.. I have checked a little bit on virtual users in roundcube but I didnt really understand it.

I also want so the imap host is choosed by the domain you've logged in with..

Im pretty lost on this so if someone could tell how this works I would be thankfull! :)

Hope you understod :)

/jenka

---

### Post by HermanAB on 2011-02-24
Howdy,

The @ character is not legal in a Citadel user name.  Therefore the closest you can get is to make the user name "user.domain.com".

That however, will result in a default primary email address of "user.domain.com@domain.com", so you would also have to edit the Citadel address entry for each user to have "user@domain.com" as an alternate email address.

That can all be done from Webcit.  It is not a problem, just go and try it.

---

### Post by jenka on 2011-02-24
Thanks for your reply! :) I think ive sort it out. Most of it anyways :P

---


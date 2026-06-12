---
title: "Cannot get mobile user/pwd for music streaming"
date: 2012-01-22
forum: Ubuntu One (CLOSED)
---

### Post by chuck.lega@gmail.com on 2012-01-22
I am creating a (mobile) java music app to stream my music from ubuntuone. Using the subsonic api from a test server works fine but I cannot manage to "log in" to the music mobile service of ubunto one.
This is what i try (following [https://one.ubuntu.com/developer/account_admin/mobile_login/cloud):](https://one.ubuntu.com/developer/account_admin/mobile_login/cloud):)

GET [https://login.ubuntu.com/api/1.0/authentications](https://login.ubuntu.com/api/1.0/authentications)
This works fine and I get the four keys, tokens, secrets.

Then I call: 
GET https://one.ubuntu.com/oauth/sso-finished-so-get-tokens/<my email address>

I construct the httrequest, sign it with the "OAuth Signpost" lib (see below) and perform the GET 

I do the oauth like this:
Creates a DefaultOAuthConsumer with received ck and cs.
call setTokenWithSecret on it with received t and ts.
call setSigningStrategy with a new AuthorizationHeaderSigningStrategy (also tried without this)

This call always fails with a 403 FORBIDDEN !!


Then I was planning to call: 
GET [https://one.ubuntu.com/phones/creds](https://one.ubuntu.com/phones/creds)
I try this even if the previous call failed. 
I am expecting a redirect response here, but instead I get a 200, with some openId html page...

What to do? What am I doing wrong?

/CL

---

### Post by chuck.lega@gmail.com on 2012-01-30
bump...

---


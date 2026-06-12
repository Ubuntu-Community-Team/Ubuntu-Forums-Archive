---
title: "user verification in signups on a new website"
date: 2020-06-19
forum: The Cafe
---

### Post by Skaperen on 2020-06-19
on a new website i want to have a means to verify that a user trying to sign up is really already a user at some other site, maybe with the same username, but not necessarily so.  my first idea is to send them, via PM on that other site, a temporary signup password.  they will then be required to login with that password.  how safe is it, in general, to do this?  what about some specific sites like ubuntuforums.org or twitter.com? could this be made reasonably secure, as secure as doing the signup the usual way?  is there a risk of exposing that password, even though they will be changing it on this new website very soon as the next step in signing up?  is there a risk of doing too many PMs on the other site?

---

### Post by TheFu on 2020-06-19
OAuth2?

---

### Post by sdsurfer on 2020-06-19
^^ Yes if you are in control of both sites it is your job to make it easy for them in as little steps/actions as possible. Look into OAuth2 or some other SSO (single sign on) option. A lot of sites are using Google authorization for this purpose ("Sign in with Google.")

---

### Post by TheFu on 2020-06-19
> **sdsurfer said:**
> ^^ Yes if you are in control of both sites it is your job to make it easy for them in as little steps/actions as possible. Look into OAuth2 or some other SSO (single sign on) option. A lot of sites are using Google authorization for this purpose ("Sign in with Google.")

There are privacy concerns using OAuth, so be aware of that, but for the stated goal it seems to be the best option. The OAuth provider will know when you login to which site(s).  Just a consideration though most people never worry about it.

---

### Post by Skaperen on 2020-06-19
i am not in control of the other site any more than i am in control o ubuntuforums.org.  if i were in control, i was just use the same database, likely eliminating signups.  the goal is to allow signups and to be sure the username is the same as on there reference site.  i won't be able to get their password this way.

OAuth appears to require the other site to grant permission.  i presume the other site needs to be running an OAuth server port of some kind.  what if they don't?

---

### Post by TheFu on 2020-06-19
> **Skaperen said:**
> i am not in control of the other site any more than i am in control o ubuntuforums.org.  if i were in control, i was just use the same database, likely eliminating signups.  the goal is to allow signups and to be sure the username is the same as on there reference site.  i won't be able to get their password this way.

OAuth appears to require the other site to grant permission.  i presume the other site needs to be running an OAuth server port of some kind.  what if they don't?

google, twitter, facebook, and most of the social networks do. Think they allow anyone.  You can run your own OAuth2 server, if you like. There are implementations in many languages - Ruby, Perl, Python, Php ... perhaps node.js too.

I don't think Ubuntu's login will allow federation outside the Canonical controlled family, but IDK.  They do use/force login.ubuntu.com for all sorts of different things like Ubuntu Core (for embedded systems), Landscape, and these forums.  For security reasons, Canonical won't redirect post-login into a deep link, just to the main page. Remember when we'd login here and be redirected back to the thread we were viewing? That stopped after the login DB got hacked.

As a personal policy, I don't use the same login multiple locations anymore. Around 2011, I did, but have since revised that to use mostly random logins.  I let my password manager create the login.

---

### Post by Skaperen on 2020-06-20
i mentioned twitter.com and ubuntuforums.org merely as examples.  they are places with the concept of a username.

my goal is *not* to allow people to use the same password for each login.  it is only to verify that for a username they are signing up on my site with, they actually are in control of the same username on the other site.  they will be asked to enter a password they wish to use on my site and confirm it as part of this signup.  i expect that password to be different than what they use on the other site or at any other site.  if they use the same password, i won't know or try to know.  once the signup is complete, they can login the usual way.

i do *not* need or want the password they use on the other site.  if they are already logged in to the other site in another window, they will *not* need to login there again.

it does not appear that OAuth's purpose is the same or even a superset.

if i were to use ubuntuforums.org as the "other site" then you would need to sign up with the same username ((like TheFu") when signing up on my site.  if you have a 2nd username here (i would if i were an admin) then you could use either and my site would never known what the other is.

to give you a key for my site, i would need to be sure no one else can get it or see it.

it's similar to verifying your email.  it does not mean the username on my site has to be the same.  it could be that i only need to know it.  for example, the other site could be twitter.com and knowing that, my site could tweet your notifications to you.

---


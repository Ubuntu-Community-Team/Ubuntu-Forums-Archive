---
title: "Can't log in to Ubuntu Wiki"
date: 2005-10-09
forum: The Cafe
---

### Post by jnoreiko on 2005-10-09
I've having trouble logging in to the Ubuntu wiki.
On my ubuntu partition, firefox has my password stored and I can log in fine.
On Windows, I'm trying to log in with the same password (and also with firefox) and it keeps telling me it's incorect.

---

### Post by mattheweast on 2005-10-09
You must have got it wrong. Firefox has probably remembered the correct one :)

The username and password you need are your [launchpad]("http://launchpad.net") username and password.

---

### Post by jnoreiko on 2005-10-09
After much strain & a nasty moment logging out of the wiki on my ubuntu system, I've figured it out.

I had to log in to the wiki with my email address rather than my wiki name.
That's just weird. :???:

---

### Post by casper_2095 on 2005-10-10
It is wierd, and I think it explains a lot of why there are so many HOWTO's in the forums rather than wiki pages of the same.  Put this quirk on top of having to register for it on a foreign site and getting access to the wiki is just all too hard.

---

### Post by mattheweast on 2005-10-10
It is really very easy to log into the wiki. You need to register with launchpad, and then use your email address and password, but the criticism you make of having to register for a foreign site is odd: the same username and password is used on:
 * the ubuntu website
 * the wiki
 * launchpad
 * shipit
In fact, the only thing I can think of where you need a different username/password is the forum. Hopefully eventually we will be able to have a unified login and password here too.
One more thing: once you have logged into the wiki once, you download a cookie that remembers your login forever, until you delete your cookies or log out explicitly.

It really is very easy.

---

### Post by jnoreiko on 2005-10-10
A unified login is a great idea.
The confusion arises because the wiki asks for a wikiname in the form FirstnameLastname. On other wikis, this is also what you use to login. The login page should say something other than "name", otherwise people will assume this is the wikiname they have set.
This paragraph further down the login page adds to the confusion:

> It is best to choose a WikiName (like FirstnameLastname) as username 

---

### Post by mattheweast on 2005-10-10
yeah, i agree that that paragraph you quote might cause confusion. We need to hack it out of the moin config. However the user/password dialog itself is quite clear:

> (Use your Launchpad login or create an account.)

---


---
title: "What the..."
date: 2009-07-11
forum: The Cafe
---

### Post by Mehall on 2009-07-11
Just logged in to my free hosting website, as I'm gonna upload a copy of the Crunchbang 9.04.01 32bit ISO (full, not lite)

When I did, I saw they had updated the control panel they use.

It now displays my ftp password for the account (which is the same as the ACCOUNT password, no way of changing that) in plain text. And it's not even obscured by Javascript, if someone intercepts the page (which isn't SSL secured) they will see my password.

What.... :/

---

### Post by stwschool on 2009-07-11
I'd recommend a swift email discussing security. Of course no web app should ever store passwords in plain text anyway, in fact one should always build with one-way encryption. In fact, scratch that, a swift move away would be a sensible idea.

---

### Post by Mehall on 2009-07-11
I've changed the account password to something simple that someone could guess in all of 5 minutes anyway.

I don't have anything in there anyway. The only things I hold there are files for download, so I can deal if people guess a password that I use when signing up for somewhere that is probably insecure. Just like I also tend to use fake email address for that.

---

### Post by stwschool on 2009-07-11
Fair enough but I still think you should have a chat with them about their security practices, as obviously if it's showing up in the panel then they've obviously either got it in the db in plain text or some other easily-decoded form which is a poor show.

---

### Post by red_Marvin on 2009-07-11
Well, that would make no difference, if you access it with ftp at least, since ftp sends *everything* in plaintext anyway (IIRC), so it's just a question of what traffic to intercept.

However if you do not use ftp otherwise there would be a difference.

---

### Post by stwschool on 2009-07-11
Yeah I know you send plain text, but that requires interception of traffic. In this case, poorly stored passwords on databases only require that database to be compromised. All my apps use one-way-encryption in the passwords, it just seems like pure idiocy to do it any other way to be honest. Now with passwords poorly encrypted and things like email address stored on the database (and people's tendency to use insecure password practices like same password on every site) that gives you a whole bunch of email addresses to break into and use for whatever purposes (maybe bank fraud). It's opening up customers to far too much risk.

---


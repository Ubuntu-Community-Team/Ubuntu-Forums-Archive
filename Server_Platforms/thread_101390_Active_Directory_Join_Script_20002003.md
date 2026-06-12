---
title: "Active Directory Join Script 2000/2003"
date: 2005-12-09
forum: Server Platforms
---

### Post by Darksun on 2005-12-09
I've written a small bash script that will join your Ubuntu Breezy box to AD.

I've tested it on my bench domain without injury...ymmv...

I hope this helps some folks out :smile:

Update 12/13/05 - Added check for root, fixed some typos...works quite well imho :)

Rename to UbuntuADS.sh
chmod +x UbuntuADS.sh
./UbuntuADS.sh

Answer simple questions and away you go...

---

### Post by Darksun on 2005-12-09
new to this...I forgot to post the file...then saw I could edit the first post...etc..I'm dumb :P

---

### Post by TeeSeeJay on 2005-12-09
Nice. It looks like you've got to be root to run...can it check for permissions before executing?

---

### Post by Darksun on 2005-12-11
[QUOTE=TeeSeeJay]Nice. It looks like you've got to be root to run...can it check for permissions before executing?[/QUOTE]

I've quite new to Linux and scripting therein, the next version should be a bit less rough...thanks for the idea :)

---

### Post by mrtrick on 2007-05-17
Thanks for this! I was actually considering writing one of these myself. 

One question though...

> Now joining domain:  DOMAIN enter your AD password when prompted!
username's password: 
[2007/05/17 08:47:23, 0] utils/net_ads.c:ads_startup(289)
  ads_connect: Invalid or incomplete multibyte or wide character

domain and name scrubbed to protect the innocent :)

Thoughts?

---

### Post by albinoraven on 2007-07-20
You probably typed the domain in lower case.

When the script runs kinit with the passed varible of lab.domain.com it passes the string to kinit which has a "feature" that doesn't like lower case.

you can try it manually on the commandline using sudo

kinit [email]Administrator@LAB.DOMAIN.COM[/email] <----the domain has to be in upper case.
Password: superduperpassword

You'll have to make sure that your krb5.conf file is setup properly.

---

### Post by eSPiYa on 2007-07-24
Why I can't make this work?
> ads_connect: Connection refused

---

### Post by ottacon on 2007-07-25
this is very nice.

Worked Flawlessly. Keep up the good work !!!

Thx

---

### Post by commonplace on 2007-08-14
> **eSPiYa said:**
> Why I can't make this work?

I get the same error. Anyone have any ideas?

---


---
title: "Locking the Home folder"
date: 2009-12-01
forum: Security
---

### Post by Ulfgeir on 2009-12-01
It would be really handy if I could password protect my Home folder from people using my computer.  I realize I could set-up more than one user account, but generally speaking I'm the only person on this PC, so it seems like overkill.  

Whenever I do have someone else using my computer, it's normally just a visiting relative or friend that wants to check their email or do some browsing.  And while it's not a huge concern that they might be snooping through my personal folders, it's always a possibility.

You've heard about the statistics concerning the number of people who snoop around in your medicine cabinet, right?  So you never can tell.  And hey, I'm sure there are plenty of us who have some questionable stuff in our files that we wouldn't want family members looking at.

So is it possible (by default under GNOME or with an installed application) to lock-up my Home folder so that even a person running under my user account has to input a password to access it?

Thanks for any help.

---

### Post by bodhi.zazen on 2009-12-01
As you say, making a guest user makes the most sense.

If that is too much hassle, password protecting or encrypting your entire home directory makes no sense as your family will need access to the . (dot) config files ...

So , best make a crypt for your sensitive data.

This can be done in many ways , if you want a gui tool look at 

Cryptkeeper : [http://tom.noflag.org.uk/cryptkeeper.htmlCryptkeeper](http://tom.noflag.org.uk/cryptkeeper.htmlCryptkeeper) is in the repositories.

You could use Truecrypt or Luks or any of the encryption tools ...

---

### Post by Ulfgeir on 2009-12-01
I installed Cryptkeeper and it works perfectly for my purposes.  Thanks!

---

### Post by bodhi.zazen on 2009-12-02
You are most welcome.

---


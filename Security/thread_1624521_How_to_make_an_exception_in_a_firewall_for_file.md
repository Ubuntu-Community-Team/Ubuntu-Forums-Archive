---
title: "How to make an exception in a firewall for file?"
date: 2010-11-17
forum: Security
---

### Post by a quarter past seven on 2010-11-17
i have a problem with a program and a website suggests that i can fix it by 

[B][I]''To resolve this, please adjust the application controls in the firewall  of your Internet security program is allowed full access.''

[/I][/B]Im new to Linux so how would i go about doing this i have fire starter firewall but don't mind changing it,

or is it not possible to even do this as the article was probably referring to windows users,

also off topic but i didn't want to make a new thread about it in my firewall events I have a lot of blocked connections from IP'S repeatedly trying to connect is this anything to bother about?

thanks.

---

### Post by a quarter past seven on 2010-11-18
it actually says

[B] ''First thing to do is grant blank.exe full access in you Firewall as it may be being blocked by the Firewall''

[/B]how would i do this, ive already set the permissions to read write and execute is their anything else i could do?

---

### Post by Iowan on 2010-11-18
Moved to Security Discussions.

---

### Post by CharlesA on 2010-11-18
Depends on what you are trying to do.

By default, Ubuntu allows all outbound traffic. If you are using firestarter, which I don't recommend, since it's out of development and out of date, flush the rules and see if it works.

Are you trying to do something in Wine?

---

### Post by a quarter past seven on 2010-11-18
> **CharlesA said:**
> Depends on what you are trying to do.

By default, Ubuntu allows all outbound traffic. If you are using firestarter, which I don't recommend, since it's out of development and out of date, flush the rules and see if it works.

Are you trying to do something in Wine?

yep im trying to run rosetta stone in wine the customer service people said that the speech engine isnt responding and that it might be blocked by a firewall, i think im gona try it on all the different versions of wine an see if i get any look that way,

Which firewall do you think i should get i have no idea of the difference between them, also do the antivirus programs continually scan the system like in windows as avast seems like it only scans individual stuff that you choose to scan or does it not need to as linux is built differently,

thanks

---

### Post by CharlesA on 2010-11-18
Some Windows apps don't run well in Wine.

See here: [http://appdb.winehq.org/appview.php?appId=1867](http://appdb.winehq.org/appview.php?appId=1867)

---

### Post by cariboo on 2010-11-19
> also off topic but i didn't want to make a new thread about it in my firewall events I have a lot of blocked connections from IP'S repeatedly trying to connect is this anything to bother about?

Welcome to the Wild World Wide Web. There is nothing you can do about it, and you shouldn't worry about it.

---

### Post by a quarter past seven on 2010-11-19
> **cariboo907 said:**
> Welcome to the Wild World Wide Web. There is nothing you can do about it, and you shouldn't worry about it.

ok thanks i was just a bit curious,

---


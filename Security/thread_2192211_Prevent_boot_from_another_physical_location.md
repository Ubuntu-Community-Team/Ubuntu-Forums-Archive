---
title: "Prevent boot from another physical location"
date: 2013-12-06
forum: Security
---

### Post by pyrodrake on 2013-12-06
Hello all,

We are looking to build a machine for a 5 year old built around Edubuntu.  We want this machine to be accessible from a specific location ONLY (in other words, if this machine is taken from the 5 year old's fathers house to anywhere else, we would like the machine disabled).  In searching around, I can't find something that would achieve this.  Is there a way this can be set up, preferably from IP address checking?

We are building this machine specifically for the 5 year old, and no one else.  If his mother steals the machine for her personal use, we don't want her to be able to use it at all, and she lives roughly 20 miles away from him and his father.  Any help or ideas would be greatly appreciated.  Thanks!!!

---

### Post by CharlesA on 2013-12-06
Lock it up - control physical access.

---

### Post by bashiergui on 2013-12-06
Encrypt the whole drive. Then if the mom gets it she at least won't have access to anything. 

Perhaps a restraining order would make sense too. Seems like the problem might be bigger than just mom getting the computer.

---

### Post by ian-weisser on 2013-12-06
A hard solution: You can use an Upstart job to check an onboard GPS, or local network several different ways (including IP address), and to do any action you please, including simulated error, simple poweroff, or reporting in to your server...all before the login screen appears. It's not a package you merely install - you must research and write the control yourself. It's not difficult, but you do need a basic understanding of shell scripting.

Anyone with physical access and a bit of know how can bypass and/or disable the Upstart job. Physical access trumps all software protections (except encryption).



An easier solution: Uninstall *everything* that a small child won't use: Web browser, Software center, email client, LibreOffice, many games, etc. My 5-year olds played perhaps a few games, nothing else.

---

### Post by bigmonmulgrew on 2013-12-09
You could set your router to have an uncommon IP address, basically anything that wouldn't be set by default. You then check if the gateway IP address is what it should be and issue a shutdown command. Set this scheduled to run 30 seconds after log in or something like that to give the network time to connect.

Really it depends how much the undesirables know about linux and how to sort out any issues you might have.

I really don't see why this is an issue though. If the mother "Stole" the PC you simply report them to the police. Your not trying to convince them the PC only works at Dad's house are you. Either way this seems a silly question to me. Nothing sensitive should be on a Kids PC anyway and measures of physically preventing theft would be most effective.

The way you describe it the child wouldn't be able to use it anywhere else either.

---

### Post by CharlesA on 2013-12-09
> **bashiergui said:**
> Encrypt the whole drive. Then if the mom gets it she at least won't have access to anything. 

Perhaps a restraining order would make sense too. Seems like the problem might be bigger than just mom getting the computer.

QFT.

Outside of encrypting the drive and controlling physical access to the machine, there is little you can do with software for a social problem. Even with encryption, they could just wipe the drive and be done with it.

Control physical access and if the machine gets stolen, report it to the police and let them take care of it.

---


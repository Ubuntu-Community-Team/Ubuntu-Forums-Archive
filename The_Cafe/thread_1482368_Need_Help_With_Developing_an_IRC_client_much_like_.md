---
title: "Need Help With Developing an IRC client much like AIM, Yahoo IM"
date: 2010-05-13
forum: The Cafe
---

### Post by Rob@ThePCWiz.info on 2010-05-13
I'm looking to develop a cross platform (starting with windows) IRC client specifically for my network at irc.I-Have-No.Info
I want it to be much like AIM or Yahoo IM.
I want this client to ONLY connect to irc.I-Have-No.info and no other networks.

This client should have One window for channels, and one window for other users, and one window that will have messages from services combined.

I also want a message box to come up on Globals, etc.

I'm looking to create something this specific in order to distribute the program as an AIM or YahooIM like client for my Network specifically in order to attract users who are not familiar with IRC but already use services such as AIM or Yahoo IM.

I think this would give IHNIirc an upper edge if promoted correctly.

I could easily create a look for it, a shell of sorts ofc... umm, the frontend i guess you would call it, using Microsoft Visual Studio C++, however, I am not all that familiar with Sockets and such, so I could use quite a bit of extra help.

I also would like the client to have scripting capabilities, which we will call Addons of course, that third party users can create.

Anyone who is interested in helping out please join #Developers on irc.i-have-no.info or email me at [email]xnite@i-have-no.info[/email]

---

### Post by cariboo on 2010-05-13
Why reinvent the wheel, take an existing open source irc client that works on all three platforms, and remove the ability to enter in an irc address, then just hard code your irc address, distribute as binaries, but make the source code available if anyone asks.

---

### Post by Rob@ThePCWiz.info on 2010-05-14
So Caraboo, we meet again.
Do you think checking out the source of Pidgin might be a good start? If I'm not mistaken it should be available for both Windows and Linux(what I run).

---

### Post by tom66 on 2010-05-14
Pidgin supports so many services - you'd be better off with just using a Java IRC client, setting it to a fixed address, and putting it on your website somewhere.

---


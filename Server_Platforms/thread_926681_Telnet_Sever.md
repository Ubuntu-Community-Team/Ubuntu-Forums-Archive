---
title: "Telnet Sever"
date: 2008-09-22
forum: Server Platforms
---

### Post by Stusy on 2008-09-22
Hi all,

I've been using Ubuntu as a web server for some time now, but now I have a requirement to do some other bits with it.....

The first is to allow a barcode hand gun access to the server via telnet. This server is on the local intranet so security isn't really a problem.

I've installed telnet and set up a user and password specifically for the barcode scanner.

The scanner is setup to recognise prompts i.e. login: and Password: and automatically return the relevant information. This all works great up to this point, but this is where my knowledge seriously fails me.

No what do I do. For starters the screen size of the hand gun is only 24 rows and 33 columns.

PART 1: How do I get it so that if this user logs in his screen size is set so that it appears correctly on the handheld scanner?

PART 2: I then want to create a menu system. This menu system to be linked to a database. The first thing to do would be to get a user to login.
   a) How do I create a menu?
   b) How do I link it to a database (MySQL either local host of another server)?
   c) How do I get it to run after the gun has logged into the server?

I've never done any scripting and think it&#8217;s about time I did.

Any pointers will be greatly appreciated.

Regards
Stuart

---

### Post by HermanAB on 2008-09-22
The user screen settings are in .xinitrc

Cheers,

Herman

---


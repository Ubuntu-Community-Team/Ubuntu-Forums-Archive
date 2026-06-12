---
title: "Capturing a POST request ..."
date: 2005-11-12
forum: Server Platforms
---

### Post by dbee on 2005-11-12
I want to capture a POST request from my machine to a remote server.

I'm using ethereal at the moment but it just gives me some text and alot of hex.  I can see what is going on, but I want the proper html/text form as-is. 

I can't find anything on google and the ethereal filters don't seem to be up to the task. 

help ??

---

### Post by nagilum on 2005-11-12
Ethereal can do this. After you captured the relevant session select one of the first TCP packets and run "Analyze -> Follow TCP Stream". It will show you the decoded HTTP session.

---

### Post by dbee on 2005-11-12
thanks nagilum, I didn't see that :)

---


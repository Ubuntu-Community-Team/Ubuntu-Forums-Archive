---
title: "How to stop log in password request?"
date: 2010-01-04
forum: Ubuntu One (CLOSED)
---

### Post by ghoracek on 2010-01-04
I canceled my subscription to Ubuntu One because I had to enter a password every time I booted Ubuntu -- regardless of whether I wanted to use the feature or not that session.  I couldn't find any way to stop that practice so I unsubscribed.  Still  got the password request.  Finally had to delete the Ubuntu One folder to stop the request for a password.  

Maybe if I knew how to stop the request of password I would try it again.  But if I do figure this out, how do I get Ubuntu One back? 

glh

---

### Post by SteveDee on 2010-01-05
I suggest you go to Add/Remove Applications and search for Ubuntu One.
If it appears as installed, I'd un-tick the box and un-install it. Then you can re-install and hope that it also recreates your Ubuntu One folder.

I remember having problems registering UbuntoOne/LaunchPad account and having to go around the process 2 or 3 times, but unfortunately I didn't take any notes.

Anyway it works fine now (...although I'm not quite sure what to do with my Cloud!).

If you haven't already done so, take a look at this info: [https://wiki.ubuntu.com/UbuntuOne/Tutorials/Subscriptions](https://wiki.ubuntu.com/UbuntuOne/Tutorials/Subscriptions) as this might help.

---

### Post by joshuahoover on 2010-01-15
> **ghoracek said:**
> I canceled my subscription to Ubuntu One because I had to enter a password every time I booted Ubuntu -- regardless of whether I wanted to use the feature or not that session.  I couldn't find any way to stop that practice so I unsubscribed.  Still  got the password request.  Finally had to delete the Ubuntu One folder to stop the request for a password.  

Was the password request via a web page or a keyring password request? The web page shouldn't come up each time, but the keyring password request may come up as a result of either having an auto-login setup or having a keyring password that is different from your Ubuntu login password.

> **ghoracek said:**
> 
Maybe if I knew how to stop the request of password I would try it again.  But if I do figure this out, how do I get Ubuntu One back? 

The best way to remove Ubuntu One is to use the Ubuntu Software Center (under the Applications menu), type in Ubuntu One in the upper right search box of the software center app, click on the right arrow next to Ubuntu One, click the "Remove" button. Install using the same instructions, except you will click an "Install" button in the last step. :-)

---


---
title: "install java remotely"
date: 2008-06-27
forum: Server Platforms
---

### Post by skyl on 2008-06-27
Is it possible to perform java installation on my ubuntu server over a SSH session? The sun java packages were downloaded however the installation came up with license agreement screen which "hanged" the putty session.

---

### Post by unixbills on 2008-06-27
It works OK for me.  You need to answer the question with a yes.  Will TAB work to move to "<yes>" and hit enter?

I install both the run time and the dev kit on our servers with apt-get remotely.

---

### Post by unixbills on 2008-06-27
Sorry it is "<OK>" and then "<Yes>".

I just tried this with Putty.  Mine works OK except some chars are wacky but I can TAB to "<OK>" hit enter and continue.

Bill

---

### Post by skyl on 2008-06-27
The fact that it worked for you but not me over putty led me to thinking that the putty I used (ver 0.54) may not have the required feature.

Sure enough downloaded the latest ver 0.60 the TAB/Enter now worked correctly with the agreement form. Thanks!

---


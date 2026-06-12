---
title: "Webmail that supports mobile browsers?"
date: 2008-11-05
forum: Server Platforms
---

### Post by rotorcraig on 2008-11-05
I have an Ubuntu Hardy Server setup that is now working very nicely as an IMAP mail server.

As well as accessing my mail via Thunderbird/IMAP from a number of home PCs, I have installed RoundCube so that I can access remotely via webmail.

I am really pleased with RoundCube which is fantastic from Firefox on my laptop, but when I try to access it using the browser on my Blackberry I get a "your browser is not supported" error.  I have tried the various settings that allow the Blackberry browser to emulate IE6, Mozilla etc but this has not helped; nor has installing Opera Mini.

Does anyone know of a lightweight webmail app that I can install on my server alongside RoundCube that will provide a simpler interface that will work with mobile devices including my Blackberry?  I have spent quite a bit of time on Google and found many manifestations of this question, but no answers!

Thanks in advance

Craig

---

### Post by baudday on 2008-11-05
Have you tried squirrelmail? If you're using a blackberry, can't you just set up your email account on there?

---

### Post by MJN on 2008-11-06
I agree - a dedicated mail application on such a device is surely likely to be better than doing it via a web browser. I cannot think of any advantages (but several disadvantages) in using the web browser for this.
 
Notwithstanding that, as Baudday says Squirrelmail should work - as long as your browser supports frames (the v1.5.x tree is (or was planned to be) frameless should this be required).
 
Mathew

---

### Post by rotorcraig on 2008-11-07
Blackberry is a works device; can't push my personal eMail to it due to security policy and want to monitor a number of accounts via webmail anyway.

Did try squirrelmail previously but no the frames don't work very well.  It struggles to maintain state and you quickly end up with a blank screen other than a few menus that no longer work.

I think I'm looking for a vanilla / lightweight webmail app with minimal features / presentation.  Or waiting for the long promised Firefox for Blackberry browser that might get round the problem in the first place?!

Craig

---

### Post by jamesrfla on 2008-11-07
Web cit is one. It comes with citadel mail server.

---


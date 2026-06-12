---
title: "Flipped Desktop on LTSP Client"
date: 2009-05-09
forum: Server Platforms
---

### Post by gdi2k on 2009-05-09
Here's a strange one...

I'm using my desktop as an LTSP server and I'm using an [Atom-based]("http://www.upgradenation.com/705212/intel-d945-ich7-gma950-mini-itx.html") PC as a client. I have an existing user who can log in and use the thin client without any trouble. 

However, if I add a new user and that user logs in to the client, the desktop is *flipped* - by this I mean:
[LIST]
[*]The top and bottom bars are in the right places, but the letters are upside down (but still in the correct order).
[*]Objects are not where they appear to be - for example; despite the File menu showing at the bottom of the window, I have to click where it would normally be to access it. This applies to menu items and icons too. 
[/LIST]

I've attached a screenshot of the problem (don't laugh! ;-) showing the home directory and the help app open. If I log in as the new user on the server, things are fine - they just go weird when logging in on the client. 

I've tried completely deleting everything in the user's home directory (including hidden files), deleting the user completely, creating new users etc. The existing users work fine, but I cannot create new users without this problem. 

I had it running on previous Ubuntu versions without issue, since 8.04.

Any ideas?

UPDATE: Forgot to mention that the login screen looks completely normal.

---

### Post by camzrama on 2009-11-12
I am experiencing the same problem.  Did you find a fix?

---

### Post by gdi2k on 2009-11-12
No I didn't find a solution, I gave up and haven't tried again since. In hindsight, the LTSP mailinng list would have been the better pleace to post the issue - it's a busy list full of experienced LTSP users and developers.

[https://lists.sourceforge.net/lists/listinfo/ltsp-discuss](https://lists.sourceforge.net/lists/listinfo/ltsp-discuss) 

I'm sure if you post there and link back to this forum post for the screenshot, you'll get an answer. (I would do it myself, but I don't have access to the hardware anymore, so I wouldn't be much help giving technical details).

---

### Post by AnAx on 2010-06-26
I had the same problem.
Heres what I did to fix it.
Log into each client account on the LTSP server and turn off all visual effects. 
After I did that the clients wouldn't boot so then I had to do this:
sudo ltsp-update-sshkeys
sudo ltsp-update-image

After that everything worked great.
Hope this helps.

---


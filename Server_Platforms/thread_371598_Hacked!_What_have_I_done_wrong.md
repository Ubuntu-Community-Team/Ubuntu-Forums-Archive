---
title: "Hacked! What have I done wrong?"
date: 2007-02-27
forum: Server Platforms
---

### Post by Q4U on 2007-02-27
My ebay and gmail account passwords (stupid mistake: they were the same) have been reset by some scumbag who used them to bid fraudolently for various items. Luckily no damage seems to have been done (transaction revoked promptly etc)... But... what have I done wrong?

1. I use strong passwords
2. Enable iptables allowing only HTTP HTTPS and DNS
3. Browse the net with Firefox only with NoScript Adblock etc.
4. Everything is always updated two-three days maximum after new packages are available
5. When using broadband, I do so only behind a hardware router-firewall
6. Reinstall periodically (had done it two weeks ago)

You mean that now SELinux, Tripwire and all the rest is necessary even for an ordinary desktop? Damn it's gonna be hard work!

---

### Post by MJN on 2007-02-27
Have you ever accessed eBay/Gmail from anywhere other than your own PC? From the info you've given it's somewhat premature to be jumping to conclusions...
 
Mathew

---

### Post by Q4U on 2007-02-27
Nope. 

Actually, I have read that recently there have been a spate of ebay password cracks... someone is speculating that it might be someone who figured out how to compromise ebay servers... 

But still... I am seriously thinking of stepping up my security awareness... have downloaded some SELinux docs... daunting...

---

### Post by _simon_ on 2007-02-27
Also, have you ever followed an email link to ebay or gmail then had to enter your login details?

Does anyone else use your machine that might have?

---

### Post by PurplePenguin on 2007-02-27
Why are you assuming that somebody hacked into your computer?  Seems more likely that they just got into your gmail account and from there probably just read your intro email from Ebay.  How could they get into your gmail account?  Well, do you use the same password for your gmail account as you do for any website/forum registration?  This is incredibly easy stuff to crack.  In fact, I've seen a website that shows you how to use google to get passwords for stuff like this...

I doubt that anybody was actually on your system.  So having stronger security at home isn't going to help one bit.

---

### Post by Q4U on 2007-02-27
I am starting to think that the weakness in my approach was the stupid shortcut of using the link to the "the item you are watching is about to expire" ebay update... I did not check the headers all the time as I should have, now that I think of it.

I got used to the fact that gmail is pretty damn good in sorting spam from ham, and became complacent. Yes, I am starting to believe that this is the most likely explanation.

Lesson learned, I guess.

---


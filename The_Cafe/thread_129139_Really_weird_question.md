---
title: "Really weird question"
date: 2006-02-13
forum: The Cafe
---

### Post by Arktis on 2006-02-13
Okay, I'm running dapper and I use firefox 1.5.0.1 of course, and I came across something rather odd when somebody screwed up a couple links they posted.  Check this out:

[http://http://](http://http://)  <---this takes me to microsoft.com.  What the....???  :confused: Can somebody explain this to me?

---

### Post by kairu0 on 2006-02-13
It takes me to [www.elpais.es](www.elpais.es) (!), probably because my locale is set to ES.

---

### Post by prizrak on 2006-02-13
MS owns the internet?

---

### Post by mstlyevil on 2006-02-13
[QUOTE=Arktis]Okay, I'm running dapper and I use firefox 1.5.0.1 of course, and I came across something rather odd when somebody screwed up a couple links they posted.  Check this out:

[http://http://](http://http://)  <---this takes me to microsoft.com.  What the....???  :confused: Can somebody explain this to me?[/QUOTE]

It has to do with a setting in Firefox. I forgot which one it is but I have changed it before.

---

### Post by Arktis on 2006-02-13
I was thinking that maybe it had more to do with the handling of your local ISP.  But if it's a firefox setting somewhere... that's even stranger.  I don't think that's likely to be the case.

---

### Post by kaamos on 2006-02-13
Firefox uses googles "I'm feeling lucky", and that apparently wants to take you to bills site. I got to w3c.

---

### Post by briancurtin on 2006-02-13
it takes that second instance of "http://" and searches google for it, feels lucky with itself, then takes you to its first response which is most likely MS.

type in 's', it takes you to mcdonalds.com. that was a problem with a lot of people on fresh installs where links in Gaim would take you to mcdonalds' site because it sends "firefox %s" as the command but took the 's' as literal.

---

### Post by Arktis on 2006-02-13
Ah, I see.  Thanks.

---

### Post by majikstreet on 2006-02-13
:D someone asked this once at linuxquestions.org it was funny :D

---

### Post by steveneddy on 2006-06-12
[QUOTE=Arktis]Okay, I'm running dapper and I use firefox 1.5.0.1 of course, and I came across something rather odd when somebody screwed up a couple links they posted.  Check this out:

[http://http://](http://http://)  <---this takes me to microsoft.com.  What the....???  :confused: Can somebody explain this to me?[/QUOTE]

OK - this is on another thread - but if you change the command in System-->Preferences-->Prefered Applications to "firefox %s" (without the quotes) than you should be fine. Also, make the launcher on your desktop or toolbar for firefox to read "firefox %u" everything should work like you expect it to. 

I'm not sure of the complete reason for this, but this little fix will repair links you are trying to open from another application, like Gaim for instance, to open correctly. 

Another bean.....what comes after 5 cups of Ubuntu? I guess I'll just have to wait & see, huh?

Happy computing! - SE

---


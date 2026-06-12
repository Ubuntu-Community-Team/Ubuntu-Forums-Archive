---
title: "Weird character error"
date: 2006-05-11
forum: Server Platforms
---

### Post by djvishnu on 2006-05-11
I have discovered a weird error on my website:

I run ubuntu breezy with apache2

When i use these three (norwegian) letters: Æ Ø Å, i only get weird symbols in the browser. When i cat the file it contains the letters, not the symbols. Here's the weird part:

When I view the source from my browser, the letters are correct! Why arnt they displayed correct in the browser? (my point is best illustrated in IE, firefox corrupts the sourece as well)

[http://sensation.no/test2.html]("http://sensation.no/test2.html")

I tried copy-paste the source into a new local html, and IE displays it correctly. So then i figured the problem isnt the html, but the way apache sends it to the browser. Am i correct? Is this an apache configuration issue?

Please click the link and see for yourself. (Check the source)

Thank you

---

### Post by oyvindaa on 2006-05-11
I'm having the exact same problem.

I was thinking there might be some kind of package we could install to fix it but I haven't succeeded in finding anything yet.

---

### Post by djvishnu on 2006-05-24
bump

---

### Post by MJN on 2006-05-25
Being an ignorant Englishman I'm no expert when it comes to 'foreign' character sets, however it looks to me like this is the problem here.

Try removing the charset=UTF-8 from your HTML and see if that 'cures' it... (it seems to at this end - I get a jumble when viewing it from you, or locally). You might need to change/remove any Adddefaultcharset in your apache2.conf config too (as this kicks in for all pages without a defined character set). I can confirm (from a packet trace) that your Apache is announcing that UTF-8 is being used - however from this end I have no way of telling if this is solely due to it being in your HTML META tag or whether an Adddefaultcharset directive would've announced this anyway).

If I remove the charset from your HTML then it appears fine here (locally of course).

However, this does little more than pinpoint the problem - the solution here is nothing more than a fudge because ideally (particularly given the characters you're using) you need to be clear about what character sets your pages are using - hence why the (adddefault)charset directives are in the HTML and Apache config.

Whilst UTF-8 may not be the one you want, I don't know what is. I use ISO-8859-1 which has enough characters for me... ;)

Mathew

---

### Post by djvishnu on 2006-05-26
Thank you for your input MJN.

i have made a copy that does not set the charset in the html meta tag,
[http://sensation.no/test3.html](http://sensation.no/test3.html)

Could you please let me know what charset my apache is sending now?

config now:
AddDefaultCharset   UTF-8
i tried to comment it out as well

i also found something else googling, but im not sure it its relevant:
[http://www.sitepoint.com/forums/showthread.php?t=371669](http://www.sitepoint.com/forums/showthread.php?t=371669)
I changed my locale from en_US.UTF-8 to nn_NO.UTF-8 (also tried nn_NO.ISO-8859-1 and en_DK.UTF-8 - denmark has the same æøå letters)

I am really stuck here, i find this weird.

thank you

---

### Post by djvishnu on 2006-05-26
NEver mind, i actually got it working now! :)

---

### Post by MJN on 2006-05-26
Ah well done - it might be worth you recording what you did here as no doubt there'll be someone with similar troubles in due course!
 
Mathew

---

### Post by djvishnu on 2006-05-26
yes, i was going to, just had to figure out what it was that actually did the trick.

i made several changes, but since my browser used the cache until i pressed reload 5 times (!) i didnt see the results right away,

anyway, this is my configuration now:

apache config:
LanguagePriority no da en nl et fr de el it ja ko pl pt pt-br ltz ca es sv tw
AddDefaultCharset   ISO-8859-1

system locale:
LANG=en_DK.UTF-8

i could probably get away with using defaultcharset utf8 and another system locale, but right now im not touching it until it breaks something else :)

---


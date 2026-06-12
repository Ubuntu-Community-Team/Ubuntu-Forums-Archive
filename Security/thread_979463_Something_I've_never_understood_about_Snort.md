---
title: "Something I've never understood about Snort"
date: 2008-11-12
forum: Security
---

### Post by MaindotC on 2008-11-12
Snort is really nice and I set up the configuration per the tutorial on howtoforge and I used BASE to view snort's results in a web browser.  That's really cool, but something I've never understood is why isn't there some type of alarm or notification in the event something is detected in the rules?  For example, say snort detects a port scan.  Ya, I know there are billions of port scans each day, but isn't there some way I could get an email or a text message if snort detected something that I wanted to know about?  The windows version has an auditory alarm that plays through the speakers.

---

### Post by randy78 on 2008-11-13
Swatch is what you're looking for:

sudo apt-get install swatch

Then, check here: [http://www.snort.org/docs/faq/1Q05/node94.html]("http://www.snort.org/docs/faq/1Q05/node94.html")

---

### Post by MaindotC on 2008-11-13
randy you're the man!  I was reading the snort docs but I hadn't gotten to this point yet.  That's what forums are for :)  THanks!

---

### Post by randy78 on 2008-11-13
Sweet! Mark this as solved using the Thread Tools tab so others can use it :)

Take Care:guitar:

---

### Post by MaindotC on 2008-11-13
Well first I'll have to see if it works.  Some of those links on the snort site are outdated - personal web pages of .edu domains.  I'll keep you updated.

---

### Post by randy78 on 2008-11-13
Jeez, no joke... sorry for the bad links man :( 

Here's another you might try: [http://www.linuxsecurity.com/content/view/117377/171/]("http://www.linuxsecurity.com/content/view/117377/171/")

---

### Post by MaindotC on 2008-11-13
I'll google more of it but for now you've given me a good direction to research :D

---


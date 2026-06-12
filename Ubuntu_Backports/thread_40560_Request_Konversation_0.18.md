---
title: "Request: Konversation 0.18"
date: 2005-06-09
forum: Ubuntu Backports
---

### Post by Monchy on 2005-06-09
Changelog: 

Changes in 0.18:
-All nicks were blue when colored nicks are disabled with some setups
-/cycle now works as expected
-/gauge script was not working correctly when given an argument greater than 100
-/mail script has been added
-Button to invoke Regular Expression Editor (if installed) in Settings -> Highlight.
-Complete command line argument system for connection
-An option to disable clickable nicks. Add ClickableNicks=false to konversationrc to disable it.
-Fixed a big memory leak in message processing
-Nicklist slider now correctly resizes in all channels when its resized and correctly restores on startup
-[[foo]] is now a link to [http://en.wikipedia.org/wiki/foo](http://en.wikipedia.org/wiki/foo)

Changes in 0.17:
-Add an option to hide realnames in nicklist
-Show away users as disabled ala Xchat
-Remove sort by away status
-Fix whois replies for normal users on safe channels ( IRCNet alike )
-Fix whois replies from ircd-hybrid ( Efnet alike )
-Better handling of quiet bans ( especially Freenode )
-Enable clickable nicks even if colored nicks are off
-Per identity pre-shell command support with a GUI
-Bookmarking support
-Detect Japanese encoding correctly while trying to auto-detect Unicode
-Fix Logging preferences not showing with French translation

I know there are no security fixes, but the most recent version available is only 0.16. Anyway if anyone is up to the task it would be most appreciated :)

---

### Post by Mez on 2005-06-10
Pain in the ass... have to do it all manually... but ... hey - I'm doing it for ya :D feel happy :D

---

### Post by Mez on 2005-06-10
You can download a packaged version (working perfectly as far as I can see on hoary) from

[http://www.sourceguru.net/ubuntu/hoary/backports/konversation_0.18-1~5.04ubp1_i386.deb](http://www.sourceguru.net/ubuntu/hoary/backports/konversation_0.18-1~5.04ubp1_i386.deb)

John/any other dev, feel free to upload to staging

---

### Post by Monchy on 2005-06-10
Hi Mez

Thanks for doing this, really do appreciate it! :)


edit: package working perfectly here on hoary :)

---

### Post by Mez on 2005-06-10
Yeah, hopefully a dev will spot this and upload to staging... otherwise, email me (martin@sourceguru.net) if you find a problem

---

### Post by Mez on 2005-06-11
repackaged with correct version number for backports

[http://www.sourceguru.net/ubuntu/hoary/backports/konversation_0.18-1~5.04ubp1_i386.deb](http://www.sourceguru.net/ubuntu/hoary/backports/konversation_0.18-1~5.04ubp1_i386.deb)

---

### Post by dolny on 2005-06-11
A little offtopic: Is there a way to make Konversation transparent? Using the program settings? Like in XChat? Because I found it kewler than XChat but I love the transparency function.

---

### Post by Mez on 2005-06-12
yeah, use xcompmgr

---

### Post by Mez on 2005-06-15
uploaded to staging

---


---
title: "Ubuntu Web Safety"
date: 2013-09-05
forum: Security
---

### Post by jspeterson on 2013-09-05
Hello,

I understand that Linux is significantly safer than Windows when it comes to viruses because less viruses are developed for it. How safe is Ubuntu from malicious browser scripts such as cross site scripting? 

I work in a field that requires me to access some shadier parts of the web, so absolute "safe browsing" isn't as valid of an option, and programs such as NoScript aren't really an option because I need scripts enabled too frequently. Are there any preventative measures I can take?

Some further clarification- I have Firefox not accepting third party cookies, clearing cookies after it closes, telling sites "Do Not Track" (although I get the impression malicious websites don't respect this..), and although I need History enabled, I never save any passwords or form information. I don't know much about malicious scripting, but most posts about safety suggest things that aren't options to me, such as installing programs that block scripts across the board. I don't download and run anything stupid, but I do need to access very suspicious pages sometimes and I'd like to know the extent of what a malicious script on a page can do on a linux system.

---

### Post by zealibib slaughter on 2013-09-05
You may want to try a virtual machine or maybe even a live disk on a usb that way everything is sandboxed from your primary system

---

### Post by Bucky Ball on 2013-09-05
*Thread moved to **Security Discussions**.*

Moved here for now but good chance it will end up in ***Recurring Discussions***. There is a ton of information available about this already on the forums and elsewhere online.

---

### Post by Hungry Man on 2013-09-05
XSS, CSRF, etc are all the same on Linux. That's handled by the browsers policies, which don't change based on the operating system. NoScript is the best defense here.

---

### Post by Lars Noodén on 2013-09-05
You can also lock things down a bit more by adjusting an [apparmor profile](https://wiki.ubuntu.com/AppArmor) for the browser.

---

### Post by Gyokuro on 2013-09-08
Something about Do Not Track: [http://whatisdnt.com/](http://whatisdnt.com/)

---


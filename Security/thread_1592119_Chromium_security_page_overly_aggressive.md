---
title: "Chromium security page overly aggressive"
date: 2010-10-10
forum: Security
---

### Post by d5xtgr on 2010-10-10
I connect to the internet through a password-protected network which stores my login for one day (basically every morning I get a redirect to a website that prompts for a username and password).  The problem is that since my homepage is also 'https://' I get chromium's 'This is probably not the webpage you are looking for!' message.
Quite simply, I want chromium to trust the login site enough that it will simply proceed to it without confirmation without applying this reduced security to other sites.  How do I achieve this behaviour?
I spent a while looking for a solution and came up with this: [http://code.google.com/p/chromium/wiki/LinuxCertManagement](http://code.google.com/p/chromium/wiki/LinuxCertManagement)
I have difficulty understanding how I should apply this to fix my problem.

---


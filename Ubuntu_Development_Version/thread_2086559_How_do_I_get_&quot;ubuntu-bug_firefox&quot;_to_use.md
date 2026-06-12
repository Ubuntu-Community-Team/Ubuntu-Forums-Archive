---
title: "How do I get &quot;ubuntu-bug firefox&quot; to use Opera?"
date: 2012-11-21
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2012-11-21
There is a browser running, just fine, thanks, Opera.

Firefox won't run.  launch it and nothing shows on the window list.

"ubuntu-bug firefox" is hard wired to use firefox and must have firefox running perfectly to report the firefox bug??  All I get is:

"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."

I close it, try ubuntu-bug firefox, which then gets the message "Firefox is already running...."

Is there a way to get "ubuntu-bug firefox" to use opera - which is running fine, thanks?

---

### Post by mc4man on 2012-11-21
Change your default Web browser in 
System Settings > Details > Default Applications to Opera

---

### Post by sammiev on 2012-11-21
> **jerrylamos said:**
> There is a browser running, just fine, thanks, Opera.

Firefox won't run.  launch it and nothing shows on the window list.

"ubuntu-bug firefox" is hard wired to use firefox and must have firefox running perfectly to report the firefox bug??  All I get is:

"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."

I close it, try ubuntu-bug firefox, which then gets the message "Firefox is already running...."

Is there a way to get "ubuntu-bug firefox" to use opera - which is running fine, thanks?

Same bug here as well. Started after todays updates.

---

### Post by mc4man on 2012-11-21
There has been an intermittent issue with FF where sometimes when you close FF while the window exits the process doesn't. You need to end the FF process however you choose to before opening FF again. 
(system monitor, whatever
Seen this here since 12.10 dev though less so in 13.04 dev

---

### Post by jerrylamos on 2012-11-21
> **mc4man said:**
> There has been an intermittent issue with FF where sometimes when you close FF while the window exits the process doesn't. You need to end the FF process however you choose to before opening FF again. 
(system monitor, whatever
Seen this here since 12.10 dev though less so in 13.04 dev
Seems to me years ago when being thrashed by Red Hat I did some cli stuff to display processes, and there was some way to delete a process.  Haven't had to do that in eons.  Any hints?  Thanks.

Looks like there's a suggestion in this thread how to change the default browser.  I'll give that a go.  Thanks.

---

### Post by mc4man on 2012-11-21
> **jerrylamos said:**
> Seems to me years ago when being thrashed by Red Hat I did some cli stuff to display processes, and there was some way to delete a process.  Haven't had to do that in eons.  Any hints?  
When FF does this to me I just open system monitor & kill the larger of the typical 2 listed firefox processes.

---

### Post by sammiev on 2012-11-21
Hi jerrylamos, I tried Unity and FF, it worked great. I switched back to gnome and the problem was still there. Not sure what you are running but just giving you the heads up it maybe a problem with gnome.

---


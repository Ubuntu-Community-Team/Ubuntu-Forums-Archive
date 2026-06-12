---
title: "Shut Down &amp; Logout Problem"
date: 2013-03-24
forum: Ubuntu Development Version
---

### Post by roly33 on 2013-03-24
I've been running 13.04 since Friday with no issues, until yesterday where I now can no longer Logout or Shut Down (when I select Shut Down I get a dialogue box that says Are you sure you want to close all programs and shut down the computer? with Cancel & Shut Down options), but clicking on Shut Down just closes the dialogue box and doesn't do anything. Clicking on Logout has no effect what so ever & I have to resort to hard powering down & go through the disk check every boot up.

How can I fix this without doing a re-install if at all possible?

Roland

---

### Post by cariboo on 2013-03-24
What happens when you Press Ctrl-Alt-F1, login and then type:

```
sudo halt -p
```

does the system completely shutdown?

---

### Post by Virtuality314 on 2013-03-24
The temporary workaround is to open a terminal, and type in:

sudo shutdown -h now

---

### Post by dino99 on 2013-03-24
if you are logged as 'ubuntu' aka unity, then reset it. From a terminal, simply run: > unity --reset
if the problem persist, then install & use unity-tweak-tool to reset the settings

---

### Post by roly33 on 2013-03-24
I ended up doing a re-install as Software Updater kept saying I wasn't online even though I was, and everything is working now.

Roland

---


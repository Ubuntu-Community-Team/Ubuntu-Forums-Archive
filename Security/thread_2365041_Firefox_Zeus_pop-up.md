---
title: "Firefox Zeus pop-up"
date: 2017-07-01
forum: Security
---

### Post by Buntu Bunny on 2017-07-01
So I was researching tractor attachments on Firefox and got this annoying pop-up which includes an "authentication required" dialog box which states:

> [http://mdantsane.top](http://mdantsane.top) is requesting your username and password. The site says: “Call Microsoft Technical Department and claim your username 
and password to get your PC unlocked - 1-877-804-5390”

Then it wants user name and password. Well, I do have dual boot with Windows 10 (which I never use), but I don't use Wine or a virtual box, so on the one hand I'm not worried, but I can't get these two pop-up windows to go away because "cancel" does nothing. They remain even when I close out Firefox and re-open after a reboot and reopening Firefox. Obviously I'm not going to fill in a username and password, nor am I going to visit that website nor call the number. I've searched for how to remove Zeus from Ubuntu, but there is nothing out there (that I can find). 

Can anyone tell me how to get rid of these pop-up windows?

---

### Post by deadflowr on 2017-07-01
> Can anyone tell me how to get rid of these pop-up windows?
Nuke your firefox profile and then create a new one:
Open a terminal and run
```
firefox -ProfileManager
```
from there on it's simple enough to follow what to do.

See if that clears it up.
Unfortunately this also clears all settings you have including bookmarks and any saved data (passwords, etc)

---

### Post by Buntu Bunny on 2017-07-01
I will try this! No saved passwords but if I backup my bookmarks do you think it will follow, i.e. is attached to them somehow?

---

### Post by oldos2er on 2017-07-01
Until you get a better answer, have you tried running firefox with a new profile? ```
firefox -P
```

---

### Post by Buntu Bunny on 2017-07-01
> **oldos2er said:**
> Until you get a better answer, have you tried running firefox with a new profile? ```
firefox -P
```

No, I've honestly never messed with the profiles. ```
firefox -P
``` will create a new (second) one?

---

### Post by deadflowr on 2017-07-01
both commands are the same, so..

---

### Post by oldos2er on 2017-07-01
> **Buntu Bunny said:**
>  ```
firefox -P
``` will create a new (second) one?

Yes.

---

### Post by Buntu Bunny on 2017-07-01
I created a new profile, opened Firefox, and no more stupid Zeus pop-ups. I did backup my bookmarks as an html file, uploaded them and so far so good. 

Thank you deadflowr and oldos2er! I appreciate the prompt help.

---


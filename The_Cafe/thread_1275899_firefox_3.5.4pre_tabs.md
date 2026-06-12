---
title: "firefox 3.5.4pre tabs"
date: 2009-09-26
forum: The Cafe
---

### Post by aktiwers on 2009-09-26
Did they just move the "close tab" button to the right corner?
And remove it from the tab itself? Anyway to fix this?

---

### Post by Sunflower1970 on 2009-09-26
I've checked my 3.5.4pre, 3.6b1pre & 3.7 and I still have my close button on the tab in all versions...

---

### Post by Xbehave on 2009-09-26
I have mine modified anyway but to fix read this:
[http://kb.mozillazine.org/browser.tabs.closeButtons](http://kb.mozillazine.org/browser.tabs.closeButtons)
change the settings to what you want
open about:config 
edit the settings browser.tabs.closeButtons
> 0 Display a close button on the active tab only
1 Display close buttons on all tabs (Default)
2 Don’t display any close buttons
3 Display a single close button at the end of the tab strip (Firefox 1.x behavior) 

---

### Post by Tipped OuT on 2009-09-26
Looks normal to me. Are you sure you're just not doing something right?

[IMG]http://img89.imageshack.us/img89/5148/screenshotshiretoko.png[/IMG]

---

### Post by aktiwers on 2009-09-26
Hmm strange..  mine looks like this:
[img]http://img225.imageshack.us/img225/590/this.png[/img]

See how the close button has been removed from all the tabs and only one is at the right corner? 

Gonna try Xbehaves suggestion.. thanks! :)

---

### Post by aktiwers on 2009-09-26
Tried Xbehaves suggestion and its already set to 1.. hmm..

Edit: sorry about the messed up screenshot btw

---

### Post by Tipped OuT on 2009-09-26
Maybe it's your theme? Do you have a custom Firefox theme installed?

---

### Post by MaxIBoy on 2009-09-26
You can still middle-click on the tab or hit ctrl-W.

But if you really want the buttons, try it with a different theme as someone else suggested.

---

### Post by Xbehave on 2009-09-26
Start firefox in [safe mode]("http://support.mozilla.com/en-US/kb/Safe+Mode") (don't reset anything just run it in safe mode to see if it still happens)
```
firefox -safe-mode
```
btw if 1 behaves like 3 what happens if you set other numbers.
If nobody else is seeing this i suspect something has modified your chrome, this is probably a theme but it may be something in your chrome folder
what files are in ~/.mozilla/firefox/<profile name>/chrome/

---

### Post by aktiwers on 2009-09-27
I found the problem..  it was the "Tab mix plus" extension that had been reset or at least set to remove the close-button. Thanks for all the help :)

---


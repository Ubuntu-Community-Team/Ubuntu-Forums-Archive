---
title: "Firefox 4 Panorama - Doesn't Save Tabs (Really!)"
date: 2011-04-06
forum: The Cafe
---

### Post by Lucradia on 2011-04-06
[U][B][I][SIZE="2"]I did this: [Save Firefox 4 Tab Groups Between Sessions](http://browsers.about.com/od/firef2/ss/Save-Firefox-4-Tab-Groups-Between-Sessions.htm)
Don't bother telling me to do it again.[/SIZE][/I][/B][/U]

Anyway. Normally, if I close tabs, and check the "Don't warn me again" but also click "Save & Quit" firefox would save tabs. As of Firefox 3.6.15+, it would no longer abide by the "Save & Quit" when I check "Don't warn me again." It would always open new tabs, whether or not I pressed "Save & Quit." It does the same thing in Firefox 4, fresh install, try to save and quit with a mess of tabs (including panorama), none are saved. Any ideas why?

---

### Post by CharlesA on 2011-04-06
Yes it was changed. See [here]("http://www.raymond.cc/blog/archives/2011/03/23/enable-save-tabs-on-exit-for-firefox-4/") for how to reenable it in FF4.

---

### Post by Lucradia on 2011-04-06
Doesn't work: [http://www.youtube.com/watch?v=_9WPXZIPi3w](http://www.youtube.com/watch?v=_9WPXZIPi3w)

---

### Post by arzali on 2011-04-06
What have you set on Preferences>Main>Startup ?
If its "open saved session and tabs" Firefox doesn't ask but saves my tabs

---

### Post by Lucradia on 2011-04-06
> **arzali said:**
> Preferences>Main>Startup ?

Firefox 4 doesn't have that in Windows. (Instead, it's Options > General > "When firefox starts:")

Regardless, it says "Show my windows and tabs from last time." But it doesn't save them, regardless.

---

### Post by arzali on 2011-04-06
Sorry im using the german version of firefox :)

What are your privacy setting? Options >Privacy?>History?

If the history is cleared after closing, Firefox cant restore your tabs

If its not this, try makeing  a new profile with
 firefox -P 
and see if it works

---

### Post by Lucradia on 2011-04-06
> **arzali said:**
> Sorry im using the german version of firefox :)

What are your privacy setting? Options >Privacy?>History?

If the history is cleared after closing, Firefox cant restore your tabs

If its not this, try makeing  a new profile with
 firefox -P 
and see if it works

Seriously? That's whY? lol. They should allow tabs to be kept by adding a "Tabs" section to clear history options.

I don't like losing tab,s but I'd rather have everything cleared except cookies, active logins and site prefs.

---

### Post by arzali on 2011-04-06
With these settings, tabs restore works and its keeping cookies, active logins and site prefs but it disables the history.

Sorry that its German but looking at the screen shot should help :)

---


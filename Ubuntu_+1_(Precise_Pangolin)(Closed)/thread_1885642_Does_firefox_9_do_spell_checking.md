---
title: "Does firefox 9 do spell checking?"
date: 2011-11-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mc4man on 2011-11-23
On a new 12.04 install (yesterday), FF  - 9.0~b2+build1-0ubuntu1, seems to be unable to check spelling. Reverting to last FF 8 in PP & it works

---

### Post by robert shearer on 2011-11-23
Tested a moment ago...
input='does do spallchock'
returns='Showing results for does do spell check'

works here...:D

---

### Post by sammiev on 2011-11-23
> **mc4man said:**
> On a new 12.04 install (yesterday), FF  - 9.0~b2+build1-0ubuntu1, seems to be unable to check spelling. Reverting to last FF 8 in PP & it works

Noticed that a few days a go. I checked to see if it was check marked and it was. It dosen't work here.

---

### Post by kansasnoob on 2011-11-23
I noticed a few days ago that I'm not getting spell-checked but I haven't looked into it.

---

### Post by mc4man on 2011-11-23
Went ahead & installed the current PP FF9 version on OO (plus the related debs) & no spell check there either. So it's either the FF9 version ubuntu is using or ubuntu's build of that version

Did [file a bug]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/894085") though i'm sure there'll be a new FF version before too long

---

### Post by kansasnoob on 2011-11-23
> **mc4man said:**
> Went ahead & installed the current PP FF9 version on OO (plus the related debs) & no spell check there either. So it's either the FF9 version ubuntu is using or ubuntu's build of that version

Did [file a bug]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/894085") though i'm sure there'll be a new FF version before too long

I added a "me too" and subscribed.

---

### Post by PaulW2U on 2011-11-24
This is a strange one as the spell checker is working perfectly ........ now.

When I noticed that the spell checker wasn't working I set out to check if I had inadvertently switched it off or not. Everything looked fine except that it wasn't working. I right-clicked in the text field I was using too see what options were there and before I could toggle the spell checking off and back on again I noticed that a misspelled word had become underlined.

I've just noticed that my language was incorrectly set to "English/Australia" when it should have been set to "English/United Kingdom".

This wasn't a new install by the way.

---

### Post by mc4man on 2011-11-24
PaulW2U - 
Just saw the basically the same here - on 11.10 started working a moment ago on LP, I didn't do anything.

On this 12.04 install (fresh daily),  wasn't yet when starting on this reply, then opened lang., which was correct, re-clicked it **twice** & now spell checking works fine.

---

### Post by sammiev on 2011-11-24
When I right clicked in the field then pressed languages, there wasn't anything checked marked. After selecting one the spell checker worked. :)

---

### Post by PaulW2U on 2011-12-24
And now this bug affects Firefox 10.

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/894085](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/894085)

Does spell checking work for everyone else when they first install a new version of Firefox?

---

### Post by Jerriy on 2012-01-02
The spell check function of Ubuntu's Firefox 9 is totally screwed.

Up to now all Firefox upgrades never caused me spell check problem but now it does. I haver two languages installed and despite my selection Firefox reverts and selects another language.

What is wrong with Ubuntu? Why screw up something that was completely OK for YEARS?

---

### Post by sammiev on 2012-01-02
> **Jerriy said:**
> The spell check function of Ubuntu's Firefox 9 is totally screwed.

Up to now all Firefox upgrades never caused me spell check problem but now it does. I haver two languages installed and despite my selection Firefox reverts and selects another language.

What is wrong with Ubuntu? Why screw up something that was completely OK for YEARS?

Select Reply to Thread and right click with your mouse. Check Mark Check Spelling then select Languages and select your language. Close FF and start it backup to find that everything now works. :)

---

### Post by Handssolow on 2012-01-09
Thanks for sammiev, I've now got spellchecker back in FF9 after it has been away for a while.
I was foxed before I found this thread.

---

### Post by sammiev on 2012-01-09
> **Handssolow said:**
> Thanks for sammiev, I've now got spellchecker back in FF9 after it has been away for a while.
I was foxed before I found this thread.

Ran into the same thing when I installed FF9 a ways back. Now I'm on FF10 and so far you will have to do the same thing with it when it rolls around. :) Thanks for reporting back! :)

---

### Post by bitinerant on 2012-01-13
> **sammiev said:**
> When I right clicked in the field then pressed languages, there wasn't anything checked marked. After selecting one the spell checker worked. :)

This fixed mine too--thanks.  (Ubuntu 11.10, FF 9.0.1)

---

### Post by Jerriy on 2012-01-21
> **sammiev said:**
> Select Reply to Thread and right click with your mouse. Check Mark Check Spelling then select Languages and select your language. Close FF and start it backup to find that everything now works. :)No idea what you mean by right click with mouse. I always right click anyway, in order to use spell check. That's not the issue.

---

### Post by Jerriy on 2012-01-21
My entire problem is that the latest version does something that it  never did before it AUTOMATICALLY flips and selects language for me when  I spell check, causing me to flip it back every time I pause typing and  try to spell check!!! That's ludicrous!

Up to now up to this current update, this never happened. Up to now I  was the ONLY one who MANUALLY selected the language and the selected  spell-check language REMAINED the one selection UNTIL I MYSELF selected  another language at another day, time and place. I want that status  back!

The fact is the automatic selection never picks the right language. So I  don't want it, I don't want the auto detection or auto selection or  whatever the hell it is named. 

Clearly as it turned out, only I am capable of knowing in what language I  am typing, the browser guesswork software is a complete failure or none  applicable for my uses and therefore it should never have been the  default and 

I want the previous (manual) default back!

---

### Post by Jerriy on 2012-01-21
Why is my thread declared solved while I never even hinted to any such thing??????

The question that I raised in the OP is **[SIZE=4]NOT SOLVED!!![/SIZE]**

---

### Post by BlinkinCat on 2012-01-21
> **Jerriy said:**
> Why is my thread declared solved while I never said any such thing??????

The question I raised in the OP is **[SIZE=4]NOT SOLVED!!![/SIZE]**

I don't see any post for you before #11 - this is someone-else's thread - :)

---

### Post by Jerriy on 2012-01-21
> **BlinkinCat said:**
> I don't see any post for you before #11 - this is someone-else's thread - :)I specifically opened a thread and was told to go here by the person I am responding to in this thread. 

But I guess now that this thread is unilaterally declared "solved" I suppose the time has arrived to resurrect [my own thread]("http://ubuntuforums.org/showthread.php?t=1903604") that this thread initially had made obsolete :)

---

### Post by mc4man on 2012-01-21
The question posed by this thread "Does firefox 9 do spell checking?" has been answered (YES) , so it's "solved"
The way to restore spellchecking if it's not working has also been answered, so again - "**SOLVED**"

Doe that mean the bug has, no. There is a bug report linked above - go there

---

### Post by forrestcupp on 2012-02-15
Just so you guys know, this is not a bug. Dictionaries from some locales cannot be included anymore because of licensing issues. If you'll notice, the only time this happens is with a clean install. If you upgraded and you have had an older version of Firefox from when it included dictionaries, then those dictionaries carry over, and you wouldn't realize that there is anything different.

You can install [dictionary extensions from here](https://addons.mozilla.org/en-US/firefox/language-tools/) if yours wasn't included.

---

### Post by Handssolow on 2012-02-16
I regularly keep finding that I've lost spell checking and need to right click>languages and select my own version of English, whereupon a red wavy line appears under those words which I've misspelt or are in doubt. I'm not sure how this fits into it being an issue with dictionaries?  I'm on FF 10.0.1 but it was upgraded from an earlier version.

---

### Post by mc4man on 2012-02-16
> **forrestcupp said:**
> Just so you guys know, this is not a bug.
This thread isn't about dictionaires being installed or not. In most cases they are, it's just that no languge is selected

This continues on new installs, may happen on version upgrades & sometimes just happens at some point after a lang. has been selected.

Screen shows from new install I just put in, the one & only available lang. isn't selected so no spell checking till it is

---

### Post by forrestcupp on 2012-02-17
> **mc4man said:**
> This thread isn't about dictionaires being installed or not. In most cases they are, it's just that no languge is selected

Yeah, I guess you're right. I got my information from another source that said I need to install the dictionary. Now that I have, when I right click, I actually have two "English/United States" dictionaries. I guess it just wasn't selected.

---

### Post by mc4man on 2012-02-17
> **forrestcupp said:**
> Now that I have, when I right click, I actually have two "English/United States" dictionaries. I guess it just wasn't selected.
The whole deal is a bit inconsistent. The one thing for sure is that on new installs spell checking will be enabled but a lang. will not be selected

Unfortunately that's not completly obvious to the user, a cursory check will show spell checking enabled but it just won't be working  

As far as upgrades, sometimes the setting holds, sometimes it doesn't

ongoing? bug
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/894085](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/894085)

---


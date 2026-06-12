---
title: "Help!! Ubuntu virus??"
date: 2011-08-29
forum: Security
---

### Post by rvgsd on 2011-08-29
Hi, 
I have Ubuntu 10.10 32 bit installed on a 64bit machine. It was running fine since the last 5/6 months. I have installed the Stable Firefox ppa, and have Firefox 6 installed. 

Like an hour back, when I opened my firefox, this page opened as the home page:

_hxxpx://www.wizard101.com/wizardcreator?utm_campaign=disp_CxDigital&utm_content=160x600world&utm_medium=display&utm_source=CxDigital.9830-_

(NOTE: I have made it hxxpx instead of https, just in case, so that no one else gets infected!)

When I check in the preferences, and see the home page, it shows 'Mozilla Start Page'. 
When I click on the home button, it directs me to the correct page. However whenever I restart firefox, the first page that opens is the Wizard101 page. 

As far as I remember, I did not open any crappy websites.

Any suggestions??? Help!!

---

### Post by CatKiller on 2011-08-29
Clear your cache.

---

### Post by Isaacgallegos on 2011-08-29
So if we go to that domain, with the https corrected, we'll also get "infected"? 

Hmm... I almost want to open that link. 

Can an admin verify this?

---

### Post by rvgsd on 2011-08-29
> **CatKiller said:**
> Clear your cache.

Clearing the cache did the trick.. so what is it? virus? I have never ever opened that website, so how did get in there? Is my ubuntu installation still secure and safe to use??
Any help would be appreciated.!

---

### Post by lkjoel on 2011-08-29
I checked the source code, and it looks OK.
Also, [http://www.mywot.com/en/scorecard/wizard101.com](http://www.mywot.com/en/scorecard/wizard101.com)

Did you ever go to that website?

For the geeks who want to check the source code of this website:
```
wget "https://www.wizard101.com/wizardcreator?utm_campaign=disp_CxDigital&utm_cont ent=160x600world&utm_medium=display&utm_source=CxD igital.9830-"

```

---

### Post by rvgsd on 2011-08-29
> **lkjoel said:**
> I checked the source code, and it looks OK.
Also, [http://www.mywot.com/en/scorecard/wizard101.com](http://www.mywot.com/en/scorecard/wizard101.com)

Did you ever go to that website?

For the geeks who want to check the source code of this website:
```
wget "https://www.wizard101.com/wizardcreator?utm_campaign=disp_CxDigital&utm_cont ent=160x600world&utm_medium=display&utm_source=CxD igital.9830-"

```

I am pretty sure that I did not visit that website.. and I had almost forgotten those days when I used window$..

---

### Post by CatKiller on 2011-08-29
Not a virus. Just someone being scummy. "CX Digital," I guess, from the URL you posted.

You don't need to visit the site yourself. It could have been any compromised site, or a banner ad, or anything really.

It's not likely to have been able to do anything else. Certainly nothing outside your Home folder.

---

### Post by rvgsd on 2011-08-29
> **CatKiller said:**
> Not a virus. Just someone being scummy. "CX Digital," I guess, from the URL you posted.

You don't need to visit the site yourself. It could have been any compromised site, or a banner ad, or anything really.

It's not likely to have been able to do anything else. Certainly nothing outside your Home folder.

Thanks for the help guys.. as expected of the Ubuntu Community.! I guess I can then again store passwords in Firefox as well..

---

### Post by lkjoel on 2011-08-29
Could you mark this thread as solved? (Thread tools->Mark this thead as solved)

---

### Post by rvgsd on 2011-09-04
Ok, the same wizard101 page started doing the same thing again (the url exactly as in the first post), and clearing the cache did work again.
The tabs I had open in firefox were: 
1) web.im(yahoo web messenger)
2) [www.tumblr.com/login](www.tumblr.com/login)
Furthermore, my firefox was open in 'Private Browsing' mode.

In short, for sure nothing suspicious was open. This worries me.. should I reinstall?? Any help would be appreciated.

---

### Post by CatKiller on 2011-09-04
Reinstalling won't help. It doesn't have to be a site that you have open at the time that's causing problems. Such things often have a delay on the payload. Practise sceptical computing. Extensions like NoScript are useful.

---

### Post by lkjoel on 2011-09-04
What applications did you install that were not from the Ubuntu Software Center?

---

### Post by ubun2geek on 2011-09-05
> **rvgsd said:**
> Clearing the cache did the trick.. so what is it? virus? I have never ever opened that website, so how did get in there? Is my ubuntu installation still secure and safe to use??
Any help would be appreciated.!

You probably played a game by them. This happened to me.

---

### Post by cariboo on 2011-09-06
Have you tried creating a new Firefox profile?

```
firefox -Profilemanager
```

---

### Post by rvgsd on 2011-09-06
Thanks for the suggestions. 
I only have known software like google chrome, etc that I have installed from outside Ubuntu repositories. 
I have installed AdBlock plus now, and blocked that site. I'll also install no-script. 
I'll mark this problem as solved, and let you guys know if anything else comes up!

---


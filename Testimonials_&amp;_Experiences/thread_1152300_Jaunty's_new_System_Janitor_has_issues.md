---
title: "Jaunty's new System Janitor has issues"
date: 2009-05-07
forum: Testimonials &amp; Experiences
---

### Post by okubax on 2009-05-07
Been using Ubuntu now for about 3+yrs and recently upgraded to Jaunty and things have been going quite well until now when I just tried to use the all new system junk cleaner "Janitor". Started it and it went on for about 5mins and me thinking that it was cleaning up my pc until when it finished that I saw that it had completely wiped out all of my manual installations i.e VirtualBox, Adobe AIR, Adobe Reader, Codeweaver's Crossover, Xiphos....just too name a few. wtf is wrong with it :confused:, treating manual installs as junk ?. I have never commented on anything going wrong with my Ubuntu system before but including "System Janitor" in Jaunty is a BIG mistake.
I should have been content with just using BleachBit !

---

### Post by cariboo on 2009-05-07
I hate to say it, but it looks like you didn't pay to much attention to what the app was doing, have a look at the screenshot, notice where it says remove/fix? To me if there is a check mark beside an item in that column it would be removed or fixed. Personally I won't use Computer Janitor, as I find:

```
apt-get clean
```

and

```
apt-get autoremove
```

more to my liking.

---

### Post by mkvnmtr on 2009-05-07
Computer Janitor was not the first thing I removed from my new 9.04 systems but it wasn't last othe list either.

---

### Post by juancarlospaco on 2009-05-07
Janitor is a frontend to **sudo apt-get clean ; sudo apt-get autoremove**,
so new users dont have to use CLI to do it...

Bleachbit is good too, 
i help Ziem*(author)* making some cleaners, it uses .xml references to clean.

---

### Post by binbash on 2009-05-09
for cleaning BleachBit is better

---

### Post by ajackson on 2009-05-09
The moral of this story is **think**. The Janitor highlights installed debs that it can no longer find in the available repositories. Debs installed by another route will probably show, so you check the list and remove those that are incorrect rather than blindly just let it do it's thing.

---

### Post by olskar on 2009-05-09
> **ajackson said:**
> The moral of this story is **think**. The Janitor highlights installed debs that it can no longer find in the available repositories. Debs installed by another route will probably show, so you check the list and remove those that are incorrect rather than blindly just let it do it's thing.

The moral of this story is; do not include Janitor if it treats installed packages as cruft. That is plain wrong. The developer is working to fix this but in the meantime it should not be included.

---

### Post by juancarlospaco on 2009-05-10
> **olskar said:**
> The moral of this story is; do not include Janitor if it treats installed packages as cruft. That is plain wrong. The developer is working to fix this but in the meantime it should not be included.

Yeah, erase Computer Janitor, and then you got a lot of newbies posting...
*" I have to use CLI to make sudo apt-get clean ; sudo apt-get autoremove just like MS D.O.S. on 1980 "*

:(

---

### Post by doas777 on 2009-05-10
perhaps it would be best to not select third party packages by default. at the same time, when something is telling me it wants to remove truecrypt, I've been known to say 'No! I use that!'. 

so yes, concensus reached. os needs to be intutive and respectful, and user needs to take some responsibility as well. and Guis are good (unless they aren't).

---


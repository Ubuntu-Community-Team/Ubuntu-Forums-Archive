---
title: "Raspberry Pi as daily driver ?"
date: 2017-04-26
forum: Ubuntu/Debian BASED
---

### Post by linuxyogi on 2017-04-26
Hi,
I am using a Raspberry Pi 2 B+ as my main PC. The only problem is that I cant watch Youtube videos on any browser. Other than that its working good. Anyone here using Pi as their main computer ?

---

### Post by Bucky Ball on 2017-04-26
(Install Kodi and the Youtube addon. ;))

No, as I have a number of other computers, but I don't see any reason why you couldn't, depending on your requirements. If it does what you want it to, then yes, Raspberry Pi can be used as your main computer. If not, no.

I did have it setup awhile ago with Lubuntu and that was also working fine, but due to my requirements, wouldn't use as a main computer. I never tried Youtube on it, but is was mostly used for Kodi and watching catch-up TV using the addons and I used the Youtube addon in Kodi. Now have OpenElec installed which is basically a Kodi OS and boots directly to Kodi, no Ubuntu desktop.

Only ever really used the RPi as a media centre.

---

### Post by linuxyogi on 2017-04-27
I have installed youtube addon on Kodi but it prints some &#8220;Quota Exceeded" error.

---

### Post by Bucky Ball on 2017-04-27
Yea, known bug that never used to be there, but seems to pop up in recent versions. Same happened to me. Easy to fix. 

I can't remember exactly what I did, but you should [find some clues here]("https://duckduckgo.com/?q=kodi+quota+exceeded&t=h_&ia=web"). I do remember it took me less than a minute to make the change and worked first time. I'll have a look a bit later and see if I can find which method I used, but from memory I tweaked a number on a line in a file! :)

Vague, but you'll find more clues on those links. ;)

---

### Post by linuxyogi on 2017-04-27
> **Bucky Ball said:**
>  I tweaked a number on a line in a file! :) 

I searched but didn't find anything useful. Please have a look and tell me which file to edit and what to modify.

@Bucky Ball

Any ideas ?

Fixed it. 
RIght click on Youtube plugin > Settings > API> Use API Key .....Change from 1 to 4

---

### Post by Bucky Ball on 2017-04-28
Correct. You also want to change the cache size there from (probably) 5 to 20. See this vid from about 1:47. 

Glad you worked it out. Well done.

---

### Post by QIII on 2017-04-28
Are you running Raspbian on your Pi?

---

### Post by linuxyogi on 2017-04-28
> **Bucky Ball said:**
> Correct. You also want to change the cache size there from (probably) 5 to 20. See this vid from about 1:47. 

Glad you worked it out. Well done.

Which vid ?

> **QIII said:**
> Are you running Raspbian on your Pi?

Yes

---

### Post by QIII on 2017-04-28
Moved to Ubuntu/Debian BASED.

This really turned out to be a support issue rather than something for the Cafe.

Cheers!

---

### Post by Bucky Ball on 2017-04-29
> **linuxyogi said:**
> Which vid ?

Sorry. Was 5am about. [This video]("https://www.youtube.com/watch?v=WB85WkiM8P0").

---


---
title: "What about the persistent Flash problem?"
date: 2010-01-28
forum: The Cafe
---

### Post by arnab_das on 2010-01-28
Us Ubuntu users have been facing problems with our linux version of flash forever! The screen keeps flickering all the time, so much so that a perfectly awesome Adobe air app called uvlayer becomes utterly unusable. (try it out for yourself if you dont believe me)

is there any way to resolve this issue? this issue has been there forever!

---

### Post by NoaHall on 2010-01-28
It works for me, better than in Windows.. I wish people would stop making these threads.

---

### Post by Grenage on 2010-01-28
Some people have issues, some don't. _Most_ can be fixed by manually installing the latest flash file from Adobe.

---

### Post by arnab_das on 2010-01-28
> **NoaHall said:**
> It works for me, better than in Windows.. I wish people would stop making these threads.

i strongly urge you to try out adobe air apps before criticising users. just because u dont have a problem doesnt mean no one else has it! just search this forum for the flash problem related threads! they'll be in thousands!

---

### Post by Xbehave on 2010-01-28
It looks like you are on 64bit, are you running the latest 64built from adobe?

Also, what drivers are you running i had problem with flgrx, so i'd look into tweaking them/dropping them for radeon drivers if you don't need 3d.

Due to the closed nature of flash, it is hard for ubuntu todo what you want, i wish it wasn't as bad as it is, but there isn't much ubuntu devs can change.

---

### Post by arnab_das on 2010-01-28
> **Xbehave said:**
> It looks like you are on 64bit, are you running the latest 64built from adobe?

Also, what drivers are you running i had problem with flgrx, so i'd look into tweaking them/dropping them for radeon drivers if you don't need 3d.

Due to the closed nature of flash, it is hard for ubuntu todo what you want, i wish it wasn't as bad as it is, but there isn't much ubuntu devs can change.

yup am having a 64 bit version of ubuntu. i installed flash as directed here: [http://kb2.adobe.com/cps/408/kb408084.html](http://kb2.adobe.com/cps/408/kb408084.html)

---

### Post by NoaHall on 2010-01-28
> **arnab_das said:**
> i strongly urge you to try out adobe air apps before criticising users. just because u dont have a problem doesnt mean no one else has it! just search this forum for the flash problem related threads! they'll be in thousands!

Who cares? Just because they have, doesn't mean those who are at least capable do.

---

### Post by realzippy on 2010-01-28
...strange.Since edgy (yes,also 64bit) my flash used to run fine...
due to NVIDIA?

---

### Post by K.Mandla on 2010-01-28
> **arnab_das said:**
> Us Ubuntu users have been facing problems with our linux version of flash forever! The screen keeps flickering all the time, so much so that a perfectly awesome Adobe air app called uvlayer becomes utterly unusable. (try it out for yourself if you dont believe me)

is there any way to resolve this issue? this issue has been there forever!
It seems to me that directing your question to Adobe, instead of an off-topic area of a Linux forum, might be a better plan of action.

---

### Post by Xbehave on 2010-01-28
> **arnab_das said:**
> yup am having a 64 bit version of ubuntu. i installed flash as directed here: [http://kb2.adobe.com/cps/408/kb408084.html](http://kb2.adobe.com/cps/408/kb408084.html)
I was talking about [this]("http://labs.adobe.com/technologies/flashplayer10/64bit.html"), unfortunately it looks like it's just flash not AIR, but try it anyway as it **may** solve your problem.

---

### Post by pwnst*r on 2010-01-28
> **arnab_das said:**
> i strongly urge you to try out adobe air apps before criticising users. just because u dont have a problem doesnt mean no one else has it! just search this forum for the flash problem related threads! they'll be in thousands!

**Thousands**

What I love about some of this community is the lack of exaggeration injected into every other sentence by posters such as yourself!

---

### Post by Xbehave on 2010-01-28
> **realzippy said:**
> ...strange.Since edgy (yes,also 64bit) my flash used to run fine...
due to NVIDIA?
There is a lot of driver/flash interaction, so it's possible nvida workaround flash issues/fix bugs that cause them.

---

### Post by arnab_das on 2010-01-28
> **pwnst*r said:**
> **Thousands**

What I love about some of this community is the lack of exaggeration injected into every other sentence by posters such as yourself!

plz dont make this personal.

---

### Post by llawwehttam on 2010-01-28
Lol I'm running adobe flash plugin 10.1 alpha 64 bit and its really stable for me. I also am using the nvidia drivers.

ALSO: guys please read the forum rules and stop acting like kids. Sure ask for help and help others but don't criticize software or other people.

**Be respectful of all users at all times. This means please use  etiquette and politeness. Treat people with kindness and gentleness. If  you do this the rest of the code of conduct won't need more than a  cursory mention.**

[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

---

### Post by arnab_das on 2010-01-28
> **Xbehave said:**
> I was talking about [this]("http://labs.adobe.com/technologies/flashplayer10/64bit.html"), unfortunately it looks like it's just flash not AIR, but try it anyway as it **may** solve your problem.

ah thanks mate. now i just detected my flash version here: [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) and it says 10,0,42,34 installed.

but how do i know if this is the 32 bit or the 64 bit?

---

### Post by arnab_das on 2010-01-28
okay i installed flash as directed here: [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

again, i'm not sure if i'm using the 64 bit version yet, coz the adobe page simply tells me the version. but it doesnt have any info on whether its 32 bit or 64 bit.

---

### Post by Xbehave on 2010-01-28
> **arnab_das said:**
> okay i installed flash as directed here: [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

again, i'm not sure if i'm using the 64 bit version yet, coz the adobe page simply tells me the version. but it doesnt have any info on whether its 32 bit or 64 bit.
Well the 32bit version needs to use a plugin wrapper so if you run pgrep wrapper -l while flash is running something like pluginwraper should show up

---

### Post by arnab_das on 2010-01-28
> **Xbehave said:**
> Well the 32bit version needs to use a plugin wrapper so if you run pgrep wrapper -l while flash is running something like pluginwraper should show up

:( doesnt show anything actually. i type "pgrep wrapper -l" and then there's nothing but $ prompt. could u help me out?

---

### Post by Xbehave on 2010-01-28
> **arnab_das said:**
> :( doesnt show anything actually. i type "pgrep wrapper -l" and then there's nothing but $ prompt. could u help me out?
That is a good sign, it means you probably have 64bit flash working.

---

### Post by arnab_das on 2010-01-28
okey dokey. thanks mate.

---


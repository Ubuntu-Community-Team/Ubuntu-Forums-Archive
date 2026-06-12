---
title: "google linux apps not a high priority?"
date: 2009-09-22
forum: The Cafe
---

### Post by northwestuntu on 2009-09-22
why is it that linux is going to release a OS based on linux, but they have a browser like chrome and windows gets the 1st release and then linux to follow .  same with picasa.  3.5 is out for windows and not for linux.  not to mention picasa uses wine.  i know windows has a lot more users, but since there creating a whole Os on linux.  shouldn't the google linux apps be a bigger priority?

---

### Post by phrostbyte on 2009-09-22
No doubt, Google and Microsoft hate each other. Although it might not be their main priority I think Google wants to see Linux succeed as a desktop. 

But more people use Windows. It simply makes more business sense to target Windows first, because there is a bigger impact there. That's just how it is. ](*,) Plus unless you think about it beforehand porting something to Linux from Windows is often a complete rewrite. This costs millions of dollars.

--------
Edit: I give Picasa 3.5 a go in Wine, and it seems to work fine. This is by design, Google intentionally makes Picasa work well in Wine. The "native" port of Picasa is anyways compiled against Wine.

---

### Post by SomeGuyDude on 2009-09-22
I don't buy the "well it's difficult to port a browser" excuse. Opera and Firefox have done just fine with that, amongst others. And it's not like browsers are the most complicated pieces of software anyway. If we can get those along with media players and big ol' disc burning suites, surely a native Chrome port can come along.

But that's Google's MO, it seems. They haven't given us ANY native Linux apps. Not Chrome, not Picasa, not Earth. Desktop? Forget about it.

---

### Post by phrostbyte on 2009-09-22
> **SomeGuyDude said:**
> I don't buy the "well it's difficult to port a browser" excuse. Opera and Firefox have done just fine with that, amongst others. And it's not like browsers are the most complicated pieces of software anyway. If we can get those along with media players and big ol' disc burning suites, surely a native Chrome port can come along.

But that's Google's MO, it seems. They haven't given us ANY native Linux apps. Not Chrome, not Picasa, not Earth. Desktop? Forget about it.

Yeah it's hard because they use WinAPI to build Chrome. Firefox was designed with a crossplatform architecture from the start.

Portability is 100% based on what tools you use. If you using C++ against Qt, VERY EASY. If you are using VBScript against Win32 COM, VERY HARD. :)

Also I don't think you are correct that Google Earth is non-native. [It uses Qt.]("http://www.kdedevelopers.org/node/2098")

In theory, Linux Picasa is native also, because it is an ELF binary compiled against Winelib using the GNU toolchain. Winelib is a native Linux library that provides Windows compatible graphics, it's not the same Wine which loads .EXE files (the is no need for a PE loader). It's not different then compiling against Qt in a way.

---

### Post by Dimitriid on 2009-09-23
> **SomeGuyDude said:**
> Opera and Firefox have done just fine with that, amongst others.

I wouldn't go as far, im still profoundly disappointed with Firefox in Linux.

---

### Post by northwestuntu on 2009-09-23
maybe we will see a change once chrome os is here.  i have to believe they will install apps like chrome browser and picasa by default in there os.  

will be interesting to see.

---

### Post by MJWitter on 2009-09-23
I guess none of you are using Chromium on Linux? Isn't it native? 32 and 64 bit?

---

### Post by NCLI on 2009-09-23
I think it is, don't know any way to make sure though.

I'm not worried about this, I'm sure their focus will shift towards Linux when they release Chrome OS.

---

### Post by Exodist on 2009-09-23
> **Dimitriid said:**
> I wouldn't go as far, im still profoundly disappointed with Firefox in Linux.

Yea its predecessors seemed to actually run better. At least Mozilla did back in the day.

---

### Post by Paqman on 2009-09-23
Google is a big company, apps and Chrome OS/Android are developed separately from each other. There would only really need to be any kind of unified management overlook if they were projects that were likely to affect each other. Android has it's own ecosystem of apps that are unrelated to anything else. 

Chrome/Chromium almost definitely is getting some extra resources due to Chrome OS, development is moving forward really fast. I use it as my main browser now.

I'd say Linux is massive at Google, but that doesn't mean they're going to ignore the dominant OS most of their customers are using. Shipping Chrome for Windows helps it build market share faster, and acts as a springboard for Chrome OS when it reaches the market.

---

### Post by northwestuntu on 2009-09-23
> **MJWitter said:**
> I guess none of you are using Chromium on Linux? Isn't it native? 32 and 64 bit?

yes i have chromium as my 2nd browser and very pleased with the speed of it compared to firefox.  just waiting for some more extensions to come out for it.  they done great in the little time they have been working on it.

firefox seems to be going downhill with every release?

---


---
title: "i heard some ubuntu news that i think might be misinformation."
date: 2006-12-06
forum: The Cafe
---

### Post by graigsmith on 2006-12-06
i heard that ubuntu was going to start including proprietary video drivers as default?  i know it's not default in the current one.  And i doubt they would ever do it.  i read this on slashdot, from someones comments.  so I'm sure it's just that person just making up stuff.  But i was just curious if anyone else heard anything about including the video drivers by default?  

Personally i am content with the open source drivers for my ati 9200.

---

### Post by wieman01 on 2006-12-06
Isn't that the plan for Feisty Fawn? Have also heard something along these lines...

---

### Post by aysiu on 2006-12-06
Read this:
[http://www.markshuttleworth.com/archives/84](http://www.markshuttleworth.com/archives/84)

---

### Post by darkninja on 2006-12-06
> **aysiu said:**
> Read this:
[http://www.markshuttleworth.com/archives/84](http://www.markshuttleworth.com/archives/84)

From what I understand:

Wireless drivers w/ binary blob firmware: Yes, as they have always been.
Nvidia/ATi proprietary drivers: Rather unlikely. (I guess, Shuttleworth's answer was rather vague)
Flash: No.
Java: Maybe.
Proprietary codecs: No.

Installation of non-free stuff should be made a bit easier then it is now.

---

### Post by ago on 2006-12-06
I think that a better alternative would have been to activate acceleratedX by default if it can be done with FOSS drivers, otherwise have a shortcut on the desktop that reads something like "Activate 3D desktop", which when pressed explains why the 3D desktop is not enabled by default, why closed drivers are bad, invites not to purchase hardware from manufacturers that do not have a friendly attitude, and then if the user wants to proceed, it installs the closed drivers and enables acceleratedX. This would address the issue of pre-installing closed drivers, while moving acceleratedX only 1 click away (for some users).

---

### Post by rubinstein on 2006-12-06
Read this: [https://wiki.ubuntu.com/AcceleratedX](https://wiki.ubuntu.com/AcceleratedX) and the comments at [https://wiki.ubuntu.com/AcceleratedX/Comments](https://wiki.ubuntu.com/AcceleratedX/Comments)

This is the intended specification.

---

### Post by Sef on 2006-12-06
> Java: Maybe.

Java is being released under the GPL, so soon there will be no problem with it at all.

---

### Post by darkninja on 2006-12-06
> **Sef said:**
> Java is being released under the GPL, so soon there will be no problem with it at all.

I thought that some parts still had yet to GPLed. Obviously not.

---

### Post by prizrak on 2006-12-06
> **darkninja said:**
> I thought that some parts still had yet to GPLed. Obviously not.
It's not completely GPL'ed as of yet but by the time Feisty comes it will be :)

---

### Post by RChickenMan on 2006-12-06
I think that proprietary software should be included as an option, i.e. during the install, a dialog box would come up and give a brief overview of what the drivers are, the ethics behind it, and ask the user whether or not they would like to install them.  I think we all agree that Linux is about freedom--the discussion here is whether we consider freedom of choice, or freedom from proprietary software to be more fundamental.  My opinion is that the user already has the freedom to decide to install proprietary software by enabling extra repositories.  Therefor, simply making it easier would attract more users to the platform while maintaining the same ethical standards.

---

### Post by ago on 2006-12-06
The discussion so far, including Mark's posts, seem to be focused on a black or white choice to whether to enable hardware or not enable hardware using closed drivers if necessary out of the box. It makes it look like if you do not enable the hardware by default, you are doomed to use a crippled machine forever and that in turns makes the market appeal go down the drain.

But this is deceiving. The alternative is not black or white. 

The real question is whether it is desirable to have the user take ONE MORE VERY SIMPLE STEP to "enable" hardware that requires closed drivers. This allows us to inform him about closed driver EX-ANTE and give him the option to use free alternatives even if less capable. It can be implemented in several ways (shortcut on the desktop, extra step in the installation wizard...). 

All this mess is because people (including Mark) want warnings ex-post as opposed to ex-ante. I think they made the wrong decision here. I am firmly in the ex-ante camp and I really fail to see how pre-installing vs easy-installing makes such a huge difference in terms of market appeal to justify compromising on freedom.

---

### Post by zetetic on 2006-12-16
ago: very well said.

You are right. This means that there are hidden reasons why binary drivers will be shipped by default...
People should think about this...

zetetic

---


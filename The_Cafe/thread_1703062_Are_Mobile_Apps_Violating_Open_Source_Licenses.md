---
title: "Are Mobile Apps Violating Open Source Licenses?"
date: 2011-03-08
forum: The Cafe
---

### Post by WinterMadness on 2011-03-08
Yep.

Check it out
[http://www.linuxplanet.com/linuxplanet/newss/7315/1/](http://www.linuxplanet.com/linuxplanet/newss/7315/1/)

There are a lot of mobile apps that use open source software, but how many of them are in compliance with open source licensing rules? As it turns out, not very many.

A new study from open source services vendor OpenLogic reports that 71 percent of Apple iOS and Google Android apps are not in compliance. OpenLogic scanned 635 apps, including both free and paid on the Apple App store and Google Android Marketplace. Of those 635 scanned apps, 52 apps include Apache licensed code while 16 included GPL/LGPL licensed code.

Both the GPL/LGPL and the Apache open source licenses require developers to provide copies of the licenses. With the GPL/LGPL the license also requires that developers provide a means by which users can get the source code. OpenLogic has a scanning tool called, OSS Deep Discovery, which helps to identify when open source code is being used.

"The lack of compliance was not all that surprising to us," Kim Weins, senior vp of products and marketing at OpenLogic, told InternetNews.com. "Developers and companies often don't have a complete picture of their open source usage or how to comply with the licenses."

Wiens added that with mobile apps, there is an influx of non-technology companies who have now become software distributors. These companies may not have experience with the legal and licenses issues around open source compliance.

Adding further insult to injury, OpenLogic's study found several apps that appeared to write their EULAs with no awareness that their app contained open source.

"It is possible that the developers were aware of it, but the lawyers that drafted the EULAs were not," Weins said. "This is very common in companies that we work with -- often no one in the company has a complete picture of the open source being used."

She added that happens because the companies often don't have the right processes and tools in place, or because they aren't even aware that it's an issue.

"In addition, the nature of open source software, which often bundles other open source software under completely different licenses, means that even developers can miss some of the licenses for open source they are including in their code," Weins said.

App stores all have some kind of evaluation process before an app is accepted. Weins noted that the app stores should take a lead in help in to facilitate awareness of open source compliance among the developers.

"Although the developer agreement for an app store will discuss IP issues and may even reference open source code, there is very little information to help developers understand what the issues are and how to follow the rules," Weins said. "In addition, when an open source compliance issue is raised, it is likely to result in a takedown request for the app."

OpenLogic sells a product called the OLEX App Store Edition which provides tooling that can be used by developers to do a self-service scan on their apps prior to submitting to the app store and by app stores to track open source compliance.

Overall the goal of OpenLogic's study on open source license compliance for mobile apps is about raising awareness.

"We will not be reporting or sharing any names of companies or apps that failed to comply," Weins said. "We will attempt to reach out to those companies and inform them, so that they can remediate the situation and come into compliance." 

opinions?

---

### Post by Dr. C on 2011-03-08
The 71 % copyright infringement (piracy) figure is clearly wrong. Based on the results we have the following piracy rates:

Apache:  52/635 or 8.2 %
LGPL/GPL: 16/635 or 2.5 %

The app stores do need to take a lead on this and the first place to start is with the TOS for the stores itself 

Apple is among worst offenders with respect to the GPL and other copyleft licenses. They need to either amend their TOS to be compatible with the GPL and other copyleft licenses like Google (Android) or ban the GPL and other copyleft licenses from the store like Microsoft (Windows Phone 7).

As for the Free and Open Source communities, starting with the FSF, they need to stop playing Mr. Nice Guy, and start taking large corporate copyright infringers to court and demand statutory damages under US law. In addition they need to use tools such as the DMCA, even if it means shutting down a popular app store. This is especially the case after the corporate infringer has been approached in good faith with unsatisfactory results.

---

### Post by Lucradia on 2011-03-08
And since Flash isn't LGPL, Apple doesn't allow it :P

---

### Post by KiwiNZ on 2011-03-08
These are  alleged violations not proven violations.

---

### Post by Dustin2128 on 2011-03-08
Well, my guess is that the major problems would be app store restrictions on distribution of source (probably not so much) and/or ignorant/uncaring developers that may think FOSS licenses are all permissive or just don't care.

---

### Post by jwbrase on 2011-03-09
> **Dr. C said:**
> The 71 % copyright infringement (piracy) figure is clearly wrong. Based on the results we have the following piracy rates:

Apache:  52/635 or 8.2 %
LGPL/GPL: 16/635 or 2.5 %

Apache, LGPL, and GPL are not the only Open Source licenses that exist. There's BSD, X11, MIT, zlib, etc.

> 
The app stores do need to take a lead on this and the first place to start is with the TOS for the stores itself 

Apple is among worst offenders with respect to the GPL and other copyleft licenses. They need to either amend their TOS to be compatible with the GPL and other copyleft licenses like Google (Android) or ban the GPL and other copyleft licenses from the store like Microsoft (Windows Phone 7).

I don't think openly GPL'ed code can make it into the Apple App Store. The problem is when developers snag GPL'ed code, integrate it into their product, and put it into the App Store under the App Store TOS. Apple isn't at fault here, rather the developer. (Whether Apple is fostering an evironment in which developers are likely to do this by using TOS that are incompatible with the GPL is a whole different question)

> 
As for the Free and Open Source communities, starting with the FSF, they need to stop playing Mr. Nice Guy, and start taking large corporate copyright infringers to court and demand statutory damages under US law.

The FSF can do that if it's determined that FOSS code that the FSF holds copyright to is being infringed upon, but the FSF isn't the only organization that releases code under FOSS licenses, and some organizations (or individuals) that hold copyright to FOSS code just don't have the money to take a corporation to court.

Which isn't to say that we shouldn't make what noise we can about such violations when they turn up.

---


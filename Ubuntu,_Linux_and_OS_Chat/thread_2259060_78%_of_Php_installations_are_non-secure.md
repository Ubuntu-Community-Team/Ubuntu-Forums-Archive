---
title: "78% of Php installations are non-secure?"
date: 2015-01-01
forum: Ubuntu, Linux and OS Chat
---

### Post by TheFu on 2015-01-01
78% of Php installations are non-secure?  Do you believe it?   
[http://blog.ircmaxell.com/2014/12/php-install-statistics.html](http://blog.ircmaxell.com/2014/12/php-install-statistics.html)

If so, why deploy any php applications on the internet? Aren't the risks simply too high for conscientious developers when there are other languages which have a much higher chance to be secure?

---

### Post by Irihapeti on 2015-01-01
What do you propose we do instead? Learn Perl?

---

### Post by TheFu on 2015-01-01
No.  I don't need the competition. ;)

However, it appears that many people deploying php don't maintain it properly.  THAT is the real issue.  
How to get the word out to the same level that running wordpress has gotten out? ** Maintain your Php Apps, please.**  Keep them patched. Demand the core language writers and plugins be maintained.

---

### Post by SeijiSensei on 2015-01-01
His analysis misses the fact that many distributions do not update software to new versions when they are released.  Instead the distro maintainers will "back-port" security patches from later versions into the current version.  On Ubuntu, the releases with "long-term support" use this method to fix security issues.  So does RedHat.  Just looking at version numbers is misleading.  You'd actually need to look at the various reports at places like [CERT](http://www.cert.org/vulnerability-analysis/).

Moreover most serious vulnerabilities have less to do with a language like PHP than with poor coding on the part of developers.  I've written PHP applications for nearly twenty years now.  My early efforts were pretty insecure, but nowadays I'm much more careful and stringent about how I create sites.

---

### Post by Doug S on 2015-01-01
> **SeijiSensei said:**
> His analysis misses the fact that many distributions do not update software to new versions when they is released.  Instead the distro maintainers will "back-port" security patches from later versions into the current version.  On Ubuntu, the releases with "long-term support" use this method to fix security issues.  So does RedHat.  Just looking at version numbers is misleading.Hi Seiji,
The way I read the article (which was more of a skim, really), it was taking back-porting into account. I also checked the two up to date servers I have turned on right now, a 12.04.5 and a 14.04.1, and they are O.K., according to the article.

---

### Post by bashiergui on 2015-01-01
> If so, why deploy any php applications on the internet? Aren't the risks simply too high for conscientious developers when there are other languages which have a much higher chance to be secure?Your questions are valid. But they assume that everyone considers security at all during a deployment. I will be permanently employed in security because not everyone does. Many choose apps and platforms based on simplicity, usability, or something they're familiar with. (Actual quote: "I use telnet over the internet because I already know how")

Here's an interesting discussion on the topic of php insecurity
[http://security.stackexchange.com/questions/643/why-do-people-say-that-php-is-inherently-insecure](http://security.stackexchange.com/questions/643/why-do-people-say-that-php-is-inherently-insecure)

The reasons stated in that link seem plausible: php has a low barrier of entry, so it's easy to get a site up and running without understanding all the security risks. Compare that to python and perl which need more prerequisite knowledge.

The security world has known that php sites get pwned a lot. I like having statistics behind that presumption now, although I didn't know it was that bad. I imagine this will go the way of Java: it was easy to make it terribly insecure, which made it a great target for bad guys. Java suffered epic and ultimately laughable pwnage until Oracle improved security patching and browsers began sandboxing and disabling it by default. In this analogy, I think we're still going to see epic php pwnage for a while (It's not quite laughable yet) until something is changed to make default php apps a bit more secure. I wish I had creativity enough to know what that would be.> Maintain your Php Apps, please. Keep them patched. Demand the core language writers and plugins be maintained.Excellent advice, and really the only advise we can give currently. Sadly history has proven that few will heed the advise, and we must make the default version/ deployment secure.

---

### Post by Sef on 2015-01-01
Moved to Ubuntu, Linux, and OS chat.

---


---
title: "Software Development without the Internet"
date: 2012-09-13
forum: The Cafe
---

### Post by c0deblue on 2012-09-13
Consider, for security reasons, that you want to develop software on a machine that is not connected to the internet. This does not exclude ever having been connected to the internet or the lack of a nearby machine connected to the internet (although the latter may not be guaranteed). How would you prepare for the situation and continue working under this restriction? How, also, would you maintain physical security of the machine and also avoid removeable media security issues?

To further seed this discussion, what specific websites, documentation, software, and libraries would you download prior to going offline?

Thank you (and I apologize if this seems counter to the open source way. I don't necessarily want to exclude releasing the source, but rather want to ensure security of the machine as I/we develop).

---

### Post by vexorian on 2012-09-14
> Consider, for security reasons, I am not very sure about this...

> How would you prepare for the situation and continue working under this restriction? In ubuntu, lack of packages you might need is going to kill you. But I guess that if you installed all dev packages possible then the next issue would be documentation.

You would need to use a development environment that really has a lot of documentation. For the language you are using and for the libraries. And it should have a search feature that is local.

Regarding specifics. I can't really tell you because you have not mentioned what languages and libraries you intend to use. I myself would probably download the whole sgi STL documentation. The whole SDL documentation and would mirror cplusplus.com... Oh and of course, all opengl API. But that only works for c++ freaks that are into STL and opengl...

Edit: Really, if all the reason you can't use internet is security. Then there are better solutions to this problem. You could run your web browser and internet in a virtual machine (like virtualbox). That way anything that happened to you while browsing the web would only affect the virtual machine. So you could read stuff to aid you in the development but without risking your real computer to be hacked or anything (close all traffic from Host computer, only allow web tragic to guest operating system).

---

### Post by Vinton90 on 2012-09-14
I'll be honest, this sounds counter productive to me.  However, like vexorian mentioned, if I had all of the documentation I would need, and the packages prepared before I went offline (also depending on the project) I may consider it. What I would most likely do however is run a separate, cheaper machine online and develop on the other; possibly, depending on how worried I was, take the connected machine to a local Internet cafe or hotspot and do my research there. I know that can also pose security risks but it would at least not lead directly to the other machine. 

Of course there is the problem of communication. You mentioned the possibility of other developers on the same project. How would you communicate with being connected? Are you all going to be working on the same machine? And wouldn't that put a strain on productivity? 

I've never attempted what you are mentioning so this is all speculation.

---

### Post by BrokenKingpin on 2012-09-14
I prefer coding in C#, so I would ensure I have the documentation installed for .Net (MSDN, mono docs, etc.). I would also get a huge book on .Net just for reference. Aside from that I would just ensure all the stuff I would need is installed before taking the box offline.

I think with these resources I would be perfectly fine coding offline (event without them for the most part). If it was a language I was somewhat new to than library references would absolutely be necessary.

---

### Post by mevun on 2012-09-14
People used to write code before the Internet.  They had reference books.  They installed software initially with various types of portable media like floppies.

So basically, you just have to install your software development tools and be willing to write a lot of code.  For example, say you're writing some code, but discover you need to do some text pattern matching.  Oops, you did not install a library for regular expression.  You'll just have to write your own, but more likely you'll write some inflexible code that finds the pattern you need.  Even if you did have the foresight to install the regexp library, maybe someone will find/fix a bug later on.  Now you don't have the benefit of that bug fix.

Basically, as others have said, developing this way will have low productivity.

P.S.  
One scenario where I think one might have such a machine is for a "survivalist" that is worried about some catastrophic event that wipes out most of civilization.  Such a PC might not help bring back most inventions, but could let those with the remaining technology become dictators.  ;)

---


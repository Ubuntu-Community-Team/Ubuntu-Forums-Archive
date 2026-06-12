---
title: "What DC++ client are you using?"
date: 2008-06-24
forum: The Cafe
---

### Post by Trail on 2008-06-24
So which client do you use?

---

### Post by bufsabre666 on 2008-06-24
just the regular linux dc++, the only time i really used it was when i brought my laptop to school to get some nice files off the schools network, other than that never use it

---

### Post by nilarimogard on 2008-06-24
> **bufsabre666 said:**
> just the regular linux dc++, the only time i really used it was when i brought my laptop to school to get some nice files off the schools network, other than that never use it

same here

---

### Post by Trail on 2008-06-24
I have used Wine/Revconnect briefly in the past, but gave up due to lack of maintenance.

Valknut was plain too ugly for me, and I hear it won't be supporting the newest versions of the protocol.

Then I used Linuxdcpp for a while, without having issues. But I found it lacking features, and I wanted to try something else.

Then I used Wine/Apexdc++, which is awesome, but not native. There are some minor annoyances I could live with. The worst was that at times it would freeze the GUI due to some thread sync issue (rtplWaitForCriticalSection or something). Normally that happened quite rarely, but yesterday, after updating to Apex 1.1, it would occur unbearably often (read: ALL the damn time)

Today I spent a while researching the situation on Linux. I figured I'd try updating wine to 1.0 first, and see if the situation improves. Otherwise, I am aiming to go for Linuxdcpp CVS (though, it's still a few versions behind).

I don't particularly care about segmented downloading; I usually enqueue collections of large files which may take up to weeks to download. What I really enjoy about apexdc is mainly the highlighting of files while searching/browsing lists (coloring to show if the file is already on your queue/share). This feature was tremendously useful for me. But Linuxdcpp lacks it.

Depending on how things go, after I fix my desktop and laptop, and given that I'm a decent C++ programmer (I'll be awesome in a couple of years, I promise), I'm also planning to try to add the file highlighting to Linuxdcpp as well. It can't be _that_ hard, there is also an option to do not download a file if already in queue/share, which means a function that provides this information is present.

Just wanted to compare thoughts.

---

### Post by Trail on 2008-06-26
For the history, I picked the CVS version of Linuxdcpp after all. Pretty good, and definately improved a lot since the last time I used it. (And very fast).

---

### Post by Corbelius on 2008-06-26
[http://code.google.com/p/dcsharp/](http://code.google.com/p/dcsharp/)

---

### Post by Freddy on 2008-06-26
Whats so good with DC#, what does that client do that LinuxDCPP doesn't do?

---

### Post by Trail on 2008-06-27
Meh, I'm not really fond of .NET to be honest. A morals issue.

---


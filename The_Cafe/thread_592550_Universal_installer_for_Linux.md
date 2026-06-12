---
title: "Universal installer for Linux"
date: 2007-10-26
forum: The Cafe
---

### Post by maybeway36 on 2007-10-26
[http://ianmurdock.com/?p=391]("http://ianmurdock.com/?p=391")
In my opinion, I think the lack of a user-friendly universal installer is one of the big things holding it back - software manufacturers can't support Linux as one platform.
> Bottom line: Many third parties have built their businesses around proprietary software, and we can’t just ignore them. And “ecosystem” implies decentralized, which I argued in part 1 was a key tenet of open source development anyway, i.e., this should be playing to one of our core strengths. So, if your “solution” is to tell ISVs (independent software vendors) to give us their source code so the distributions can include it because that’s just how we do things, you can safely skip the rest of the post below. You’re simply not going to agree that any of this is a problem.

---

### Post by LaRoza on 2007-10-26
> **maybeway36 said:**
> [http://ianmurdock.com/?p=391]("http://ianmurdock.com/?p=391")
In my opinion, I think the lack of a user-friendly universal installer is one of the big things holding it back - software manufacturers can't support Linux as one platform.

Just add it to a repository. Easier than the endless windows and decisions to make when installing on Windows.

```

sudo aptitude install build-essential

```

Show me a Windows feature that will do anything like the above. Different distros use different methods (rpm, deb), and that can be confusing, but that is not a reason why people are possibly detered by Linux.

---

### Post by FuturePilot on 2007-10-26
I think [Autopackage]("http://www.autopackage.org/") is pretty much a universal installer. I've seen a good bunch of proprietary apps distributed with Autopackage

---

### Post by maybeway36 on 2007-10-26
Companies are not going to give away source code! Hence:
> So, if your &#8220;solution&#8221; is to tell ISVs (independent software vendors) to give us their source code so the distributions can include it because that&#8217;s just how we do things, you can safely skip the rest of the post below. You&#8217;re simply not going to agree that any of this is a problem.
Autopackage looks like a good idea. Hopefully its not incompatible with APT/deb.

---


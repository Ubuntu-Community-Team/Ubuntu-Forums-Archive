---
title: "single virus infecting both linux and windows? wha..."
date: 2006-04-27
forum: The Cafe
---

### Post by bb002 on 2006-04-27
I'm on the wxpnews.com mailing list and i checked my email for the first time in quite a while.

In the most recent article Apr. 25, 2006 titled "Best Bet for Privacy" in the "XP SECURITY NEWS, TIPS, UPDATES & PATCHES" section there was this link [http://www.eweek.com/article2/0,1895,1947703,00.asp](http://www.eweek.com/article2/0,1895,1947703,00.asp)


what kind of crap is that? OK let's say such a virus shows up, not a proof-of-concept like in the link, their potential damage on linux is minimal, right? As Linux's security model will only allow the virus to harm the current users files, unless you run it as root. but with SELinux even root can be removed from its all-powerful high-horse.

How is the proof-of-concept virus able to run on both linux and windows when they use different executable formats?  I know it is possible to write a windows application that runs in dos as they use the same executable format (mostly anyways). the win9x program "regedit.exe" does just that. regedit.exe is the only example i've seen but it is possible.

---

### Post by Nano Geek on 2006-04-27
I read that Linus Torvlads already fixed that bug in the Linux Kernel.

---

### Post by Iandefor on 2006-04-27
As I seem to recall, it took advantage of browser flaws to set up a virtual machine that could override security measures in either XP or Linux. I'm kind of fuzzy on it, but that's the impression I got.

---

### Post by lucia_engel on 2006-04-27
Articles from Newsforge:
[Hands-on testing of the new Linux virus]("http://os.newsforge.com/article.pl?sid=06/04/17/1752213&tid=2&tid=78")
[Torvalds creates patch for cross-platform virus]("http://software.newsforge.com/article.pl?sid=06/04/18/1941251&tid=78&tid=26")

The funny thing is...Torvalds didn't patch the kernel against the viral attack, but because of this "virus", he was made aware of a kernel bug that prevented the virus from replicating.

From the second article:
> Leave it to open source hackers to debug and fix aging viral code so that it works correctly. And shame on the anti-viral industry, Kaspersky Lab in particular, for its attempts to deceive the public by passing off old code as something new.

---

### Post by WebDrake on 2006-04-27
[QUOTE=lucia_engel]
The funny thing is...Torvalds didn't patch the kernel against the viral attack, but because of this "virus", he was made aware of a kernel bug that prevented the virus from replicating.[/QUOTE]
OK, so there was a bug in the kernel that *prevented* it in some cases, but if the kernel is running correctly, this virus *does* work on Linux, correct?

... right.  So let's have no more of this nonsense that some people talk about Linux users not needing antivirus software.  What needs to be done to bring free software solutions like ClamAV/KlamAV to the same level of functionality (*easy* web scanning, email scanning, etc.) that Windows AV software provides?

---

### Post by Iandefor on 2006-04-27
[quote=WebDrake]... right.  So let's have no more of this nonsense that some people talk about Linux users not needing antivirus software.  What needs to be done to bring free software solutions like ClamAV/KlamAV to the same level of functionality (*easy* web scanning, email scanning, etc.) that Windows AV software provides?[/quote] I'll wait until it gets into the wild, or else they can't spread very effectively. Also: it's more statistically likely that servers will get hit first, not the desktops. Anyways, if you look at the history of Linux viruses, they tend to be proofs-of-concept, and then they never really get into the wild. Here's a list of known Linux viruses, just for your information: [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses")

---

### Post by Brynster on 2006-04-27
The essence of a cross platform virus is a fairly simple thought.

1 Machine gets sent a virus from say a specially crafted website
2 Virus runs a basic script to discover its enviroment
3 Virus delivers payload appropriate to enviroment
4 Script kiddies giggle and snigger behind there hands.

Its a fairly simple concept and i have laid to out as basically as i possibly can. The actual practise of making it happen would be *ALOT* more complex than i have portrayed.

---

### Post by WebDrake on 2006-04-27
[QUOTE=Iandefor]I'll wait until it gets into the wild, or else they can't spread very effectively. Also: it's more statistically likely that servers will get hit first, not the desktops. Anyways, if you look at the history of Linux viruses, they tend to be proofs-of-concept, and then they never really get into the wild. Here's a list of known Linux viruses, just for your information: [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses")[/QUOTE]
With respect, I think that sort of attitude is going to be responsible for a serious Linux virus problem one of these days.

If the concept is possible we should have tools to deal with it---that is, there should be simple, easy, user-friendly and well-integrated antivirus software available to Linux users.

If people keep going around saying, "Oh, there are no real threats, you don't need it..." it just means that, when a threat *does* arrive, the vast majority of Linux users will have no means to combat it.

---

### Post by ssam on 2006-04-27
to be effected by this virus you would have to run an infected binary and have write access to the binaries on your system.

---

### Post by BoyOfDestiny on 2006-04-27
[QUOTE=ssam]to be effected by this virus you would have to run an infected binary and have write access to the binaries on your system.[/QUOTE]

For many that means, downloading something mysterious, and running it as root.

I honestly can't see a virus problem as a huge issue in Linux. Bugs/holes get fixed and those fixes passed on to us rather quickly. Not to mention there are anti-virus tools, although the current goal (AFAIK) is to keep "harmless" viruses (harmless to Linux) from effecting windows' folks.

What I do see as a potential problem is malware. With opensource and the repositories, it's highly unlikely. However, if people keep their old habits of downloading pre-compiled binaries on the web from random sites... 

There are folks who think bittorrent comes bundled with ads. It did for them because they got it off some warez size instead of the official site.

---

### Post by Iandefor on 2006-04-28
[quote=WebDrake]If the concept is possible we should have tools to deal with it---that is, there should be simple, easy, user-friendly and well-integrated antivirus software available to Linux users.[/quote] This is true. I'm just saying I don't see much of a threat right now, so I'm not going to worry about it.

---


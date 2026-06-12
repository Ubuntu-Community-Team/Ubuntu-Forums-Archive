---
title: "FUD on FOSS?  Article on Technology Review."
date: 2010-06-07
forum: The Cafe
---

### Post by samalex on 2010-06-07
This article was posted on Technology Review today:
[http://www.technologyreview.com/computing/25480/?a=f](http://www.technologyreview.com/computing/25480/?a=f)

And it talks about a paper that was written about Open Source software being more vulnerable because "the ability to access the code of open-source applications may give attackers an edge in developing exploits for the software".

Honestly I see having the source code out there for everyone to view a huge PLUS because it gives the community the ability to find and fix possible exploits, unlike Closed Source software which has an unknown amount of vulnerabilities that are just waiting to be discovered.  

It's like a game of poker...  when everyone's cards are on the table it's easy to spot who's bluffing.  Unfortunately closed source software keeps their cards hidden, so you have no idea how secure or insecure their stuff is.

Sorry, this article just really rubbed me wrong.

Sam

---

### Post by whiskeylover on 2010-06-07
inb4recurring.

Who cares? I mean how many people do you think are going to read the article and be like "Hmm... that's it. I'm not using Open Source software anymore."

---

### Post by SunnyRabbiera on 2010-06-07
Yes its FUD as yes open source can be hacked`because the code is open but it can also be patched just the same.

---

### Post by McRat on 2010-06-07
Sure, it's easier to find problems with a debugger AND source code, but you can find them with just a debugger.  Not sure if they use disassemblers anymore, but you used to have programs that would try to build source code from the binary.

Like someone in the articles stated, it's up to the programmer.  You can have holes in either kind of software.  The goal is not to hide the source to protect yourself, it's to find the holes.

---

### Post by McRat on 2010-06-07
Some companies deliberately installed holes so they themselves could "exploit" them.  This dates all the way back to DOS and the TSR programs (terminate and stay resident).  People got ahold of the functions anyhow, for both good and evil purposes.

---

### Post by samalex on 2010-06-07
> **McRat said:**
> Some companies deliberately installed holes so they themselves could "exploit" them.  This dates all the way back to DOS and the TSR programs (terminate and stay resident).  People got ahold of the functions anyhow, for both good and evil purposes.

I agree, old school apps were full of back doors and exploits added by developers, and this is something that can't hid in open source software.  Reminds me of a few BBS applications back in the day that had backdoors coded by developers to allow them full access to any BBS running their software.  It's been years ago so I can't remember the name of the particular one that comes to mind, but i remember it being a huge problem those days when you had one or two developers working on large applications.

Update -- just found it... Hermes BBS, and here's [a thread]("http://groups.google.com/group/alt.2600/browse_frm/thread/8a460725f947e595/") on the Alt.2600 newsgroup from 1995 talking about it.

Sam

---

### Post by eriktheblu on 2010-06-07
[http://weis2008.econinfosec.org/organization.htm]("http://weis2008.econinfosec.org/organization.htm")Notice the number of MS influences "Workshop on the Economics of Information Security"?

I find it difficult to believe their findings are completely impartial. The article itself displays minimal evidence, but loads of inference.

It's saying that vulnerabilities are found faster (makes sense) and are exploited more frequently. 

Here are my questions:
How long were those vulnerabilities left unpatched?
Of what value was the data on the exploited systems?
Where is the evidence (beyond suspect correlations) that the source code is being used for this?

This statement is quite telling:
> attacks on vulnerabilities in open-source software occurred sooner than attacks on closed-source software, **as measured from the first report of the vulnerability by each company**
(emphasis added)
This means my software can have a perfect security record, so long as I don't tell anyone.

Saying that Linux is hacked more that Windows can be concerning until put into the context that the vast majority of web servers run on Linux. I'll bet a shiny nickel that convenience stores are robbed more than lemonade stands too.

Correlation != Causation.

---

### Post by Sporkman on 2010-06-07
MS is a big sponsor of Technology Review.

---

### Post by McRat on 2010-06-07
> **samalex said:**
> I agree, old school apps were full of back doors and exploits added by developers, and this is something that can't hid in open source software.  Reminds me of a few BBS applications back in the day that had backdoors coded by developers to allow them full access to any BBS running their software.  It's been years ago so I can't remember the name of the particular one that comes to mind, but i remember it being a huge problem those days when you had one or two developers working on large applications.

Update -- just found it... Hermes BBS, and here's [a thread]("http://groups.google.com/group/alt.2600/browse_frm/thread/8a460725f947e595/") on the Alt.2600 newsgroup from 1995 talking about it.

Sam


PS - I had a Trash 80 with 2 FDD's and 48k? RAM.  It was a real hotrod for the time.  TRS-DOS OWNZ YOUSE!!!  :P

---

### Post by McRat on 2010-06-07
> **Sporkman said:**
> MS is a big sponsor of Technology Review.

Seems MS is a sponsor of about 90% of the technology newsletter sites.  It's spooky.

Popups from Hell.

---

### Post by Yes on 2010-06-07
I never understood the argument that having the source open will make it more secure, since more people are looking at it and finding holes.  How many people do you really think just spend their time looking through thousands of lines of code for security holes?

---

### Post by Backharlow on 2010-06-07
Real life is not like caper movies. just because you possess to schematics to a bank vault doesn't mean you can actually break into it any easier.

Another easily digestible comparison; the advance in all sciences is due to rigorous peer review. Meaning, I develop a cure for cancer, then publish my findings in a peer reviewed medical journal. Others quickly check my results and find all of my findings totally false. 
Now, if I had had reputation before this, it would be gone now and no one would ever work with me again. But if my research had been done behind the walls of a pharmaceutical company, there would be a pill in the pipeline before before anyone knew anything.

---

### Post by red_Marvin on 2010-06-07
@Yes, the difference is that company P says 'we are secure' without proving it and giving you no way of checking it yourself, while company O at least gives you the possibility to check for yourself.

---

### Post by aysiu on 2010-06-07
Even though the title of the article is sensationalist FUD ("Open-Source Could Mean an Open Door for Hackers"), the article's contents seem reasonable, and the conclusion is ultimately > "Drawing a broad conclusion that open-source software is easier to exploit is definitely not true," he says. "You could draw the exact opposite conclusion from the body of exploits that are available on [research sites, such as] Packetstorm."

Other security professionals take a broader view, that it's less about open- or closed-source and more about how a company develops its software. Attackers can eventually get the information they need to exploit a bug, whether through automated attack software, by reverse engineering patches, or by somehow gaining access to the source code, so companies should expect that, says Gary McGraw, chief technology officer of Cigital, a software-security consultancy.

"It is a myth that you have to have source code to exploit vulnerabilities," McGraw says. "You (software developers) need to realize that your software is out there, and you are giving your attacker everything they need to exploit it." Seems to end in favor of "we can't draw a conclusion." The title is quite clever, because on the surface it doesn't say anything "Open source *could* mean an open door for hackers" (meaning also that it could not), but the subtext is that it does.

---

### Post by Mr. Picklesworth on 2010-06-07
It's the sort of thing that sounds like a reasonable hypothesis on paper. Even though I disagree with it, I can see why some people may see interest in playing with it.

In practise, though, it's obvious this has turned out differently. The open source community has an incredible response time for security threats, where a patch for a new security issue can find its way to my system within 24 hours.

There are also things made possible by the open source model, like Debian's package management system, that tip this over the top. It's painless to reference dependencies, so the idea of shipping external code *with* an application rarely crosses peoples' minds. That methodology means a developer only has to worry about the security of his own code, not that of code he depends on. It's something the proprietary competition just doesn't have.

---

### Post by SunnyRabbiera on 2010-06-07
> **Yes said:**
> I never understood the argument that having the source open will make it more secure, since more people are looking at it and finding holes.  How many people do you really think just spend their time looking through thousands of lines of code for security holes?

It goes down to one factor: in open source you can look at the code, find errors, and correct them faster then closed source.

---


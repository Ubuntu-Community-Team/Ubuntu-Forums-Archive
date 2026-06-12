---
title: "Please stop giving newbies complicated networking advice!"
date: 2010-01-02
forum: The Cafe
---

### Post by peepingtom on 2010-01-02
** People Often Use interfaces and pppoeconf. This Breaks NetworkManager  **

It's really common for people to use pppoeconf instead of NetworkManager's built-in PPPoE configuration. Most of these people will not use CLI for much more than running ppoeconf, and it causes headaches in the future. For example, this type of configuration makes it really hard to troubleshoot people's problems, needless duplication of labour and needless prefaces on tutorials. While their experience with Ubuntu could have been very easy, people are always posting about how to get their DSL connection working. Inevitably, somebody tells them to use pppoeconf. This is inappropriate

Just check the Networking subforum, its really frustrating to undo work done after reading half a tutorial. I think there should be an effort to update Ubuntu's support documentation! It already has a high google ranking, but people should be encouraged to use NetworkManager as a matter of policy. Anyone who wishes to use /etc/network/interfaces will have the skill to read more complicated documentation, but people who NEED GUIs tend to skim documentation.

Does anyone else think this is a problem that should be solved?

---

### Post by sudoer541 on 2010-01-02
yes

---

### Post by Shpongle on 2010-01-02
good point!

---

### Post by m4tic on 2010-01-02
u said it better. i addressd a similar thing to another thread concerning networking. network manager is underestimated sometimes

---

### Post by t0p on 2010-01-02
> **peepingtom said:**
> I think there should be an effort to update Ubuntu's support documentation! It already has a high google ranking, but people should be encouraged to use NetworkManager as a matter of policy.
[...]
Does anyone else think this is a problem that should be solved?

This problem is [eminently solvable]("https://wiki.ubuntu.com/DocumentationTeam").

---

### Post by murderslastcrow on 2010-01-02
This is what annoys me. When people suggest you use the command line when there's a perfectly usable noob-friendly tool already there for it.

I read a tutorial yesterday that asked you to type a command to verify if a graphical application is installed, when the user could have just as easy clicked ONCE on their applications menu and moved to the category to see if it was there.

Some people are a bit zealous with the commands. We need to accept that GUIs and CLIs both have their times and purposes, none are better than the other, it's just easier to utilize GUIs in the majority of current desktop uses.

If you're running a server, using GUIs will sound silly. It's all about the application, you guys.

---

### Post by jflaker on 2010-01-02
To come to a conclusion, commands are absolute.  

The alternative is describing to someone who has likely never seen a GUI utility, the exact thing to look for and the need to post screen caps for each step....

What would be better is to explain WHY and WHAT instead of just publishing a solution without explanation....we all learn by doing,knowing WHY you are doing helps understanding.

---

### Post by peepingtom on 2010-01-03
The scary thing is that Ubuntu Forums threads often have a higher Google PageRank than the wiki or other support docs. The amount of content that exists solely on the forums is amazing, and obviously it takes manpower to transcribe this stuff.

But what i'm mostly worried about is that this bad advice propagates so much. When the (wrong) answer is a simple one liner, it's easily picked up and repeated. I suppose the real solution is to develop proper support docs and hope that people will link to it from here and the "ubuntu blogs". It'd certainly prevent a lot of redundant labour, but not as much adsense revenue for the bloggers.


for example....
[http://www.google.ca/search?q=Ubuntu+pppoe](http://www.google.ca/search?q=Ubuntu+pppoe)


I'm not really an expert a PageRank. If enough of us link to proper support docs from this single forum, will it make much of a difference? Ideally, people shouldn't be turning to the web for this type of advice anyway. It's so common that it should be part of the installation slideshow!


Oh, another big, "simple fix": Modelines :D

I'll connect to that ForumCouncil IRC channel on Thursday, I think we need a forum where we can discuss this kind of issue. Ubuntu has a documentation problem, and these forums are a great source!

---


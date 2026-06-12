---
title: "Iran Powered by Windows - FAIL"
date: 2010-09-27
forum: The Cafe
---

### Post by asddf on 2010-09-27
[http://news.sky.com/skynews/Home/Technology/Irans-Atomic-Energy-Organisation-Meets-To-Discuss-Response-To-Stuxnet-Worm-Over-Nuclear-Plant-Fears/Article/201009415743426?lpos=Technology_Third_Home_Page_Article_Teaser_Region__1&lid=ARTICLE_15743426_Irans_Atomic_Energy_Organisation_Meets_To_Discuss_Response_To_Stuxnet_Worm_Over_Nuclear_Plant_Fears](http://news.sky.com/skynews/Home/Technology/Irans-Atomic-Energy-Organisation-Meets-To-Discuss-Response-To-Stuxnet-Worm-Over-Nuclear-Plant-Fears/Article/201009415743426?lpos=Technology_Third_Home_Page_Article_Teaser_Region__1&lid=ARTICLE_15743426_Irans_Atomic_Energy_Organisation_Meets_To_Discuss_Response_To_Stuxnet_Worm_Over_Nuclear_Plant_Fears)

---

### Post by Paqman on 2010-09-27
More of a Siemens fail than a Windows one. Not only does their SCADA system autorun executables on USB sticks (doh!), but they advise *against* changing the system's default passwords. That's just monumentally lax.

SCADA systems are a bit of a soft target anyway, they tend to have little or no security. The industry really needs to sort it's act out.

---

### Post by MooPi on 2010-09-27
The mistake is that this one was discovered. For the Stuxnet to accomplish its goal, ethereal existence would be the first function.  The best assassin goes unnoticed ? Or maybe it did accomplish it's main goal and the authors discovered it could do more ?

---

### Post by ubunterooster on 2010-09-27
> **MooPi said:**
> The mistake is that this one was discovered. For the Stuxnet to accomplish its goal, ethereal existence would be the first function.  The best assassin goes unnoticed ? Or maybe it did accomplish it's main goal and the authors discovered it could do more ?
Most likely it did finish whatever goal it was designed for

---

### Post by Paqman on 2010-09-27
> **ubunterooster said:**
> Most likely it did finish whatever goal it was designed for

Seems likely. Since it used USB sticks as the vector I think you can assume that it's designers made sure the payload was delivered to the target. I can't imagine they spent thousands of man-hours developing the thing and then just relied on random chance to get it into the system they wanted to hit.

Loving the hysteria on the news though:

BBC news anchor to interviewee:
> What can people do?
Er, you mean those people at home who have a Siemens' WinCC/PCS 7 SCADA system controlling their toaster?

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2010-09-27
I'm baffled by the sheer idiocy of the people who allowed this to happen. Why the hell would you hook up a computer that controls nuclear reactors to the internet or directly transfer files to it through any medium, much less execute them? Physical isolation is the best, and, in such cases, only solution.

---

### Post by Paqman on 2010-09-27
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> Why the hell would you hook up a computer that controls nuclear reactors to the internet

It's useful for remote diagnostics. In this case though, the malware didn't get in from the internet, it came via sneakernet. Proper oldskool, reminds me of the days of infected floppies.

> 
or directly transfer files to it through any medium, much less execute them? 


How would you install updates? A lot of SCADA systems are basically a lot of small computers daisy-chained with RS232, but ethernet is becoming more common. Either way, plugging a laptop into one of the boxes is a common maintenance task. As is uploading a patch.

> 
Physical isolation is the best, and, in such cases, only solution.

Hmm, i'd disagree. There's no such thing as perfect isolation for a system which is a network (unless you never replace or upgrade any components of course!) And you're still vulnerable to attack via sneakernet, as mentioned above.

Traditionally, SCADA designers haven't had to worry about security too much. If you're running proprietary code on custom hardware over serial comms then the chance of malicious code getting in is negligible. But once you're running a bunch of Windows or Linux boxes chatting to each other over TCP/IP then you need to start upping your game.

---

### Post by sdowney717 on 2010-12-14
[http://www.foxnews.com/scitech/2010/12/09/despite-iranian-claims-stuxnet-worm-causing-nuclear-havoc/](http://www.foxnews.com/scitech/2010/12/09/despite-iranian-claims-stuxnet-worm-causing-nuclear-havoc/)

stuxnet is still messing up their systems. It sounds like they will never be able to rid themselves of it. So it is still doing the job the creators wished.

Reading of the scientists being killed tells me that some government agency is behind this.

---

### Post by nolag on 2010-12-14
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> I'm baffled by the sheer idiocy of the people who allowed this to happen. Why the hell would you hook up a computer that controls nuclear reactors to the internet or directly transfer files to it through any medium, much less execute them? Physical isolation is the best, and, in such cases, only solution.
 
Nah, the banks are connected to the internet and no one has damaged them yet (at least the Canadian and American ones).  Security can prevent this, I guess.  How do we know it was a windows box, or that it auto ran executables?  Viruses can be made for unix/linux (mac is unix no need to say it also).
 
> **sdowney717 said:**
> [http://www.foxnews.com/scitech/2010/12/09/despite-iranian-claims-stuxnet-worm-causing-nuclear-havoc/](http://www.foxnews.com/scitech/2010/12/09/despite-iranian-claims-stuxnet-worm-causing-nuclear-havoc/)
 
stuxnet is still messing up their systems. It sounds like they will never be able to rid themselves of it. So it is still doing the job the creators wished.
 
Reading of the scientists being killed tells me that some government agency is behind this.
 
I don't know, Iran claimed they stopped it.  It is hard to know who to believe, so much bais.  Iran would lie (like when they originally said it did no damage), but so would a news network in the states...
 
Who says the incidents are related?  It was likely a government, but to be fair there is a lot of civil unrest there as well, both could have been unhappy people or unrelated to each other.

---

### Post by Paqman on 2010-12-14
> **nolag said:**
> How do we know it was a windows box, or that it auto ran executables?

Because we know exactly what SCADA system was being used: [Siemens WinCC]("http://en.wikipedia.org/wiki/WinCC").

---

### Post by Spice Weasel on 2010-12-14
Ach, why did you revive this thread when everyone's just going to use it to flame Windows?

---

### Post by CharlesA on 2010-12-14
> **Spice Weasel said:**
> Ach, why did you revive this thread when everyone's just going to use it to flame Windows?
With that thought in mind.

Thread closed before it degrades (as is inevitable.)

---


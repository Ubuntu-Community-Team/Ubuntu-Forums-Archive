---
title: "Eric S. Raymond: Goodbye Fedora, Hello Ubuntu"
date: 2007-02-21
forum: The Cafe
---

### Post by Perfect Storm on 2007-02-21
> After thirteen years as a loyal Red Hat and Fedora user, I reached my limit today, when an attempt to upgrade one (1) package pitched me into a four-hour marathon of dependency chasing, at the end of which an attempt to get around a trivial file conflict rendered my system unusable.

[http://www.redhat.com/archives/fedora-devel-list/2007-February/msg01006.html](http://www.redhat.com/archives/fedora-devel-list/2007-February/msg01006.html)

Edit: found the news as well on linux.com - [http://enterprise.linux.com/enterprise/07/02/21/1340237.shtml?tid=23&tid=12](http://enterprise.linux.com/enterprise/07/02/21/1340237.shtml?tid=23&tid=12)

---

### Post by ComplexNumber on 2007-02-21
i don't see anything there other than a white page with "Thread prev", "Thread next" etc at the top.

---

### Post by steven8 on 2007-02-21
Here ya go:

> Goodbye, Fedora

    * From: esr thyrsus com (Eric S. Raymond)
    * To: fedora-devel-list redhat com
    * Cc: lwn lwn net, editors newsforge com, sjvn vna1 com, editors linuxtoday com
    * Subject: Goodbye, Fedora
    * Date: Wed, 21 Feb 2007 03:03:50 -0500 (EST)

After thirteen years as a loyal Red Hat and Fedora user, I reached my
limit today, when an attempt to upgrade one (1) package pitched me
into a four-hour marathon of dependency chasing, at the end of which
an attempt to get around a trivial file conflict rendered my system 
unusable.

The proximate causes of this failure were (1) incompetent repository
maintenance, making any nontrivial upgrade certain to founder on a
failed dependency, and (2) the fact that rpm is not statically linked
-- so it's possible to inadvertently remove a shared library it
depends on and be unrecoverably screwed.  But the underlying problems
run much deeper.

Over the last five years, I've watched Red Hat/Fedora throw away what
was at one time a near-unassailable lead in technical prowess, market
share and community prestige.  The blunders have been legion on both
technical and political levels.  They have included, but were not
limited to:

* Chronic governance problems.

* Persistent failure to maintain key repositories in a sane,
  consistent state from which upgrades might actually be possible.

* A murky, poorly-documented, over-complex submission process.

* Allowing RPM development to drift and stagnate -- then adding
  another layer of complexity, bugs, and wretched performance with yum. 

* Effectively abandoning the struggle for desktop market share.

* Failure to address the problem of proprietary multimedia formats with
  any attitude other than blank denial.

In retrospect, I should probably have cut my losses years ago.  But I
had so much history with Red-Hat/Fedora, and had invested so much effort in
trying to fix the problems, that it was hard to even imagine
breaking away. 

If I thought the state of Fedora were actually improving, I might hang
in there.  But it isn't.  I've been on the fedora-devel list for
years, and the trend is clear.  The culture of the project's core
group has become steadily more unhealthy, more inward-looking, more
insistent on narrow "free software" ideological purity, and more
disconnected from the technical and evangelical challenges that must
be met to make Linux a world-changing success that liberates a
majority of computer users.

I have watched Ubuntu rise to these challenges as Fedora fell away
from them.  Canonical's recent deal with Linspire, which will give
Linux users legal access to WMF and other key proprietary codecs, is
precisely the sort of thing Red-Hat/Fedora could and should have taken
the lead in.  Not having done so bespeaks a failure of vision which I
now believe will condemn Fedora to a shrinking niche in the future.

This afternoon, I installed Edgy Eft on my main development machine --
from one CD, not five.  In less than three hours' work I was able to
recreate the key features of my day-to-day toolkit.  The
after-installation mass upgrade to current packages, always a
frightening prospect under Fedora, went off without a hitch.

I'm not expecting Ubuntu to be perfect, but I am now certain it will
be enough better to compensate me for the fact that I need to learn
a new set of administration tools.

Fedora, you had every advantage, and you had my loyalty, and you blew it.  
And that is a damn, dirty shame.
-- 
					Eric S. Raymond



---

### Post by Perfect Storm on 2007-02-21
Try the new link I have added.

---

### Post by drfalkor on 2007-02-21
Here is another link: [http://www.linux-watch.com/news/NS6401388051.html](http://www.linux-watch.com/news/NS6401388051.html)

maybe we'll see ESR on ubuntuforums.org one day with a thread like "How can I install WM-Ware?"  ( lol, just kidding :) )

---

### Post by Bloodfen Razormaw on 2007-02-21
Very bad news for Ubuntu.  Canonical certainly should not be after a joke like ESR as their spokeman.  Men who try to destroy software freedom from the inside (and complain about distributions that DO respect their freedom, as in that email), who try to pretend they are coders when their only major project was something they took over, then ran into the ground by making it known as one of the least secure applications on the UNIX platform (*coughfetchmailcough*), who has no understanding of hacker culture or hacking yet calls himself a hacker, who has never put a line of code into the linux kernel but calls himself a linux developer, who is openly racist, and so on and so on, are not the kind of people Ubuntu users should want representing them.

---

### Post by ComplexNumber on 2007-02-21
> **Artificial Intelligence said:**
> Try the new link I have added.
ahh yes, i can actually see some text there :mrgreen:.


having read it, it sounds to me more  like a knee-jerk reaction to a bad day at the office.

---

### Post by Hendrixski on 2007-02-21
> **Bloodfen Razormaw said:**
> Very bad news for Ubuntu.  Canonical certainly should not be after a joke like ESR as their spokeman.  Men who try to destroy software freedom from the inside (and complain about distributions that DO respect their freedom, as in that email), who try to pretend they are coders when their only major project was something they took over, then ran into the ground by making it known as one of the least secure applications on the UNIX platform (*coughfetchmailcough*), who has no understanding of hacker culture or hacking yet calls himself a hacker, who has never put a line of code into the linux kernel but calls himself a linux developer, who is openly racist, and so on and so on, are not the kind of people Ubuntu users should want representing them.

Whoa, grow up.  A developer is not someone who writes lines of code.  A monkey can do that. ESR has resolved numerous conflicts in open source, including preventing a fork of the Linux kernel. He has written many articles that challenge developers to create newer, better software, and he has largely shaped the direction of the OpenSource movement, and Linux development as a whole.  He is, by those standards, a developer (oh yeah, and he does write code too, so he's a developer by those standards as well).

I see ESR's support of Ubuntu as good news for Canonical because it may draw more people away from RPM based distros and into the debian fold.

---

### Post by BLTicklemonster on 2007-02-21
> **Hendrixski said:**
> Whoa, grow up.  A developer is not someone who writes lines of code.  A monkey can do that....

My new LIFE ambition. I aspire to be a monkey. Devolution at its finest!

---

### Post by Kindred on 2007-02-21
I think i'll Cc a bunch of linux publications next time I switch distros... or not.

---

### Post by kripkenstein on 2007-02-21
> **Bloodfen Razormaw said:**
> Very bad news for Ubuntu.  Canonical certainly should not be after a joke like ESR as their spokeman.  Men who try to destroy software freedom from the inside (and complain about distributions that DO respect their freedom, as in that email), who try to pretend they are coders when their only major project was something they took over, then ran into the ground by making it known as one of the least secure applications on the UNIX platform (*coughfetchmailcough*), who has no understanding of hacker culture or hacking yet calls himself a hacker, who has never put a line of code into the linux kernel but calls himself a linux developer, who is openly racist, and so on and so on, are not the kind of people Ubuntu users should want representing them.

All the other issues aside, his racism (or, more precisely, his offensive and incorrect notions about race issues) is enough to get me to dislike him.

Anyhow, he won't be (I hope and assume) any sort of official spokesperson for Ubuntu. People will forget about this comment quickly anyhow.

---

### Post by raublekick on 2007-02-21
Was he ever really a spokesperson for Fedora / Red Hat? An advocate is much different than a spokesperson. He's nothing more than a famous user at this point. 

Can you guys provide some examples of his racism? I've never heard that before.

---

### Post by kripkenstein on 2007-02-21
> **raublekick said:**
> Was he ever really a spokesperson for Fedora / Red Hat? An advocate is much different than a spokesperson. He's nothing more than a famous user at this point. 

Can you guys provide some examples of his racism? I've never heard that before.

Here is an example of his misguided thoughts on race and IQ: [http://esr.ibiblio.org/?p=129]("http://esr.ibiblio.org/?p=129")

He may know something about software (yet even that is debatable), but about the social sciences and IQ tests in particular, he is far off.

---

### Post by EdThaSlayer on 2007-02-21
Seems Ubuntu got some extra press here. :)
Soon Ubuntu will become the dominant species of Linux until another far more evolved species pops up. :D

---

### Post by jamboarder on 2007-02-21
> **kripkenstein said:**
> All the other issues aside, his racism (or, more precisely, his offensive and incorrect notions about race issues) is enough to get me to dislike him.

Anyhow, he won't be (I hope and assume) any sort of official spokesperson for Ubuntu. People will forget about this comment quickly anyhow.

Same here.  I've had enough of his visceral imperialist rantings for me to care about his other perspectives.  Ubuntu is and has been well off enough without him.

---

### Post by Hendrixski on 2007-02-21
That is a valid point: that nobody will remember this comment by the end of the day. I wasn't aware he was a Red Hat user.  I don't know which distro Linus uses, or which one RMS uses (which, he probably doesn't use Linux, he probably struggles with a HURD kernel based system).

---

### Post by Hendrixski on 2007-02-21
> **kripkenstein said:**
> Here is an example of his misguided thoughts on race and IQ: [http://esr.ibiblio.org/?p=129]("http://esr.ibiblio.org/?p=129")

He may know something about software (yet even that is debatable), but about the social sciences and IQ tests in particular, he is far off.

So if I understand that article correctly, he advocates fighting racism and sexism by understanding some of the underlying genetic differences between ethnic groups such as the difference between the mean intelligence between races, and the layout of the bell curve of intelligence between men and women.  I do not doubt that understanding what makes us different is a good goal.  What I doubt is if that the studies that he cites are accurate.  (like the one about an 80 point difference between the average IQ of Caucasians and an African-Americans).  All in all, I'm sure he means well, even if he is politically incorrect.

---

### Post by kripkenstein on 2007-02-21
> **Hendrixski said:**
> So if I understand that article correctly, he advocates fighting racism and sexism by understanding some of the underlying genetic differences between ethnic groups such as the difference between the mean intelligence between races, and the layout of the bell curve of intelligence between men and women.  I do not doubt that understanding what makes us different is a good goal.  What I doubt is if that the studies that he cites are accurate.  (like the one about an 80 point difference between the average IQ of Caucasians and an African-Americans).  All in all, I'm sure he means well, even if he is politically incorrect.

The studies he quotes are accurate, or at least I have seen extremely similar results published (but he didn't say 80 point difference, he said 15). The problem is that he misinterprets it completely. Here are a few problems with what he says:

1. He apparently doesn't understand what 'heritability' is. It is a technical term, when used by researchers, it doesn't mean what the layperson thinks it does. In particular, 'heritability' is a value that can change from one environment to another. IQ can be heritable in New York but not heritable in Moscow, theoretically.

2. He mentions that men and women have the same mean IQ. This is true. But it does not mean men and women are equally intelligent! In fact, the test was **calibrated** so that men and women would get the same average score. So the comparison is meaningless. This is like saying "this stick is 1 sticklength long", and then measuring the stick with itself, concluding that the stick is indeed one sticklength long.

3. It is well known that IQ tests are culturally biased. That does not mean they are **intentionally** biased. But they are. This explains why, for example, adopted black children raised by white parents have around the same average IQ as white children. They have the same genetics as other black children, but, being raised by white parents, they are closer to the culture of the people who **write** IQ tests.

Sorry to write a long rant...

---

### Post by raublekick on 2007-02-21
I don't really sense any racism in that article. Misinterpretation of studies? Maybe. But definitely NOT racism. I can't really comment on the validity of the studies or what he says, because that is not my field of study. 

I do somewhat agree with him though. It is easy to be aware of the differences between individuals, groups of individuals, countries, religious, and so forth. It is also easy to see (both visually and not visually) the differences between races, but for some reason the answer to racism is to pretend that these differences don't exist. I agree with ESR that understanding the differences between people is more important than trying to level the playing field and make those differences disappear. And that goes for anything; race, religion, political beliefs, software beliefs, favorite foods, and so on. 


But let's let the conversation continue as intended. I think the racist discussion is proof enough that this is not going to be neither a gain or a loss for Ubuntu.

---

### Post by Nikron on 2007-02-21
> **kripkenstein said:**
> 
3. It is well known that IQ tests are culturally biased. That does not mean they are **intentionally** biased. But they are. This explains why, for example, adopted black children raised by white parents have around the same average IQ as white children. They have the same genetics as other black children, but, being raised by white parents, they are closer to the culture of the people who **write** IQ tests.


An example of biased IQ tests, if you don't believe kripknstein, because I recently took one.  It asked me what the Book of Genesis was.  Hello?  I'm not Christian, and I'm pretty sure that's a religious Christian document, feel to correct me.  But yes, IQ tests are culturally biased. 

Back on topic, I'd have to say that the whole post makes him too much a of drama king for such things.  Yes, he changed distros...  People do it all the time, even if they aren't famous win the open source movement..

---

### Post by cowlip on 2007-02-21
> **Hendrixski said:**
> I don't know which distro Linus uses, or which one RMS uses (which, he probably doesn't use Linux, he probably struggles with a HURD kernel based system).

Oh god, HURD comments never fail to make me laugh! Thank you.

On topic...I think it's .  It seems like he's conflating some things together though---it was dependancy hell that drove him away (Which can happen in apt too right, as in recent dapper updates?) but he's happy about the Easy Codec tool?  

Well whatever...so am I, but I think Canonical should also be applauded for sticking to FLOSS too, not just painted as some proprietary mess, which I think the name "Lindows" inspires.  Such as the recent decision not to include 3d drivers in the fave of "nouveau" free driver development, even though I understand those aren't their only reasons.

---

### Post by macogw on 2007-02-21
> **Nikron said:**
> An example of biased IQ tests, if you don't believe kripknstein, because I recently took one.  It asked me what the Book of Genesis was.  Hello?  I'm not Christian, and I'm pretty sure that's a religious Christian document, feel to correct me.  But yes, IQ tests are culturally biased. 

Back on topic, I'd have to say that the whole post makes him too much a of drama king for such things.  Yes, he changed distros...  People do it all the time, even if they aren't famous win the open source movement..

And there have been analogies where comparisons are made between things that upper-class people know well, middle-class know of, and lower-class may have a vague idea exists, but  don't understand.  Using parts of an opera for your analogies can easily skew it so that the lower-class looks stupid, justifying the upper-class's place in society on the basis that the intelligent obviously rule in such a case...when really, the test was made to fit their culture and has nothing to do with their intelligence.

RAV TUX has a copy of Debian Hurd (instead of Debian Linux).  He keeps trying to get me to try it.

---

### Post by Hendrixski on 2007-02-21
> **kripkenstein said:**
> The studies he quotes are accurate, or at least I have seen extremely similar results published (but he didn't say 80 point difference, he said 15). The problem is that he misinterprets it completely. Here are a few problems with what he says:

1. He apparently doesn't understand what 'heritability' is. It is a technical term, when used by researchers, it doesn't mean what the layperson thinks it does. In particular, 'heritability' is a value that can change from one environment to another. IQ can be heritable in New York but not heritable in Moscow, theoretically.

2. He mentions that men and women have the same mean IQ. This is true. But it does not mean men and women are equally intelligent! In fact, the test was **calibrated** so that men and women would get the same average score. So the comparison is meaningless. This is like saying "this stick is 1 sticklength long", and then measuring the stick with itself, concluding that the stick is indeed one sticklength long.

3. It is well known that IQ tests are culturally biased. That does not mean they are **intentionally** biased. But they are. This explains why, for example, adopted black children raised by white parents have around the same average IQ as white children. They have the same genetics as other black children, but, being raised by white parents, they are closer to the culture of the people who **write** IQ tests.

Sorry to write a long rant...

Hhhmm. now I know. You obviously know a lot more about this topic than I do.  Thank you for sharing. :)

I think raublekick has a point though, it doesn't sound like ESR intentionally trying to be racist.  Which, I mean, you don't have to be filled with hate to be a racist... perhaps just being ignorant can make someone a racist. I admit I don't know.

And a quick comment about the Book of Genesis as an IQ question ... it's in 2 of the worlds 3 major religions is it not?  Is there a Muslim version of that test that asks about The Family of Imran (the third book of the Koran).  Is the problem only if you take a culturally biased IQ test while not part of that culture? So if one were to take a culturally biased IQ test, but they are part of the culture it is biased towards, then it's accurate right?

---

### Post by Hendrixski on 2007-02-21
> **macogw said:**
> 
RAV TUX has a copy of Debian Hurd (instead of Debian Linux).  He keeps trying to get me to try it.

Is it on a liveCD?  I would be interested to try it.  Where may I download one?

---

### Post by kripkenstein on 2007-02-21
> **Hendrixski said:**
> And a quick comment about the Book of Genesis as an IQ question ... it's in 2 of the worlds 3 major religions is it not? 

You are talking about the world's major **monotheistic** religions, I presume? ;) Yes, it is in 2 out of the top 3 (but the 3rd place is far, far below the first 2...). But if you consider **all** major religions, then the picture is more complex. The book of Genesis doesn't appear in Hinduism nor Buddhism, which account for a tremendous amount of people.

So, I would say yes, asking about the book of Genesis shows some cultural bias. (But then there is no such thing as a test without cultural bias...)

---

### Post by MetalMusicAddict on 2007-02-21
Did I miss something? Were posts removed from this thread? Its taking some odd turns. :-k

---

### Post by kripkenstein on 2007-02-21
> **MetalMusicAddict said:**
> Did I miss something? Were posts removed from this thread? Its taking some odd turns. :-k

Hmm, looks like my somewhat offtopic rant was deleted (but still appears in a quote)... and perhaps other things. Odd. Were we going too far offtopic?

---

### Post by hkgonra on 2007-02-21
> **kripkenstein said:**
> Here is an example of his misguided thoughts on race and IQ: [http://esr.ibiblio.org/?p=129]("http://esr.ibiblio.org/?p=129")

He may know something about software (yet even that is debatable), but about the social sciences and IQ tests in particular, he is far off.

I will admit I just skimmed the article but I didn't see anything racist in there. 
Looked like he was talking along the same lines at this previous study which is pretty much established fact now. 
[http://en.wikipedia.org/wiki/The_Bell_Curve](http://en.wikipedia.org/wiki/The_Bell_Curve)

---

### Post by bunabattoir on 2007-02-21
> **EdThaSlayer said:**
> ...
Soon Ubuntu will become the dominant species of Linux until another far more evolved species pops up. :D

[It already has]("http://www.gentoo.org/").


Flame on!:twisted:

---

### Post by Hendrixski on 2007-02-21
> **kripkenstein said:**
> You are talking about the world's major **monotheistic** religions, I presume? ;) Yes, it is in 2 out of the top 3 (but the 3rd place is far, far below the first 2...). But if you consider **all** major religions, then the picture is more complex. The book of Genesis doesn't appear in Hinduism nor Buddhism, which account for a tremendous amount of people.

So, I would say yes, asking about the book of Genesis shows some cultural bias. (But then there is no such thing as a test without cultural bias...)

Good point, Buddhism and Hinduism probably do rank near the top in terms of size.  So if I can ask my question again, in different words:
If there was an IQ test that asked a Hindu about the Mahabharata, and an IQ test that asked a Christian or Jew about the book of Genesis, then is the end result the same?  Because each test is culturally biased but each time in favor of the people who are taking it, are the exam results equivalent?

---

### Post by Vorian on 2007-02-21
This thread has gone off topic

all off-topic posts were moved to the bakcyard [http://ubuntuforums.org/showthread.php?t=366987](http://ubuntuforums.org/showthread.php?t=366987)

---

### Post by cowlip on 2007-02-21
Vorian, I'm just curious as to why did you moveed my on topic post about this, while the (off topic) IQ posts are still in this thread?

---

### Post by Bloodfen Razormaw on 2007-02-21
> Whoa, grow up. A developer is not someone who writes lines of code. A monkey can do that. ESR has resolved numerous conflicts in open source, including preventing a fork of the Linux kernel.
This is a laughable statement.  ESR has done nothing but cause conflicts.  For the sake of corporate power he infiltrated the free software movement, then tried to remove freedom as a goal from that movement.  You can see his contempt for people's rights in the very email that prompted this thread, in which he condemns Fedora for respecting the rights of its users.  He was so transparent in his attempts to derail the movement that the man who helped him form OSI, Bruce Perens, had to not-so-subtly *denounce ESR before the United Nations*.  And lets not mention how poorly ESR takes being exposed as the fraud he is: he has threatened Perens with physical harm.  If flagrant attempts to tear apart the movement for software freedom and threatening to kill people is called resolving conflicts, I must be in bizarro world.

And yes, actually, a developer does write code.  That's what developers do.  Developers develop.  ESR has never developed anything of significance.  A look at his portfolio finds nothing but a handful of scripts, a laughable bad and rejected attempt to rewrite Linux configuration, and fetchmail, which he drove into the ground and turned into a laughing stock.  Not exactly a stunning history.

---

### Post by hkgonra on 2007-02-21
Then again if you want to talk about true fruitcakes in the open source movement no conversation would be complete without mentioning. 

[http://en.wikipedia.org/wiki/Richard_Stallman](http://en.wikipedia.org/wiki/Richard_Stallman)

---

### Post by ComplexNumber on 2007-02-21
> **cowlip said:**
> Vorian, I'm just curious as to why did you moveed my on topic post about this, while the (off topic) IQ posts are still in this thread?
i moved yours back. it was probably moved in error.

---

### Post by darkhatter on 2007-02-21
who is Eric S. Raymond???

---

### Post by ComplexNumber on 2007-02-21
> **darkhatter said:**
> who is Eric S. Raymond???
[this]("http://en.wikipedia.org/wiki/Eric_S._Raymond") guy.

---

### Post by darkhatter on 2007-02-21
> **ComplexNumber said:**
> [this]("http://en.wikipedia.org/wiki/Eric_S._Raymond") guy.

thanks, I should of went to wikipedia myself.

ok next question, why is this important?

---

### Post by maniacmusician on 2007-02-21
Wow, I didn't know he was that prominent of a person. Must be a big ouch for fedora people, I guess, to loose someone of his experience.

---

### Post by bogolisk on 2007-02-21
He's full of himself anyway

[list]
[*] dressed as ObiWan in a gathering in front of Microsoft building
[*] wrote dead-threath to fellow FOSS big-mouth Bruce Perens  (actually it was just a serious threat but since he's a gun-nut, it should be considered as a dead-threat.)
[*] got told by the kernel developers to go away because he couldn't code and CML2 is a piece of junk.
[*] went on to write the book "The Art of Unix Programing" (thinking he's a great as the author of "The Art of Programing" classic books)
[*] I haven't read his book, but a colleague of mine did, and he told me in that book, ESR's fetchmail is acclaimed as the best program ever written. Having used fetchmail back in the 90s, I've laughed so hard.
[/list]

I'm not sure that will enjoy his presence on ubuntuforums.

---

### Post by 454redhawk on 2007-02-21
> **kripkenstein said:**
> 

3. It is well known that IQ tests are culturally biased. That does not mean they are **intentionally** biased. But they are. This explains why, for example, adopted black children raised by white parents have around the same average IQ as white children. They have the same genetics as other black children, but, being raised by white parents, they are closer to the culture of the people who **write** IQ tests.

Sorry to write a long rant...

LOL.  Please tell me you dont actually subscribe to that crap.:lolflag:

---

### Post by spockrock on 2007-02-21
any way we can send him back to fedora?

---

### Post by ComplexNumber on 2007-02-21
> **spockrock said:**
> any way we can send him back to fedora?
you should want to keep him. he's the leader of a coven, so he can concoct a  spell using eye of toad and leg of newt to boost ubuntu's chances of coming preinstalled on the next wave of Dell PC's.

---

### Post by Bloodfen Razormaw on 2007-02-21
Richard Stallman is just weird, not malicious like ESR (who is also weird, on levels Stallman could only dream of).

Stallman is a completely different animal from ESR:
[LIST]
[*]Unlike ESR, he actually knows how to code[*]Unlike ESR, he doesn't despise freedom and try to tear it apart
[*]Unlike ESR, he has not sent anyone death threats
[*]Unlike ESR, he actually is responsible for a large part of GNU/Linux systems (as opposed to none at all, like ESR)
[*]Unlike ESR, he doesn't pathetically struggle to use big words in a sad attempt to not look like a moron (and in the process misusing those words, attributing quotes to the wrong people, misstating facts about subjects he is trying to pretend he is knowledgeable in etc.)
[*]Unlike ESR, Stallman does not come up with discredited reasons to claim that black people are inferior to whites.
[*]Stallman fought to save software freedom when it was threatened by proprietary software, whereas ESR fought to destroy free software when it became a threat to proprietary software.
[/LIST]

If it takes being a crazy person who behaves strangely to get that package, I'll take it.  I'd rather a person be bizarre than be a criminally violent, self-obsessed, racist, xenophobic, freedom-hating wannabe hacker.

---

### Post by spockrock on 2007-02-21
> **ComplexNumber said:**
> you should want to keep him. he's the leader of a coven, so he can concoct a  spell using eye of toad and leg of newt to boost ubuntu's chances of coming preinstalled on the next wave of Dell PC's.

hahhaha, I am not really a satanist, just some one who loves the idea of SE, due to their love for the extreme end of metal.

---

### Post by JPMaximilian on 2007-02-21
Eric S. Rayman seems like a bit of a nut bar.  Does Ubuntu want an Anarchist-Witch-Doctor-Gun-Toating-Haxzor in their ranks?  Doesn't seem like "humanity to others".

And his whole shpeal about Blacks, being 12% of the population and commiting 50% of the crimes because they're "less intelligent" is stupid.  I don't have all the numbers/stats in front of me, but consider this:  maybe Blacks have a lower IQ because they don't have a stable family, as much education, etc, a lot of blacks are also in poor areas and poverty will motivate many people to crime.  Its not like blacks have a lower IQ because they actually have a lower IQ, it could very easily be because of their social situation.  IQ tests are supposed to test your ability to learn and not what you have learned, but I don't think that they are perfectly fair/ work that way flawlessly.  The 12 point IQ difference could be explained away.  The majority of the black community is still feeling the effects of slavery IMHO.

Whats the difference between a black person and a white person?  One is black and one is white.  In other words, basically nothing.

Anyways, back to the point, how can a person with ESR's views exhibit "Humanity to Others"?

---

### Post by spockrock on 2007-02-21
> **JPMaximilian said:**
> Eric S. Rayman seems like a bit of a nut bar.  Does Ubuntu want an Anarchist-Witch Doctor, Gun-Toating haxzor in their ranks?  Doesn't seem like "humanity to others".

ugh he is an anarcho-capitalist, anarchism(anarcho-syndicalism, libertarian socialism)  and anarcho-capitalism are on opposite ends of political and ideology.

---

### Post by JPMaximilian on 2007-02-21
> **spockrock said:**
> ugh he is an anarcho-capitalist, anarchism(anarcho-syndicalism, libertarian socialism)  and anarcho-capitalism are on opposite ends of political and ideology.

That statement is contradictory to the definitions of these words.

Wikipedia:

Anarcho-capitalism (also known by other names, most frequently as free-market anarchism[1] or simply market anarchism) is a form of **individualist anarchism**

**Individualist anarchism** (or anarchist individualism, anarcho-individualism, individualistic anarchism, philosophical anarchism or scientific anarchism) refers to any of several traditions that hold that "individual conscience and the pursuit of self-interest **should not be constrained by any collective body or public authority.**"

Anarchism is a political philosophy or group of doctrines and attitudes centered on** rejection of any form of compulsory government **(cf. "state"[1]) and supporting its elimination.

---

### Post by ComplexNumber on 2007-02-21
guys, i thought i'd move your posts (and mine) to the parallel thread in the backyard due to them discussing his beliefs and such.

---

### Post by aysiu on 2007-02-21
**Edit**: Oh, so a merger is cool? All right. I'll leave them merged, then.

---

### Post by spockrock on 2007-02-21
> **JPMaximilian said:**
> That statement is contradictory to the definitions of these words.

Wikipedia:

Anarcho-capitalism (also known by other names, most frequently as free-market anarchism[1] or simply market anarchism) is a form of **individualist anarchism**

**Individualist anarchism** (or anarchist individualism, anarcho-individualism, individualistic anarchism, philosophical anarchism or scientific anarchism) refers to any of several traditions that hold that "individual conscience and the pursuit of self-interest **should not be constrained by any collective body or public authority.**"

Anarchism is a political philosophy or group of doctrines and attitudes centered on** rejection of any form of compulsory government **(cf. "state"[1]) and supporting its elimination.

Anarchism, the political ideology has for the most part been socialist and anti capitalism while both are stateless forms of self governance, anarchism and anarcho-capitalism are on the opposite end of the economic spectrum.

---

### Post by Trebuchet on 2007-02-21
> **JPMaximilian said:**
> The majority of the black community is still feeling the effects of slavery IMHO.How can the majority of the black community still be suffering the effects of slavery when none of them have actually lived in it? (Racism, of course, is another issue entirely.)  If slavery were the indirect cause of black Americans' problems those should be decreasing steadily as the slavery recedes into the past.

Amusingly, I just read *The Cathedral and the Bazaar* today for the first time. I had no idea the author was such a character. I thought some of his points in the article were valid, if oversimplified.

---

### Post by SuperMike on 2007-02-21
> **Bloodfen Razormaw said:**
> Very bad news for Ubuntu.  Canonical certainly should not be after a joke like ESR as their spokeman.  Men who try to destroy software freedom from the inside (and complain about distributions that DO respect their freedom, as in that email), who try to pretend they are coders when their only major project was something they took over, then ran into the ground by making it known as one of the least secure applications on the UNIX platform (*coughfetchmailcough*), who has no understanding of hacker culture or hacking yet calls himself a hacker, who has never put a line of code into the linux kernel but calls himself a linux developer, who is openly racist, and so on and so on, are not the kind of people Ubuntu users should want representing them.

Wow, I'll watch out for this live wire. Thanks for the heads-up. I wonder what alias such a person will take here?

I guess if I ask an innocent question in a forum and some fruitcake goes off on me...it could be him.

---

### Post by SuperMike on 2007-02-21
> **spockrock said:**
> any way we can send him back to fedora?

Hilarious! We should try something funny. Perhaps if someone types fetchmail, it can reboot the computer or something.

---

### Post by SuperMike on 2007-02-21
> **Bloodfen Razormaw said:**
> Richard Stallman is just weird, not malicious like ESR (who is also weird, on levels Stallman could only dream of).

Stallman is a completely different animal from ESR:
[LIST]
[*]Unlike ESR, he actually knows how to code[*]Unlike ESR, he doesn't despise freedom and try to tear it apart
[*]Unlike ESR, he has not sent anyone death threats
[*]Unlike ESR, he actually is responsible for a large part of GNU/Linux systems (as opposed to none at all, like ESR)
[*]Unlike ESR, he doesn't pathetically struggle to use big words in a sad attempt to not look like a moron (and in the process misusing those words, attributing quotes to the wrong people, misstating facts about subjects he is trying to pretend he is knowledgeable in etc.)
[*]Unlike ESR, Stallman does not come up with discredited reasons to claim that black people are inferior to whites.
[*]Stallman fought to save software freedom when it was threatened by proprietary software, whereas ESR fought to destroy free software when it became a threat to proprietary software.
[/LIST]

If it takes being a crazy person who behaves strangely to get that package, I'll take it.  I'd rather a person be bizarre than be a criminally violent, self-obsessed, racist, xenophobic, freedom-hating wannabe hacker.

RS is "recursive", someone blogged. He's been known during a presentation to take off his shoes and eat excessive toe skin while you ask questions. I kid you not -- someone's got the video on the web somewhere and blogged about it. He's a hit at frat parties.

As for RS, I like only 40% of his political thoughts but he's a right decent coder. Many GNU tools have his hand in them, along with the docs.

---

### Post by spockrock on 2007-02-21
> **SuperMike said:**
> Hilarious! We should try something funny. Perhaps if someone types fetchmail, it can reboot the computer or something.

hahahaha I was thinking some one could write a patch to the installer when you put in the name Eric S. Raymond, it pops up a window saying, 'GFTO ESR, no ubuntu for you!! >:('

---

### Post by SuperMike on 2007-02-21
> **spockrock said:**
> hahahaha I was thinking some one could write a patch to the installer when you put in the name Eric S. Raymond, it pops up a window saying, 'GFTO ESR, no ubuntu for you!! >:('

Or perhaps when you launch fetchmail, it also launches Firefox and goes to the moonbat site on Wikipedia but in a background process for something like 2 minutes before being killed, which, obviously, he'll catch and get a chuckle out of. Read his Wikipedia entry to see what I'm talking about.

---

### Post by spockrock on 2007-02-21
> **SuperMike said:**
> Or perhaps when you launch fetchmail, it also launches Firefox and goes to the moonbat site on Wikipedia but in a background process for something like 2 minutes before being killed, which, obviously, he'll catch and get a chuckle out of. Read his Wikipedia entry to see what I'm talking about.

I dunno he might send us threatening emails, and then try to drop kick us in the head with his black belt.

---

### Post by Iandefor on 2007-02-21
> **darkhatter said:**
> thanks, I should of went to wikipedia myself.

ok next question, why is this important?Because he's a loud, self-important troll and gets people riled up about absolutely nothing at all. He's switching to Ubuntu from Fedora? Good for him. I've done the same thing and gone the other way, too.

---

### Post by IYY on 2007-02-21
As much as I dislike Eric, it's one of his essays that got me into the world of GNU/Linux to begin with.

---

### Post by DoctorMO on 2007-02-21
hmm, I think some people confuse racism; I always thought racism was about using a persons race to sort of guess what a persons skill, standing, intelligence, wealth, worth and respect quotants were in order to save time bothering to meet people and find out.

sort of like reading a html-css background-color value and assuming the content, javascript events, style, language and html version.

Now I must go away and laugh at the complete daftness of all racists, sexists and xenophobes; it's probably not their fault they think they're saving time by making sweeping generalisations. but sometimes you just have to process the entire html page before rendering.

---

### Post by SunnyRabbiera on 2007-02-22
I am not really havy on this as yes he is racist, I am surprised he did go buntu as Mark Shuttleworth is black.

---

### Post by Iandefor on 2007-02-22
> **SunnyRabbiera said:**
> I am not really havy on this as yes he is racist, I am surprised he did go buntu as Mark Shuttleworth is black.[No, he's not.]("http://en.wikipedia.org/wiki/Image:Mark_Shuttleworth_NASA.jpg")

---

### Post by SuperMike on 2007-02-22
> **IYY said:**
> As much as I dislike Eric, it's one of his essays that got me into the world of GNU/Linux to begin with.

Gosh, I hate to say it, but before I actually learned of Eric's other thoughts, you're right. The Cathedral and the Bazaar was a defining moment for my psyche. I was so stuck on Microsoft while I was consulting with them for a few years, even when I got backstabbed by some of the M$ consulting guys I worked with, that it took essays like his to sway me outside of that to really think at where I was. Now when I look at Microsoft's logo I get a bad taste in my mouth.

---

### Post by kripkenstein on 2007-02-22
> **454redhawk said:**
> LOL.  Please tell me you dont actually subscribe to that crap.:lolflag:

Well, I'd be willing to debate the topic with you, if you want. We should probably move to the Backyard, since it's offtopic, though.

---

### Post by spockrock on 2007-02-22
off topic but I agree kripkenstein, IQ tests do vary cuturally, my OAC(gr.13) Biology teacher wrote an IQ test in detroit and did very poorly, but wrote another one in Canada he did quite well..... IQ test do have a cultural influence......and can affect your score.

---

### Post by slimdog360 on 2007-02-22
> **Iandefor said:**
> [No, he's not.]("http://en.wikipedia.org/wiki/Image:Mark_Shuttleworth_NASA.jpg")

maybe he just saw a ghost.

---

### Post by DoctorMO on 2007-02-22
In space?

---

### Post by JPMaximilian on 2007-02-22
> **Trebuchet said:**
> How can the majority of the black community still be suffering the effects of slavery when none of them have actually lived in it? (Racism, of course, is another issue entirely.)  If slavery were the indirect cause of black Americans' problems those should be decreasing steadily as the slavery recedes into the past.

It probably is decreasing.  

However, lets go back through history a little bit, somewhat hypothetically, you're black and you're free, but your parents were slaves, they have no education and no money, therefore you have no education and no money, then your kids in turn have no education and no money.  It can be hard to break out of that trend, obviously many have, but some haven't.  I realize this is a simplification, and I don't pretend to understand all of the socio-economic issues surrounding slavery and the black community, but it seems plausible to me.  Racism is also involved as well as other factors.  Anyways, thats what I meant.

---

### Post by JPMaximilian on 2007-02-22
> **SunnyRabbiera said:**
> I am not really havy on this as yes he is racist, I am surprised he did go buntu as Mark Shuttleworth is black.

African != Black

---

### Post by Iandefor on 2007-02-22
> **DoctorMO said:**
> In space?Space ghosts can be pretty damn scary. No wonder he turned so white.

---

### Post by Mr.Auer on 2007-02-22
Ok, Id read the "Bazaar" writing of his a long time ago, that was all I knew of him before this. But when i read this in Wikipedia:

"He has also stated that the Western world should embark on an "imperialist" military campaign to "civilize" the Muslim world and eliminate what he claims is its tendency for jihad through "military defeat, Western occupation, and a forced restructuring of society" because of the risk of nuclear terrorism after the September 11 attacks; he acknowledged that some might call this plan "deliberate cultural genocide."[9]

I knew I dont like him one bit :)

Carry on, bozo!
(Maybe Bush admin could use an advocate??)

---

### Post by matthew on 2007-02-22
This thread has drifted pretty far off topic from a discussion of the news item that ESR decided to switch from Fedora to Ubuntu. We've seen sidelines in politics and racism among other things, and those are topics for the backyard. 

In any event, I think the news is out so I'm going to put this drifting thread out of its misery before we end up in an off topic flame war over whether vi or emacs is better. :)

---


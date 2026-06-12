---
title: "Ubuntu: 1/3 of Installs, Upgrades Result in Fail?"
date: 2009-12-04
forum: The Cafe
---

### Post by YosefKaro on 2009-12-04
How on earth could this writer even possibly come up with such statistics?  Especially since every one ubuntu CD can be used to install ubuntu on numerous computers.  What a bogus article this is.  Have a look for yourselves [here]("http://www.suseblog.com/ubuntu-installs-upgrades-fail")

-Yos

---

### Post by madnessjack on 2009-12-04
While I accept that upgrading to a major distro has always failed for me (being about 4 times I've tried) I've never seen problems with a fresh install.

I've given the articles a quick skim, but I don't see any clear citation for that data. Where is he getting it from?

I'm also guessing that's what this guy is going on about :P

---

### Post by Kazade on 2009-12-04
In the linked spreadsheet it says some of the figures come from here... a support forum.

I'm pretty sure that data is skewed, I've never had any major problems upgrading on any PC.

---

### Post by the yawner on 2009-12-04
I know. We should create a reverse support forum. Help! My Ubuntu installation is awesome! That should counter that. Or not?

---

### Post by 3rdalbum on 2009-12-04
I don't believe the "installs with unsolvable issues" actually has its basis in any statistics yet gathered anywhere. Well, I didn't see any way for me to become part of those statistics.

Ubuntu moves much more quickly than OpenSuse. We do a lot more innovation, they just update their packages and add a few more features to Yast. And change their default desktop environment. Considering this, it's amazing that Ubuntu doesn't really seem to be any more broken than OpenSuse anyway; all the major Ubuntu issues I can think of have actually been upstream issues.

---

### Post by mivo on 2009-12-04
The percentage of failed upgrades (not clean installs) is probably much higher than 30%. The percentage of failed clean installs is likely much lower. So, an average of 30% may not be that far off. The dist upgrade option breaking installs is a well known issue of Ubuntu (not only Ubuntu), which is why most people recommend and perform a clean reinstall.

---

### Post by koleoptero on 2009-12-04
I posted a comment on that article. We'll see what he's about if he moderates it.

---

### Post by YosefKaro on 2009-12-04
I wonder how much MicroSloft is paying him.

:popcorn:

-Yos

---

### Post by K.Mandla on 2009-12-04
Ah, Internet journalists. They never cease to amuse me.

---

### Post by Diluted on 2009-12-04
Looks like the spreadsheet came from [here](http://ubuntuforums.org/showthread.php?t=1305924). The author simply copied the columns at the end.

---

### Post by RiceMonster on 2009-12-04
> **YosefKaro said:**
> I wonder how much MicroSloft is paying him.

:popcorn:

-Yos

Do you honestly believe "MicroSloft" is paying some guy to write a blog? Scroll down and look at some of the other blog posts and it makes your conspiracy theory look even more ridiculous.

---

### Post by Dougie187 on 2009-12-04
> **Diluted said:**
> Looks like the spreadsheet came from [here](http://ubuntuforums.org/showthread.php?t=1305924). The author simply copied the columns at the end.

If it really did come from here, the author must have missed the disclaimer at the top.

---

### Post by YosefKaro on 2009-12-04
I left a comment there but will see if this guy will allow it on his blog; I also used the 'contact me' at the left to send him an email.

-Yos

---

### Post by clanky on 2009-12-04
> **YosefKaro said:**
> How on earth could this writer even possibly come up with such statistics?  Especially since every one ubuntu CD can be used to install ubuntu on numerous computers.  What a bogus article this is.  Have a look for yourselves [here]("http://www.suseblog.com/ubuntu-installs-upgrades-fail")

-Yos

That one CD could install an OS which works on one PC, but not on another, I guess it depends on your definition of fail (i Don't have time to read the article) if you mean that it doesn't work flawlessly without further fixes then 30% is probably right, if you mean that it is fundamentally flawed then it sounds very high.

---

### Post by Dragonbite on 2009-12-04
So where are his numbers for the other distributions and how often they fail?

Without a comparison, the whole value of the data becomes moot.  Doesn't matter if he tries smoothing it over with an account for Fedora and openSUSE's failures.

---

### Post by toupeiro on 2009-12-04
*shrug*

I have a machine that I've upgraded on every release since 6.10 and its still running.  Yes, a few things have broke (httpd.conf, postgres and mysql configs) from time to time but nothing that I would say was a dramatic show-stopper.  I couldn't dream of upgrading a windows machine and getting the same success rate.

---

### Post by ZankerH on 2009-12-04
How is it that the overwhelming majority of the people complaining about poor install/upgrade results are completely new users clueless about GNU/Linux, while most of everyone who has the slightest clue about what's happening in their system has had a mostly flawless upgrade?

---

### Post by mivo on 2009-12-04
> **ZankerH said:**
> How is it that the overwhelming majority of the people complaining about poor install/upgrade results are completely new users clueless about GNU/Linux, while most of everyone who has the slightest clue about what's happening in their system has had a mostly flawless upgrade?

Because they don't use the "upgrade" button and just do a fresh install. Beginners and "just users" do. Also, more experienced people have a separate /home partition, so doing fresh installs isn't a huge issue. However, the Ubuntu installer does not create a separate /home partition, and most people who are new to Linux will not use the option to manually partition the disk (they don't know how to and the installer offers no information about it or explains the advantages).

It's one of my gripes with Ubuntu, by the way. That is, the combination of the unreliable (broken) upgrade feature paired with no option to use a pre-defined partitioning layout. It could be something simple like this:

a) Use the entire disk and create one large partition.
b) Use 12 GB for the core system and the rest of the disk for your personal files.
c) Use the partitioner for manually setting up partitions ("?" for more information)

Seems simple enough.

---

### Post by ZankerH on 2009-12-04
> **mivo said:**
> Seems simple enough.

Reading the documentation before you install an operating system you've never used before seems simple enough.

---

### Post by mivo on 2009-12-04
> **ZankerH said:**
> Reading the documentation before you install an operating system you've never used before seems simple enough.

Link me to something on the official Ubuntu site that is compact, covers the basics and is comparable to Arch's Beginner Guide in one, easy-to-read-and-understand document. And, if there is such a link, is it prominently featured on the download page?

That aside, the audience that Ubuntu wants to appeal to is not IT experts and people used to having to read technical documentation before installing an OS. They are mostly people who are used to either purchasing a computer with a pre-installed OS or to just having to insert a CD/DVD.

The Ubuntu installer also contains no recommendation to first read up on the OS. Not even the partitioner includes any links.

If the distro wants to appeal to (and be successful with) a larger number of desktop users, basic stuff like this needs to be covered.

---

### Post by 3rdalbum on 2009-12-04
> **mivo said:**
> The dist upgrade option breaking installs is a well known issue of Ubuntu (not only Ubuntu), which is why most people recommend and perform a clean reinstall.

The Linux Format guys say that Ubuntu's dist-upgrading process is more reliable than, say, Fedora's.

I haven't tried upgrading any other distribution, but I can honestly say I've never had a broken upgrade* (except when going to an alpha) on Ubuntu. I've even dist-upgraded someone else's machine with absolutely no ill effects.

*Not counting the bug in Envy that used to cause graphics cards to not be recognised after a dist-upgrade, but that bug has been fixed for years and the effects could easily be reversed too.

---

### Post by peakshysteria on 2009-12-04
Guess I was pretty lucky then when all four machines in our household worked flawlessly after the last upgrade :popcorn:

---

### Post by clanky on 2009-12-04
> **ZankerH said:**
> How is it that the overwhelming majority of the people complaining about poor install/upgrade results are completely new users clueless about GNU/Linux, while most of everyone who has the slightest clue about what's happening in their system has had a mostly flawless upgrade?

because Ubuntu is only for 1337 haxors right?

---

### Post by madnessjack on 2009-12-04
> **clanky said:**
> because Ubuntu is only for 1337 haxors right?
"Linux for Human Beings"

Apparently...

---

### Post by teward on 2009-12-04
Well, I found a massive flaw in the reasoning.

Those percentages do not add up to 100%.  The "1/3 of installs and upgrades fail" is not statistically valid.

Consider:

Upgrades with problems + Fresh Install with problems + Flawless Upgrades + Flawless Installs = 100%

This **must** be true in order to claim this statistic.

Now, consider this:

If I decide to add these (for Karmic), we get a total of: 136.00% of votes/information.  This poll info, then, cannot be valid due to the overall percentages being over 100%.


Now, also consider:

If I were to add the upgrades groups together, it does not add up to 100%, and if I were to add the install groups together, it does not add up to 100%.

If you REALLY want me to break out the use of the high-powered quad-core computers I have access to, I'd be more than happy to take the raw data from the polls (GIVE ME THE DATA, NOT PERCENTAGES), and I'll run statistical analysis on that.

But don't go around claiming random crap that isn't statistically valid.

---

### Post by teward on 2009-12-04
FINALLY!  I FOUND THE DATA I WAS LOOKING FOR (the poll).

Give me an hour, I'll post the **true** statistics here in a spreadsheet.

---

### Post by teward on 2009-12-04
Okay, here's the statistics from the poll on these forums.

Overall statistics show this:

Flawless installs/upgrades make up 31.58% of the data.
Installs/upgrades with a few but not serious problems make up 32.32% of the data.
Installs/upgrades with serious problems make up 36.11% of the data

For upgrades (and only within the upgrades category):
29.93% of upgrades were flawless.
36.02% of upgrades had a few problems but nothing serious.
34.05% of upgrades had serious problems.

For clean installs (and only within the upgrades category):
33.49% of installs were flawless.
28.01% of installs had a few problems but nothing serious.
38.50% of installs had serious problems.


THIS data is statistically sound, but not the data on the web page linked to us.  That person had NO knowledge of statistics, and did not present the data efficiently.

However, this data is technically not valid for these analyses because the data is not a random sample, thus there's a higher chance for bias.

Okay, I'm done.  I've refuted my own original statements by doing my own statistical analysis. :P

NOW FEAR MY WRATH!!!!!

---

### Post by aysiu on 2009-12-04
Polls are not scientific fact. They can be indicators of truth if you think about the context in which they are given and take that with a grain of salt (and consider the sample size and the sample bias).

Stating that 1/3 of installs and upgrades fail based on a poll on the forums is not a very helpful conclusion to draw. Some things to think about: [list][*]The Ubuntu Forums are only a small segment of the general Ubuntu-using population.[*]There are people who gave up on Ubuntu and did not hang around to the answer the poll. There are also others who happily use Ubuntu without hanging around to answer polls. You have no idea what these populations are.[*]Considering the vast majority of installations and upgrades are on computers that came with Windows preinstalled, 1/3 wouldn't be so bad, even if it were true (we don't know if it is--it could be higher or lower than the actual truth).[/list] More importantly, even if you take the polls at face value, the percentage of successful installs and upgrades actually appears to be growing with every release.

More details here:
[Putting the bad press about Karmic in perspective](http://ubuntuforums.org/showthread.php?t=1316155)

Remember: use your head. Polls aren't totally meaningless. But they are also not the same as irrefutable proof. Polls are rough indicators that have some caveats.

I also think in the long-term improving the installation and upgrade experience will not bring droves of new users to Ubuntu. *Properly configured* preinstallation of Ubuntu with *adequate and well-thought-out* advertising and marketing will bring in "the masses." I don't know many people who do Windows installations or upgrades themselves. They either buy Windows preinstalled or ask their tech-savvy Windows power user friends to do upgrades for them. Hell, even Mac OS X (with its tight hardware-software integration) can have [upgrade problems.](http://ubuntuforums.org/showthread.php?t=80341)

The real question should be "Why do major OEMs who *do* offer Ubuntu preinstalled use Broadcom wireless cards and other Linux-unfriendly hardware components?" or "Why do major OEMs who 'sell' Linux preinstalled still 'Recommend Windows' even on the Linux pages?"

A handful of geeks and power users may enjoy installing and configuring operating systems on self-built computers, but the vast majority of people do not get operating systems--they get computers... and whatever operating system is on the computer when purchased is what these people will use.

---

### Post by teward on 2009-12-04
True, however since I do not have the data of Karmic installs for the entire planet (only these forums), we can guess this is an approximation.

But since this only accounts for 4000-some installs/upgrades/etc, we can only use it as sample data.  Without the population standard deviation, I can't give you all more specific data.  I can, however, do one last statistical evaluation.

I SHALL UNLEASH ONE FINAL BURST OF STATISTICAL DATA, then forget I ever did this.  :P

Be back in about an hour with my statistical data.  :)

---

### Post by Dragonbite on 2009-12-04
> **TrekCaptainUSA said:**
> Okay, here's the statistics from the poll on these forums.

Flawless installs/upgrades make up 31.58% of the data.
Installs/upgrades with a few but not serious problems make up 32.32% of the data.
Installs/upgrades with serious problems make up 36.11% of the data

For upgrades (and only within the upgrades category):
29.93% of upgrades were flawless.
36.02% of upgrades had a few problems but nothing serious.
34.05% of upgrades had serious problems.

For clean installs (and only within the upgrades category):
33.49% of installs were flawless.
28.01% of installs had a few problems but nothing serious.
38.50% of installs had serious problems.

So you are saying that "1/3 of Installs, Upgrades Result in Fail?" is not far from the truth?

(I failed Quantitative and Statistical Analysis the first time through)

---

### Post by aysiu on 2009-12-04
> **TrekCaptainUSA said:**
> True, however since I do not have the data of Karmic installs for the entire planet (only these forums), we can guess this is an approximation.

But since this only accounts for 4000-some installs/upgrades/etc, we can only use it as sample data.  Without the population standard deviation, I can't give you all more specific data.  I can, however, do one last statistical evaluation.

I SHALL UNLEASH ONE FINAL BURST OF STATISTICAL DATA, then forget I ever did this.  :P

Be back in about an hour with my statistical data.  :)
My issue isn't with you. It's with the person linked to in the first post.

---

### Post by t0p on 2009-12-04
> **RiceMonster said:**
> Do you honestly believe "MicroSloft" is paying some guy to write a blog? Scroll down and look at some of the other blog posts and it makes your conspiracy theory look even more ridiculous.

While I agree that YosefKaro's statement is probably unfounded, I think you're either ignorant, naive or disingenuous when you say his "conspiracy theory" is "ridiculous".

Microsoft engaged in astroturfing in the past, and it isn't ridiculous to think they might get up to such shenanigans again.

---

### Post by aysiu on 2009-12-04
> **t0p said:**
> While I agree that YosefKaro's statement is probably unfounded, I think you're either ignorant, naive or disingenuous when you say his "conspiracy theory" is "ridiculous".

Microsoft engaged in astroturfing in the past, and it isn't ridiculous to think they might get up to such shenanigans again.
In other words... general trend, correct; this specific instance, incorrect.

---

### Post by Kevbert on 2009-12-04
In my case it's probably about 1 in 20 installs fail (and that includes Alpha and Beta revisions of Ubuntu).

---


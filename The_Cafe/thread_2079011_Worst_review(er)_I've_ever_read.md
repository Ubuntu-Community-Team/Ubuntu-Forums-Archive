---
title: "Worst review(er) I've ever read"
date: 2012-11-01
forum: The Cafe
---

### Post by kansasnoob on 2012-11-01
I'm just about to lose it! What the heck is this:

[http://distrowatch.com/weekly.php?issue=20121029#feature](http://distrowatch.com/weekly.php?issue=20121029#feature)

What totally blows my mind is where he says:

> After a day and a half of using Ubuntu 12.10 it was an internal struggle not to wipe my hard drive and just find another distribution to review. **[COLOR="Red"]During the first twenty-four hours Ubuntu spied on me[/COLOR]**, provided performance which was distinctly sub par

Just freakin' nuts ](*,)](*,)](*,)

---

### Post by sffvba[e0rt on 2012-11-01
Meh.


404

---

### Post by kansasnoob on 2012-11-01
In a later post the reviewer says:

> Unless you specifically disable the feature Ubuntu monitors your activity, **[COLOR="Red"]keyword searches and keystrokes. Some of these, along with your IP address, are transmitted to third parties.[/COLOR]** As to how i found out, check the privacy settings in your System Settings panel and read the project's legal notice (I linked to the appropriate documents in my review).

I think it's important that we clear that up!

There is undoubtedly some truth to that but that could easily be misconstrued to the point that folks will think their personal passwords and such are at risk in Ubuntu.

BS is BS no matter which way the wind is blowing! Sometimes the smell is just more overwhelming - this is one of those times.

---

### Post by offgridguy on 2012-11-01
I am more interested in this part of the review.
> 
provided performance which was distinctly sub par 

---

### Post by bryanl on 2012-11-01
One man's bug is another's feature ...

and it looks like those who think all features are bugs tend to be more emotional and expressive.

There is also the purist envy thing going on as well and that is tied into anti-capitalist and related ideologies (i.e. it is nearly religious). That is why Ubuntu, especially, is so frequently a target for venemous reviews.

It is an interesting phenomena to study and there have been some papers written about it. The 'privacy' part of this gets a lot of attention which is interesting because the same folks with all the worry about privacy also tend to be those most interested in community and relationships. The smiley in my sidebar - :guitar: - seems quite appropriate here for some reason.

---

### Post by jrog on 2012-11-01
> **kansasnoob said:**
> In a later post the reviewer says:



I think it's important that we clear that up!

There is undoubtedly some truth to that but that could easily be misconstrued to the point that folks will think their personal passwords and such are at risk in Ubuntu.

BS is BS no matter which way the wind is blowing! Sometimes the smell is just more overwhelming - this is one of those times.
What part of what the reviewer said in the passage that you quoted is BS, exactly? It looks as though there is not only "some truth" to what is said in that passage, but complete truth.

What's more, I believe there was (is?) some reasonable concern that even your personal passwords **could** be transmitted by mistake. Here is how. Suppose that you have a terminal open and are about to enter your password (perhaps for some command you are running with 'sudo'). As you are typing, you accidentally hit the Windows key (perhaps with your palm or with a missed attempt to strike 'z', or 'x', or 'SHIFT', or perhaps because you're using a laptop and you accidentally tapped the touchpad with your palm while the pointer was over the Ubuntu logo on the launcher), which causes Dash to open. Since you are a speedy typist, you didn't stop entering your password immediately after accidentally hitting the Windows key (or tapping the touchpad, or whatever), so a few stray characters from your password got entered into Dash's search bar. Those characters from your password are transmitted, AFAIK. This could be a substantial part of your password, particularly if your password is not very long. (There are other possibilities here, too; a new, inexperienced user -- e.g., my grandmother -- might not understand exactly what that bar on Dash is, and think that she should enter her password there. If she does so, it is transmitted, AFAIK.)

You might think that that's no real problem, because whatever is typed in Dash is transmitted securely (over HTTPS) to Canonical's servers. However, there's more to the story. With online search enabled by default, whatever you type is also transmitted to Amazon's servers (along with your IP address), as well as to other servers (e.g., Facebook, Twitter, BBC). In the case of Amazon at least, Amazon's servers return search results based on what you typed, and those search results are **not returned securely**, but are instead returned over a normal (**insecure**) HTTP connection. This allows someone snooping in on your connection to gather information about what you typed into Dash. It may have been your password. It also may have been something else that you don't want others to know about. It is at least disconcerting.

Here are two links with more information about the privacy issues:

[https://www.eff.org/deeplinks/2012/10/privacy-ubuntu-1210-amazon-ads-and-data-leaks](https://www.eff.org/deeplinks/2012/10/privacy-ubuntu-1210-amazon-ads-and-data-leaks)
[http://nakedsecurity.sophos.com/2012/11/01/ubuntu-search-amazon-privacy/](http://nakedsecurity.sophos.com/2012/11/01/ubuntu-search-amazon-privacy/)

---

### Post by snowpine on 2012-11-01
I haven't tried 12.10 yet, but if it's half as bad as 12.04 (which I used extensively) then it deserves the bad review. Surely everyone is entitled to their opinion? :)

---

### Post by mips on 2012-11-01
> **snowpine said:**
> I haven't tried 12.10 yet, but if it's half as bad as 12.04 (which I used extensively) then it deserves the bad review. Surely everyone is entitled to their opinion? :)

Not over here, you can't say bad things about Ubuntu here. It's kinda like going onto a apple forum and saying bad things about os x. It's frowned upon.

---

### Post by snowpine on 2012-11-01
> **mips said:**
> Not over here, you can't say bad things about Ubuntu here. It's kinda like going onto a apple forum and saying bad things about os x. It's frowned upon.

The bad review was on distrowatch.com.

---

### Post by KiwiNZ on 2012-11-01
Following my experience with 12.10 I would have to agree with review, however I would be somewhat less generous about the performance, it is very poor.

---

### Post by Warpnow on 2012-11-01
And the EFF has raised protests that 12.10 does report your searches on your own hard drive in an unsecure way. Someone could tap into your internet and know what files you are searching for on your own computer.

---

### Post by javagreen on 2012-11-01
My personal endeavour with 12.10 has been spectacularly problematic, owing to the fact that they "forgot" to bundle the Linux Headers for their kernel. 

So, after I installed the proprietary driver, Ubuntu (Unity) decided that my 24" LeD is a "Laptop" and wouldn't go a nit above 1024x768 rendering it unusable because it didn't scale properly and I couldn't see neither the sidebar nor the menubar. Luckily for me, I found out I had to drop back to the Nouveau driver, install the Linux headers and *then* go for the proprietary driver.  How many others know about this?

Unity in 12.10 is also *far* far more sluggish than 12.04 ever was on my Quad Core + 4 GB RAM system, there's no other way to put it.  I can second the reviewers statement, that performance has in fact worsened considerably.

---

### Post by KiwiNZ on 2012-11-01
> **Warpnow said:**
> And the EFF has raised protests that 12.10 does report your searches on your own hard drive in an unsecure way. Someone could tap into your internet and know what files you are searching for on your own computer.

These sort of features should not be default they should be "opt in" and password activated, it simply bad and unprofessional design as it is currently implemented.

---

### Post by viperdvman on 2012-11-01
> **mips said:**
> Not over here, you can't say bad things about Ubuntu here. It's kinda like going onto a apple forum and saying bad things about os x. It's frowned upon.

Freedom of speech, my man. If you can intelligently say that you dislike (e.g.) 12.10 or 12.04, giving logical reasons as to why you dislike it, then that's perfectly acceptable. But 
outright bashing and trolling, and harassing the other people in the forums, is what's frowned upon here.

I really haven't played with Ubuntu 12.10's Unity much outside of a LiveUSB environment, so I really can't form an opinion. I use KDE as my primary DE, which is why I switched to Kubuntu for this 6-month cycle. So I can say that at least Kubuntu got a lot of stuff done right, and it flies every bit as much as Kubuntu 12.04 did.

But yeah, Distrowatch really did not like 12.10... about as much as they didn't like 11.10 *(very few, if any, bad reviews can top 11.04)*.

> **javagreen said:**
> My personal endeavour with 12.10 has been  spectacularly problematic, owing to the fact that they "forgot" to  bundle the Linux Headers for their kernel. 

So, after I installed the proprietary driver, Ubuntu (Unity) decided  that my 24" LeD is a "Laptop" and wouldn't go a nit above 1024x768  rendering it unusable because it didn't scale properly and I couldn't  see neither the sidebar nor the menubar. Luckily for me, I found out I  had to drop back to the Nouveau driver, install the Linux headers and *then* go for the proprietary driver.  How many others know about this?

Unity in 12.10 is also *far* far more sluggish than 12.04 ever was  on my Quad Core + 4 GB RAM system, there's no other way to put it.  I  can second the reviewers statement, that performance has in fact  worsened considerably.

Again, I ran Ubuntu 12.10 in a LiveUSB environment, having switched to the onboard intel since my graphics card takes up plenty of space, and I needed my IDE adapter (whose slot was partially blocked by the graphics card). I did that as part of the final phase of my data recovery (recovering older files and file tree structures from my older data hard drive). I didn't pay much attention to it since I was only doing data recovery, but Unity's performance on the onboard Intel graphics seemed to be pretty okay. But then again I haven't tested it with the proprietary NVidia drivers (nouveau doesn't work with my GeForce GTX 560).

I too have been hearing all around that Ubuntu 12.10 didn't come with the linux-headers, which is a mistake, thus making installing proprietary graphics drivers difficult... if not easily bricking your Ubuntu install. My Kubuntu 12.10 came with the linux-headers, so I was able to install the NVidia drivers from the repositories with no problems at all (using software sources in Kubuntu didn't work... I just installed from the repositories).

---

### Post by Paqman on 2012-11-01
> **KiwiNZ said:**
> I would be somewhat less generous about the performance, it is very poor.

This must be hardware-dependent. I've found 12.10 to be significantly faster than 12.04, specifically the speed of the Dash. It was annoyingly slow before, but now I actually use it.

---

### Post by localhost8080 on 2012-11-01
i am quite concerned that ubuntu is turning into an advertising platform for amazon.  though I do know that there is a way to uninstall all that madness, it would surely be better for the users to have it as an optional installation, maybe by asking them a question during install, like

to support us by letting us install these adverts and get affiliate money when you buy things, please tick this box

and have the button UNTICKED by default, making it an opt-in rather than an opt-out...

---

### Post by KiwiNZ on 2012-11-01
> **Paqman said:**
> This must be hardware-dependent. I've found 12.10 to be significantly faster than 12.04, specifically the speed of the Dash. It was annoyingly slow before, but now I actually use it.

I would agree if I had only tested on one machine, however I have tried it on the following....

Antique Core 2 Duo 2GHZ, 8GB Ram, Nvidia Graphics

i5 Dual Core, 8 GB Ram ATI Graphics

i7 Quad Core , 16 GB Ram ATI Graphics

AMD Multi core, 16GM Ram, Dual ATI Graphics

Now I did not expect stellar performance on the Core2 Duo but the other machines are no slouches, but the performance was abysmal for a modern OS on modern hardware, frankly I expect way better.

---

### Post by nothingspecial on 2012-11-01
> **mips said:**
> Not over here, you can't say bad things about Ubuntu here. It's kinda like going onto a apple forum and saying bad things about os x. It's frowned upon.

No it is not. Going on and on and on about it over and over again is.

---

### Post by Pilot6 on 2012-11-01
That is exactly true. I have almost identical experience.

---

### Post by jrog on 2012-11-01
> **KiwiNZ said:**
> I would agree if I had only tested on one machine, however I have tried it on the following....

Antique Core 2 Duo 2GHZ, 8GB Ram, Nvidia Graphics

i5 Dual Core, 8 GB Ram ATI Graphics

i7 Quad Core , 16 GB Ram ATI Graphics

AMD Multi core, 16GM Ram, Dual ATI Graphics

Now I did not expect stellar performance on the Core2 Duo but the other machines are no slouches, but the performance was abysmal for a modern OS on modern hardware, frankly I expect way better.
I notice no Intel cards. I've also found 12.10's performance to be excellent, but I've only used it on Intel graphics.

---

### Post by KiwiNZ on 2012-11-01
> **jrog said:**
> I notice no Intel cards. I've also found 12.10's performance to be excellent, but I've only used it on Intel graphics.

I am going to test it on an old i5 laptop I have here that has Intel Graphics today, I just have to throw some more Ram in it first, it only had 4GB at present, its been sitting unused for quite some time.

It will interesting to see how it goes.

---

### Post by Mikeb85 on 2012-11-01
> **jrog said:**
> I notice no Intel cards. I've also found 12.10's performance to be excellent, but I've only used it on Intel graphics.

+1

It's incredibly fast on my i7 w/ Intel HD 4000...

---

### Post by x-shaney-x on 2012-11-01
I don't think performance itself is that bad, it's decent but the dash is horrible, simply horrible on the hardware I've tried it on and to anyone using the dash regularly that may give an impression of sluggishness in general.

as far as "spying", whether or not this is the case (and no, I don't think it is), plenty of people are getting that impression and I think this whole shopping lens business has been a disaster for canonical.

Of course the fuss will pass in time, like all the other big ubuntu issues have come and gone.

Though it does make me wonder, how many people complaining about the shopping lens have a smartphone in their pocket that is full of apps connecting to one place or another?

---

### Post by Chdslv on 2012-11-01
Jesse's computers play havoc most of the time. His reviews are biased anyway. Its time someone started an "alternate" web site like that. In the first few days, that Distrowatch is a place for some guys to rant about--see the comments--these comments are practically always the same; most of them are Ubuntu-bashing ones.

12.10 was with me from its Alpha and was updated/upgraded to the final 12.10 release. One could say, it was already 12.10 final the day before it was released. The apport problem was annoying alright, but could be easily turned off--there was never a real crash in my nearly 4 year old laptop.

I am on Raring now, starting from 12.10 mini.iso and turning to raring repos. It actually flies. 

It is bleeding edge and quite naturally all apps would be checked thoroughly, before added. I have no idea, why anyone would want another bleeding edge distro (Arch or Gentoo), when we really have good devs, both Cannonical and the Community. I like this bleeding edge touch. :)
I have a Raring Gnome-Plasma-Unity distro! 

Reviewer, usually looks for problems, so is biased even before he starts.

---

### Post by mamamia88 on 2012-11-01
I don't get it.   In the conclusion he says the performance was subpar but in the text of the review he says it performed fairly well.   there is a difference.  anyway i don't think it's the worst review ever.

---

### Post by cprofitt on 2012-11-01
> **KiwiNZ said:**
> I would agree if I had only tested on one machine, however I have tried it on the following....

Antique Core 2 Duo 2GHZ, 8GB Ram, Nvidia Graphics

i5 Dual Core, 8 GB Ram ATI Graphics

i7 Quad Core , 16 GB Ram ATI Graphics

AMD Multi core, 16GM Ram, Dual ATI Graphics

Now I did not expect stellar performance on the Core2 Duo but the other machines are no slouches, but the performance was abysmal for a modern OS on modern hardware, frankly I expect way better.

I have 12.10 on two different machines as well... and not found it to be sluggish.

i7-3720 16GB ram Intel Graphics
t8400 4GB ram Intel Graphics

I did notice that you have one common feature to your rigs -- ATI graphics; could that be the issue vs. my Intel Graphics?

what specific benchmarks or areas are you finding issue with?

---

### Post by forrestcupp on 2012-11-01
> **KiwiNZ said:**
> These sort of features should not be default they should be "opt in" and password activated, it simply bad and unprofessional design as it is currently implemented.If they made these things "opt in", nobody would opt in. ;)

> **KiwiNZ said:**
> I would agree if I had only tested on one machine, however I have tried it on the following....

Antique Core 2 Duo 2GHZ, 8GB Ram, Nvidia Graphics

i5 Dual Core, 8 GB Ram ATI Graphics

i7 Quad Core , 16 GB Ram ATI Graphics

AMD Multi core, 16GM Ram, Dual ATI Graphics

Now I did not expect stellar performance on the Core2 Duo but the other machines are no slouches, but the performance was abysmal for a modern OS on modern hardware, frankly I expect way better.It's time to give in to the dark side and just use KDE. :D

> **KiwiNZ said:**
> I am going to test it on an old i5 laptop I have here that has Intel Graphics today, I just have to throw some more Ram in it first, it only had 4GB at present, its been sitting unused for quite some time.

It will interesting to see how it goes.I have an i3 with only 4GB of RAM and Intel HD Graphics 3000. It runs just fine without any problems. It's starting to look like intel graphics are the best for Linux, if you're not into heavy gaming.

---

### Post by kuvanito on 2012-11-01
it's been a while since i last posted
people here know me for being controversial
but after a week of using 12.10 i am now back to 10.04
what an oops!

---

### Post by kuvanito on 2012-11-01
> **forrestcupp said:**
> I have an i3 with only 4GB of RAM and Intel HD Graphics 3000. It runs just fine without any problems. It's starting to look like intel graphics are the best for Linux, if you're not into heavy gaming.

best statement i have read lately,hurray! finally some one figures this out :) AMD,ATI and Nvidia are out!

---

### Post by jerome1232 on 2012-11-01
> **forrestcupp said:**
> 
It's time to give in to the dark side and just use KDE. :D


You know it's funny, I even like Unity but have been giving KDE a look or two recently, maybe I'll actually try it when the next LTS comes out.

I think Unity's sluggishness is getting to me on my netbook, it's just slow. Pretty, but slow.

---

### Post by KiwiNZ on 2012-11-01
> **forrestcupp said:**
> If they made these things "opt in", nobody would opt in. ;)

It's time to give in to the dark side and just use KDE. :D

I have an i3 with only 4GB of RAM and Intel HD Graphics 3000. It runs just fine without any problems. It's starting to look like intel graphics are the best for Linux, if you're not into heavy gaming.

I have a test machine running Kubuntu 12.10, its a i5, 8GB Ram with Nvidia Graphics and it is fine.

---

### Post by eddier on 2012-11-01
Jrog-thats a pretty small window of opportunity you describe there. 

You best shut your curtains in case the guy (or guy-ess) is watching you from across the road with binoculars.

In comparison to the Windows scenario this pales into insignificance.

I wonder what OS the reviewer uses??

eddie

---

### Post by jrog on 2012-11-01
> **eddier said:**
> Jrog-thats a pretty small window of opportunity you describe there.
For the password thing, perhaps. Not necessarily in the case where someone wants to monitor the things you're searching for, though; there is the real possibility for long-term snooping on returned results. See the EFF article for more on that.

Let me just also say that I'm not trying to argue that this is a massive security disaster. All I'm saying is that there is at least some room for concern; the review isn't just "BS," as was suggested earlier.

> You best shut your curtains in case the guy (or guy-ess) is watching you from across the road with binoculars.
There's at least one crucial difference between these two cases. Anyone who opens their curtains chooses to do so and is well aware that people could be looking through the window in some way if they are open. They are also well aware of the need to close their curtains for privacy, and of how to do so. In the case of Dash, however, the policy is **opt-out** rather than opt-in, and there is nothing very conspicuous to make you aware of what it is doing, or of the fact that parts of the process are transferred over an insecure connection that some third party could see, or of how to disable it to re-establish your privacy. All of these things can be discovered if one chooses to investigate (and sometimes it requires a bit of work), but, if one doesn't, one remains more or less unaware of the fact that one's search results on one's computer are being transmitted to various places and having the results sent back insecurely (etc.), or of how to rectify the situation. That isn't the case with one's curtains and one's windows. This is presumably one reason that people (like the EFF) are pushing for this to be opt-in rather than opt-out.

> In comparison to the Windows scenario this pales into insignificance.

I wonder what OS the reviewer uses??

eddie
I don't know, and I can't see how it matters. I don't use Windows, and I wasn't making any comparison to Windows -- nor was the reviewer, in the small parts of the review that I read. Even if Windows is worse, the old saying that "two wrongs don't make a right" seems to apply here. Windows may be worse, but this thing that Ubuntu does could still be concerning.

---

### Post by Warpnow on 2012-11-01
> **KiwiNZ said:**
> These sort of features should not be default they should be "opt in" and password activated, it simply bad and unprofessional design as it is currently implemented.

Definitely unprofessional. I feel the last few Ubuntu releases have been like that. Features that might be good, but not 100% perfected before being pushed out. 

Product searches isn't a horrible idea. It provides funding, could be useful, but its a very delicate issue. Implementing it without it being fully fleshed out is just unprofessional. 

I can deal with code that's faulty, glitchy, or incomplete. But when it is ideas that are, it just feels half-assed.

---

### Post by KiwiNZ on 2012-11-01
> **warpnow said:**
> definitely unprofessional. I feel the last few ubuntu releases have been like that. Features that might be good, but not 100% perfected before being pushed out. 

Product searches isn't a horrible idea. It provides funding, could be useful, but its a very delicate issue. Implementing it without it being fully fleshed out is just unprofessional. 

I can deal with code that's faulty, glitchy, or incomplete. But when it is ideas that are, it just feels half-assed.

+1

---

### Post by sffvba[e0rt on 2012-11-02
YMMV and this seems to hold true for many distro's (just go to some of them with forums and see)...

As for performance, I posted this in another thread already but anyhow... I installed 12.10 on a I7 with 8GB Ram and AMD/ATI Radeon 6850 graphics, installed the proprietary drivers and the system was super stable, responsive and on par with my 12.04 experience (which is also stable and fast).

Upgraded from 12.04 to 12.10 on my laptop (oldish HP 530 with Core Duo 32-bit processor) and Intel 945 graphics... no issues what so ever.  If this had been my first install of Ubuntu I would have been very impressed and happy with it.


404

---

### Post by mr john on 2012-11-02
Every time I search for something on my computer through the dash  the search query is getting sent over the Internet to third parties? That's a bit of an invasion of privacy. Is the search query encrypted before it's sent? Do new users get informed of this activity?

For me there isn't much different in performance. I know there are much faster distros out there, but don't want to sacrifice having a good sized support community.  I do like being able to have my favourite web services in the sidebar though, it makes the OS look more modern than any other OS.

---

### Post by viperdvman on 2012-11-02
> **forrestcupp said:**
> It's time to give in to the dark side and just use KDE. :D

> **jerome1232 said:**
> You know it's funny, I even like Unity but  have been giving KDE a look or two recently, maybe I'll actually try it  when the next LTS comes out.

I've been using KDE regularly since the beginning of the second quarter of the year, and off and on before that... to the point that I'm using Kubuntu for the 12.10 cycle. So consider me having given in to the dark side :D

> **KiwiNZ said:**
> I have a test machine running Kubuntu 12.10, its a  i5, 8GB Ram with Nvidia Graphics and it is fine.

Core i3 with 8GB RAM and an NVidia GTX 560... proprietary drivers *(nouveau drivers don't work for my newer card... but have always sucked with my past NVidia setups)*. Kubuntu 12.10 works perfectly fine on my system.

> **mr john said:**
> Every time I search for something on my computer  through the dash  the search query is getting sent over the Internet to  third parties? That's a bit of an invasion of privacy. Is the search  query encrypted before it's sent? Do new users get informed of this  activity?

The way I see it... it's really not much different than anyone who uses Google Chrome... or Chrome OS... or Android. Most everything you do in **any** of those browsers/OS's is sent to 3rd parties.

---

### Post by kansasnoob on 2012-11-02
A couple of things I'd like to clarify :)

#1: I did encounter considerable performance problems with Ubuntu Quantal and wrote a bit about that here:

[http://ubuntuforums.org/showpost.php?p=12316768&postcount=143](http://ubuntuforums.org/showpost.php?p=12316768&postcount=143)

#2: My greatest concern is all of the FUD surrounding the integration of Amazon search results in the Dash. Mark addressed a great number of those here:

[http://www.markshuttleworth.com/archives/1182](http://www.markshuttleworth.com/archives/1182)

Be sure and browse through the replies :)

---

### Post by Linuxisfast on 2012-11-02
What an irony, Ubuntu 12.10 runs like a dream on my icore5 laptop and several other laptops and netbooks I have installed it in, different strokes for different folks, time Linux starts tying up hardware to software a la Apple I guess.

---

### Post by forrestcupp on 2012-11-02
> **KiwiNZ said:**
> I have a test machine running Kubuntu 12.10, its a i5, 8GB Ram with Nvidia Graphics and it is fine.Like I said, KDE! :)
But even Unity works well for me on my intel graphics.

> **not found said:**
> 
As for performance, I posted this in another thread already but anyhow... I installed 12.10 on a I7 with 8GB Ram and AMD/ATI Radeon 6850 graphics, installed the proprietary drivers and the system was super stable, responsive and on par with my 12.04 experience (which is also stable and fast).Yeah, I think we still need the proprietary drivers for the best performance, in most cases. I'd be interested to know whether Kiwi used the proprietary drivers or not. I have a hard time believing it would be that sluggish on a system that beefy.

---

### Post by jrog on 2012-11-02
> **mr john said:**
> Every time I search for something on my computer through the dash  the search query is getting sent over the Internet to third parties?
Thanks for your post. The fact that you didn't know this is further evidence that there may be good reasons to be concerned about it. (The answer to your question is "yes," by the way -- your keystrokes are sent to third parties such as Facebook, Twitter, Amazon, and BBC. Here is the legal notice describing this: [https://ubuntuone.com/13SGu7nK2SuqlgiR8zkmXF](https://ubuntuone.com/13SGu7nK2SuqlgiR8zkmXF))

> That's a bit of an invasion of privacy. Is the search query encrypted before it's sent?
Yes. However, the returned results are apparently not encrypted, which means that someone snooping on your connection could theoretically use them to determine what you typed. See the example given in the article here: [https://www.eff.org/deeplinks/2012/10/privacy-ubuntu-1210-amazon-ads-and-data-leaks](https://www.eff.org/deeplinks/2012/10/privacy-ubuntu-1210-amazon-ads-and-data-leaks).

> Do new users get informed of this activity?
In a sense, yes, and in a sense, no. If you are using 12.10, you should see a little 'i' icon in the lower right corner of Dash when you use it. If you click that icon, you will see the legal notice to which I linked above. But that is the only notification, AFAIK, and is not very conspicuous. (Again, if you are already using 12.10 and didn't know about it, then that it is some evidence that it may not be conspicuous enough.)

---

### Post by malspa on 2012-11-02
> **jrog said:**
> (The answer to your question is "yes," by the way -- your keystrokes are sent to third parties such as Facebook, Twitter, Amazon, and BBC. Here is the legal notice describing this: [https://ubuntuone.com/13SGu7nK2SuqlgiR8zkmXF](https://ubuntuone.com/13SGu7nK2SuqlgiR8zkmXF))

Thanks for posting this.

I'm not sure if this will make me want to stop using Ubuntu in the future, because I would certainly opt out of using of the online search, but I hope they'll change it to "opt-in."

Note the last part of that notice. Maybe concerned folks will want to drop them a line:

> How to contact us
Please submit any questions or comments about searching in the dash or this legal notice by contacting us at the following address: Canonical Group Ltd, 5th Floor, Blue Fin Building, 110 Southwark Street, London, England, SE1 0SU.

---

### Post by samalex on 2012-11-02
I'm still not sold on Unity, so when I moved from 10.04 to 12.04 I jumped from Ubuntu to XUbuntu since it's just cleaner and simpler.  I've been using Linux for 15 years now, 10 of that as my primary desktop, and I just don't like the way Ubuntu has changed the desktop with Unity.  Less is more -- and I'm finding XFCE does that very well.

---

### Post by drawkcab on 2012-11-02
If 12.10 is junk, it's junk.  Ubuntu is not a religion.  

That said, I haven't given it a shot yet.  12.10 doesn't have anything to recommend it over 12.04 which has been just great for me on all my machines.

---

### Post by Chdslv on 2012-11-02
> **drawkcab said:**
> If 12.10 is junk, it's junk.  Ubuntu is not a religion.  

That said, I haven't given it a shot yet.  12.10 doesn't have anything to recommend it over 12.04 which has been just great for me on all my machines.

If you've not given it a shot, then you don't really know what it is, so how about "giving it a shot" and then "recommend" it or not?

How do you recommend a Honda, while driving a Toyota?

---

### Post by drawkcab on 2012-11-02
> **Chdslv said:**
> If you've not given it a shot, then you don't really know what it is, so how about "giving it a shot" and then "recommend" it or not?

How do you recommend a Honda, while driving a Toyota?

In the same spirit, how about making a sincere attempt to understand what I'm saying in my post before offering criticism that is inappropriate?

---

### Post by Warpnow on 2012-11-03
> **viperdvman said:**
> 
The way I see it... it's really not much different than anyone who uses Google Chrome... or Chrome OS... or Android. Most everything you do in **any** of those browsers/OS's is sent to 3rd parties.

But its better implemented. Google explains how it works in pretty good detail, and does take action to keep it anonymous to prevent anyone from connecting it to an actual person. Its not what Ubuntu is doing that's the problem-- its the poor implementation .

---

### Post by cariboo on 2012-11-04
> **Warpnow said:**
> But its better implemented. Google explains how it works in pretty good detail, and does take action to keep it anonymous to prevent anyone from connecting it to an actual person. Its not what Ubuntu is doing that's the problem-- its the poor implementation .

The shopping lens was implemented quite late in the development cycle, I'd suggest we all come back at the end of the Raring Ringtail development cycle to revisit everything that has been mentioned in this thread.

---

### Post by skyiscrying on 2012-11-04
If you happen to use Libre Office, stay with 12.04. There's Libre Office installed there alright but without the Menu Bar which is supposed to be managed by the HUD in Unity. I'm not happy as I use Calc quite a bit. Strange though, if you install GNOME through the software centre and select that, Libre Office works as per normal. I think Unity is going the same way as Windows 8  - it's a dogs breakfast.

---

### Post by Linuxisfast on 2012-11-04
12.04 has LO menubar that works quite well when installed via USC, also if you add the LO ppa, it updates to latest 3.6 which works without a hitch.

---

### Post by jrog on 2012-11-04
> **Linuxisfast said:**
> 12.04 has LO menubar that works quite well when installed via USC, also if you add the LO ppa, it updates to latest 3.6 which works without a hitch.
The global menubar in LibreOffice is quite broken in 12.10 right now (and has been since release... and was before release, too).

---

### Post by kdrainey on 2012-11-04
I have had some problems with 12.10 which concern me.  It did slow down.  There was a lot of clutter with the Amazon ads.  I am not an Amazon hater.  I own a Kindle.  I used Amazon a lot before 12.10.  

And there are more "Aw Jim he's dead" notices in Chrome.

I would be a grateful for a step-by-step guide to how we can turn off all the new tracking features until we can get better assurance of privacy and that these features are not costing a lot in performance.

---

### Post by codingman on 2012-11-04
I'm so glad I switched over to Xubuntu, I have to update it to 12.10 and try that out, this useless Athlon FX-55's slowness is really getting to me...

---

### Post by kansasnoob on 2012-11-04
I could very well be wrong but I believe most of the performance issues are related to "compiz + llvmpipe" rather than how "search" is handled from dash :confused:

But regarding security I choose to trust SABDFL, it's just that simple :D

---

### Post by kurt18947 on 2012-11-04
> **skyiscrying said:**
> If you happen to use Libre Office, stay with 12.04. There's Libre Office installed there alright but without the Menu Bar which is supposed to be managed by the HUD in Unity. I'm not happy as I use Calc quite a bit. Strange though, if you install GNOME through the software centre and select that, Libre Office works as per normal. I think Unity is going the same way as Windows 8  - it's a dogs breakfast.

It's the first release after an LTS.  I'm currently using 12.10 gnome remix.  It works mostly okay.  I also have a 12.04 install which is rock solid.  I also have an Xubuntu 12.04 install just in case:P.  Hard drive space is still pretty cheap, 25 GB is plenty for a *buntu install and I'm not gonna get any visits from the BSA thugs so no worries here.

---

### Post by cariboo on 2012-11-05
> **kdrainey said:**
> I have had some problems with 12.10 which concern me.  It did slow down.  There was a lot of clutter with the Amazon ads.  I am not an Amazon hater.  I own a Kindle.  I used Amazon a lot before 12.10.  

And there are more "Aw Jim he's dead" notices in Chrome.

I would be a grateful for a step-by-step guide to how we can turn off all the new tracking features until we can get better assurance of privacy and that these features are not costing a lot in performance.

Go to System Settings->Privacy, to turn off the shopping lens.

---

### Post by viperdvman on 2012-11-26
Kubuntu 12.10 ran perfectly on my system, and was actually more stable than 12.04 (which has tendencies to segfault... not the least bit debilitating, just an annoyance... and Flash is mostly the culprit). However, it also seemed to use more RAM than 12.04 as well. 

A few things I did miss from 12.10 was: **AWN** and **Kompozer** removed from the repos (and probably a number of other apps and packages that I haven't noticed), and **snes9x-gtk** from Bearoso's PPA doesn't have Quantal support.

AWN can easily be installed from a PPA, and Kompozer has to be installed from the Ubuntu archives. Snes9x-gtk, however, has to be downloaded and either compiled or run as a pre-made execute... the former which is a major PITA (and I never got to work... probably 'cause I didn't have the right gtk-dev packages and other dependencies), and the latter is very inconvenient.

Granted, AWN has been troublesome in 12.04 with the **+ always showing** problem in the task manager and simple launcher applets (rendering the latter useless). But the PPA seemed to fix that, at least in Quantal. I do use these apps quite a bit, so for now I'm back to running Kubuntu 12.04 (with KDE 4.9.3 installed via PPA).

---

### Post by letkajenkka on 2012-11-26
I don't know if it's the worst review of Ubuntu, but definitely nowhere close to being the worst review in general. Compared with stuff like game informer's review of Sonic Generations it's actually a good review, seeing people's impressions of 12.10.

---

### Post by mastablasta on 2012-11-26
> **viperdvman said:**
>  
 and **Kompozer** removed from the repos .
 
kompozer is rubish (stable was ok but latest version is missing in functions) and it's development has stalled. there are plenty better alternatives with active development out there.  you have blue fish, blue griffon... have a lok: [http://en.wikipedia.org/wiki/Comparison_of_HTML_editors](http://en.wikipedia.org/wiki/Comparison_of_HTML_editors)

---

### Post by D_E_H0987 on 2012-11-26
I was reading this and I notice people who have tried Ubuntu 12.10 for the most part say its slower, but most of the ones that mention it works well for them say they are using Intel video or a laptop.  

I'm wondering if those of you that say 12.10 works well are using on board graphics rather than a separate video card?   Most laptops are on board video.

Now if this is the case, then my guess,  is that the PCIe drivers mite be the source of the slowdown.     As I recall Intel had a few bugs in its drivers for its early PCIe chipsets on Windows.

---

### Post by Mikeb85 on 2012-11-26
Recently upgraded my desktop to 12.10 (Intel Core 2 Duo + Nvidia GT 560), and it works great.  

One thing I found is that Google Chrome had some sort of regression, it really slowed down both of my systems, I purged it and installed Chromium and both are nice and snappy again.

---

### Post by cbennett926 on 2012-11-27
> **D_E_H0987 said:**
> I was reading this and I notice people who have tried Ubuntu 12.10 for the most part say its slower, but most of the ones that mention it works well for them say they are using Intel video or a laptop.  

I'm wondering if those of you that say 12.10 works well are using on board graphics rather than a separate video card?   Most laptops are on board video.

Now if this is the case, then my guess,  is that the PCIe drivers mite be the source of the slowdown.     As I recall Intel had a few bugs in its drivers for its early PCIe chipsets on Windows.

I have a laptop with the specs below, its got dedicated and integrated. I also have a desktop with an Intel chipset and it's running amazing. I for one love 12.10, it's a great step forward for the younger bunch.

---

### Post by TeamRocket1233c on 2012-11-27
Well, Ubuntu 12.10 with Unity being slower really depends on the hardware. I have an HP Compaq dc5750 with an AMD Sempron 3400+ ~1.8GHz  and half a gig of RAM under the hood, running Ubuntu 12.10 with Unity, and it's blazing fast, but it could be **painfully** slow on a P4 with the same amount of RAM, for example.

---

### Post by mythic97 on 2012-11-27
yes 12.10 is not that stable but if it is unstable go get 12.04 that's what I did or try Lubuntu or Xbutuntu unity is slow on my laptop but still better than windows

---

### Post by viperdvman on 2012-11-27
> **mastablasta said:**
> kompozer is rubish (stable was ok but latest version is missing in functions) and it's development has stalled. there are plenty better alternatives with active development out there.  you have blue fish, blue griffon... have a lok: [http://en.wikipedia.org/wiki/Comparison_of_HTML_editors](http://en.wikipedia.org/wiki/Comparison_of_HTML_editors)

I do have BlueFish already for most of my coding needs. However, BlueGriffon is not in the repos (at least not in Precise).

---

### Post by jerome1232 on 2012-11-28
> **jrog said:**
> What part of what the reviewer said in the passage that you quoted is BS, exactly? It looks as though there is not only "some truth" to what is said in that passage, but complete truth.

What's more, I believe there was (is?) some reasonable concern that even your personal passwords **could** be transmitted by mistake. Here is how. Suppose that you have a terminal open and are about to enter your password (perhaps for some command you are running with 'sudo'). As you are typing, you accidentally hit the Windows key (perhaps with your palm or with a missed attempt to strike 'z', or 'x', or 'SHIFT', or perhaps because you're using a laptop and you accidentally tapped the touchpad with your palm while the pointer was over the Ubuntu logo on the launcher), which causes Dash to open. Since you are a speedy typist, you didn't stop entering your password immediately after accidentally hitting the Windows key (or tapping the touchpad, or whatever), so a few stray characters from your password got entered into Dash's search bar. Those characters from your password are transmitted, AFAIK. This could be a substantial part of your password, particularly if your password is not very long. (There are other possibilities here, too; a new, inexperienced user -- e.g., my grandmother -- might not understand exactly what that bar on Dash is, and think that she should enter her password there. If she does so, it is transmitted, AFAIK.)

You might think that that's no real problem, because whatever is typed in Dash is transmitted securely (over HTTPS) to Canonical's servers. However, there's more to the story. With online search enabled by default, whatever you type is also transmitted to Amazon's servers (along with your IP address), as well as to other servers (e.g., Facebook, Twitter, BBC). In the case of Amazon at least, Amazon's servers return search results based on what you typed, and those search results are **not returned securely**, but are instead returned over a normal (**insecure**) HTTP connection. This allows someone snooping in on your connection to gather information about what you typed into Dash. It may have been your password. It also may have been something else that you don't want others to know about. It is at least disconcerting.

Here are two links with more information about the privacy issues:

[https://www.eff.org/deeplinks/2012/10/privacy-ubuntu-1210-amazon-ads-and-data-leaks](https://www.eff.org/deeplinks/2012/10/privacy-ubuntu-1210-amazon-ads-and-data-leaks)
[http://nakedsecurity.sophos.com/2012/11/01/ubuntu-search-amazon-privacy/](http://nakedsecurity.sophos.com/2012/11/01/ubuntu-search-amazon-privacy/)
I find it more likely that a user might tab to their google search and type their password in there instead of into the email login box which is where they intended to type it.

I mean really? You're really arguing that someone might accidentally be smashing around their keyboard and accidentally type their password into this giant semi-transparent window that pops up because they "accidentally" hit a key that is rather out of the way of the normal typing area?

It sounds like that rubbish that people where accidentally hitting ctrl+alt+backspace and so the key combo was changed to restart the xserver.

---

### Post by jrog on 2012-11-28
> **jerome1232 said:**
> I find it more likely that a user might tab to their google search and type their password in there instead of into the email login box which is where they intended to type it.

I mean really? You're really arguing that someone might accidentally be smashing around their keyboard and accidentally type their password into this giant semi-transparent window that pops up because they "accidentally" hit a key that is rather out of the way of the normal typing area?

It sounds like that rubbish that people where accidentally hitting ctrl+alt+backspace and so the key combo was changed to restart the xserver.
A couple (TL;DR?) things about this:

First, there seem to be a couple of important differences between the Google search example that you mention here and the example involving Dash. I'm not sure exactly what scenario you're envisioning, but maybe it's one of the following: 

[LIST=1]
[*]a user is about to type in their email password, but accidentally hits the tab key enough times to change the focus to the URL bar (or the Google search bar, if they have one) and types in their password there;
[*]a user is about to type in their email password, but accidentally hits the keys that cause a new tab to open, where the default page is the Google search, and begins typing their password into the Google search box; 
[*]a user is about to type in their email password, has the Google search page open in another tab, accidentally hits the keys that switch the focus to that tab, and types in the password into the Google search box. 
[/LIST]

But here are some important differences:

[LIST=1]
[*]In case #1, none of the password gets sent unless the user hits enter to submit what he or she has typed, and the user has to hit the tab key about eight times to get the focus to the search bar in the first place; that isn't true in the case of Dash, which begins transferring data immediately on the first keypress, and can be opened accidentally with the press of a single key.
[*]In case #2, the user has to first hit a combination of two **very** distant keys (e.g., CTRL and T in Google Chrome) to open a new tab, and also has to have manually set Google search as their default new tab page in their browser (it isn't the default, AFAIK, at least in Chrome, so the user has to effectively "opt in" to this); neither of those things is true in the case of Dash -- Dash's online search is the default, and it requires only one keypress to be initiated (and I'm not sure about your keyboard, but my Windows key is not "out of the way" at all -- it is directly below my 'z' key). 
[*]In case #3, the user also has to hit a combination of two very distant keys (e.g., CTRL and 2 in Google Chrome) to switch to the other tab, and also has to have already manually navigated that tab to the Google search page in order to have that page open; again, two non-negligible differences from Dash. 
[/LIST]

There are even additional differences beyond these. Even if all of the above circumstances do occur, what is transferred in the Google case is a password to one email account, whereas what would be transferred in the case of Dash is the root password for one's computer. What's more, Google's search is already end-to-end SSL encrypted by default if you are signed in to a Google account, and that can be set as your default even when you are not signed in, if you want; this isn't true of Dash, as the EFF article to which I linked indicates: your results are returned insecurely.

Second, suppose the examples really are **exactly** the same, contrary to everything else that I just said. So what? This is a case where the saying "Two wrongs don't make a right" really applies. Even if it's true that there is an equal risk (or even more of a risk) with mistyped Google passwords, that doesn't mean that the risk with Dash is therefore acceptable. Instead, both should be fixed (by using end-to-end SSL by default, for example, as Google is already doing for users who are signed in). 

Hopefully what I've said already indicates why this isn't "like that rubbish that people where accidentally hitting ctrl+alt+backspace and so the key combo was changed to restart the xserver." Hitting CTRL+ALT+BACKSPACE, all at the same time, by accident, is orders of magnitude more difficult than accidentally hitting the Windows key (or perhaps accidentally tapping your palm on a laptop touchpad and causing Dash to open) -- for one, it requires two hands, or extremely large hands and a lot of coordination. Furthermore, the ability to restart a broken X server from the keyboard is pretty clearly (or so it seems to me) a very important ability to have, whereas the ability to be able to search Amazon, Facebook, the BBC, etc., from my keyboard with the press of one key does not seem nearly as important.

I've gone on about this more than I'd like to by now, so I'll stop. I'm not trying to argue that Dash is absolutely awful, by the way. I just think that the privacy concerns are legitimate. (And remember, the privacy concerns are not just about passwords, either. **Everything** you type in Dash is transmitted, and thus potentially returned insecurely, including searches of your local drive for porn and things like that. The EFF article discusses this, so I'll just defer to that article for the details.)

---

### Post by weasel fierce on 2012-11-28
It seems most of the performance problems are tied to  Unity then. I've had zero issues with 12.10 on Kubuntu, and I haven't seen the same sort of outcry either. My system is pretty modest by todays standards (core duo, and some nvidia card) and it runs very smooth and stable.

I guess an easy way to test would be to install something else alongside Unity and compare side by side.

---

### Post by BigSilly on 2012-11-28
> **weasel fierce said:**
> It seems most of the performance problems are tied to  Unity then. I've had zero issues with 12.10 on Kubuntu, and I haven't seen the same sort of outcry either. My system is pretty modest by todays standards (core duo, and some nvidia card) and it runs very smooth and stable.

I guess an easy way to test would be to install something else alongside Unity and compare side by side.

Yes same here. Kubuntu 12.10 runs beautifully for me, but Unity not so great. Lots of work to do on performance for the next release then. I wonder how Sam Spilsbury leaving Compiz/Canonical will affect that. But I really hope to see it improve.

BTW weasel fierce - your Doctor Who link doesn't work! ;)

---

### Post by weasel fierce on 2012-11-28
> **BigSilly said:**
> Yes same here. Kubuntu 12.10 runs beautifully for me, but Unity not so great. Lots of work to do on performance for the next release then. I wonder how Sam Spilsbury leaving Compiz/Canonical will affect that. But I really hope to see it improve.

BTW weasel fierce - your Doctor Who link doesn't work! ;)

Rats! I changed the page, since I wanted to include Star Trek stuff too. I'll fix!

---


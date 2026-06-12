---
title: "security of debian vs. ubuntu's universe"
date: 2005-09-21
forum: Server Platforms
---

### Post by ry_ry on 2005-09-21
I hope this becomes a sticky.

The extra repositories in the Unofficial Ubuntu Guide are not officially seen nor officially supported by Ubuntu. This means that they are unsafe and unsecure since they have not had any review by the Official Ubuntu team and using them is "Using them at your own risk!".  [-X 

Only use the Official Ubuntu repositories if you want to make sure your system stays secure. This means to NOT use any repositories in your sources.list file that has the words Universe, or Multiverse or Backports in it. These are not reviewed in any way by the Official Ubuntu team or by Ubuntu Security. Any packages out of these repositories are highly questionable and should not be trusted.

---

### Post by jimcooncat on 2005-09-21
Not that I don't believe you have our best interests at heart, ry_ry, but can we get a witness on this issue from someone with more longevity in the community?

---

### Post by John.Michael.Kane on 2005-09-21
Please read this ry_ry [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

Ubuntu Backports is an official, community-driven project, that is recognized by Canonical Ltd., who makes Ubuntu. However, Ubuntu Developers are not responsible for these packages, so please don't send any bug reports to the Ubuntu Bugzilla. Please report all bugs to me via Ubuntu Forums, and NOT to Canonical!

---

### Post by ry_ry on 2005-09-21
I'm not trying to be a jerk or anything, but I guess coming from the Windows world it helps to be paranoid.

I've seen the Backports website, and I still don't know who runs the Backports or the other Universe or Multiverse repositories? They don't even state that they check the security of the packages before uploading them to these repositories. 

From the Backports website:
"Ubuntu Backports is an official, community-driven project, that is recognized by Canonical Ltd., who makes Ubuntu. However, Ubuntu Developers are not responsible for these packages"

So yes, Canonical recognizes officially that the Backports are a community-driven project, I'm wondering who in this community is responsible for everything that goes into these repositories and who is responsible for checking out the security and the code in these packages as well, before they're posted? The Ubuntu Team nor the Ubuntu Security don't review any of these packages. So who's in charge of keeping these packages and repositories clean, with secure packages that have been reviewed?

Also from Backports website:
" I've taken it into my own hands to recompile newer packages from Hoary and Debian Sid for Warty."

Who is this that is doing this work, and are they just recompiling packages and posting them to the repositories without checking their security?

Sorry for sounding so paranoid, but I've never seen a good explanation about these extra repositories and who's in charge of them and what is being done to make sure that they contain safe, secure, malicious-code-free packages?

Are all of the packages in Universe, Multiverse and Backports from Debian Sid? And have they been reviewed by the Debian Security Team?

Yes, I'm still newb-ish, but I think it's a good idea to ask these types of questions about packages and security and to know where stuff is coming from and to have as secure as Ubuntu OS as possible.

---

### Post by John.Michael.Kane on 2005-09-21
Also it is by one. but by all who wish to add there said backport i belave may do so. if you however have an issue with using backports then dont. you are free to down load and install your programs from other sources.

[http://www.ubuntuforums.org/showthread.php?t=40291](http://www.ubuntuforums.org/showthread.php?t=40291)

---

### Post by jimcooncat on 2005-09-21
[QUOTE=ry_ry]Yes, I'm still newb-ish, but I think it's a good idea to ask these types of questions about packages and security and to know where stuff is coming from and to have as secure as Ubuntu OS as possible.[/QUOTE]I agree, but I think it's a bit alarmist to post as you did, "The extra repositories in the Unofficial Ubuntu Guide are not officially seen nor officially supported by Ubuntu."

It definitely did not sound like a question to me, but a warning from someone with authority.

---

### Post by LordHunter317 on 2005-09-21
[QUOTE=ry_ry]I'm wondering who in this community is responsible for everything that goes into these repositories[/quote]Whoever is packging the packages in them.

> and who is responsible for checking out the security and the code in these packages as well, before they're posted?The developers of the software.

Ubuntu doesn't do any code auditing of note I'm aware of, so if your concern is, "The packaged code is secure," then no repository can make that promise to you, regardless of who packages stuff in it.

If your concern is, "The packaged code is built from the offical source," then that solely comes down to due dilligence on the developer's part to make sure the source downloaded, packaged, and signed is untrojaned.  In which case, the repository doesn't matter, as the problem lies at a higher level.

The real, and important difference is that if a security flaw is found, the offical repositories have a team to correct the problem post haste.  The unofficial ones are left to their own devices, which aren't always as thorough.

> Who is this that is doing this work, and are they just recompiling packages and posting them to the repositories without checking their security?I dunno and yes, because it's not really the job of the packager to audit the code.  Many packagers would lack the technical skill required.

> and what is being done to make sure that they contain safe, secure, malicious-code-free packages?The short answer is nothing.  But the other side of the coin is that AFAIK, the official repositories don't do anymore besides what I outlined above: make sure the source code is clean and perform the build on a clean system.

> And have they been reviewed by the Debian Security Team?Nope, Debian Security Team has nothing official to do with sid.

But the Debian Security Team doesnt' really proactively audit that much code, either.  There sole purpose is to provide immediately fixed packages when a security problem is found, not to fix them in the first place.  IOW, they're a reactive, not a proactive defense.

But that's true of every distribution and every OS vendor, really.

---

### Post by Leif on 2005-09-21
You should have asked around before making unfounded claims. There is a whole section of the forums dedicated to the backports - you should have asked there. 

But no, despite what you may think, the backports, all of it, is quite safe to use, and worked on by active members of the community. The extras, however, not guaranteed not to break your system, just to have been put together with good intentions.

---

### Post by ry_ry on 2005-09-21
Sorry jimcooncat. Didn't mean to cause alarm, just to bring attention to this issue.

The link provided above did help answer my questions. But I must say that I still can't recommend using the backports or the extra repositories. It appears that the only testing being done is during the staging area by regular individuals who will test these packages on their own. And personally, jdong, who seems to be in-charge of this operation is just a high school kid from his public profile. I can't trust the security of my Desktop to some high school student.

I guess the Ubuntu distro. is not for me, since I'm not comfortable with this type of security model being used. I'm going to check out other distros. and see what they have to offer.

Good luck with Ubuntu.

---

### Post by jimcooncat on 2005-09-21
"But I must say that I still can't recommend using the backports or the extra repositories."

I'm sorry, but it seems although your recommendations are well intentioned, they're not the ones of the community. I respect your right to your opinion, but not for you to present it as fact in the Security forum of a community driven distro. We're all looking to keep our systems secure, and nobody knows all the answers.

"And personally, jdong, who seems to be in-charge of this operation is just a high school kid from his public profile. I can't trust the security of my Desktop to some high school student." 

I can, and I'm 44. If you've been following jdong's postings for a while you'd see he is reliable and intelligent.

"I guess the Ubuntu distro. is not for me, since I'm not comfortable with this type of security model being used. I'm going to check out other distros. and see what they have to offer."

Sorry to see you go, but we've had some fun with this today. You might be more interested in a source-based distro, so you have control of the compiler. Gentoo is quite popular, but there's many others as well. I don't know, but I suppose it would be possible to build Debian or even Ubuntu from their source repositories as well.

Or perhaps you might want to build Linux from Scratch! Then you could use source code as straight from the author as you can. It's certainly doable if you have the time, and you could ensure security every step.

---

### Post by matthew on 2005-09-21
[QUOTE=ry_ry]I guess the Ubuntu distro. is not for me, since I'm not comfortable with this type of security model being used. I'm going to check out other distros. and see what they have to offer.

Good luck with Ubuntu.[/QUOTE]
Well, now that you have posted your concerns in two separate threads (see also: [http://www.ubuntuforums.org/showthread.php?t=67542](http://www.ubuntuforums.org/showthread.php?t=67542) ) and said essentially the same thing in both, I guess you are right. You will probably be happier with a different distro. I wish you well.

---

### Post by John.Michael.Kane on 2005-09-21
Shame to base your choice of distros on the age of some of the coder's.. however you will be hard pressed to find a distro that does not have coder's ect who are in highschool. i hope you find a distro more suited to your needs. if you are a coder yourself then maybe you would want to compile your own distro as was stated before.

---

### Post by skoal on 2005-09-21
[QUOTE=ry_ry]And personally, jdong, who seems to be in-charge of this operation is just a high school kid from his public profile. I can't trust the security of my Desktop to some high school student.[/QUOTE]
ry_ry, I appreciate your posts and some of your insight.  However, I would hope by now you have had some time to read the "Code of Conduct" here.  I really don't understand such blanket generalisms like this.  Please, at least be constructive in your comments here, or this thread will be shut down faster than you can shake a stick at.  I have a masters in CS, but I've seen enough from jdong to safely say he could probably code circles around me, as can countless others (no doubt)...

Thanks.

\\//_

---

### Post by aysiu on 2005-09-21
Nobody's twisting your arm to install the extra repositories--that's why they're extra.
I sort of agree with you that if you want to ensure you have a stable system, you shouldn't complain if you enable extra repositories, but you shouldn't imply that by enabling extra repositories, you're putting your system in some kind of danger.

If you're really that paranoid, download and install things from source. That's the beauty of open source software--the source code is open. For every single package you install, view the source, examine it---make it sure it's not sneaking in some malicious code, and then install it from source using a compiler. You'd have to do this for every distro you use, if you're as paranoid as you come across, because most distros have some kind of packaging system, and to have added functionality (multimedia codecs, commercial DVD-viewing, etc.) you'll often need to enable extra repositories.

Honestly, though, just be practical. Think about it. Almost every single Ubuntu user uses the extra repositories--seriously. (Can someone confirm this?) If there were a problem with using the extra repositories, this message board would be flooded with newbies and veteran users saying, "Extra repositories killed my system," or "Such-and-such package is unstable. It messed up my x-config." On the contrary, you see people time and time again recommending people enable extra repositories, and this recommendation comes from *experience*, not paranoia.

That's the beauty of the Linux model for installing software--since it all comes from one place, if that place does become corrupt, everyone would know almost right away. Also, there's usually someone trustworthy maintaining that one place (either a developer or a fan of the distro), so the likelihood of it becoming corrupt is almost nil. In Windows, people download .exe setup files from all over the internet, sometimes from sketchy places, and sometimes from reputable places that have sketchy software (download.com, for example).

If you want to ensure that you're always safe, pay for and use Linspire, and don't run as root. Otherwise, stop getting people all worked up for nothing. Would you yell "Fire" in a movie theater just because you saw someone smoking a cigarette outside and imagined the cigarette might be thrown on the floor instead of the ashtray?

---

### Post by aysiu on 2005-09-21
[QUOTE=ry_ry]I can't trust the security of my Desktop to some high school student.[/QUOTE] You must not use Firefox, then. I happen to think it's an amazing browser. Didn't one of its main contributors start off when he was only a teenager?

> I hope this becomes a sticky. It will when we have a section in the forums called **What not to Do**.

---

### Post by matthew on 2005-09-21
[QUOTE=aysiu] It will when we have a section in the forums called **What not to Do**.[/QUOTE]
I just about spit coffee all over my computer and desk when I read this. [Due to laughter.] Thanks for saying what we all were thinking.

---

### Post by LordHunter317 on 2005-09-21
[QUOTE=ry_ry] But I must say that I still can't recommend using the backports or the extra repositories.[/quote]Did you ignore what I said?  The process Ubuntu goes thorugh to put somethign in the first place isn't any more rigorious per se than what the unofficial repositories go through.

The difference is that the offical repositories have an offical mechanism to deal with flaws when they're found, the unoffical do not. 

> I guess the Ubuntu distro. is not for me, since I'm not comfortable with this type of security model being used. I'm going to check out other distros. and see what they have to offer.The security model of every other distro is no different, so I guess Linux is just not for you.

---

### Post by aysiu on 2005-09-21
[QUOTE=LordHunter317]
The security model of every other distro is no different, so I guess Linux is just not for you.[/QUOTE] Is this necessarily true? I mean, if you install Linux from Scratch and then install each package from source after examining the source code of each program, couldn't that ease the paranoia of someone who actually knows how to read source code?

---

### Post by Leif on 2005-09-21
[QUOTE=aysiu]Is this necessarily true? I mean, if you install Linux from Scratch and then install each package from source after examining the source code of each program, couldn't that ease the paranoia of someone who actually knows how to read source code?[/QUOTE]

Even assuming amazing code reading (and bug, backhole etc. finding) skills, I doubt it would be humanly possible to read all the code necessary for an average linux install.

---

### Post by az on 2005-09-21
While it is true that not every line of code is seen by every developer, you have to remember that these packages come from debian.  It is not easy to become a debian developer.  The bar is very high.

Not just any application is packaged, and the packaging process is quite rigorous.  I put a lot of faith in the competency of debian developers.

It is not just anyone who can upload a patch here and there and infect your computer.

---

### Post by LordHunter317 on 2005-09-21
[QUOTE=aysiu]Is this necessarily true?[/quote]Yes.

> I mean, if you install Linux from Scratch and then install each package from source after examining the source code of each program, couldn't that ease the paranoia of someone who actually knows how to read source code?The amount of manhours required for this is simply astounishing.

Consider:
OpenBSD does regular audits of their codebase, usually targeted after one bug or potential bug per cycle.
They're still doing this, so obviously not all the bugs have been fixed yet.
Their codebase is about 250MB of source, which is orders of magnitude smaller than any Linux distro.
The have more than one developer.

Draw conclusions as needed, but if a team of developers can't do it on a smaller codebase, it's reasonably safe to infer one person cannot do it on a larger scale codebase.

---

### Post by matthew on 2005-09-21
[QUOTE=LordHunter317]Consider:
OpenBSD does regular audits of their codebase, usually targeted after one bug or potential bug per cycle.
They're still doing this, so obviously not all the bugs have been fixed yet.
Their codebase is about 250MB of source, which is orders of magnitude smaller than any Linux distro.
The have more than one developer.[/QUOTE]
You know what, provided the OP feels he can trust the BSD developers, one of those may be a good choice for a recommendation, especially OpenBSD, although FreeBSD is quite good from a security standpoint as well from what I have heard.

---

### Post by skoal on 2005-09-21
I went back to freeBSD recently, and it was quite good.  However, even after recompiling the kernel (which is very limited in config options compared to a linux kernel compile), I still got occasional deadlocks from my network.  Just my experience. But after three kernel compiles, I felt like Michael Spinx against Mike Tyson.  KO!

As far as portage and package management applies to the OP's original post...

FreeBSD is good from a security standpoint, up until you start installing anything outside of their repos.  I think the OP is still going to have those same "objections", I believe.  I had to use far far more isolated ftp repos (from who knows where) on freeBSD than I ever had to while here at Ubuntu, or Debian.  And, even fetching the latest KDE was a mixture of packages and source (which took ages to compile).

I guess, ultimately, the bottom line is all the "good stuff" has always been in "non stable" "3rd party" repos for any distro I've tried, and I've always paid attention to the apt-get (synaptic) warnings they provide when installing from such "non base" repos...

\\//_

---

### Post by gambarimasu on 2005-12-04
[http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian](http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian) says about tor (the onion router):

"Do not use the packages in ubuntu's universe. They are not maintained and most likely old and therefore miss out on stability and possibly security fixes."

if i used breezy, i might have missed that and just dowloaded from universe.

as i am considering switching to breezy from debian, i would like to know if i would be vulnerable to other potential problems like that that would not happen with etch or sid.

this is not meant to be a troll.  i want to know as much as i can about repository differences between debian and ubuntu before i switch to ubuntu.

thanks.

---

### Post by aysiu on 2005-12-04
[QUOTE=gambarimasu]
"Do not use the packages in ubuntu's universe. They are not maintained and most likely old and therefore miss out on stability and possibly security fixes."[/QUOTE] I've never had any problems using Universe, and I've seen a *lot* of posts here complaining about sound issues, multimedia support, lack of GUI for certain tasks--almost anything you can imagine.

I've yet to see someone (based on experience, not just suspicion) complain about the security or stability of apps from Universe.

The closest I could find is the thread I just merged you with, which is just FUD.

---

### Post by jobezone on 2005-12-04
[QUOTE=LordHunter317]
Nope, Debian Security Team has nothing official to do with sid.
[/QUOTE]
Actually a Debian testing security team has been formed a few months ago. From their website [http://secure-testing-master.debian.net/](http://secure-testing-master.debian.net/):
>  The team is in the process of beginning full security support for testing by providing security advisories and fixes built against testing without the usual delays sometimes involved in getting a security fix into testing. 

---

### Post by az on 2005-12-04
[QUOTE=jobezone]Actually a Debian testing security team has been formed a few months ago. From their website [http://secure-testing-master.debian.net/](http://secure-testing-master.debian.net/):[/QUOTE]
Testing is not Sid.

---

### Post by gambarimasu on 2005-12-05
[QUOTE=aysiu]
The closest I could find is the thread I just merged you with, which is just FUD.[/QUOTE]

thanks for your reply, but i would like to request that you unmerge the thread.  i believe that you meant well but very much misunderstood my question.  here is why:

first, i want to know the real-world consequences of the switch from debian to ubuntu in particular.  moving the thread here confuses it with a thread that is not directly related to my question.

second, you quoted out of context by not mentioning that it was said about tor (the quote implies that they said it about all programs in universe).  the tor people were not fudding -- they were talking about their own package -- and they were only talking about tor, not all of universe.

third, tor is a special case where you typically want a high level of bug-freeness and security, so i think that even if universe is typically excellent, which i am willing to believe, you might not want certain types of packages like tor sitting around there without upgrades for too long.  if the tor people say it's unsupported, i am willing to believe them.

i feel like you buried my post in a thread that is, in my opinion only tangentially related.

i am new here and don't know the rules, but i feel strongly that it would be better for the thread that i started to be unmerged.  is it possible for you to unmerge the thread for the sake of the original author even if you disagree?

thanks.

---

### Post by gambarimasu on 2005-12-05
[QUOTE=aysiu]
The closest I could find is the thread I just merged you with, which is just FUD.[/QUOTE]

another reason that i would like to politely request that you undo your merging of the threads (which i did not ask you to do) is that if possible i want my very different questions answered without having it merged into this discussion.

i have no interest at this time in my questions causing fudding, being accused of being fud, being used for fud, being accused of fudding, being lumped in with fud, being buried because somebody thinks they are fud, being buried because somebody thinks they are not fud, or anything else having to do with fud.

i am just hoping, if possible and if you would be so kind as to undo your action, for a few honest, well-considered answers related to my switch from DEBIAN to ubuntu, in, again if possible, my own thread.  you did not answer my question, but instead merged it with a different question.

i know you meant well, but could you please unmerge so somebody else can read the subject line and answer my question instead of this thread's question/statement?

thanks.

---

### Post by jobezone on 2005-12-05
[QUOTE=azz]Testing is not Sid.[/QUOTE]
true, my mistake.

---

### Post by gambarimasu on 2005-12-10
[QUOTE=gambarimasu]thanks for your reply, but i would like to request that you unmerge the thread.  i believe that you meant well but very much misunderstood my question.  here is why:
[/QUOTE]

well, 5 days have passed without aysiu replying, not even to my pm.  my question has not been answered either, which is not surprising because he buried it in a thread about a different topic.

perhaps he doesn't want the question to be asked because of his own opinions on the subject.  i am not happy about this.  i wasn't trolling and don't deserve that kind of unilateral action by an admin.

i had nothing to do with the thread my thread was merged into.  i have a genuine question that is of enough interest to deserve its own thread.  i don't think it's too much to ask.

i would like to believe that ubuntu forums and the ubuntu community in general are not always this heavy handed.  although the thread was not deleted, it was buried and I VERY MUCH consider this a free speech issue.  my thread deserves its own thread.

---


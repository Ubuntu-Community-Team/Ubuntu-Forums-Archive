---
title: "Trusting a PPA"
date: 2016-12-12
forum: Ubuntu, Linux and OS Chat
---

### Post by FerryGnu on 2016-12-12
OK, I get it, no one wants to be blamed for recommending a bad PPA but it is inane for everyone to just ignore the "how to trust" question.

I have been searching for hours for info on "ppa:webupd8team/nemo" and keep finding comments like "only you can decide if you trust that PPA."

While that is true, it is an **idiotic answer** to someone asking the question. IF the 'ask-er' knew HOW to decide trust they would NOT be asking here.

I have looked for download numbers (as a hint to trust) for specific PPAs but to no avail. As a Mechanical Engineer I am used to dealing with facts to make a decision. Telling me that as a novice to Linux, I have to decided whether I trust a specific PPA is like saying "let the snake bite you to see if it is poisonous."

Is there no list of trusted PPAs with suitable indemnifying comments or caveats for the pending-user to consider?

Is there perhaps a list of commonly used PPAs where people have commented on placed-trust or misplaced-trust?

Is there a list of very qualified users (max coffee beans, Admin/Moderator etc) here with the PPAs that they use, while indemnifying themselves in not advocating we all blindly follow, but at least provide a guide on how to begin to build trust in some PPAs.

It is very difficult getting started with Ubuntu/Linux et-al, when a lot of questions such as this simply go unanswered or ignored.

---

### Post by #&amp;thj^% on 2016-12-12
webupd8 has been one of the very few i DO trust as they host Applications that Ubuntu can't or won't due to ELUA .
When describing the Term "TRUST" it should be noted that security is not the only factor here.
Also should be looked at how well they maintain and update Important Security fixes IE Patches and that installing their offerings won't "Break Your System" .
Just My 2 Cents here...and I am sure others will also Report in on the Subject.
Kind regards

---

### Post by Habitual on 2016-12-12
Your Question is valid. I trust and have trusted ppa:webupd8team for java for at least 2 years.
I generally trust software I install from there. Showing you my PPAs wouldn't change anything.


More information and installation instructions: [http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)
More info: [https://launchpad.net/~webupd8team/+archive/ubuntu/nemo](https://launchpad.net/~webupd8team/+archive/ubuntu/nemo)

---

### Post by QIII on 2016-12-12
Hello!

This is certainly a valid question, but not a subject with a simple answer.  Since PPA is an acronym for Personal Package Archive, each is a grab bag of the good, the bad and the ugly.  We can certainly recommend (I use webupd8), but we can't guarantee anything.  There is no governing body inspecting the contents of PPAs for compliance with any regulatory requirements.

List with caveats:  not that I know of.

List of common trusted ones:  not that I know of.

Admins/Staff/beans:  No bearing.  Meaningless with regard to this question.  Everyone here is a volunteer with a unique set of experiences, but none of us is certified in any particular area.  Beans are for dinner, not for judging the inherent trustworthyness or expertise of the user. Staff are chosen for their ability to be helpful and to moderate, not necessarily for their expertise. 

If you see something you like, the ask about that PPA here.  If the preponderance of opinion is positive, assess the risk and make a decision.  But please don't expect people to stick their necks out to give a definitive "Yay" or "Nay" regarding something they have no control over.

---

### Post by wildmanne39 on 2016-12-12
I do not use ppa's much, there really is not a need very often, but when I do they are always on launchpad.

Also the new snaps system that is being implemented is going to be replacing the need for ppa's at all from what I understand.

Also I suggest you read the CoC to help improve your posting style.
[https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)

---

### Post by ian-weisser on 2016-12-12
> **FerryGnu said:**
> OK, I get it, no one wants to be blamed for recommending a bad PPA but it is inane for everyone to just ignore the "how to trust" question.

You misunderstand.

We're not employees (try to remember that - you're not our customer; you're not the only engineer here; be nice), and there is no substantive penalty in the community for giving bad advice. 'Blame' is irrelevant.

Here are some of the facts you seek:

- There is NO way to assess trust in a PPA. None. Zero. Reason: PPAs are intended for distribution of software for testing purposes.

- There is no screening process for PPAs precisely because they are intended to be experimental. The ONLY two ways to gauge the safety of a PPA are to audit the code yourself, or to assess the community reputation of the author.

- Using PPAs for widespread independent distribution is a tolerated misuse. Reason: The misuse has been generally harmless and non-malicious in the past. The PPA infrastructure's owner, Canonical, can change their policy any time they wish

- PPAs are not supported software. Use them at your own risk. If you ask for help with PPA software here and in other Ubuntu help venues, the #1 answer you will get is "uninstall the PPA software and use the tested, supported Ubuntu version instead"


Advice: A new user adding PPAs is a very good indicator of a new user about to break their package manager quite badly. Your previous power-user skills may be leading you astray, and you may soon be spending an afternoon repairing or rebuilding your system. It's a fairly common mistake made by Win and Mac power-users unfamiliar with package management, and part of their ordinary learning curve for Ubuntu. Ensure you have regular backups of your data.

---

### Post by FerryGnu on 2016-12-12
Ummm, are you not attesting to my point?

Where on earth did you get the idea I was regarding you as employees of whatever?

I include the PPA in question such that someone may comment on it as trusted or not.

I, like I am sure, many others are trying to port over to Ubuntu from windows. It is a steep learning curve and asking questions is the only way to get things going smoothly. I reiterate, getting a "make up your own mind," comment is useless. It just adds to people's frustration and serves no valid purpose than to allow the poster to laud their superior knowledge over newbies to Linux. Not that way to get Linux into the mainstream.

I have obviously made the mistake of thinking this is a "help" forum.

---

### Post by oldos2er on 2016-12-12
Beans are nearly meaningless. They are just post counts (and spam reports) and [not intended to be anything but an amusement.]("https://ubuntuforums.org/showthread.php?t=239560")

---

### Post by QIII on 2016-12-12
No.  You made a very honest mistake in assuming that there was some objective way to assess the trustworthiness of PPAs.  There simply is not.  That is why you are getting these answers.

Sometimes answers are not to our liking.

I, for one, did say that I use webupd8.  I have had some communication with the maintainer and know his attitude and attention to detail.  That does not mean that he is immune to errors that may render your system unusable.  He's one guy with a real life outside of the portfolio of applications in his PPA.

---

### Post by Habitual on 2016-12-12
End users install PPAs at their own risk.[[1]("https://help.ubuntu.com/community/PPA")]
[what are some &#8220;red flags&#8221; to watch out for?]("http://askubuntu.com/questions/35629/are-ppas-safe-to-add-to-my-system-and-what-are-some-red-flags-to-watch-out-fo") - little dated but principles are still valid.

---

### Post by vasa1 on 2016-12-15
> **FerryGnu said:**
> Ummm, are you not attesting to my point?

Where on earth did you get the idea I was regarding you as employees of whatever?

I include the PPA in question such that someone may comment on it as trusted or not.

I, like I am sure, many others are trying to port over to Ubuntu from windows. It is a steep learning curve and asking questions is the only way to get things going smoothly. I reiterate, getting a "make up your own mind," comment is useless. It just adds to people's frustration and serves no valid purpose than to allow the poster to laud their superior knowledge over newbies to Linux. Not that way to get Linux into the mainstream.

I have obviously made the mistake of thinking this is a "help" forum.This _is_ a help forum. The forum "helpers" are users just like you, some very experienced, others not so. The mistake, if it can be termed that, is that some people assume that helpers here have all the answers and that these answers will be palatable to the questioner. I'm not sure that assumption holds true in any aspect of life.

Your question, omitting the frustration, is a very nice one and the answers here **collectively** will be of use to others asking the same question.

So what's my screening method? I first try and work out whether I really need a particular PPA, knowing full well that I have to take full responsibility for my decision. With that out of the way, I try to "profile" the persons (or team) who made the PPA available. Some of them post here and have helped me in the past or are actively helping others here. I look at their Launchpad page to see what their experience is and how active they are in fields that matter. How closely are they associated with the software?

Then there are PPAs which are available from elsewhere.  I trust Google, despite what others may feel, and so have no hesitation in installing Google Chrome.

I trust the developers of the Vivaldi browser project and have no hesitation in installing their PPA. The Vivaldi browser isn't really a must have but I appreciate what they're trying to achieve.

If a user wants to know about a specific PPA, there's absolutely nothing wrong in asking for opinions here.
> I have been searching for hours for info on "ppa:webupd8team/nemo" and keep finding comments like "only you can decide if you trust that PPA."
If that is your question, I'd ask a few questions of you: Which file manager to do currently use? Why are you unhappy with it? Have you tried other file managers that are already available in the standards repositories? What is it about nemo that makes you want to install it? Answers to these questions may help you decide.

As for a list of trusted PPAs even with indemnifying clauses, caveats, etc, I'm not sure that's a good idea. People are known to ignore warnings. It's better that each person details a need for which a solution can then be crafted, perhaps without recourse to a PPA.

---

### Post by zircon_34 on 2016-12-18
> **FerryGnu said:**
> 

I, like I am sure, many others are trying to port over to Ubuntu from windows. It is a steep learning curve and asking questions is the only way to get things going smoothly.


If you are new to linux (assumption), I do not suggest to add a PPA. I just added a PPA this week, because a software that used to work in Ubuntu 16.04 stopped working in 16.10. 2 days later I had broken dependencies, error messages and couldn't update any of my packages. I removed that PPA, purged all the files associated to it. Relief, everything is fixed. Conclusion, not easy for a newbie to fix broken package dependencies. I understand that sometimes you want to install a software not available in your distro. I would first try it out and its updates in a system installed in a virtual machine (e.g. virtualbox) to check you are not braking your system. 

Hope you get the answer you seek about your PPA.

---


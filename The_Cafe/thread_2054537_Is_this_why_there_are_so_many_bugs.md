---
title: "Is this why there are so many bugs?"
date: 2012-09-07
forum: The Cafe
---

### Post by VanillaMozilla on 2012-09-07
Shortly after I reported a bug that turned out to be a duplicate, I found this:  [https://bugs.launchpad.net/globalmenu-extension/+bug/1045196](https://bugs.launchpad.net/globalmenu-extension/+bug/1045196) .  I'm trying to be nice, but I couldn't help commenting.  My experience trying to report bugs in Ubuntu projects has been consistently infuriating.

To spare you some reading, I'll summarize what happened.  A recent update broke some Thunderbird menus, and someone duly reported the bug.  The first action on the bug report was to mark it invalid because it was not reported with Apport.  A link to an article was posted, which says not to report bugs to Launchpad using the Launchpad form!  The article further says that bugs will be ignored or marked invalid (presumably as a kneejerk reaction) if they are not reported with Apport.

Really?  All the documentation I have seen says that Apport captures crashes.  Period.  Just how does one use Apport to capture a broken menu?

Am I missing something here?

If it was just this one case (which has been fixed), it wouldn't bother me.  But there are other examples.  I previously reported a bug that always crashes the entire login session, and yet Apport does not generate a crash report.  The bug reports are "invalid", but as far as I know, the bug is still there.

Are serious bug reports being defined away without fixing the bugs?  And how *does* one report a broken menu, with or without Apport?

---

### Post by mips on 2012-09-07
[http://ubuntuforums.org/showpost.php?p=12222349&postcount=40](http://ubuntuforums.org/showpost.php?p=12222349&postcount=40)

---

### Post by VanillaMozilla on 2012-09-07
Yes, some of us also failed to get Mozilla to fix a severe data loss bug.  Sometimes bureaucrats dig in their heels.  It's a similar problem.  Is that what you're referring to?

---

### Post by Paqman on 2012-09-07
> **VanillaMozilla said:**
> Just how does one use Apport to capture a broken menu?


Open a terminal or hit Alt-F2 and type:
```
ubuntu-bug packagename
```

You'll then be able to fill in any additional details in the Launchpad bug it raises.

---

### Post by cariboo on 2012-09-07
There really aren't that many bugs, it's just that there are so many duplicates. To help in making sure your bug isn't marked as a duplicate, or marked as invalid due to not enough information, have a look at this wiki page:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

BTW the wiki pages are a great resource, more than likely anything you are looking for is available at:

[https://help.ubuntu.com/](https://help.ubuntu.com/)

There is also IRC if you can't wait a few days for an answer to your question.

---

### Post by VanillaMozilla on 2012-09-07
Paqman, Cariboo, yes, thanks, the ubuntu-bug command actually works.

Now, if you will notice, there is not a word about that procedure at wiki.ubuntu.com/Apport .  Nor is there any notification whatsoever if you file a bug report starting from the Launchport Answers tab.

Do you have any suggestion for getting these problems fixed?  It is quite possible to waste huge amounts of time on this.  To be useful the information needs to be concise *and* easily available.


(The command is found at [https://wiki.ubuntu.com/MozillaTeam/Bugs](https://wiki.ubuntu.com/MozillaTeam/Bugs) , however.  Sorry, I missed it the first time, although I wish the instructions had been more concise.)

---

### Post by Primefalcon on 2012-09-07
Ummmm.... go to the linked posted in the OP...... a fix has been released.......

So bug has been fixed..... do a sudo apt-get update.....

---

### Post by cariboo on 2012-09-07
> **VanillaMozilla said:**
> Paqman, Cariboo, yes, thanks, the ubuntu-bug command actually works.

Now, if you will notice, there is not a word about that procedure at wiki.ubuntu.com/Apport .  Nor is there any notification whatsoever if you file a bug report starting from the Launchport Answers tab.

Do you have any suggestion for getting these problems fixed?  It is quite possible to waste huge amounts of time on this.  To be useful the information needs to be concise *and* easily available.


(The command is found at [https://wiki.ubuntu.com/MozillaTeam/Bugs](https://wiki.ubuntu.com/MozillaTeam/Bugs) , however.  Sorry, I missed it the first time, although I wish the instructions had been more concise.)

If you find a wiki pages is missing information, you can edit the page yourself.

---

### Post by Primefalcon on 2012-09-07
> **cariboo907 said:**
> If you find a wiki pages is missing information, you can edit the page yourself.again this whole Thread is mute.... the act that the bug was fixed from the thread shows the OPs whole point is invalid

---

### Post by VanillaMozilla on 2012-09-07
PrimeFalcon, the reported bug in thunderbird-globalmenu is not the problem.  The problem is the very poor documentation on how to file a bug report.

---

### Post by VanillaMozilla on 2012-09-07
Cariboo, suppose for the moment that I did edit the wiki pages.  That *might* solve one problem, although it may well be a fool's errand.  But what about the Launchpad problem?  Any suggestions?

---

### Post by Primefalcon on 2012-09-07
that's because typically.. you don't have to worry about it, most times when a program crashes... you'll get a message asking if you wish to file a bug report....

otherwise filing a bug report is as simple as typing ubuntu-bug <program_name>

if you the ubuntu lense thing and type in help and launch the help program and type in file a bug, you'll see the entry how do I report a problem in Ubuntu. You'll see the whole process of alt+f2 and blah blah right there.... **so the documentation exists in Ubuntu itself**...

---

### Post by forrestcupp on 2012-09-08
> **Primefalcon said:**
> Ummmm.... go to the linked posted in the OP...... a fix has been released.......

So bug has been fixed..... do a sudo apt-get update.....

> **Primefalcon said:**
> again this whole Thread is mute.... the act that the bug was fixed from the thread shows the OPs whole point is invalidThis thread is not a help request for Thunderbird. That was just an example of the fact that it's not obvious how to file a report for something that doesn't cause a crash.

> **Primefalcon said:**
> that's because typically.. you don't have to worry about it, most times when a program crashes... you'll get a message asking if you wish to file a bug report....

otherwise filing a bug report is as simple as typing ubuntu-bug <program_name>

if you the ubuntu lense thing and type in help and launch the help program and type in file a bug, you'll see the entry how do I report a problem in Ubuntu. You'll see the whole process of alt+f2 and blah blah right there.... **so the documentation exists in Ubuntu itself**...It's not true that typically you only want to file a report when something crashes. I've noticed lots of bugs that don't actually cause the app to crash.

It's great to know about **ubuntu-bug**, but if you don't know about that command, filing reports is pretty confusing. If they're going to be that strict about doing it this way, they need to put it in the menus and make it obvious.

---

### Post by sffvba[e0rt on 2012-09-08
Reporting bugs is something I have done from time to time when prompted... but in general I have no idea if I did it right, and I try and avoid it as it does seem to be more voodoo than I can handle.

I should have a look at those wiki entries I think :)


404

---

### Post by zer010 on 2012-09-08
I was not aware of the "ubuntu-bug" command, so thanks for that!  ^_^d

---

### Post by Primefalcon on 2012-09-08
As I said however... the documentation is easily found inside of Ubuntu itself.... so it's not like its obscured information

---

### Post by CarpKing on 2012-09-08
So it sounds like the documentation in Ubuntu is fine, and the wiki can be improved, but the main problem is that Launchpad lets you file bugs that will be automatically marked invalid without warning you of this fact.  Maybe for official Ubuntu packages (I assume other projects hosted on Launchpad use the manual bug-reporting feature) it should redirect you to the directions for running ubuntu-bug.

---

### Post by cariboo on 2012-09-08
If you subscribe to the bug, you will get email notification if the bug is a duplicate or invalid, you can then post a comment asking what else is needed to help solve the problem.

All the documentation in the world, isn't going to help, if no one reads it.

---

### Post by VanillaMozilla on 2012-09-08
OK, thanks for the information on Apport.  That solves the immediate problem.

It's easy enough to find if you know exactly where to look and what to look for.  I'm not going to waste time fixing anything if the most knowledgeable users think there's no problem.  However, here's a *concise* guide I wrote for myself, using information I compiled from several sources.

**My bug-reporting documentation**
============================
	Almost all bugs in Ubuntu-distributed software should be reported using Apport.  Apport gathers extensive information on the local system, and is also capable of gathering information on crashes.  Apport and various supporting packages are installed by default on Ubuntu systems.  Launchpad allows reporting bugs without using Apport, but this is discouraged.

	Run Apport from a terminal, as follows.  The 'ubuntu-bug' command has an alternate form, 'apport-bug'.

**To report information on a program**
ubuntu-bug -w
and click on the window.  This will gather information on that program.

**To report on a specific package name**
ubuntu-bug <package-name>

**To collect crash information**
Start Apport (once) and then run the program that crashes.
sudo service apport start force_start=1

**To report crash information**
??

**To report non-specific problems**
ubuntu-bug
This will present a form with different types of problems.

**To report non-specific problems**
ubuntu-bug linux


**More information**
	More information on ubuntu-bug can be found in the following places.  None of these sources has complete documentation.

1. The Ubuntu Help utility.  Search for 'file a bug'.
2. The man page has partial information.  man ubuntu-bug
3. [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)
4. [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
5. [https://wiki.ubuntu.com/MozillaTeam/Bugs](https://wiki.ubuntu.com/MozillaTeam/Bugs)

---

### Post by forrestcupp on 2012-09-08
> **Primefalcon said:**
> As I said however... the documentation is easily found inside of Ubuntu itself.... so it's not like its obscured information
Maybe, but if they actually want people to help with bug reports, they need to make it obvious instead of tucking instructions for some unknown command away in their documentation. I would think that would be something important enough to put in the menus. The way things are now, it almost seems like they're being put out by doing us the favor of accepting our bug reports, when it's really that we are trying to help *them* out.

---

### Post by vexorian on 2012-09-08
No, there are "so many bugs" because all software has bugs.

---

### Post by alexfish on 2012-09-08
Bugs, Oops, Dam , Heck what happened. Shudder bugs,

This bugs me.

There is one distro  I have trusted to sort out Bugs, and it be fairly automated, but not in as seconds or minutes.

So if you reading this thread , then you are connected, time will tell.

Bug disappears = a job well done. Kernel fails after update "Safe Mode", If that fails , back to live install.

if Live install fails ,  Squeal like a pig . There again if Live Install work first time, !!!!!, so not.

Sometimes Developers of Software do not keep in touch. Remember most do so FOC. don't forget about TGTLTGE.

read the info as regards what you are installing , or what you have installed, is it supported by Ubuntu ?

It be amazing what info the Software Centre provides.

Everything on a plate does not exist , on this side or any other

Enjoy.

alexfish

PS, the Spell-check still can't Recognise , "Ubuntu" , Now that be a bug of all bugs ;)

---

### Post by vasa1 on 2012-09-08
> **forrestcupp said:**
> Maybe, but if they actually want people to help with bug reports, they need to make it obvious instead of tucking instructions for some unknown command away in their documentation. ...
Yes and no.
Anyone who frequents software forums of any sort will agree that that are hordes of "newbies" convinced they've found a bug. If filing a bug were easy, the triagers, if no one else, would be snowed under.

---

### Post by Primefalcon on 2012-09-09
simple answer as to why there are bugs..... Ubuntu is a leading edge distro....

if you don't want to see bugs... stick to LTS, and only upgrade to the next when the one your on in near end of support...

For example you should still be using 10.04 and upgrade to 12.04 around April next year then onto 14.04 around April 2017... that is if you really hate bugs.

For example my Desktop is running 12.04... I am happy to deal with bugs.... but on the Netbook which both my wife and I use is still running 10.04

---

### Post by forrestcupp on 2012-09-09
> **vasa1 said:**
> Yes and no.
Anyone who frequents software forums of any sort will agree that that are hordes of "newbies" convinced they've found a bug. If filing a bug were easy, the triagers, if no one else, would be snowed under.

I know what you're saying is true, but where's the balance? If it's really that bad, then they need to stop making people feel like filing bug reports is a good way to give back to the community. People feel guilty about taking free software without giving anything back, so they end up doing the only thing they know how to do to give back. Then the triagers get snowed under and mad about it. 

So if they're upset about getting snowed under, maybe they need to stop advertising that bug reports is a good way to give back.

---

### Post by vasa1 on 2012-09-09
> **forrestcupp said:**
> I know what you're saying is true, but where's the balance? If it's really that bad, then they need to stop making people feel like filing bug reports is a good way to give back to the community. People feel guilty about taking free software without giving anything back, so they end up doing the only thing they know how to do to give back. Then the triagers get snowed under and mad about it. 

So if they're upset about getting snowed under, maybe they need to stop advertising that bug reports is a good way to give back.
I made up that bit about triagers getting snowed under or mad. I agree that striking a balance (in so many things) isn't simple.

My personal preference is to first ask around in the relevant forum and only then to file a bug if the consensus is that there's really a bug and that it hasn't been reported so far.

---

### Post by sffvba[e0rt on 2012-09-09
> **vasa1 said:**
> My personal preference is to first ask around in the relevant forum and only then to file a bug if the consensus is that there's really a bug and that it hasn't been reported so far.

Why not just disable to ability to do so and only have people that can figure out how to do it be able to file bugs... or better yet, only let people that have been certified as being able to do this successfully file bugs (like after passing a 6 hour written test to prove your competence)...

Or we welcome all attempts and strive to make the system as idiot proof as possible?!


404

---

### Post by vasa1 on 2012-09-09
> **not found said:**
> Why not just disable to ability to do so and only have people that can figure out how to do it be able to file bugs... or better yet, only let people that have been certified as being able to do this successfully file bugs (like after passing a 6 hour written test to prove your competence)...

Or we welcome all attempts and strive to make the system as idiot proof as possible?!


404
If my posts have upset you, please delete them.

---

### Post by sffvba[e0rt on 2012-09-09
> **vasa1 said:**
> If my posts have upset you, please delete them.

If my post has upset you then ... well uhm... I was simply giving my opinion on your opinion ;)


404

---

### Post by vasa1 on 2012-09-09
> **not found said:**
> If my post has upset you then ... well uhm... I was simply giving my opinion on your opinion ;)


404
My take is that there's quite a bit of ridicule there.

In case there's some misunderstanding, let me rephrase.

[LIST]
[*]I think there's something wrong with the OS, or app.

[*]I post my observation and ask people whether others have the same experience. And if so, whether they know whether a relevant bug exists.

[*]In case it needs mentioning, Launchpad has a feature that enables a person to indicate whether a bug affects them too.

[*]If the response generally is that there is a problem and that a bug should be filed, then I'm willing to do so.
[/LIST]
That is what I meant by: "*My personal preference is to first ask around in the relevant forum and only then to file a bug if the consensus is that there's really a bug and that it hasn't been reported so far*."

I totally fail to see how a response such "*only let people that have been certified as being able to do this successfully file bugs (**like after passing a 6 hour written test to prove your competence**)...*" is applicable.

It maybe that  my understanding of the English language isn't adequate but I find it hard to appreciate your opinion on my opinion in a positive light.

---

### Post by VanillaMozilla on 2012-09-09
> **vasa1 said:**
> Yes and no.
Anyone who frequents software forums of any sort will agree that that are hordes of "newbies" convinced they've found a bug. If filing a bug were easy, the triagers, if no one else, would be snowed under.
I'm not a newbie.  I have filed lots of bug reports on various projects from compilers to Web browsers, and a lot of them get fixed.  And they made it hard for me.

In order to prevent exactly the problem you mentioned, I always discuss a possible bug in a forum before submitting.  If you do that in Launchpad, you will not see the information that they say you need.  And even if you look at the Ubuntu Wiki on Apport (which I did), it doesn't give you the information you need.

That's why I posted my own, *concise* article here.  Use it if you wish, or ignore it.

---

### Post by VanillaMozilla on 2012-09-09
> **Primefalcon said:**
> if you don't want to see bugs... stick to LTS, and only upgrade to the next when the one your on in near end of support...
Actually, the latest LTS version I have doesn't even run right on my test machine.  It gives unspecified "system errors".  And except for security updates, applications in LTS releases receive no bug fixes.

---

### Post by vasa1 on 2012-09-09
> **VanillaMozilla said:**
> I'm not a newbie.  ...
I did not say or imply you are. As happens in threads of this type, people comment and my comment was in response to one by forrestcupp which I quoted.

---

### Post by VanillaMozilla on 2012-09-09
Fair enough.  I just meant that I'm not a newbie, but I still found it hard.

Other people disagree, and that's fine.  I'm not trying to be disagreeable.  Now, thanks to people who contributed to this discussion, we know how to use Apport.  Thanks, guys.

---

### Post by forrestcupp on 2012-09-09
> **vasa1 said:**
> I made up that bit about triagers getting snowed under or mad. I agree that striking a balance (in so many things) isn't simple.

My personal preference is to first ask around in the relevant forum and only then to file a bug if the consensus is that there's really a bug and that it hasn't been reported so far.

Well, my main point is that I'm willing to help to an extent. But once they start making it hard for me to help, or start criticizing me and making me feel guilty for making it hard on them to have to mess with accepting my help, my willingness  starts to wane.

And that point isn't against you, but about how the current system works.

---

### Post by Primefalcon on 2012-09-09
> **VanillaMozilla said:**
> Actually, the latest LTS version I have doesn't even run right on my test machine.  It gives unspecified "system errors".  And except for security updates, applications in LTS releases receive no bug fixes.
12.04 is still a relatively new LTS release, which why which is why I said people who can't handle bugs should still be using **10.04**, which by the way... is still getting a lot of updates (I am running it on the netbook here)...... I'll upgrade to 12.04 once 10.04 is end of lifed.... by then any bugs in 12.04 should pretty much be nuked.

If you really need a new version of an application, such as say webm support in vlc or whatnot.... you can always add a ppa for that specific application.

If you don't care about bugs? why not try beta releases.... by that stage they are pretty much solid... but you will come across bugs.. for the OP though.... with the issues your having.... I'd advise never trying beta

---


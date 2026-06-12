---
title: "Bug on Launchpad. Importance is... LOW?!"
date: 2010-02-07
forum: The Cafe
---

### Post by PryGuy on 2010-02-07
I have filled the bug on Lanchpad three months ago. Here it goes:
[Nautilus shows blank window when I try to get shares list on a remote server sometimes]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/480832")

It is about Nautilus that shows blank window browsing Samba shares. I use Samba frequently so it's very serious for me. So do my clients. I cannot start offering Karmic to them because of that! And they set importance as LOW! Am I the only one who uses Samba and the bug is not important? Please vote for it on Launchpad if it affects you!

There are also some other (very serious IMHO) bugs that are still not fixed, this one for instance:
[CD/DVD won't unmount after manual removal]("https://bugs.launchpad.net/ubuntu/+bug/510021")

The following bug is very annoying for me 'cause I use CLI frequently. "Fix released" they say, but the problem is still here!
[MC (Midnight Commander) does not wish to keep CONFIG]("https://bugs.launchpad.net/ubuntu/+source/mc/+bug/397497")

What's going on???!!!

EDIT: Canonical, do you think people will keep loving Ubuntu if it's release (and support) quality will be that low? Think again, please.

---

### Post by juancarlospaco on 2010-02-07
XP and 7 and sometimes shows blank window on explorer.exe, SMB protocol is buggy.

---

### Post by PryGuy on 2010-02-07
So why won't devs fix it?! It's not a new bug after all... Everything works great for me on Jaunty and Debian Lenny when I browse the same server, so I'm not sure it's SMB that I should blame.

---

### Post by sideaway on 2010-02-07
I kind of agree with PryGuy here. Samba is a pretty damn important part of a modern computer, efficient, reliable networking is probably one of the most under developed aspects of the modern operating system in terms of importance.

Samba, IMHO is an important part of a linux OS. It's why I use Nautilus and Dolphin, because few other file managers have such great Samba integration, if they have any at all!

---

### Post by 3rdalbum on 2010-02-07
Using the words "sometimes" and "pushing the Refresh button works" is guaranteed to get your bug report triaged as "low".

Submit a bug against Nautilus on Gnome's bugzilla and see what happens. You probably won't get a lot of joy unless you can narrow down exactly why this happens, or what conditions cause it to happen. Maybe looking at the Nautilus source code will help you work out exactly what Nautilus is doing, and then reproducing what Nautilus does may let you find out what's going wrong.

It's easy to say "Why won't you fix this bug" but from your description it's impossible to know what's going wrong, and if the Ubuntu developers can't reproduce the bug on their own Samba test servers there's not really anything they can do!

---

### Post by PryGuy on 2010-02-07
I think Launchpad simply doesn't do the things it was designed for. I understand that UbuntuOne for instance is very important for Canonical and all (I get ubuntuone-clent updates almost each day), but hey, there are people that plan to work with Ubuntu and eyecandy is not enough for them. I want a stable system and I don't want to switch to another distro!

---

### Post by cariboo on 2010-02-07
If a bug says fixed released, it just means what it says, the fix has been released, but the new package, hasn't made its way through the build farm and then on to the mirrors yet.

---

### Post by PryGuy on 2010-02-07
> **3rdalbum said:**
> Using the words "sometimes" and "pushing the Refresh button works" is guaranteed to get your bug report triaged as "low".

Submit a bug against Nautilus on Gnome's bugzilla and see what happens. You probably won't get a lot of joy unless you can narrow down exactly why this happens, or what conditions cause it to happen. Maybe looking at the Nautilus source code will help you work out exactly what Nautilus is doing, and then reproducing what Nautilus does may let you find out what's going wrong.

It's easy to say "Why won't you fix this bug" but from your description it's impossible to know what's going wrong, and if the Ubuntu developers can't reproduce the bug on their own Samba test servers there's not really anything they can do!

If you read the comments, I asked them how do I help them solve the problem. I don't even know where Nautilus produces it's logs, if it does at all. I asked them and I had no answer! the word "sometimes" was used to start the dialogue that would come to a solution (as I planned), 'cause as I said before I have no information why it happens and I don't know how to diagnose this problem.

It's strange to me they couldn't reproduce the bug 'cause I had it on THREE machines at home. I could submit my smb.conf if they asked, I could submit everything, but... Well, again, you can read the comments. I agree with you, but that's not the case I'm afraid... Yet, why should I try Bugzilla if I kinda have Launchpad for that?

Okay, my post is bad, but what's wrong with this ['CD/DVD unmount problem']("https://bugs.launchpad.net/ubuntu/+bug/510021") bug report? They haven't even answered it, and the bug desribed there is VERY critical IMHO. 25 days passed since it was filled.

---

### Post by PryGuy on 2010-02-07
> **cariboo907 said:**
> If a bug says fixed released, it just means what it says, the fix has been released, but the new package, hasn't made its way through the build farm and then on to the mirrors yet.
If you are talking of the [mc bug]("https://bugs.launchpad.net/ubuntu/+source/mc/+bug/397497"), the last post saying:> When will the fixed version be uploaded to karmic repository?was dated 2010-01-23. 15 days is not enough to "make it's way"?

---

### Post by Techsnap on 2010-02-07
> 
XP and 7 and  sometimes shows blank window on explorer.exe, SMB protocol is buggy.

Ah right, it happens on Windows so it's fine to ignore it on Ubuntu then.

---

### Post by PryGuy on 2010-02-07
> **Techsnap said:**
> Ah right, it happens on Windows so it's fine to ignore it on Ubuntu then.Yeah, that's what I'm afraid of, another buggy OS. I really hope Ubuntu quality won't fall that low.

As for Windows thing, it mostly happens 'cause there's no Samba Domain Master controller on the network. *nix systems used to work with Samba *flawlessly* having properly configured server.

---

### Post by fewt on 2010-02-07
> **PryGuy said:**
> If you are talking of the [mc bug]("https://bugs.launchpad.net/ubuntu/+source/mc/+bug/397497"), the last post saying:was dated 2010-01-23. 15 days is not enough to "make it's way"?

Just wait till April, maybe it'll be there then.

;)

---

### Post by fewt on 2010-02-07
> **PryGuy said:**
> Yeah, that's what I'm afraid of, another buggy OS. I really hope Ubuntu quality won't fall that low.


Uhh, too late?  It's already there.

---

### Post by PryGuy on 2010-02-07
> **fewt said:**
> Just wait till April, maybe it'll be there then.

;)That's a very sad joke, pal... :(

---

### Post by llawwehttam on 2010-02-07
> **PryGuy said:**
> That's a very sad joke, pal... :(

Err WHAT???
In april 10.04 LTS is released and it should be very stable. I am counting on it to fix several of my current problems.

---

### Post by PryGuy on 2010-02-07
> **llawwehttam said:**
> Err WHAT???
In april 10.04 LTS is released and it should be very stable. I am counting on it to fix several of my current problems.The fact they have LTS as the next release doesn't mean they should totally ignore the problems we have for months I think! Correct me if I'm wrong.

By the way, the [Mystical disappearing Samba shares problem]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/480832") seems to be fixed in Lucid. Care to backport it, Canonical?

---

### Post by Techsnap on 2010-02-07
> The fact they have LTS as the next release doesn't mean they should  totally ignore the problems we have for months I think! Correct me if  I'm wrong.

You're absolutely right however that is the way Ubuntu is done and it's totally wrong. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579) This bug in particular really annoys me, especially considering Ubuntu is marketed as a "Beginner Friendly" distro.

---

### Post by PryGuy on 2010-02-07
> **Techsnap said:**
> You're absolutely right however that is the way Ubuntu is done and it's totally wrong.Is there a way we can change this situation?

> **Techsnap said:**
> This bug in particular really annoys me, especially considering Ubuntu is marketed as a "Beginner Friendly" distroThat's why I still use ext3. :(

---

### Post by fewt on 2010-02-07
> **PryGuy said:**
> That's a very sad joke, pal... :(


Oh, you thought I was JOKING?

No no, I am quite serious.  It's not a security problem, expect it not to be fixed until a fix is pulled downstream.

---

### Post by fewt on 2010-02-07
> **PryGuy said:**
> The fact they have LTS as the next release doesn't mean they should totally ignore the problems we have for months I think! Correct me if I'm wrong.

By the way, the [Mystical disappearing Samba shares problem]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/480832") seems to be fixed in Lucid. Care to backport it, Canonical?

See my article on this:

[http://www.fewt.com/2009/10/dear-mr-shuttleworth-canonical-and.html](http://www.fewt.com/2009/10/dear-mr-shuttleworth-canonical-and.html)

---

### Post by PryGuy on 2010-02-08
I've read it! My thoughts exactly!

---

### Post by PryGuy on 2010-02-08
Just wanted to add... I've just installed Fedora 12 Constantine and:
- [Samba is working fine out of the box]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/480832");
- [CD/DVD ejects just fine out of the box]("https://bugs.launchpad.net/ubuntu/+bug/510021");
- [Midnight Commander saves settings and it has mcedit as a default editor]("https://bugs.launchpad.net/ubuntu/+source/mc/+bug/397497").
Should I say something else? :-\"

---

### Post by 3rdalbum on 2010-02-08
> **PryGuy said:**
> Just wanted to add... I've just installed Fedora 12 Constantine and:
- [Samba is working fine out of the box]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/480832");
- [CD/DVD ejects just fine out of the box]("https://bugs.launchpad.net/ubuntu/+bug/510021");
- [Midnight Commander saves settings and it has mcedit as a default editor]("https://bugs.launchpad.net/ubuntu/+source/mc/+bug/397497").
Should I say something else? :-\"

No, just become a Fedora user. What works well for you is fine by me.

---

### Post by 3rdalbum on 2010-02-08
> **Techsnap said:**
> You're absolutely right however that is the way Ubuntu is done and it's totally wrong. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579) This bug in particular really annoys me, especially considering Ubuntu is marketed as a "Beginner Friendly" distro.

Some people experience corruption, some don't. I ran a test, copied a 25 gig file from an Ext3 partition to an Ext4 and back. The original and the twice-copied file were hashed and compared - no difference.

They've advised users of the problem in the release notes, and there's no upstream fix as far as anyone knows. Some of the original problem reporters are saying that it might not be an ext4 issue. What would you have Ubuntu do?

---

### Post by Techsnap on 2010-02-08
> What would you have Ubuntu do?What do you think? Not use it as a default filesystem on a "beginner friendly distro" and since it's upstream and will affect other distros any distro which isn't "cutting edge" or marketed at beginners should not have it selected by default.

It should be confirmed that there is no problem with the FS at all before it is selected as a default option. Since they know about this as it's in the release notes, they should have held it off.

---

### Post by PryGuy on 2010-02-08
> **3rdalbum said:**
> No, just become a Fedora user. What works well for you is fine by me.Thanks, but I'd love to stay with Ubuntu actually...

---

### Post by GepettoBR on 2010-02-09
> **PryGuy said:**
> Thanks, but I'd love to stay with Ubuntu actually...

Well, you have to make a choice. Weigh the pros and cons - if Fedora fixes a critical bug that Ubuntu doesn't, then you must have a really strong reason to stay with Ubuntu.

---

### Post by Kenny_Strawn on 2010-02-09
> **3rdalbum said:**
> No, just become a Fedora user. What works well for you is fine by me.

Oh, yeah - if I want to deal with package management headaches.

Case in point: You cannot do a distribution upgrade from YUM, and, especially in Fedora, you have much less packages than in Ubuntu.

In Ubuntu, everything just works. In Fedora, you have to hack the things that, in Ubuntu, work fine, such as the package manager and hardware support.

---

### Post by fewt on 2010-02-09
> **Kenny_Strawn said:**
> Oh, yeah - if I want to deal with package management headaches.

Case in point: You cannot do a distribution upgrade from YUM, and, especially in Fedora, you have much less packages than in Ubuntu.

In Ubuntu, everything just works. In Fedora, you have to hack the things that, in Ubuntu, work fine, such as the package manager and hardware support.

Not so sure about this.  I just did a proof of concept conversion test .. I installed fedora, I used alien to convert more than a dozen personal packages to RPM from deb, then I installed every app that I used in Ubuntu without adding any sources.

It's very likely that Fedora is a better distribution in all ways possible.  Fedora hasn't shown any of the instability issues that exist (and are repeatable) within Karmic.

---

### Post by Tibuda on 2010-02-09
> **Kenny_Strawn said:**
> In [s]Ubuntu[/s] **Windows**, everything just works. In [s]Fedora[/s] **Linux**, you have to hack the things that, in [s]Ubuntu[/s] **Windows**, work fine...

I have heard this before.

---

### Post by phrostbyte on 2010-02-09
There is something like 500,000+ bugs on Launchpad. Is it surprising that not every bug gets utmost priority, when there are only a handful of bug triagers and fixers? Actually there is a really 'easy' way to get a bug marked "High", you pay Canonical. :D

---

### Post by fewt on 2010-02-09
> **phrostbyte said:**
> There is something like 500,000+ bugs on Launchpad. Is it surprising that not every bug gets utmost priority, when there are only a handful of bug triagers and fixers? Actually there is a really 'easy' way to get a bug marked "High", you pay Canonical. :D

Don't you think the statement of having 500,000+ bugs is in itself an indicator of poor quality?

;)

---

### Post by phrostbyte on 2010-02-09
> **fewt said:**
> Don't you think the statement of having 500,000+ bugs is in itself an indicator of poor quality?

;)

Or a lot of Ubuntu users.

---

### Post by 23meg on 2010-02-09
> **fewt said:**
> Don't you think the statement of having 500,000+ bugs is in itself an indicator of poor quality?

;)

That old argument was most recently refuted by Karl Fogel:
[[list][*]Bug Growth is Proportional to User Growth, and Bugs are not Technical Debt.[/list]]("http://www.rants.org/2010/01/10/bugs-users-and-tech-debt/")

---

### Post by fewt on 2010-02-09
> **phrostbyte said:**
> Or a lot of Ubuntu users.

Wow, that's some excuse.  It's not really quantifiable that more users equals more bug reports though.

Windows, MacOS, they all have a lot more users than all distributions combined and they don't have that error rate.

Having a lot of users doesn't quantify added bugs, but poor quality control, an immature software development model, and a lack of test suites sure does.

How can you really argue that having lots of users justifies a bug that panics the kernel, or an incomplete computer janitor product that removes software only because it doesn't exist in a repository?

Answer: You cannot. :)

---

### Post by 23meg on 2010-02-09
> **fewt said:**
> Wow, that's some excuse.  It's not really quantifiable that more users equals more bug reports though.

Windows, MacOS, they all have a lot more users than all distributions combined and they don't have that error rate.

Having a lot of users doesn't quantify added bugs, but poor quality control, an immature software development model, and a lack of test suites sure does.

How can you really argue that having lots of users justifies a bug that panics the kernel, or an incomplete computer janitor product that removes software only because it doesn't exist in a repository?

Answer: You cannot. :)

Bug != bug report.

---

### Post by fewt on 2010-02-09
> **23meg said:**
> That old argument was most recently refuted by Karl Fogel:
[[list][*]Bug Growth is Proportional to User Growth, and Bugs are not Technical Debt.[/list]]("http://www.rants.org/2010/01/10/bugs-users-and-tech-debt/")

"The number of bug reports is proportional to the number of users, not to the number of defects."

This "rant" is a misguided method of saying there are more bug reports because there are more users reporting them made by a Canonical employee.  It doesn't make the case for or against an increase in bugs due to lack of quality.

---

### Post by fewt on 2010-02-09
> **23meg said:**
> Bug != bug report.

I'll give you that one.

---

### Post by 23meg on 2010-02-09
> **fewt said:**
> 
This "rant" is a misguided method of saying there are more bugs because there are more users

Bug reports, not bugs.

> **fewt said:**
> reporting them made by a Canonical employee with how much real world experience? 

[This much]("http://producingoss.com/").

[QUOTE=fewt]It doesn't make the case for or against an increase in bugs due to lack of quality.[/QUOTE]

Neither does a bare statement of the number of open bug reports in a project's bug tracker, which is the fallacy that the article argues against.

---

### Post by fewt on 2010-02-09
> **23meg said:**
> Bug reports, not bugs.


You'll see that I corrected that statement before your reply.

> **23meg said:**
> 
[This much]("http://producingoss.com/").


It's not difficult to write a book, the most difficult challenge is time.  You don't even need to be a subject matter expert to be published.  The fact that he wrote a book neither makes his rant accurate or inaccurate.  Literary inaccuracies have plagued humanity for eons.  See Sarah Palin's recent book for a fine example of how "anyone" (right or wrong) can get published.

> **23meg said:**
> 
Neither does a bare statement of the number of open bug reports in a project's bug tracker, which is the fallacy that the article argues against.

I will accept that the number of bug reports does not equal the number of bugs, but I will argue that a measurement of success would be users not needing to report bugs.  The only thing bug reports are good for is being indicators that there are problems with software quality, or usability.

Users that have no problems do not report bugs because it is not necessary.

The same is true of technical support, users don't call tech support if they do not need to.

In the case of Linux distributions, you can make the argument that a bug report is the equivalent of calling tech support.

---

### Post by dmizer on 2010-02-09
Many of you do not seem to understand how bugs are rated. It would be a good idea to understand how bugs are rated in the first place.

The severity of the bug is not rated by how many people it effects. The severity of a bug is rated by what kind of effect it has on the opperation of the system. In other words, a critical bug is one which prevents the system from booting, causes the system to crash, or become inoperable.

Edit to add source:
[https://wiki.ubuntu.com/Bugs/Importance](https://wiki.ubuntu.com/Bugs/Importance)

---

### Post by 23meg on 2010-02-09
[QUOTE=fewt]It's not difficult to write a book, the most difficult challenge is time. You don't even need to be a subject matter expert to be published. The fact that he wrote a book neither makes his rant accurate or inaccurate. Literary inaccuracies have plagued humanity for eons. See Sarah Palin's recent book for a fine example of how "anyone" (right or wrong) can get published.[/QUOTE]

I'm not stating that he's experienced or right solely due to the fact that he wrote *a* book. I'm pointing to an actual, written book on developing open source software in which his experience in the field is manifest. If you browse through the table of contents, you'll get an idea.

If you have further doubts about the credibility of the author, a web search should reveal a summary of his past "real life experience", including his experience as co-creator and long time developer of Subversion.

[QUOTE=fewt]but I will argue that a measurement of success would be users not needing to report bugs. The only thing bug reports are good for is being indicators that there are problems with software quality, or usability.

Users that have no problems do not report bugs because it is not necessary.[/quote]

The first half of the article challenges this very notion. There can be no active software project of any reasonable complexity where reporting bugs will not be necessary, thus is best to dispense with that picture of bug-free or zero-open-bug-report software as an ideal.

[quote=fewt]In the case of Linux distributions, you can make the argument that a bug report is the equivalent of calling tech support.[/quote]

Posting one's problem to a support forum or answer tracker is closer to being an equivalent of that.

---

### Post by fewt on 2010-02-09
> **23meg said:**
> I'm not stating that he's experienced or right solely due to the fact that he wrote *a* book. I'm pointing to an actual, written book on developing open source software in which his experience in the field is manifest. If you browse through the table of contents, you'll get an idea.

If you have further doubts about the credibility of the author, a web search should reveal a summary of his past "real life experience", including his experience as co-creator and long time developer of Subversion.

The first half of the article challenges this very notion. There can be no active software project of any reasonable complexity where reporting bugs will not be necessary, thus is best to dispense with that picture of bug-free or zero-open-bug-report software as an ideal.

Posting one's problem to a support forum or answer tracker is closer to being an equivalent of that.

So what you are saying is that you cannot be wrong because he wrote an open source software product called subversion and wrote a book so you have to believe that he's right.

Proprietary software has been successful at the very thing that you are arguing against for more than 40 years.

Not only that, you haven't introduced any measurable metric that proves that his "RANT" is an accurate view of bug reporting other than he has been a successful member of a single software product.

This forum is the last place to go for technical help.  The level of arrogance, and bad attitude towards users with issues in this forum is atrocious.

I stand firm that the view is extremely flawed, and until you can prove it with a quantifiable measurement of success, I'll continue to hold that view.  In my opinion, this just adds to the lackluster product that is Ubuntu.  Coming from a member of the quality team it speaks volumes.

1. What are your key performance indicators? - How do you measure successful quality control?

2. Where is your test suite?  What test cases do you execute against the distribution, and what test hardware is used for the execution of the testing?

3. Where are your test reports published?  Where can I go to review which modules were benchmarked prior to getting the green light to release?

4. What is in place to test for code regressions?  How do you ensure that new code being released doesn't re-introduce old flaws?

You cannot use posts in a forum as an accurate method of technical support, because you cannot measure against it.

You can however measure against the number of open bugs.  Prove to me that users do not open bug reports because of issues of software quality or usability.

Your launchpad bug tracker is full of both types of issues, which is a key performance indicator leaning towards a lack of quality.  This is true even if you don't like it, or agree with it.

Go look for yourself.

---

### Post by GepettoBR on 2010-02-10
> **fewt said:**
> This forum is the last place to go for technical help.  The level of arrogance, and bad attitude towards users with issues in this forum is atrocious.

This is irrelevant to the point of discussion.

Open bugs are not a safe indicator of anything simply because there is no way to measure the proportion of people who have problems that actually report them. If a certain project happens to target an audience that for whatever reason is more prone to reporting bugs, it will have many more bug reports than a similar project with a comparable number of bugs and a less contributive user base. The issue of duplicate bug reports, including those that are not easily flagged as duplicates because the same error in coding can produce more than one symptom (especially in lower-level code) adds to the complete inaccuracy of the number of bug reports as a way to measure anything at all.

---

### Post by caravel on 2010-02-10
I believe the bug in question is *upstream*.

---

### Post by fewt on 2010-02-10
> **GepettoBR said:**
> This is irrelevant to the point of discussion.


> **23meg]
Posting one's problem to a support forum or answer tracker is closer to being an equivalent of that.
[/quote]

That statement makes it relevant.

[QUOTE=GepettoBR said:**
> 
Open bugs are not a safe indicator of anything simply because there is no way to measure the proportion of people who have problems that actually report them. If a certain project happens to target an audience that for whatever reason is more prone to reporting bugs, it will have many more bug reports than a similar project with a comparable number of bugs and a less contributive user base. The issue of duplicate bug reports, including those that are not easily flagged as duplicates because the same error in coding can produce more than one symptom (especially in lower-level code) adds to the complete inaccuracy of the number of bug reports as a way to measure anything at all.

It sure sounds like a good baseline to me.  Users with issues report problems.  The number of users using and reporting problems with an application has an effect, sure.  Users that don't use an app don't report bugs with that app.  That's not rocket science.  You can't disregard any bug report or you flag a user with a problem as irrelevant and unimportant.

Duplicate bugs just help to prove the fact that a bug report wouldn't exist if a user didn't have a problem in the first place.

There is a variance for error, absolutely.  It is still valid measurable data.

Count your bugs, separate unconfirmed and confirmed bugs into two piles.  Unconfirmed bugs count as usability problem bugs, and confirmed bugs count as software quality issues.  Count duplicate reports.

Now, measure those against your number of users.  Use real numbers, not Marks unsubstantiated number of 10,000,000.

Anyone that implies that you cannot measure bug reports as a metric of quality doesn't understand quality.  Users that don't have problems don't report bugs, and that's the bottom line.

---

### Post by PryGuy on 2010-02-10
They've set [my bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/480832") as confirmed! Hallelujah!!! No comments...

---

### Post by GepettoBR on 2010-02-10
> **fewt said:**
> Users that don't have problems don't report bugs, and that's the bottom line.

Users who do don't necessarily report them, though, and that was the point of my last post.

My argument is that the margin of error for the "number of bug reports" data as a way to measure software quality is huge, which makes it unreliable data.

---

### Post by fewt on 2010-02-10
> **GepettoBR said:**
> Users who do don't necessarily report them, though, and that was the point of my last post.

My argument is that the margin of error for the "number of bug reports" data as a way to measure software quality is huge, which makes it unreliable data.

I don't agree.  There is a margin of error no matter what metric you are reporting on, for any data set.  That doesn't in any way make it unreliable data.  Users not reporting issues they have just don't get counted in your metric, that doesn't invalidate the data it just reduces the numbers.

---

### Post by phrostbyte on 2010-02-10
> **fewt said:**
> Wow, that's some excuse.  It's not really quantifiable that more users equals more bug reports though.

Windows, MacOS, they all have a lot more users than all distributions combined and they don't have that error rate.


Wow you work for Microsoft and Apple at the same time? :p

---

### Post by doas777 on 2010-02-10
> **juancarlospaco said:**
> XP and 7 and sometimes shows blank window on explorer.exe, SMB protocol is buggy.
true, but on a correctly configured network, it only happens a handful of times per year.

---

### Post by fewt on 2010-02-10
> **phrostbyte said:**
> Wow you work for Microsoft and Apple at the same time? :p

Way to add to the thread.

Gold Star: :KS

---

### Post by phrostbyte on 2010-02-10
> **fewt said:**
> Way to add to the thread.

Gold Star: :KS

Well you seem to imply that you had intimate knowledge of Microsoft's and Apple's *internal* bug tracking processes. So it's safe to assume you are an employee of both companies. Or you were just making that up.

---

### Post by fewt on 2010-02-10
> **phrostbyte said:**
> Well you seem to imply that you had intimate knowledge of Microsoft's and Apple's *internal* bug tracking processes. So it's safe to assume you are an employee of both companies. Or you were just making that up.

Microsoft and Apple don't have customers then?  I implied that they had customers and that they were successful.

I have also attended Microsoft Solutions Framework training, it's not internal, it is published information.

---

### Post by phrostbyte on 2010-02-10
> **fewt said:**
> Microsoft and Apple don't have customers then?  I implied that they had customers and that they were successful.

I have also attended Microsoft Solutions Framework training, it's not internal, it is published information.

How do I access this nonexistent public bug tracker? :D

---

### Post by fewt on 2010-02-10
> **phrostbyte said:**
> How do I access this nonexistent public bug tracker? :D

I guess you get to go to my ignore list.

---

### Post by 23meg on 2010-02-10
[QUOTE=fewt]So what you are saying is that you cannot be wrong because he wrote an open source software product called subversion and wrote a book so you have to believe that he's right.[/QUOTE]

No, I'm saying that he has a strong argument against the classic fallacy of the correlation between the number of bug reports and software quality, and upon your questioning of his real life experience with which to back that argument, I pointed to his past work. That's it.

[QUOTE=fewt]Proprietary software has been successful at the very thing that you are arguing against for more than 40 years.[/QUOTE]

To rewind a few posts: the thing I was arguing against was your implication that lots of bug reports might mean low software quality. 

[QUOTE=fewt]Not only that, you haven't introduced any measurable metric that proves that his "RANT" is an accurate view of bug reporting other than he has been a successful member of a single software product.[/QUOTE]

[http://people.canonical.com/~brian/graphs/](http://people.canonical.com/~brian/graphs/) can present some clues. Note the peaks in open bugs around the release dates in April and October.

[QUOTE=fewt]This forum is the last place to go for technical help. The level of arrogance, and bad attitude towards users with issues in this forum is atrocious.[/QUOTE]

I agree that this forum isn't a good place to get technical help any longer outside certain scenarios such as "absolute beginner looking for help on the very basics", at which it excels, but I didn't say anything about this particular forum being a good place to get help. I said (note the emphasis):

[QUOTE=23meg]Posting one's problem to **a** support forum or answer tracker is closer to being an equivalent of that.[/QUOTE]

By which I meant: bug reports aren't intended as a support mechanism in free software. Support is handled in user forums, mailing lists and answer trackers. Filing a bug report is generally an act that signifies that you want to help fix a software defect that you think others might be suffering from as well, *for everyone*, rather than just jump over an annoying error dialog yourself and continue your daily work.

[quote=fewt]I stand firm that the view is extremely flawed, and until you can prove it with a quantifiable measurement of success, I'll continue to hold that view. In my opinion, this just adds to the lackluster product that is Ubuntu. Coming from a member of the quality team it speaks volumes.[/quote]

Your unnecessarily hostile attitude makes me reluctant to take the time and effort to prove anything to you. Feel free to use Launchpad advanced search, the Launchpad API or various snapshots of Ubuntu bug statistics that you can find via a web search, which I'm absolutely confident will display a growing number of reported bugs per release, and a relatively steady number of triaged, actual bugs fixed per release. 

[quote=fewt]1. What are your key performance indicators? - How do you measure successful quality control?[/quote]

I'm not really interested or involved in the messy business of quantifying success, but in the realm of numbers that's typically done by looking at the amount and severity of genuine bugs reported, triaged and fixed in a release cycle.

[quote=fewt]2. Where is your test suite? What test cases do you execute against the distribution, and what test hardware is used for the execution of the testing?

3. Where are your test reports published? Where can I go to review which modules were benchmarked prior to getting the green light to release?[/quote]

[https://wiki.ubuntu.com/Testing/Automation](https://wiki.ubuntu.com/Testing/Automation)
[https://wiki.ubuntu.com/AutomatedTesting](https://wiki.ubuntu.com/AutomatedTesting)
[http://testcases.qa.ubuntu.com/](http://testcases.qa.ubuntu.com/)
[http://people.canonical.com/~fader/hw-testing/current](http://people.canonical.com/~fader/hw-testing/current)

[quote=fewt]4. What is in place to test for code regressions? How do you ensure that new code being released doesn't re-introduce old flaws?[/quote]

[http://qa.ubuntu.com/reports/regression/regression_tracker.html](http://qa.ubuntu.com/reports/regression/regression_tracker.html)
[https://wiki.ubuntu.com/QATeam/RegressionTracking](https://wiki.ubuntu.com/QATeam/RegressionTracking)
[https://lists.ubuntu.com/archives/ubuntu-devel/2008-September/026480.html](https://lists.ubuntu.com/archives/ubuntu-devel/2008-September/026480.html)

[quote=fewt]You cannot use posts in a forum as an accurate method of technical support, because you cannot measure against it.

You can however measure against the number of open bugs. Prove to me that users do not open bug reports because of issues of software quality or usability.[/quote]

I never said anything so absurdly incorrect as that users don't report bugs because of quality or usability issues. 

[quote=fewt]Your launchpad bug tracker is full of both types of issues, which is a key performance indicator leaning towards a lack of quality. [/quote]

A bug tracker having lots of bugs or bug reports in it, by itself, is indicative of nothing other than *activity*. Feel free to point to a single study by a credible QA engineer or department, a single peer reviewed paper, or any other credible study in the field that takes the number of bugs reported in a project as directly indicative of its quality.

---

### Post by phrostbyte on 2010-02-10
> **23meg said:**
> No, I'm saying that he has a strong argument against the classic fallacy of the correlation between the number of bug reports and software quality, and upon your questioning of his real life experience with which to back that argument, I pointed to his past work. That's it.

I don't really think it's a "classic fallacy", if that means something that truly a lot of educated people believe. It's similar I think to trying to judge the value of a company based on the number of shares in circulation. Clearly without at least knowing the value of those shares, you can't really make any conclusions. 

If this isn't bad enough, fewt made a impossible comparison, implicitly assuming that some group like Microsoft or Apple doesn't get as many bug reports as Ubuntu. Something I doubt is true but you can't prove it one way or another, because their bug trackers are internal. Instead of disputing this or accepting it, he ragequits. =D>

---

### Post by 23meg on 2010-02-10
> **PryGuy said:**
> They've set [my bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/480832") as confirmed! Hallelujah!!! No comments...

"Confirmed" is a status that anyone can set any bug to, and the person who set the status of that bug isn't a developer or a bug triager.

More on bug status:

[https://wiki.ubuntu.com/Bugs/Status](https://wiki.ubuntu.com/Bugs/Status)

---

### Post by fewt on 2010-02-11
> **23meg said:**
> No, I'm saying that he has a strong argument against the classic fallacy of the correlation between the number of bug reports and software quality, and upon your questioning of his real life experience with which to back that argument, I pointed to his past work. That's it.

Fair enough.


> **23meg]
To rewind a few posts: the thing I was arguing against was your implication that lots of bug reports might mean low software quality. 
[/QUOTE]

Ok, you have argued against it, what you haven't done though is made the case that lots of bug reports might NOT mean low software quality.  said:**
> 
[http://people.canonical.com/~brian/graphs/](http://people.canonical.com/~brian/graphs/) can present some clues. Note the peaks in open bugs around the release dates in April and October.


This is great, I like this a lot.  How do you seperate bugs that are closed as fixed in a past release when a new release supercedes it?  IE:  A bug in Jaunty is unrepaired in Jaunty yet fixed in Karmic so it is flagged as fixed in Jaunty.

Example:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337199](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337199)

> **23meg]
I agree that this forum isn't a good place to get technical help any longer outside certain scenarios such as "absolute beginner looking for help on the very basics", at which it excels, but I didn't say anything about this particular forum being a good place to get help. I said (note the emphasis):
[/quote]

Fair enough.  I don't believe that this is a safe place for absolute beginners either though, there is too much mis-information by users that have little to no experience beyond something working for them.

[QUOTE=23meg]
By which I meant: bug reports aren't intended as a support mechanism in free software. Support is handled in user forums, mailing lists and answer trackers. Filing a bug report is generally an act that signifies that you want to help fix a software defect that you think others might be suffering from as well, *for everyone*, rather than just jump over an annoying error dialog yourself and continue your daily work.
[/quote]

Right, they aren't intended as a support mechanism.  I am implying that they could, and that maybe they should be.  I don't see the user forum, mailing list, or answer tracker mechanism working out.  I have seen far too often bad information or ignoring of questions (including questions I have posed on launchpad).  Filing a bug report generally signifies that a user has a problem.  I don't know that you can make the case that it's only because a user wants to help.  In my experience, it means they have a problem.  Sort of like an enterprise ticketing system.  You can peruse bug reports and see this trend.

[QUOTE=23meg]
Your unnecessarily hostile attitude makes me reluctant to take the time and effort to prove anything to you. Feel free to use Launchpad advanced search, the Launchpad API or various snapshots of Ubuntu bug statistics that you can find via a web search, which I'm absolutely confident will display a growing number of reported bugs per release, and a relatively steady number of triaged, actual bugs fixed per release. 
[/quote]

It's interesting that you imply that I am being hostile, that's not the case at all.  I'm mearly stating what I see.  There is no implication of emotion in either direction, if you want to improve you should become better at accepting criticism if you think that this is hostile in any way.

If you are using it as an excuse to ignore my statements, well that's your choice.  Reluctance to prove anything to me doesn't help you.  It doesn't do anything for me except justify my observations further.  Believe me, I've been looking at bugs for a long time.  I have spent months waiting for critical bugs to get fixed.  I'm not just another clueless user.  said:**
> 
I'm not really interested or involved in the messy business of quantifying success, but in the realm of numbers that's typically done by looking at the amount and severity of genuine bugs reported, triaged and fixed in a release cycle.


You would have to be interested in the business of quantifying success if Canonical expects to get out of the black.  It wouldn't be a smart business decision to ignore critical success factors.

[QUOTE=23meg]
[https://wiki.ubuntu.com/Testing/Automation](https://wiki.ubuntu.com/Testing/Automation)
[https://wiki.ubuntu.com/AutomatedTesting](https://wiki.ubuntu.com/AutomatedTesting)
[http://testcases.qa.ubuntu.com/](http://testcases.qa.ubuntu.com/)
[http://people.canonical.com/~fader/hw-testing/current](http://people.canonical.com/~fader/hw-testing/current)
[http://qa.ubuntu.com/reports/regression/regression_tracker.html](http://qa.ubuntu.com/reports/regression/regression_tracker.html)
[https://wiki.ubuntu.com/QATeam/RegressionTracking](https://wiki.ubuntu.com/QATeam/RegressionTracking)
[https://lists.ubuntu.com/archives/ubuntu-devel/2008-September/026480.html](https://lists.ubuntu.com/archives/ubuntu-devel/2008-September/026480.html)
[/quote]

Thanks, I'll research these before commenting on them.

[QUOTE=23meg]
I never said anything so absurdly incorrect as that users don't report bugs because of quality or usability issues. 
[/quote]

Sorry if I misunderstood you, as it seemed to be implied.

[QUOTE=23meg]
A bug tracker having lots of bugs or bug reports in it, by itself, is indicative of nothing other than *activity*. Feel free to point to a single study by a credible QA engineer or department, a single peer reviewed paper, or any other credible study in the field that takes the number of bugs reported in a project as directly indicative of its quality.[/QUOTE]

I would start with ITIL incident and problem management - [http://en.wikipedia.org/wiki/Information_Technology_Infrastructure_Library](http://en.wikipedia.org/wiki/Information_Technology_Infrastructure_Library)

---

### Post by GepettoBR on 2010-02-11
> **fewt said:**
> I don't agree.  There is a margin of error no matter what metric you are reporting on, for any data set.  That doesn't in any way make it unreliable data.  Users not reporting issues they have just don't get counted in your metric, that doesn't invalidate the data it just reduces the numbers.

The existence of a margin isn't a problem. The fact that the margin is significantly large, however, is. I made that clear in my last post (emphasis added): 

> **GepettoBR said:**
> My argument is that **the margin of error** for the "number of bug reports" data as a way to measure software quality **is huge, which makes it unreliable data**.

If I told you that an election poll put the leading candidate at a 52% vote intention and the runner-up at 40%, but that the error margin was 30% in either direction, would you call my poll a reliable indication of the electorate's vote intention?

That poll would mean that the actual vote intention could be anywhere between 82% for candidate A and 10% for candidate B or 70% for candidate B and 22% for candidate A. in other words, the data tells us nothing and the size of the error margin is to blame.

---

### Post by fewt on 2010-02-11
> **GepettoBR said:**
> The existence of a margin isn't a problem. The fact that the margin is significantly large, however, is. I made that clear in my last post (emphasis added): 


You seem to assume that your statements are fact, but there isn't any evidence provided to support that implication.  How do you measure that the margin is large if you don't apply any measurements?

[QUOTE=GepettoBR]
If I told you that an election poll put the leading candidate at a 52% vote intention and the runner-up at 40%, but that the error margin was 30% in either direction, would you call my poll a reliable indication of the electorate's vote intention?

That poll would mean that the actual vote intention could be anywhere between 82% for candidate A and 10% for candidate B or 70% for candidate B and 22% for candidate A. in other words, the data tells us nothing and the size of the error margin is to blame.[/QUOTE]

An election has clearly defined measurements and goal definitions and what you are arguing as "fact" doesn't currently.

An election doesn't have a 30% margin of error because it's properly measured.

---

### Post by fewt on 2010-02-11
Its pointless to try to help those that don't want to be helped, or are blinded by arrogance so I guess further attempts to try to help improve quality are a waste of time.

---

### Post by dmizer on 2010-02-11
> **fewt said:**
> Its pointless to try to help those that don't want to be helped, or are blinded by arrogance so I guess further attempts to try to help improve quality are a waste of time.

To be fair, you're talking about responses to things you've posted in a public forum. That's like trying to change how a business is run by talking in the parking lot after work.

Or in other words, there are probably better places (and better people) to present your case regarding quality management.

---

### Post by fewt on 2010-02-11
> **dmizer said:**
> To be fair, you're talking about responses to things you've posted in a public forum. That's like trying to change how a business is run by talking in the parking lot after work.

Or in other words, there are probably better places (and better people) to present your case regarding quality management.

It is no different than a meeting in any public place.

Golf course, Airplane, most deals are made this way.  I didn't imply changing how a business is run, I just saw an area where I thought there could be improvement and I spoke my mind.  I've seen questions go unanswered all over the place, and I'm sure there are better places, but any opportunity that's not taken advantage of is an opportunity missed.

I don't use Ubuntu anymore (due to its lack of quality) so it doesn't really impact me.  I guess I should just shut my mouth and not try to take advantage of opportunities (no matter how big or small) to lend my experience.  ;)

 /unsubscribed

---

### Post by dmizer on 2010-02-11
Closed for review.

---


---
title: "Why dosent my work place use Linux?"
date: 2007-05-24
forum: The Cafe
---

### Post by DR_K13 on 2007-05-24
So at work we use windows 2000. However, all our apps run off redhat servers and via emulators . Every single app is linux. Wouldnt it be easy to run Nix  and have the apps installed on out computers? 
I dont get it. The only other programs we use that are windows are Outlook and IE. The company is upgrading to XP and they are bitching about the costs. 

:rolleyes:

---

### Post by stmiller on 2007-05-24
What!? That is crazy.

---

### Post by aktiwers on 2007-05-24
Didnt you ask them?

---

### Post by juxtaposed on 2007-05-24
That seems like the 100% perfect place to use linux.

Odd :P

---

### Post by davahmet on 2007-05-24
I know of a small business that was in a similar situation.  However, rather than dumping about $20,000 for new computers to replace their old Win2000 machines, their IT director recommended delaying the purchase long enough to run a 6-month experiment for running a mixed environment in their office.

Aside from the business owner who loves Outlook and can't see why he should dump it, and a few applications that are Windows-only and have no substitute, most of the productivity on the office desktop computers are easily replaced by Linux substitutes.  He also found that of the 16 employees plus the owner, at most only two of them ever use the Windows-only apps at any given time.  This is their scenario and business need.

He recommended purchasing a new system for $1,600, installing CentOS along with VMWare server to provide 4 virtual windows machines loaded with the necessary Windows applications.  The remaining office desktops (including the owner's) were then wiped clean and Ubuntu 6.10 installed.

The office staff was taught to use Ubuntu for 90% of their work.  For those Windows-only applications, the users were taught to use the Gnome Remote Desktop to log into one of the Windows virtual machines.  From what I have been told, they are about two months into their experiment and so far it has gone very well for them.  The only issue is that apparently they must keep their experiment a secret because a number of their clients  would disapprove.

---

### Post by Zyphrexi on 2007-05-25
that's incredible and very cool. More businesses should use linux. A lot of people argue since windows is pretty much business, that switching to linux isn't practical. Or at least that's what i'm told when i'm out jobhunting looking for businesses that use linux instead of windows. The only thing that validates that claim is microsoft's refusal to integrate open global standards into their programs, but instead in essence proclaim that they are the world standard. Standardization is the biggest argument when it comes to document types, of which business uses a great deal.

---

### Post by dca on 2007-05-25
Well, I hope the firm is not buying blanket MS WinXP licenses for outdated workstations?  Better to standardize, call Dell or HP and get XP machines from them...  At least the MS EULA is subsidized (based on OEM disconunts) so the savings are passed down to you.
 
I did consulting work for a law firm a little while back and their big thing was going mobile.  They had a bunch of old Celeron-based laptop(s) along w/ tons of other equipment:  servers, old workstations, etc.  The Dell servers were turned from Windows 2000 server (nobody knew where the licenses were, it was junk otherwise) into Linux boxes which allowed them to convert all their mounds and mounds of documents to digital media and the laptops got SLED10...  From there they can access anything they need from anywhere...  Oh, their email was web-based to eliminate the need for Outlook.  The pain in the rear thing was if you're laptop was not connected to the network you couldn't save a bunch of emails or reply to a bunch and keep them in your Outbox until your email client detected a network to send, but, hey, it saved them a bunch of moneys...

---

### Post by esaym on 2007-05-25
The old saying:

"No one ever got fired for going with microsoft"

---

### Post by Brunellus on 2007-05-25
> **esaym said:**
> The old saying:

"No one ever got fired for going with microsoft"
although the original was "nobody ever got fired for buying IBM"

---

### Post by esaym on 2007-05-25
> **Brunellus said:**
> although the original was "nobody ever got fired for buying IBM"


Yea I think it changed in 1998 maybe? :-s

---

### Post by MOS95B on 2007-05-25
So, important question that hasn't been asked, where do you work.   

Biggest reason to stick with Windows:  No training required.  The people that work there already are used to windows.  Anyone they hire in the near future is likely to know windows.  In an interview, if asked "Do you know how to operate a computer?" 99% of the time, it means "Can you work with Windows".   Unless you work at a tech company, they're going to expect the average employee to be a Windows/Outlook/IE user.  Why train someone to use Linux, when the knowledge base is already out there for Windows.  MS/Windows licensing is cheaper than the costs in manpower to train/retrain employees

Already been down this exact same route with my previous employer, and it was a tech company.  The people that ran the servers had windows desktops, even though the servers (100's of them) were almost all Unix/Linux.  Mine was the only exception I know of.  It was MS Server 2003

---

### Post by jackmc on 2007-05-25
> **MOS95B said:**
> So, important question that hasn't been asked, where do you work.   

Biggest reason to stick with Windows:  No training required.  

Exactly. The cost/effort of converting/retraining people is seen as too large.

---

### Post by arsenic23 on 2007-05-25
Here's an even odder one:

A year ago a quit my job managing a small computer repair shop.  While I worked there I pretty much ran the place without input from the owner.  I had only one guy working under me, unless you count random high school students that the owner would occationally hire.  They never stuck around, because I pretty much refused to schedual them any kind of hours; they just didn't work hard enough.  

While I was working there I had begun switching over to Ubuntu for more and more tasks at home and the other fellow had pretty much been using Fedora at his home since his very first computer.  So needless to say by the time I left almost all of the repair side of the busness was run using linux.  We had one hard drive with XP on it which was only used for Nod32 and Acronis.

When I left the owner decided to try her hand at running the shop herself and took over managing the repair side of the bussness.  I spent a few weeks showing her what our setup was and then I scooted off out of town. Shortly after my number2 guy also left because he felt working under her was not nearly as fun as working with me, and well he never really needed the money he got from working there. 

ANYWAY, I recently paid a visit to my parents and while I was back in town I thought I'd stop in and see how the shop was doing.  What surprised me was that not a single machine had kept it's linux install.  This wouldn't be so surprising, save I know that the owner's first experience with computers was with Unix, that she had worked in the command line for years and years, and even though it had been awhile, she had often deomonstrated that she knew her way around a *nix command line.  

When I asked her why she put XP on all of these boxes, she didn't really have an answer.  It's just that she had bought a site lisense from Microsoft and put fresh installs of XP on nearly everything.  She'd been having some serious trouble, though, because she couldn't keep alot of stuff running properly.  For some reason she had even installed Server 2003 on the security systems computer, which wasn't even compatible with the cameras I had set up.  I got paid to get alot of this stuff back up and running, but now I get calls all the time whenever something just mysteriously stops working.  She still can't give me a good reason why she won't switch back to running linux on some of the work boxes.  When I ask her she normally just says that it's a matter of taste, she just likes Windows better.  Go figure.

---

### Post by jfdill_2 on 2007-05-25
> **DR_K13 said:**
> So at work we use windows 2000. However, all our apps run off redhat servers and via emulators . Every single app is linux. Wouldnt it be easy to run Nix  and have the apps installed on out computers? 
I dont get it. The only other programs we use that are windows are Outlook and IE. The company is upgrading to XP and they are bitching about the costs. 

:rolleyes:

$200-300 for XP Pro + labor to install on (probably) computers that won't run it adequately (or pay for memory upgrades and such to bring them up to spec) not to mention may be out of warranty with hardware likely to fail soon?  I hope at least they are planning to backup user files and deploy images and not try to apply the "upgrade" to each individual computer.  Probably cost about the same to replace the computers.  Donate the old ones to a non-profit and take the tax write off, unless they suck so bad that even a public school won't take them.

What are people doing for Linux to address the issue of sharing documents with other businesses, for example if some dingbat sends you something in some special Office 2007 format?  I guess you could tell them to resend it in some other format, but if you are a service-oriented business, you don't want to lose a customer over making them convert a doc into some other format--sounds silly, but I'm sure it does happen.  If someone is asking for bids from multiple vendors, and you're the only one that complains about the file format, they'll probably just skip you or at least there will be delays.

The only thing I've found is to load the file on a Windows workstation then re-save in a format that I can work with on Linux, then I may have to do the reverse to send it back to them in a format they can handle and edit if necessary.

---

### Post by davahmet on 2007-05-26
If your office uses Windows XP machines with Office 2003, which is still very common, you also have no way to read an Office 2007 document.  This issue has arisen with every release of Microsoft Office breaking compatibility with previous versions.

Alternatively, if someone sends a .odt document to an office that has only Windows and Microsoft Office, unless they know to unarchive the file, thay also may no read it.

---

### Post by jfdill_2 on 2007-05-26
> **davahmet said:**
> If your office uses Windows XP machines with Office 2003, which is still very common, you also have no way to read an Office 2007 document.  This issue has arisen with every release of Microsoft Office breaking compatibility with previous versions.

Alternatively, if someone sends a .odt document to an office that has only Windows and Microsoft Office, unless they know to unarchive the file, thay also may no read it.

There is a patch available from Microsoft to allow older versions of office to open Office 2007 documents:

[http://www.microsoft.com/downloads/details.aspx?FamilyID=941b3470-3ae9-4aee-8f43-c6bb74cd1466&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=941b3470-3ae9-4aee-8f43-c6bb74cd1466&displaylang=en)

---

### Post by Zyphrexi on 2007-05-29
I have a hard time hiding my love for linux when applying for jobs, since a lot of interviewers don't know what linux is. I forget this of course, using it every day. I think, Linux > Windows, so if I know how to use and run stuff on linux, I can troubleshoot windows comps no problem. Once in a great while I'll get lucky and someone will know what it is, or has used it/seen it/etc. I remember looking for schools online that I could enroll that taught linux, I found one and called up the school, the guy I talked to thought linux was a word processing program. I explained that it was an OS (funny since the school was a TECH school, and taught a lot of linux classes), and got into a long argument explaining why E-mail clients fundamentally work the same and I did NOT need outlook express to be able to take an online course. I guess the class communicated via newsgroup, and I spent about 20 minutes explaining what a newsgroup was.

In short, most people aren't techs, haven't heard of linux, or don't care. The other ones are stubborn idiots, like this guy, who refuses to acknowledge anything. (I make him sound decent, but in reality I swear I was arguing with a kid)

Oh yeah, and think of this as well, managers won't use what they don't know. Super tech A uses and loves linux, but uber-manager-san thinks it's a type of foliage.

---


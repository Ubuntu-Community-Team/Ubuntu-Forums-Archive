---
title: "Reasons businesses should switch to Linux"
date: 2010-01-14
forum: The Cafe
---

### Post by Calixte on 2010-01-14
I'm writing an article on [TechHaze]("http://techhaze.com") on why businesses should switch to Linux that will probably also be published in y[our business ezine]("http://yourbusinessezine.com") . Most of it is really straight-forward, but I'm afraid I'll miss some good points. Do you have any opinions or ideas you would like to share?

Also, questions like that of software stability are debatable. Does anyone have concrete numbers?

Thanks,
C.

---

### Post by Madel on 2010-01-14
[B]its reasons business should switch to mac, not linux. i mean the link.
[/B]

---

### Post by Calixte on 2010-01-14
No, that's the link to the blog. Florian Wardell has published the pro-Mac article, and I'll publish a pro-Linux one.

---

### Post by anaconda on 2010-01-14
the obvious advantages are:
1. safety from viruses etc.
2. saving loads of money, if you can find free applications that fullfill your need.
3. more robust servers (really)
4. Office2007 works in wine. (a business will propably need some office licenses, because other businesses use it)
5. you can let your employers install whatever linux programs they want, without worrying about licenses, and that are you "legal"



But I wouldn't suggest moving completely to linux. there almost always are some windows programs that a business needs and that wont work in wine. So it would be worth the invested money to have a couple of windows machines too... they could be machines that everyone has the right to use.. eg. to convert an office2010 file to a format that openoffice can handle better..

---

### Post by Calixte on 2010-01-14
> **anaconda said:**
> 
3. more robust servers (really)
Do you have numbers to defend that? (It's obvious, I've read enough to know that, but I'd like my arguments to be as strong as possible

> **anaconda said:**
> 
4. Office2007 works in wine. (a business will propably need some office licenses, because other businesses use it)
I didn't know (MS products cost too much for me anyway) but it's somethis to be noted. Thanks.

> **anaconda said:**
> 
5. you can let your employers install whatever linux programs they want, without worrying about licenses, and that are you "legal"

I didn't think of that. I'll definitively *will* write something about the (lack of) legal hassle.

Thanks a lot for your suggestions :)

---

### Post by gsmanners on 2010-01-14
- Compiz, which improves usability for some people.
- Repositories, which contain nearly everything you need in one convenient place.
- Authenticated developers contribute code to the repositories, which makes it hard to sneak malicious code in.
- Source code is available on most applications, which can be handy if you need to do a custom version of the software you use.
- Most of the applications adhere rigidly to open standards. This allows the documents you create to remain professional-looking and usable for as long as you store the document.

---

### Post by SchizmWolf on 2010-01-14
I've thought about bringing it up to my boss, though I know he wouldn't go for it. My reasoning is that Ubuntu isn't vulnerable to the vast majority of viruses, trojans, etc. that are out there. Recently one of the computers at my place of work got infected with a virus that I had to remove. It turned out that it was because an email from our shipping site somehow got infected with a trojan. Thankfully that trojan was pretty easy to remove, but it got me thinking, what if it had contained a more malicious script that allowed, say, remote control via VNC? I work in a retail business, and the way our system is set up, at the end of each day our computer takes all the stored credit card information of every customer who buys in our store, encrypts it, and adds it to a huge .rar archive, which is then locked. This is all automated. If a virus allowed a hacker to simply download that archive (which is very easy to find) and attack it with a brute-force algorithm and maybe a rainbow table generator, they would instantly have all the credit card information of every customer that's ever come through our doors (and not payed in cash >.>)
Is it just me, or does it seem like with that kind of process, someone who knew a little about what they were doing would easily be able to defraud thousands and thousands of honest citizens?

---

### Post by DestructionsRightHand on 2010-01-14
for desktop reasons there is no reason not to.  If there is a application that has to be windows run it off a terminal server.  Even with terminal server cal's this strategy will be a lot cheaper.

---

### Post by Icehuck on 2010-01-14
> **anaconda said:**
> the obvious advantages are:
1. safety from viruses etc.


Malware can exist on any platform. The recent malware on gnome-look/kde-look and android market are proof of this. This is not a selling point to a business.

> 
2. saving loads of money


True to a point. Most software development is done in house and  employees are paid to develop it. If they switch, they now have to waste time porting code to another platform or start from scratch.  Also, if you can't get support for some GPL code, you might have to hire/train programmers to use QT, GTK, python, etc.

How much is it going to cost to get employees trained? Are you going to have to hire on additional people to ensure a smooth migration and minimal loss of productivity?

> 
5. you can let your employers install whatever linux programs they want, without worrying about licenses, and that are you "legal"


As an administrator you don't let anyone install whatever they want. The more junk installed onto a machine the greater chance for an exploit to be found.

---

### Post by Tristam Green on 2010-01-14
I would say that for things like a file or printer server, possibly.  But really that only works if you *know* how to fix it, should something go awry.

In a small business environment, it would work only if the people who own the business first and foremost know what they're working with.

Likewise, in a large business, it only works if the IT departments are willing to spend the big dollars to hire truly Linux-capable sysadmins, and to tell the truth it would probably be cheaper to run RHEL and deal with corporate support contracts...which are expensive anyway.

---

### Post by Icehuck on 2010-01-14
> **gsmanners said:**
> - Compiz, which improves usability for some people. 

This one gave me a chuckle, because I can't see anyone in an environment actually installing this. It's fluff and most admins probably won't even install it.

> 

- Repositories, which contain nearly everything you need in one convenient place.



I guess this is good for an initial download. Most admins are going to build packages to suit their needs. I know quite a few people who take apart RPMs and DEBS because the packages don't do what they need. They also keep their own repositories for software but everyone already does that.


> 
- Source code is available on most applications, which can be handy if you need to do a custom version of the software you use.


How much does this cost your company when your developers are trying to figure out what the original programmer did wrong? I can be the worlds best programmer in the world, but if I never seen the code of open office how will I know my way around?


I'm not trying to discredit linux, but I want to see really GOOD reasons for others to switch.

---

### Post by Roasted on 2010-01-14
> **Icehuck said:**
> 
How much does this cost your company when your developers are trying to figure out what the original programmer did wrong? I can be the worlds best programmer in the world, but if I never seen the code of open office how will I know my way around?


I'm not trying to discredit linux, but I want to see really GOOD reasons for others to switch.

You'd be surprised.

We recently went with an open source application that saved our workplace 32,000 dollars of licensing fees and whatnot. We ran into a minor snag along the way, which looked like it was bad. Checked out the installation script and did some researching. It took about a full week to crack it and get it rolling. It's also important to note that this included figuring out the issue, researching, AND deploying the server with the software on it for public usage. Had we went with the proprietary choice, there would still have been time involved with setup and deployment. So while it took a week to get the open source one rolling, in actuality it was only a matter of 1-3 days in addition to the time it would have taken to get the proprietary one rolling.

Let's do the math here:

32,000 dollars for the proprietary package, OR 1 week of admin salary to fix a free and open source one...

I don't know about you, but if anybody here is making 32 grand a week in IT, sign me up!!

---

### Post by Icehuck on 2010-01-14
> **Roasted said:**
> You'd be surprised.

We recently went with an open source application that saved our workplace 32,000 dollars of licensing fees and whatnot. We ran into a minor snag along the way, which looked like it was bad. Checked out the installation script and did some researching. It took about a full week to crack it and get it rolling. It's also important to note that this included figuring out the issue, researching, AND deploying the server with the software on it for public usage. Had we went with the proprietary choice, there would still have been time involved with setup and deployment. So while it took a week to get the open source one rolling, in actuality it was only a matter of 1-3 days in addition to the time it would have taken to get the proprietary one rolling.

Let's do the math here:

32,000 dollars for the proprietary package, OR 1 week of admin salary to fix a free and open source one...

I don't know about you, but if anybody here is making 32 grand a week in IT, sign me up!!

Edit, didn't read that properly.

---

### Post by RiceMonster on 2010-01-14
> **anaconda said:**
> 2. saving loads of money, if you can find free applications that fullfill your need.

But then you don't get corporate support, if you need it.

> **anaconda said:**
> 4. Office2007 works in wine. (a business will propably need some office licenses, because other businesses use it)

Sounds like a nightmare. You can't honestly tell me that businesses will want to run their software in wine.

> **gsmanners said:**
> - Compiz, which improves usability for some people.

Ehhhh.... I really can't see how, in a business case.

> **gsmanners said:**
> - Repositories, which contain nearly everything you need in one convenient place.

But now I'm stuck with the version in the repos. It gets a lot more difficult once I want to stick with an older version or update to a newer. Yes, this is highly important.

> **gsmanners said:**
> - Authenticated developers contribute code to the repositories, which makes it hard to sneak malicious code in.

If you buy legal software from trusted vendors, you wouldn't have this worry in the first place.

> **gsmanners said:**
> - Source code is available on most applications, which can be handy if you need to do a custom version of the software you use.

Very few companies have in house developers. If they have a problem, they go to the vendor.

---

### Post by lukeiamyourfather on 2010-01-14
All good points so far but I'd like to add another perspective. True that Linux is free if you want it to be (by using distribution without support) but that's not the most important point. Its more like a perk in an already awesome deal.

Let me explain, even if Windows was free I still wouldn't use it if given a choice because of all the reasons why it sucks anyway. I run both Windows and Linux at work because some software works in one and some in the other but I wish all of it ran in Linux. Setting up a new workstation in Windows goes something like this. Bring the optical media, if it doesn't have a DVD drive then bring a USB DVD drive too, sit there for a half hour while it installs and enter the product key in the middle, then start installing drivers specific to that workstation (audio, network, graphics, etc.) which are spread all over the internet, update everything which might take overnight, then start installing applications which are also on optical media most of the time and require constant disc changes, a day later the workstation is ready for use. Don't forget antivirus software and all the licensing muck and updates that go with that too.

For Linux I pop in my flash drive with Ubuntu on it, install in 10 minutes (literally) without having to fart around with any papers or product keys to keep track of, update everything which is typically a few hundred megabytes versus a few gigabytes with Windows, finally install a few applications with a single apt-get command. Start to finish it takes an hour or two instead of a day or two. 

Sorry for the long sentences but you get the idea. True that some tasks in getting Windows going can be automated (copy machine images, automate the installers with tools like nLite) but even that takes a lot of time which isn't necessary with Linux to begin with. The exact situation will be different based on the size of the organization and complexity of the environment but again and again that's been my experience. It might be worth your time to do a comparison setup of a workstation for your article. How many minutes does it take to get Windows workstation going with average office software versus an Ubuntu workstation (drivers, all updates and service packs, other software like PDF readers). The results will speak for themselves.

Like I said before all are good points mentioned so far in addition to this. Cheers!

---

### Post by whiskeylover on 2010-01-14
Let me try to put a different perspective on this.

A few years ago, back in 1999, I used to work for a company that was a Microsoft Solution Provider (Its a pretty big company with its own products.) One of the products was used by system admins of big companies like Boing. And it was database intensive (MS SQL and Oracle was used in the backend.)

In one of the very informal meetings over lunch in the cafeteria, I asked the director of the company as to why we don't use open source directory servers like Novell's LDAP server (at that time.) Everybody looked at me with astonishment, like I said something crazy.

The director explained to me that "if one day Novell LDAP server was suddenly yanked out of the market, who would support it? Atleast with SQL Server and Oracle, the vendor has a legal obligation to keep supporting the product for X number of years."

And mind you, this is a big company. Even the slightest change in the IT infrastructure has to go through millions of approvals from all departments. Then there is development cost, migration cost, training cost etc. Its not as easy as flipping a switch and moving to Linux. In most cases, it costs them millions of dollars. And also, its a big decision that has to come from the top management. Contrary to popular belief, the IT department itself doesn't make these decisions, in most cases.

---

### Post by KiwiNZ on 2010-01-14
For large Corporations the cost of conversion is not worth it . The cost of staff training alone is huge .Not to mention all of the infrastructure costs

For SME's its also cost issues , sure the software costs are low , but the support costs are high , they either have to hire their own staff , not always an option or use third party support which has high costs.

Then there is the issue of interoperability with their customers etc given that greater than 90% will be Windows based. Also finding software to meet their specific needs is always one huge pain in the butt.

As for such things as Compiz ...not even a starter, This is Corporate world  not home desktop.

The reality is the Corporate take up of Linux is going to be in the Server market not the Desktop.

---

### Post by fewt on 2010-01-14
> **anaconda said:**
> the obvious advantages are:
1. safety from viruses etc.


Unless you share files with Windows users.

> **anaconda said:**
> 

2. saving loads of money, if you can find free applications that fullfill your need.

What about VPN? Vpnc doesn't always do the job.



Sometimes this is true, many times it isn't.  How do you replace VirtualCenter?

> **anaconda said:**
> 
3. more robust servers (really)


Not if they are Ubuntu, RHEL or OEL, maybe.

> **anaconda said:**
> 
4. Office2007 works in wine. (a business will propably need some office licenses, because other businesses use it)


Kind of, but it's very unstable and shouldn't be used daily by end users.  I wrote an article on this last year and have since switched back to Office in a VM because it just didn't work well.

> **anaconda said:**
> 
5. you can let your employers install whatever linux programs they want, without worrying about licenses, and that are you "legal"


No, this couldn't be less true.  Depends on your definition of "legal".  The last thing you want is 10,000 random applications installed on desktops across your organization, and then getting a call from the FSF because one of them somewhere wasn't quite legal.

Try auditing that!

> **anaconda said:**
> 
But I wouldn't suggest moving completely to linux. there almost always are some windows programs that a business needs and that wont work in wine. So it would be worth the invested money to have a couple of windows machines too... they could be machines that everyone has the right to use.. eg. to convert an office2010 file to a format that openoffice can handle better..

If you need Windows, use Windows.  If you need to maintain Unix or Linux servers and only have 1-2 Windows application requirements consider switching.

---

### Post by fewt on 2010-01-14
> **lukeiamyourfather said:**
> All good points so far but I'd like to add another perspective. True that Linux is free if you want it to be (by using distribution without support) but that's not the most important point. Its more like a perk in an already awesome deal.

Let me explain, even if Windows was free I still wouldn't use it if given a choice because of all the reasons why it sucks anyway. I run both Windows and Linux at work because some software works in one and some in the other but I wish all of it ran in Linux. Setting up a new workstation in Windows goes something like this. Bring the optical media, if it doesn't have a DVD drive then bring a USB DVD drive too, sit there for a half hour while it installs and enter the product key in the middle, then start installing drivers specific to that workstation (audio, network, graphics, etc.) which are spread all over the internet, update everything which might take overnight, then start installing applications which are also on optical media most of the time and require constant disc changes, a day later the workstation is ready for use. Don't forget antivirus software and all the licensing muck and updates that go with that too.

For Linux I pop in my flash drive with Ubuntu on it, install in 10 minutes (literally) without having to fart around with any papers or product keys to keep track of, update everything which is typically a few hundred megabytes versus a few gigabytes with Windows, finally install a few applications with a single apt-get command. Start to finish it takes an hour or two instead of a day or two. 

Sorry for the long sentences but you get the idea. True that some tasks in getting Windows going can be automated (copy machine images, automate the installers with tools like nLite) but even that takes a lot of time which isn't necessary with Linux to begin with. The exact situation will be different based on the size of the organization and complexity of the environment but again and again that's been my experience. It might be worth your time to do a comparison setup of a workstation for your article. How many minutes does it take to get Windows workstation going with average office software versus an Ubuntu workstation (drivers, all updates and service packs, other software like PDF readers). The results will speak for themselves.

Like I said before all are good points mentioned so far in addition to this. Cheers!

It's just as difficult to automate deployment of Windows and Linux, I happen to have done both, so I know they are unique, but just as challenging.

To imply that you can put in a thumb drive and build an enterprise is laughable at best.

Deployments take lots of time to standardize, document, automate, test, and deploy.  The length of time to build and deploy an MSI is no different than the time to build and deploy a deb.

What about VPN?  What about HR applications?  What about Video conference?

You can't just download a distribution and have these things, and if you are in a mixed environment then it becomes even more of a challenge.  (Does Ekiga talk to Netmeeting? No.)  What about conference white boarding, or internally developed apps?

---

### Post by KiwiNZ on 2010-01-14
> **fewt said:**
> It's just as difficult to automate deployment of Windows and Linux, I happen to have done both, so I know they are unique, but just as challenging.

To imply that you can put in a thumb drive and build an enterprise is laughable at best.

+1

People read ITIL

It applies to building Linux enterprises as well :rolleyes:

---

### Post by oldsoundguy on 2010-01-14
One only has to look at Lowe's home centers to see the advantage of going to a Linux outfit and having them custom design your system.  
Lowe's uses Red Hat Enterprise Linux as a base .. and they paid Red Hat to build the system.
The money they save in down time alone vs the Windows based system of Home Depot is more than they pay for the system itself!
One of the (many) reasons that Lowe's has a better bottom line than Home Depot!

But for a 10 computer business .. VERY marginal cost wise to convert.  Those businesses will be the last to even THINK of converting to a Linux based system.  They need to be able to pick up the phone and get support and most Linux builds do NOT offer such until you get into a full enterprises solution.

---

### Post by Icehuck on 2010-01-14
> **oldsoundguy said:**
> One only has to look at Lowe's home centers to see the advantage of going to a Linux outfit and having them custom design your system.  
Lowe's uses Red Hat Enterprise Linux as a base .. and they paid Red Hat to build the system.
The money they save in down time alone vs the Windows based system of Home Depot is more than they pay for the system itself!
One of the (many) reasons that Lowe's has a better bottom line than Home Depot!



So home depot is losing to lowes because of Windows destroying home depot? I guarantee you have absolutely no proof.

---

### Post by Tristam Green on 2010-01-14
> **oldsoundguy said:**
> The money they save in down time alone vs the Windows based system of Home Depot is more than they pay for the system itself!
One of the (many) reasons that Lowe's has a better bottom line than Home Depot!

You imply causation rather than simple coincidence.

---

### Post by oldsoundguy on 2010-01-14
> **Icehuck said:**
> So home depot is losing to lowes because of Windows destroying home depot? I guarantee you have absolutely no proof.

Note the word (MANY) in front of the word reasons.  Point is, they are saving money on their computers, and do not have down time.
But there are other reasons for that bottom line .. including just a NICER environment.. better lit, wider aisles, better customer service, and so on.
(and I could add .. a better hot dog stand at the one I frequent!)(JKOC)

---

### Post by lukeiamyourfather on 2010-01-14
> **fewt said:**
> It's just as difficult to automate deployment of Windows and Linux, I happen to have done both, so I know they are unique, but just as challenging.

To imply that you can put in a thumb drive and build an enterprise is laughable at best.

Deployments take lots of time to standardize, document, automate, test, and deploy.  The length of time to build and deploy an MSI is no different than the time to build and deploy a deb.

What about VPN?  What about HR applications?  What about Video conference?

You can't just download a distribution and have these things, and if you are in a mixed environment then it becomes even more of a challenge.  (Does Ekiga talk to Netmeeting? No.)  What about conference white boarding, or internally developed apps?

That's why I said it depends on the size of the organization and complexity of the environment. If you read my post again I'm sure you'll see the word "enterprise" isn't there. Also not every business is what you would call "enterprise" or anywhere close. Walk down the street and look at what local businesses are running on, Windows 98 SE and Office 2000 is probably what you'll find, or Windows XP with Office 2003 if you're lucky.

These folks in small offices with a dozen or two computers running typical office applications could certainly benefit from Linux in many ways, yes, even from a flash drive. Big business could benefit as well but like you said its not as simple. Cheers!

---

### Post by fewt on 2010-01-14
> **lukeiamyourfather said:**
> That's why I said it depends on the size of the organization and complexity of the environment. If you read my post again I'm sure you'll see the word "enterprise" isn't there. Also not every business is what you would call "enterprise" or anywhere close. Walk down the street and look at what local businesses are running on, Windows 98 SE and Office 2000 is probably what you'll find, or Windows XP with Office 2003 if you're lucky.

These folks in small offices with a dozen or two computers running typical office applications could certainly benefit from Linux in many ways, yes, even from a flash drive. Big business could benefit as well but like you said its not as simple. Cheers!

If you have more than one desktop then you need to think about standards unless you are a home user.

---

### Post by lukeiamyourfather on 2010-01-14
> **fewt said:**
> If you have more than one desktop then you need to think about standards unless you are a home user.

So? I don't get your point, like Linux is incapable of implementing standards? :-s

---

### Post by KiwiNZ on 2010-01-14
> **lukeiamyourfather said:**
> That's why I said it depends on the size of the organization and complexity of the environment. If you read my post again I'm sure you'll see the word "enterprise" isn't there. Also not every business is what you would call "enterprise" or anywhere close. Walk down the street and look at what local businesses are running on, Windows 98 SE and Office 2000 is probably what you'll find, or Windows XP with Office 2003 if you're lucky.

These folks in small offices with a dozen or two computers running typical office applications could certainly benefit from Linux in many ways, yes, even from a flash drive. Big business could benefit as well but like you said its not as simple. Cheers!

Oh , the messes I have cleaned up after that attitude has been used.

---

### Post by fewt on 2010-01-14
> **KiwiNZ said:**
> Oh , the messes I have cleaned up after that attitude has been used.


Clean-up crew pays well though. ;)

---

### Post by lukeiamyourfather on 2010-01-14
> **KiwiNZ said:**
> Oh , the messes I have cleaned up after that attitude has been used.

Wow, tough crowd. Doesn't anyone else besides me have a successful experience with Linux at work? :-({|=

---

### Post by RiceMonster on 2010-01-14
> **lukeiamyourfather said:**
> Wow, tough crowd. Doesn't anyone else besides me have a successful experience with Linux at work? :-({|=

Yes, on the server.

---

### Post by Linuxforall on 2010-01-14
I have, running around 35 PCs here at the institute on desktop Ubuntu Linux.

---

### Post by Frak on 2010-01-14
> **Roasted said:**
> You'd be surprised.

We recently went with an open source application that saved our workplace 32,000 dollars of licensing fees and whatnot. We ran into a minor snag along the way, which looked like it was bad. Checked out the installation script and did some researching. It took about a full week to crack it and get it rolling. It's also important to note that this included figuring out the issue, researching, AND deploying the server with the software on it for public usage. Had we went with the proprietary choice, there would still have been time involved with setup and deployment. So while it took a week to get the open source one rolling, in actuality it was only a matter of 1-3 days in addition to the time it would have taken to get the proprietary one rolling.

Let's do the math here:

32,000 dollars for the proprietary package, OR 1 week of admin salary to fix a free and open source one...

I don't know about you, but if anybody here is making 32 grand a week in IT, sign me up!!
I'd like to hear what application that was. For the $35,000 per week, I was paid $11,000 once to fly across the US and help supplant an entire backup-server system within a week while the servers that were already there were being seized for an ongoing investigation. $11,000 for an 80-hour workweek, all expenses paid.

---

### Post by jollysnowman on 2010-01-14
The built in security model is a pretty good reason by itself. There's also the ease of setting up intranetwork email. IMO everything else is icing.

---

### Post by Frak on 2010-01-14
> **jollysnowman said:**
> The built in security model is a pretty good reason by itself. There's also the ease of setting up intranetwork email. IMO everything else is icing.
I'll take Exchange over Linux Email anyday, just sayin.

---

### Post by kevin11951 on 2010-01-14
> **Frak said:**
> I'll take Exchange over Linux Email anyday, just sayin.

Look up Zimbra, you may just change your mind, I did ;)

---

### Post by hobo14 on 2010-01-14
> **Frak said:**
> I'd like to hear what application that was. For the $35,000 per week, I was paid $11,000 once to fly across the US and help supplant an entire backup-server system within a week while the servers that were already there were being seized for an ongoing investigation. $11,000 for an 80-hour workweek, all expenses paid.

How does $5500 for a standard week, or even $11,000 for a week have relevance to his request for a $32,000 week?

---

### Post by SirBismuth on 2010-01-15
> **lukeiamyourfather said:**
> Wow, tough crowd. Doesn't anyone else besides me have a successful experience with Linux at work? :-({|=

Our mail server, intranet server, and firewall are Linux-based.  But they are using 2003 server for the rest.  On my work computer, I am using Ubuntu as my primary OS, with XP running in VirtualBox for a couple of custom-applications that do not even work in Wine.  

I also access XP for a couple of sites that will only authenticate in IE (*oh the horror!*), at least one or two will work in FF in XP, so that makes up for it.  I reckon I could get at least one of them authenticating in FF in Ubuntu, but haven't had the time yet to investigate it thoroughly.

I reckon that a business starting out, could go only open-source, and use Windows in a virtual machine as necessary, depending on what their requirements are there.  For an organisation to convert is often not feasible, it seems.

B

---

### Post by Frak on 2010-01-15
> **kevin11951 said:**
> Look up Zimbra, you may just change your mind, I did ;)
We've tried it before, and as far as I am aware, it didn't meet our needs. I've personally tried Zimbra, so I do know how good it is, but it didn't meet our needs.

---

### Post by fewt on 2010-01-15
> **lukeiamyourfather said:**
> Wow, tough crowd. Doesn't anyone else besides me have a successful experience with Linux at work? :-({|=

Sure, I have had Linux on my work computer for 12 years, and I still do.

That's why I can very easily form an argument against it.

:popcorn:

---

### Post by dmillerct on 2010-01-15
Chiming in on the topic here...

I am the director of a company with approx. 500 PCs, 15 servers, multiple remote sites and offices connected though VPN / MPLS.

I love linux, love open source and think it will soon be prevalent in every company's network, but not yet. Here are the main reasons why:

(Keep in mind these apply to my specific situation only, others may have different experiences)

Being able to easily manage a node from one central location. This saves LOTS of money in man hours, making it easy saves even more money by not having to hire top level personnel. (i.e. group policy)

Centrally managing patches / software updates. (i.e. WSUS -landscape is getting there)

The number one reason: Industry specific software, especially in small to medium sized industries we still create software that is windows dependent. I mean really windows dependent, not even capable of running in wine. Even the newer web based applications require active x controls and assembly files native to windows. 

Just my 2 cents.

---

### Post by sunscape on 2010-01-15
I'd try to tie in something about the recent cyber attacks by the Chinese government. 

I hope it is a good article. I'll be sure to digg/twitter/whatever it after it is done.

---


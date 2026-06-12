---
title: "Your own company based on  Ubuntu"
date: 2007-09-23
forum: The Cafe
---

### Post by borobudur on 2007-09-23
Hi there,
I'm thinking of starting a company based on open source and ubuntu in particular.

The concept would be to support small and medium-sized businesses with:
[LIST]   
[*]ubuntu in general   
[*]migrating from windows   
[*]supporting software (cms, groupware, wiki's, backuping, communication, ...)   
[*]schooling   
[*]etc. [/LIST] What do you think about that? Do you see any license problems with ubuntu? 

Would you have any more good arguments to change to ubuntu (free software, no virus problems, secure)? 

Cheers, borobudur

---

### Post by Martje_001 on 2007-09-23
> **borobudur said:**
> Would you have any more good arguments to change to ubuntu (free software, no virus problems, secure)? 
Straight to the point, Compiz fusion, stable

There not any license problems. You can modify Ubuntu in any way legal!

---

### Post by n3tfury on 2007-09-23
> **Martje_001 said:**
> Straight to the point, Compiz fusion, stable



what?

---

### Post by elvis on 2007-09-23
I'm an IT contractor by trade, and support a number of businesses' IT needs.  My focus is on replacing legacy non-free systems with free-software alternatives as an upgrade path.

I use Ubuntu for a few reasons:

1) Easy to use desktop - Yes, GNOME is GNOME (ditto for KDE, XFCE, whatever), and SuSE and Fedora and many other distros have easy to use desktops too.   But Ubuntu certainly emphasises the need to make the non-technical end-user a real focus.

2) APT.  I hate RPM/YUM.  Portage (Gentoo) is nice, but not for those pressed for time, nor the non-technical.  APT still reigns supreme as the best package manager I've ever used.  Simply put: if Ubuntu was RPM based, I wouldn't be using it.  That would be a show stopper for me.

3) Consistency - pre Ubuntu I was a Debian and occasionally Gentoo user (again, for APT and Portage/USE-flags).  Now that I have clients needing Linux desktops as well, Ubuntu means I can do both Desktop and Server on the same platform, which means simplified support.  Also it means neat things like using a single in-house apt-proxy configuration for an entire building of people, or a single LDAP config file for single-sign-on locations.

4) Sensible release schedules.  Debian (and others) have a "when it's done" approach.  That's fine, but businesses get nervous when you say these things.  Ubuntu means knowing when to expect change, and Linux in general means not being forced to change if you don't want to.

I use free software in general for a few reasons also:

1) No license management nightmares.  It's not about up-front cost.  It's about long-term management.  Windows has a thousand and one licensing schemes for all different sizes of businesses, and they are a pain in the ****.  I know, because I used to be an IT Manager for a large multi-national corporate that was 100% Windows.  I spent more time managing licensing than I did doing real work, and that pissed me off.  With free software, I can just install software and know it works, and will never be restricted by something as non-technical and intangible as a "license".  That just makes good business sense, and stops wasting everybody's time, letting them get back to making the business work.

2) Performance.  I can get such enormous longevity out of hardware with Linux it's not funny.  I can run firewalls with squid-proxies on hardware that is 3 years older and/or on fifth the cost compared to if I used Microsoft ISA.  Likewise for Samba vs WinNT/Win2K-AD domain controllers,  PHP/Perl/Python+MySQL vs VB/.Net+MS-SQL Server, etc, etc.  

3) Simple hardware migrations.  I never re-install anything anymore.  If I buy new hardware, I migrate existing machines to a disk image, and run them from a virtual server using Xen.  Moving whole servers around from one bit of physical hardware to another takes minutes, not days.

4) No forced upgrades.  Canonical will never ring me and tell me I can't use Edge Eft any more.  Microsoft have already told a number of my clients that they are not allowed to downgrade their Vista licenses to WinXP.  Likewise, Apple have told several of my clients that they must use OSX 10.4 that was shipped with their Macs, despite the fact that the other 1000 machines in their network are still on 10.3 and some of the in-house software won't port across without significant effort.

5) Multi-platform.  Microsoft have Active Directory.  Apple have Open Directory.  They're both wonderful, but only if you have 100% homogeneous networks.  Most of my clients have 3 or more operating systems in their building, and OpenLDAP means building something that everyone can talk to.  Likewise, MySQL, Apache, PHP/Perl/Python, etc, etc - all of these are multi-platform.  If the in-house developers absolutely refuse to move away from Windows, that's fine.  They can keep their install, but still play ball with the rest of the business on other base platforms but with the same client apps.

6) Cost.  No, not the upfront cost (although that does make some folks happy - especially accountants).  But the cost of maintenance.  As one individual I assist around 6 businesses on a regular basis, and another 10 or more on a semi-regular basis.  I can remote-access all of these businesses using secure technology (OpenSSH, OpenVPN, etc) and offer complete systems maintenance on an hourly rate.  Some of these companies have told me that they've saved well over 80% or more on their IT maintenance bills since moving away from non-free software.  Likewise, they are happier with the faster turn-around thanks to the remote access.  Whereas before they regularly needed support, and had to wait hours for it, now they need it less frequently, and when they do problems are solved in minutes, not hours.

7) Redundancy.  This ties in to "licensing" and "cost" as well.  It's common sense to build two (or more) servers in a business.  Nobody in their right minds would put all their eggs in one basket.  That's risky business.  Painfully, under non-free software you are required then to pay for everything a second time.  Pay for a second database server, mail server, file server, etc.   Despite the fact that you will (hopefully) never use these things, you still owe your pound of flesh.  With free software, that goes away.  There's no charge for a second copy of MySQL, Postfix, Samba, etc.  Your redundant systems are no longer dead capital.  Instead you can spend that money on something far more beneficial to the business.

8 ) It's open and honest.  Free software wears its heart on its sleeve.  The term "full disclosure" comes to mind.  I'm never left second-guessing if, as a customer, I'm being lied to or having certain things withheld.  Good or bad, free software bares all to anyone who will listen.  Look through any changelog, bugtracker, todo list, etc of a free software system, and you'll get a pretty good idea pretty quickly if you can trust it.  Free software never claims it's perfect.  And any software that does isn't worth risking.

Well, that's quite a long post.  I'll stop it there.  If you have any specific questions on how I deal with specific problems, feel free to ask and I'll do my best to describe my solutions.

---

### Post by mridkash on 2007-09-23
Wow really good post!

---

### Post by JAPrufrock on 2007-09-23
Just found an interesting article called ["Can Ubuntu Linux really run my small business?"]("http://www.allbusiness.com/technology/4353657-1.html")

One of the authors conclusions is that the Ubuntu community saves him money because it provides IT support. "What is so great about Ubuntu? 'It has the best user community built around it.'"

I also agree with the author that Ubuntu's biggest shortcoming is that it lacks a good accounting program like Quickbooks.

---

### Post by Irihapeti on 2007-09-23
Really good post, elvis!

I have a small business in the very early stages - currently part time. That puts me in a grey area where I'm not a non-commercial user of software - and so not eligible for home-user/student concessions - but neither making enough money to support commercial licence fees. I don't think I'd be the only one in this situation. 

Friends have told me that I'm being over-scrupulous, but I'd really rather not have to worry about it if I have a choice. Free software gives me that choice.

Irihapeti

---

### Post by BLTicklemonster on 2007-09-23
Accounting?

[http://www.aaxnet.com/design/linuxacct.html](http://www.aaxnet.com/design/linuxacct.html)

[http://www.gnucash.org/](http://www.gnucash.org/)

---

### Post by elvis on 2007-09-23
> **JAPrufrock said:**
> I also agree with the author that Ubuntu's biggest shortcoming is that it lacks a good accounting program like Quickbooks.
As well as GNUCash mentioned above, there's:

KMyMoney: [http://kmymoney2.sourceforge.net/](http://kmymoney2.sourceforge.net/)

SQL Ledger: [http://www.sql-ledger.org/](http://www.sql-ledger.org/)

Grisbi: [http://www.grisbi.org/](http://www.grisbi.org/)

Plenty of options available.  With that said, I have a lot of clients who still stick with an Australian product called [MYOB]("http://www.myob.com.au") due entirely to the "support" they offer.  When I say "support", I mean they send out up-to-date tax tables on a semi-regular basis.  Their actual telephone support is utterly useless.  

True story: One of my clients was refused support from MYOB when they rang up to complain about a performance issue.  They use MYOB Enterprise on a Win2K Terminal Services box, and their Linux desktops connect to that via [rdesktop]("http://www.rdesktop.org/") (which I should add is how the product is designed to be used).  The tech on the support line was utterly convinced that because Linux was being used somewhere in the equation, all support and warranty was void because (and I quote) "they were running on an emulation layer, and therefore the problem is with Linux".   After a lengthy argument, I spoke to his superior, and the problem was solved.    The MYOB package itself is a low-quality product (slow, kludgey, ugly, non-intuitive), and the phone support sucks.  If it wasn't for the updated tax tables, they'd be out the door.

---

### Post by JAPrufrock on 2007-09-23
Gnucash doesn't include a POS.  I've looked at other linux compatible accounting packages and, so far, I haven't found any that are as good as an old version of Quickbooks that I have.

---

### Post by BLTicklemonster on 2007-09-23
Can you run it in Wine?

---

### Post by Wiebelhaus on 2007-09-23
> **elvis said:**
> I'm an IT contractor by trade, and support a number of businesses' IT needs.  My focus is on replacing legacy non-free systems with free-software alternatives as an upgrade path.

I use Ubuntu for a few reasons:

......... solutions.

Posts & Users like this make this forum , thanks mate.

---

### Post by elvis on 2007-09-23
> **BLTicklemonster said:**
> Can you run it in Wine?
I believe Quickbooks is very compatible with WINE.  There was a news article on it some months back where the Quickbooks developers themselves mentioned that they'd been playing with Quickbooks under WINE/Linux.  It's certainly an option worth testing, if you're a Quicken license owner.

> **sx66gns said:**
> Posts & Users like this make this forum , thanks mate.
Thanks. :)  

I've worked for a long time in IT, and I've heard some of the worst nonsense you could ever imagine in board rooms and CIO offices.  A lot of people make decisions about software for the silliest reasons.  I work at the coal-face of systems management all day, every day.  (Literally - I've had 2 weeks holiday total in the last 5 years, and was on call for most of that).  When it comes to business-critical software, you use what works best.  Not what's trendy or what the CEO thinks looks the prettiest, but what makes the business move forward.  Linux isn't always the perfect answer, but in my humble opinion it certainly shines through as the sensible option in the vast majority of case studies.  Sadly, it isn't always sensible people who are in charge of things for most IT departments.  That, and IT as an industry gets lazier and lazier by the hour.

---

### Post by Compucore on 2007-09-23
Well  I can say this as well over here since I am in IT as well as a computer technician, programmer, and help desk analyst. It depends on the company themselves. If it is for creating documents, doing finance, marketing, etc. it is great. But in some instances like in one of the jobs that I had to go in for was for a law firm. Not the idea situation for taking away the enviroment that all the lawyers, paralegals. and some of the secretaries that are use in using windows. In the instant like with this law firm it would have been kaotic to have open source in there. I don't want to sound like lawyers don't know how to use linux if there are some out there. The more to them if they like linux. But in some case depending on the company. its a touchie situation with going into open source like ubuntu.

Compucore

---

### Post by elvis on 2007-09-24
> **Compucore said:**
> Not the idea situation for taking away the enviroment that all the lawyers, paralegals. and some of the secretaries that are use in using windows. In the instant like with this law firm it would have been kaotic to have open source in there.

As someone who has done a number of corporate Windows->Linux conversions, I disagree.

People hate change.  That much is certain.  But desktop users who exist in an environment that is limited to office documents and emails (of which lawyers are) is one of the most perfect scenarios for switching to free software.

The single biggest anti-Linux rhetoric I hear is that "Linux is too hard".  My question is: "for whom?".

Systems administrators run the system as a whole.  No end-user in a corporate environment is expected to set up printers, faxes, scanners, computers, monitors, etc - the IT department does that.  So why then is the "ease of use" factor of Windows a deciding issue in a corporate environment?

The desktop is simple: A few icons with simple, plain-langauge comments underneath that tell the user what they do.  If all a user needs to do is use email, internet, and create office documents, then put just those icons on their desktop.  15 minutes of "training" should be all you need to migrate those sorts of users across.

One of my clients is a 1500-staff retail chain.  Previously they used Windows print servers which required constant administration.  I've recently migrated them entirely to CUPS print servers which export all available printers to a central, redundant printserver (named printserver.companyname.com) and makes them all available via IPP for printing from Windows, Linux and Mac.  Administration time for the helpdesk staff is one tenth what it was previously, and the end-users don't even know the difference.

I feel people confuse the home environment with the corporate environment.  Non-technical people try Linux at home, and come to the conclusion that it's "too hard to use" on the desktop.  What needs to be remembered is that, in a corporate/work environment, as long as the IT staff understand how to use the system, the end-users only need the most basic of training.  Basic desktop paradigms are consistent on most platforms.  Anyone who knows how to open a new MS Word document only needs 5 minutes to be shown the equivalent in Open Office.  Anyone who knows how to browse to an Internet site in MSIE only needs 5 minutes to be shown the same in Konqueror or Firefox.  

End users DO NOT need to be system administrators.  Configuring screen resolutions, printers, scanners, and other hardware, or installing software and services is not the domain of an end-user.  I've seen businesses where the users are in charge of their own machines, and in all cases utter chaos ensues as users install anything they like regardless of licensing, and nobody follows any sort of standard.  

Additionally, I find Linux easier to administrate and maintain remotely as a systems admin.  Windows requires full GUI access to do most tasks, which is slow and bandwidth hungry.  It also usually means needing VPN/subnet access to the network.  Linux desktops running SSH mean I can administrate any system even over a slow dial-up connection.  From there I can add and remove printers, install and uninstall software, perform security patching, and manage a whole host of desktop-related issues without the end user even noticing.  Compare and contrast to Windows, where I need either VNC access (and users get to see everything I do), or RDesktop (where an administrator and user cannot be logged in at the same time, or again, the admin takes over control, and the user sees everything).

With all of that said, there are many businesses out there where Linux on the desktop does no suit.  I find most of them are in that boat simply because of software vendor lock-in (see the MYOB/Quicken discussion above).  In cases where desktop tasks of the employees boils down to very simple tasks (word processing, spreadsheeting, email, IM, VOIP), Linux makes an excellent target.  What's more important that the choice of software is ensuring staff are led gently into the alternative.  As mentioned, no matter what you are running today, and what you will upgrade to tomorrow, people will fight change.  I've seen the same thing happen back in the Win98->Win2K days.  Even in Microsoft->Microsoft migrations, it happens.

---

### Post by Irihapeti on 2007-09-24
I was talking recently to the office manager of a charity organisation. He was telling me that their software was donated by MS, so they wouldn't save money by going open-source. Then in the next breath he tells me that he runs some anti-malware software (Trend Micro, I think) and it finds about 4 or so trojans a week. I don't know if it's occurred to him just what those trojans might have been doing before he jumped on them.

What about the cost of time spent fixing such things? What about the cost of potentially sensitive data getting out? Surely these things need to be considered.

Irihapeti

---

### Post by n3tfury on 2007-09-24
> **JAPrufrock said:**
> Just found an interesting article called ["Can Ubuntu Linux really run my small business?"]("http://www.allbusiness.com/technology/4353657-1.html")

One of the authors conclusions is that the Ubuntu community saves him money because it provides IT support. "What is so great about Ubuntu? 'It has the best user community built around it.'"



for small businesses support would be fine, but for larger, it's not.  i applaud those that are using mostly/strictly open source in small businesses though.  that's just fkn fantastic.

---

### Post by borobudur on 2007-09-24
Great posts, thanks to all!

How would you start such a business? Just by presenting yourself and your service on the internet; by going from door to door until you have your first client; by sending letters; or join some smb exhibition.

---

### Post by Johnsie on 2007-09-24
All of them, including business cards etc... You have to work your butt off to start a business. People need know you exist without swamping people or going on about it too much. Word of mouth is the best way to spread business so do a real good job and people will say good stuff. 

I think the biggest problem with this kind of project is convincing people to make change. Most people dont like change and there are alot of Windows fanboys out there who dont like Linux. Most people in schools and colleges learnt Windows and are familiar with Windows software so you need to make sure they know the benefits of using free open-source software. Providing efficient user support is a good way of doing that.

---

### Post by JAPrufrock on 2007-09-24
> **elvis said:**
> I believe Quickbooks is very compatible with WINE.  There was a news article on it some months back where the Quickbooks developers themselves mentioned that they'd been playing with Quickbooks under WINE/Linux.  It's certainly an option worth testing, if you're a Quicken license owner.

I've tried, but haven't been able to run it in Wine.  Problem is I don't have the installation disk.  In XP and earlier versions of Windows I was able to just copy the files to a folder on the hard drive and start the program by running the main EXE file.  It doesn't work when I do that in Wine. It's a very old program that I bought more than 10 years ago, maybe the first non-DOS Quickbooks version, but it works great and I can run it on multiple machines at no extra cost.  Most of the Quickbooks development since then seems to have been mostly bells and whistles.  I do run it in VirtualBox, but I would like to get away from Microsoft entirely. Actually, Quickbooks is the only reason why I still have an Ubuntu/XP dual boot, and why I'm not pure Ubuntu.

---

### Post by lancest on 2007-09-24
Curious as to whether the Linux file system being different has ever been an issue when changing users over from Windows. I have had a few people who had trouble with the difference when sending attachments from Ubuntu. Any tips on that?

---

### Post by Black Mage on 2007-09-24
What are other applications available for Linux, like OpenOffice, that can make is comparable to the variety of Microsoft Products. It has good email I know, and now some decent accounting software, but what about things such as databases? Something that can compare to Everest but for Linux? Things like that.

---

### Post by elvis on 2007-09-24
> **lancest said:**
> Curious as to whether the Linux file system being different has ever been an issue when changing users over from Windows. I have had a few people who had trouble with the difference when sending attachments from Ubuntu. Any tips on that?

As I mentioned in my previous post, training is essential.  With that said, it's not nearly as difficult as you'd think.

Most Windows users understand the concept of the "My Documents" folder.  The simplest explanation is that under Linux, your "home directory" is the same thing.   When I train new-to-Linux users, I focus on what they already know, and leverage their existing understanding and training to show them the similarities between the systems.

Likewise any user from a small workgroup through to a large corporate environment will have some basic understanding of shares (or drive letters) that exist on network servers.  Explaining to a user that "what used to be S: drive is now /network/accounts" is not difficult.  It's the same idea, just with a different label.  "A rose by any other name", as someone more famous than me once put it.

These are all Windows examples of course, but the same applies to anyone migrating to and from any system you can think of.

With any migration I print out a one-page "cheat sheet" in large font that gets laminated and put under each user's keyboard.  It contains the most basic "translation" tools to help them remember what the name and location of certain features is on the new system, compared to what it was called on the old system.

These are the little things that take away an end-user's frustration.  And these are the little things that make or break a migration.

> **Black Mage said:**
> What are other applications available for Linux, like OpenOffice, that can make is comparable to the variety of Microsoft Products. It has good email I know, and now some decent accounting software, but what about things such as databases? Something that can compare to Everest but for Linux? Things like that.

It's important to understand that a business is just a collection of tasks.  The first and biggest mistake I see in IT departments is that people think about software first, and tasks second.

We've all seen the classic software faux pas: people who use a Spreadsheet as a data store (what a Database is designed for).  Similarly, I constantly see people use Microsoft Word to paste in screen grabs when reporting application errors.  Both are a ridiculous way to store and share information.

Instead of thinking about what software you need, think about what tasks your business does.  This is precisely what good business analysts and systems architects do when planning major changes to an IT system.

That's enough of the wishy-washy crap.  To answer your question directly: Linux is not shy of databases.  One of my clients is a 40 store retail chain that uses MySQL exclusively.  Each store has a retail / point of sale frontend that talks directly to an in-store MySQL database as a data store.  From here I use MySQL's in-built replication tools to replicate the data over the WAN back to their head office.  This has two advantages: 1) Replicated data can be used to run reports at head office, rather than needing to batch fetch data from stores, and 2) there is a live backup at all times, meaning that in the event of a total store destruction (fire/flood/cyclone/etc) data exists up to the minute, and a new store can be rebuilt quickly without loss of information.

Outside of MySQL there are dozens of free databases for Linux.  PostgreSQL, Firebird (aka Interbase's free version), Sleepycat / Berkley DB, SQLite, "Base" (as part of OpenOffice), etc, etc.  All of these have very different target markets, from the outrageously huge multi-site corporates to the single user and most things in between.

Here's a few links covering both free and non-free databases for Linux:
[http://linas.org/linux/db.html](http://linas.org/linux/db.html)
[http://www.topology.org/soft/db.html](http://www.topology.org/soft/db.html)

I'm not sure what "Everest" is.  If you can give me a link to the manufacturer's page, I might be able to suggest an alternative.

---


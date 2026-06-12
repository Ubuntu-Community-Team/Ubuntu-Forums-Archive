---
title: "Powering a Small Business with FOSS"
date: 2007-11-03
forum: The Cafe
---

### Post by DarkOx on 2007-11-03
Recently, my Dad has been thinking about striking out on his own as a consultant, and I'd like to help him with the move as much as possible. I'm an accounting student, and have *some* technical experience thanks to my Linux use -- but not much.

What I'd like to do is help him cut costs by employing FOSS solutions whenever possible. Specifically, I'd like to provide his new business with an IT framework: a server running [SugarCRM]("http://www.sugarcrm.com/crm/") for customer relationship management, [CATS]("http://www.catsone.com/") to track resumes, and possibly setting up a website and email server.

So, first of all: are Sugar and CATS the best FOSS applications for these tasks? Does anyone have any experience using them?

Secondly, can anyone recommend any books, websites or tutorials to begin learning the ins and outs of using Linux as a small business server? I'd like to stick to Ubuntu/Debian for this, since that's where what experience I have lies.

Thanks for reading this, and I appreciate any advice anyone has to offer!

(Also: I'm not sure where exactly I should have posted this, since the Server section seems to be more for technical discussion than just starting out. But I've seen other business-related posts in the Cafe, so I figured here was as good a place as any.)

---

### Post by -grubby on 2007-11-03
I've heard of people setting up businesses off of Ubuntu

---

### Post by n3tfury on 2007-11-03
> **nathangrubb said:**
> I've heard of people setting up businesses off of Ubuntu

-1 insightful.

---

### Post by p_quarles on 2007-11-03
Definitely go with Debian Etch for the server. It works very similarly to Ubuntu, obviously, and has a great deal more guaranteed stability than any version of Ubuntu. Packages are *never *released to the Stable repos until they've been tested extensively in Lenny and Sid. The chances that apt-get upgrade is going to break something are virtually nil. 

I don't have any experience with the software you're thinking about, but I can point out one thing: there are a lot of Perl/PHP-based web apps out there, and some may have the functionality you're looking for. In any case, it's easier for non-programmers (like myself) to modify the workings of a script-based app than a compiled app.

---

### Post by Palmyra on 2007-11-03
> **n3tfury said:**
> -1 insightful.

Are you some sort of an Internet thug who goes around annoying other people?  If you have nothing to contribute, don't bother.  In a thread about someone buying a new computer, you bring up the ethics of Wal-Mart!  Do yourself a favor, and start a blog with all your rants.  Why don't you do something on topic for ONCE, and answer the damn question that was asked to begin with.

OP, excuse my tirade, but I wanted to offer something on topic, but unfortunately, I can't offer any specific answers.  I don't have a business at the moment, but I intend on making the moves soon with the intention of using a FOSS supported system.  For the most part, I have read that businesses have been doing pretty well using FOSS, but there are areas of limitations.

You should be pretty comfortable with knowing that, on the server side of things, you should be perfectly fine.  Your father should be able to have a good server, with everything pretty well done, but on the applications side, it is difficult to tell.  It depends on what his needs are.  Whatever business he'll be running, he'll need accounting software, and this may be an area of difficulty.

I am an accounting clerk right now for a non-profit association, and the vast majority of what I do can be done using FOSS, but finding suitable accounting software must be difficult.  For example, I need a single application that can print checks, manage invoices, figure out whether members are paying what they should be, and if they are not, print out automated letters that indicate the difference to mail to them.  This needs to be an all-in-one solution. 

Unfortunately, despite the fact that we could easily be saving a ton of money, the powers that be at work are not particularly good with technology, and I am sure they don't know what FOSS is.  For example, I could easily use OpenOffice Writer to create letters sent to members.  Also, I could use Calc to produce invoices (I now use Excel for invoices).  If the powers that be took the time to learn about these things, they'd know that there is a lot of money to be saved.  A new person was hired to look over these things, and I can honestly tell you she doesn't give a damn how much money is spent.  She is building a case for buying Office 2007, despite objections that I, and possibly others have.  If Office 2003 (what we're using now) is perfectly fine, why upgrade?  If OpenOffice could cover all the office related work I do, why even pay for Office 2003 or 2007?  It makes no sense, but of course, this new person doesn't pay out of her pocket: she does not care.

Alright, my main advice is to keep the focus on applications.  Ask him what is involved in running the business, and see what's out there.  Check to see what other consultants using Linux have done, and what they are now using.

PS: GnuCash offers, it appears, some accounting features.  Even if you must go with Windows at the end, don't forget FLOSS.  Use FLOSS based applications as much as you can.

---

### Post by michaelzap on 2007-11-03
I'm sure that an Ubuntu server could be made to work well for your father. However you might consider using a commercial web host for much of what you need to do instead of setting up your own internet-connected server. I do this for a number of clients, and I find that it saves me a lot of expense and grief.

For example, if you get an account with a normal web host (offering a Linux/Apache/PHP/MySQL installation), you'll end up paying $100 or so per year (assuming you don't need way more resources than most of our clients do). You can install SugarCRM and any other PHP-based software that you like there, and you'd have access to it from anywhere. The host would take care of security updates and all the other important details that a sysadmin needs to stay on top of (which is no small thing because this takes quite a lot of time and effort), and you'd have tech support for whenever you might have problems.

By comparison, if you set up your own server you might end up paying more in order to get your own ip address and a fast enough connection to host your website properly. You'd need to maintain your own server, which means you can do whatever you like, but you also need to deal with any problems that come up (the first time you're hit with a DDOS attack, you'll know just how much trouble this can be). You'll also need to make sure that the server stays on and up all the time, which will mean paying for the electricity, etc.

I find that a hybrid setup is ideal for most smaller organizations. You can set up a local file server and keep shared files that don't need to be accessed over the internet on it, which is much more secure than putting them online. And you can have your email, website, and groupware/CRM/etc. software on a commercial web host.

I also really like Google Apps for Domains, since it allows you to keep practically unlimited email on the server and access it via IMAP, POP, or webmail from anywhere and using any email client.

---

### Post by HermanAB on 2007-11-03
Note that you can get a Sugar CRM VM from the VMware web site.  That will save you from the installation head-ache.

---

### Post by Frak on 2007-11-03
I suggest either Debian or a Web-Host, other than that, I couldn't suggest any books to read, but Google is your best friend.

+1 I like the Enthusiasm

---

### Post by -grubby on 2007-11-03
> **n3tfury said:**
> -1 insightful.

are you scoring my posts now?

---

### Post by eljoeb on 2007-11-03
I've tinkered with the idea of doing it for my company.  To sum up the entire experience for a manufacturing company: PASS.  Most CRM and ERP's did not suit my needs.  It really depends on what your dad wants the software to do.  Interoperability with suppliers and customers really destroyed my efforts, but your experience might vary.

Also, try not to let the software force you into a particular business process.  It can really nuke your competitive advantage.

Big hint: do not use GNUCash for a company's accounting.  I have no idea why people think this is suitable for a business.
2nd hint: If you find yourself convincing business partners they need to use open document format, stop for $%^&'s sake.  The reason should be obvious so I won't continue.

Good luck!

---

### Post by in_flu_ence on 2007-11-03
I would recommend that servers to be outsourced and maintained by the specialist. I have heard that some companies have used ubuntu for the server OS but to be honest I see it more of a desktop OS. There are other Linux OS which are more focused on server.

SugarCRM is good but I feel myself that you might need to optimise and modify to suit your needs.

Has your father used Ubuntu as his desktop OS? Simple things like Openoffice and other softwares in the repo is always a good start. 

Lastly, I am very confident that Linux and FOSS will be a good and stable option for business use. However, you have to account for a portion of expenses for initial cost to optimise the codes for one's use.

---

### Post by 50words on 2007-11-03
I am a small business (law practice), and I use Ubuntu for my business. I don't have a server, since it is just me, but I probably will set one up in the future, mainly for backups, potentially to hold client and business files.

OOo satisfies all my document, spreadsheet, and presentation needs.

I use GnuCash for my business bookkeeping/accounting. My accountant (CBIZ) uses spreadsheets to check my work, and GnuCash is pretty much just a glorified set of spreadsheets. If you want something more like Quickbooks, AppGen is a similar program, and it is available for Windows, Linux, and OS X. I've heard that it is a full replacement for Quickbooks. I can't stand Quickbooks and similar software (I just want to work with the numbers); I prefer something more barebones like GnuCash.

My timekeeping and billing needs are simple, so I just use custom spreadsheets for this. Spreadsheets are fine for timekeeping at any size, but AppGen is set up with billing. GnuCash will also do billing, but I don't think it is very strong in that category.

Evolution is a full replacement for Outlook, obviously. And that about covers the basics.

---

### Post by DarkOx on 2007-11-03
Thanks for all your replies.

> Has your father used Ubuntu as his desktop OS?

Actually, Dad wanting to try Linux is the reason I started using Kubuntu myself (at first just so I could then try setting it up for him. Now I use it just because I like the software better). He's been using Windows at work and Kubuntu at home -- so far, Open Office has handled his .doc, .xls and .ppt files fine.

> Interoperability with suppliers and customers really destroyed my efforts, but your experience might vary.

I don't think this'll be an issue. Dad is an IT/Management consultant, so his work is entirely service based: no suppliers to speak of. Like I said, Open Office has done alright at handling his files -- and even if he has to switch to Windows for Office compatibility, all of the Linux-based server stuff can still be accessed with a browser.

> do not use GNUCash for a company's accounting

I've been wondering about that, actually. I pointed him towards GNUCash when he asked about personal accounting software, and Dad seems to think it'll work alright for his company's books. I have my doubts -- and I'll look into AppGen (though one potential problem is that our books would be Canadian, not U.S. GAAP)

> However you might consider using a commercial web host for much of what you need to do instead of setting up your own internet-connected server.

That's probably not a bad idea, and we'd definitely go with commercial hosting for the new company's website. But what about e-mail? Are there any advantages to hosting it yourself? Also for e-mail, is it worth investing in something like [Open-Xchange]("http://www.open-xchange.com/header/products/openxchange_express_edition.html") or is it better to set up the mail server yourself?

---

### Post by Frak on 2007-11-03
For using Quickbooks and other office apps, try out Crossover Office.

---

### Post by Palmyra on 2007-11-09
> **eljoeb said:**
> I've tinkered with the idea of doing it for my company.  To sum up the entire experience for a manufacturing company: PASS.  Most CRM and ERP's did not suit my needs.  It really depends on what your dad wants the software to do.  Interoperability with suppliers and customers really destroyed my efforts, but your experience might vary.

Is PASS an acronym, or do you mean pass (as in passing something)?

> Also, try not to let the software force you into a particular business process.  It can really nuke your competitive advantage.


The software he uses shouldn't affect whatever competitive advantage he has, open source or proprietary.  

> 
Big hint: do not use GNUCash for a company's accounting.  I have no idea why people think this is suitable for a business

I figured GNUCash would not be suitable.  The accounting software that I use is not even that special, but it gets the job done (albeit being very old, and strange - its a Windows application).  
.
> 2nd hint: If you find yourself convincing business partners they need to use open document format, stop for $%^&'s sake.  The reason should be obvious so I won't continue.


I am guessing you use Microsoft Office?  If that's the case, there's nothing to worry about.

---

### Post by marcelo.matos on 2008-01-20
> **50words said:**
> I am a small business (law practice), and I use Ubuntu for my business. I don't have a server, since it is just me, but I probably will set one up in the future, mainly for backups, potentially to hold client and business files.

OOo satisfies all my document, spreadsheet, and presentation needs.

I use GnuCash for my business bookkeeping/accounting. My accountant (CBIZ) uses spreadsheets to check my work, and GnuCash is pretty much just a glorified set of spreadsheets. If you want something more like Quickbooks, AppGen is a similar program, and it is available for Windows, Linux, and OS X. I've heard that it is a full replacement for Quickbooks. I can't stand Quickbooks and similar software (I just want to work with the numbers); I prefer something more barebones like GnuCash.

My timekeeping and billing needs are simple, so I just use custom spreadsheets for this. Spreadsheets are fine for timekeeping at any size, but AppGen is set up with billing. GnuCash will also do billing, but I don't think it is very strong in that category.

Evolution is a full replacement for Outlook, obviously. And that about covers the basics.

1- Dear 50words, I'm a lawyer too. I'd like to ask what do you use to track your cases?

Now, i'm trying some spreadsheets, but the scalability and the "non professional look" will be a problem some day. In fact, I work with my mom (a lawyer too) and she isn't *"computer-friendly"*, but she is a great lawyer. She does the basics only, like some word processing, e-mail and internet tasks.

I'm searching for a specific software to make things easier for us. I understand my tables and databases, but no one else does (I'm not a developer or anything like that).

I'll try the kumula cases, but do you (or anyone) know about a very reliable, stable and good software for this task?

2- About Evolution, I think it's very good, but I need to sync my contacts with my palm, so I can have my entire client's data with me, and my experience with Evolution was terrible.

I think the database on palm and Evolution are different and the sync missed and merged a lot of fields. I had problems only with contacts sync, but it was very important to me. So i changed to Kontact.

> **Palmyra said:**
> 
The software he uses shouldn't affect whatever competitive advantage he has, open source or proprietary.  

I figured GNUCash would not be suitable.  The accounting software that I use is not even that special, but it gets the job done (albeit being very old, and strange - its a Windows application).  


1- I think a software (at least in this case) is a tool made to affect your competitive advantage. It can be for good or for bad.

Sometimes you use of a software that make some task/process in a different way. Then, you have to adapt yourself to the software way, change to another software or change the software code.

In some cases, this difference,  the way you make your job and not exactly the job you make, is your competitive advantage. If you change your business process you may become just like everybody else.

The best point of free/open source is the fact that you can make the software works the way you want. This is nice. (Off course, if you are not a developer, you may lack the necessary knowledge to change the software).

2 - About the use of gnucash on business accounts. I read on the net that gnucash uses floating-point numbers instead of integers to store currency values (search the net using the words: "floating point error gnucash").

I'm not an accountant to know exactly "how" it affects the use of gnucash, but according to a lot of people, including the own developer, it make the software lacks the "necessary reliability" to be "enterprise ready" ([http://slashdot.org/interviews/01/07/05/1456248.shtml](http://slashdot.org/interviews/01/07/05/1456248.shtml)  - Question 8.).

Making it quick, your accounts can have some veeeeery strange and mysterious values. It may not be a problem for personal or small use, but imagine if your company needs to explain it to your government because of taxes problems? Also, one little wrong change can spread over your books and mess it all.

PS.: I'm beginning to learn English, sorry if i made any mistake or didn't expressed myself clearly.

---

### Post by walterbyrd on 2008-02-07
Interesting thread. Has anybody taken a look at TinyERP?

[http://tinyerp.org/](http://tinyerp.org/)

This is supposed to integrate with SugarCRM. However, my understanding is that  the newest version 4.2, does integrate correctly with SugarCRM. The older version 4.1 should work.

Also, I am interesting in why anybody would want to run a business with F/OSS? Is there really a financial advantage? Or is it just idealism? From my analysis, F/OSS software is missing a lot when it comes to financials.

fossfin.txt

What foss financial software seems to be missing:

All of the following is based my limited understanding, and my opinions. Please correct me if I am wrong about any of this.

* Cost advantage: QuickBooks simple start is free:

[http://quickbooks.intuit.com/product/accounting-software/free-accounting-software.jhtml](http://quickbooks.intuit.com/product/accounting-software/free-accounting-software.jhtml)

Or I can buy the full version of QuickBooks in only $128:

href="http://www.qbpro2008.com/quickbooks-2008-coupons-for-amazon/

Seems to me that any cost advantage of using a foss alternative is negligible.

* Ease of use: Somewhat debatable. But some people site this as a primary reason for Intuit's amazing success with QuickBooks - supposedly 87% of small businesses use QuickBooks. Although, I have to wonder how the number of foss users can be accurately counted?

* Integration with online banking: my understanding is that only intuit or msft products can easily integrate with online banking. Not absolutely sure about that.

* Payroll: very regional, and changes often == not well suited for foss.

* Taxes: somewhat regional, and changes often == not well suited for foss.

* Wide acceptance: I think most businesses are much more comfortable using products that are accepted standards.

* Wealth of available add-ons: Intuit has a very active community of 3rd party developers. You can buy practically any kind of an add-on you can imagine. These add-ons cost money, but at least they are available.

* Major company: I think a lot of businesses are not comfortable with a product unless there is a major company behind that product. I have to admit, even I am not comfortable with software  products that are essentially one man operations.

* Support: I can always hire somebody who knows quickbooks, or find a "ProAdvisor" consultant, or I can get support from the company, and there are hundreds - if not thousands - of developers who specialize in developing for quickbooks. I can not see where that is true for any project.

* Documentation: If I had to pick one thing that kills the usefulness of more foss projects than anything else, this would win in a slam-dunk. Of course, this varies among projects, some foss projects have great documentation. But, I can always find plenty of books, or other documentation for popular proprietary financial apps.

* Some Accountants will only work with QB.

---

### Post by DarkOx on 2008-02-08
> Also, I am interesting in why anybody would want to run a business with F/OSS? Is there really a financial advantage? Or is it just idealism? From my analysis, F/OSS software is missing a lot when it comes to financials.

The main consideration for looking at FOSS for Dad's company was cost. It's only just started operating, so our goal was to keep expenses down. As a secondary consideration, most FOSS solutions are based on a Linux stake of technology, and I have more experience with the internals of Linux vs. the internals of Windows.

As for the state of financial software, that's not really a problem for us. As a pure service-based consulting firm, we're mostly looking at improving processes. So we're looking for:
[LIST]
[*]CRM for keeping track of clients and bids
[*]A repository of materials related to bids (templates, price quotes, etc.) so they can be made quickly and easily
[*]Collaboration tools: email, shared calendars, shared documents
[*]Possibly a blog -- if we go ahead with this, it would largely be an extension of speeches Dad already makes at industry events.
[*]Possibly an Applicant Tracking System
[/LIST]

Accounting really isn't an issue right now, as we don't have that much to account for -- only a handful of invoices. As the company expands, that will obviously change, and naturally we'll go with what works, proprietary or FOSS.

---

### Post by fatality_uk on 2008-02-08
Here's my experience. I have done this and it works. I ran a jewellery import company and all below was done using FOSS.

I'd start by mapping out your requirements and maybe a comparison chart against software he currently uses, so that you know when you have gone through that exercise, what areas you will have easy FOSS software to use and which areas might be harder to cover.

Server Debian Etch is a first choice as said before!! 

On the CRM side, I prefer TinyErp It's a little cumbersome to initially set-up, but once that's done, it has many many advantages. There are lots of modules outside the base install and will work well with Debian Etch. It also handles ERP,CRM,HR,Stock management and order tracking in a much cleaner way than others I have tried. Look here: [http://www.debianhelp.co.uk/tinyerp.htm](http://www.debianhelp.co.uk/tinyerp.htm)

Email and shared calendars can be handled with CalDav. [http://rscds.sourceforge.net/](http://rscds.sourceforge.net/)

OOo for office of course

Evolution for PIM client

Use Planner for project management. Even if your not a project manager, that tool can be used to ensure that projects large or small can stay on track

GnuCash is more than sufficient for a single person business.

I'd get scribus. There ALWAYS needs for small leaflets and flyers that you need, so why pay a printer to do the layout for simple stuff. There's a lot of templates out there as well.

Don't forget things like SKYPE! Free phone calls are great and if your customer can use SKYPE or similar then winners all round

Hope that adds to the sum of knowledge.
Let us know how it's going

---

### Post by walterbyrd on 2008-02-09
If you are using TinyERP for CRM, then why use GnuCash for accounting? Why not just use TinyERP's accounting module?

What about income tax? TurboTax or TaxCut with work with QuickBooks; what works with TinyERP or GnuCash? 

Do you use an accountant? If so, how do you send your accountant your financial statements? Spreadsheet? 

Thanks

---

### Post by Sabot on 2008-03-11
Here are the tools that I use to run my consulting firm:

1. **Quasar** for Accounting

I created a .deb file for this accounting software.  This .deb only works on a 32 bit X86 system. It is the best accounting software that I have found for a FOSS system.  You will find the download and instructions here [http://ubuntuforums.org/showthread.php?t=597734](http://ubuntuforums.org/showthread.php?t=597734).  It does not have a payroll module.

2. **OpenOffice** for Documents

3. **Thunderbird with the Lightning Extension and Sunbird** for my calendar, contacts, and e-mail.  

Thunderbird has a nice notes section for each contact, so you can use it for a simple relationship manager if you want.  When you install these three apps they combine into a very powerful tool. You open all three by just opening Thunderbird. 

4. **Kompozer** for Website Development

Kompozer is a Wysiwyg web development tool and it is great for banging out a site.

5. **Gimp** for creating and editing images for my web site.

6. **Inkscape** for creating vector images for my web site.

7. **Gnumeric** for Spread Sheets

8. **Scribus** for creating any flyer's,door hangers, and artwork for print.

The key thing about Scribus is it will create CMYK images that print houses need.  I don't know of any other tools that do this well in FOSS.

9.  Ubuntu Perfect Server **Apache/php5/mysql** for hosting my companies web sites.

There are instructions on how to set up an Ubuntu Perfect Server here [http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10) .

10. **SecPanel **an excellent replacement for Putty to set up your Perfect Ubuntu Server.

You can also use SecPanel to access your computer from home.

11. **gftp** for ftping files to your server.

12. **Skype** for a Second Phone Line.

The one peace of the puzzle that I am still trying to fill is a good contact manger like Act!.  I think some type of CRM may fill the bill, but I have not found one yet that I like.  I will update this when I find a solution.

---

### Post by zazuge on 2008-04-19
Well I don't know but maybe that migh help
[http://en.wikipedia.org/wiki/Open_Source_CRM_Software](http://en.wikipedia.org/wiki/Open_Source_CRM_Software)
bye ;-)

---

### Post by zazuge on 2008-04-19
> **marcelo.matos said:**
> 
2 - About the use of gnucash on business accounts. I read on the net that gnucash uses floating-point numbers instead of integers to store currency values (search the net using the words: "floating point error gnucash").

I'm not an accountant to know exactly "how" it affects the use of gnucash, but according to a lot of people, including the own developer, it make the software lacks the "necessary reliability" to be "enterprise ready" ([http://slashdot.org/interviews/01/07/05/1456248.shtml](http://slashdot.org/interviews/01/07/05/1456248.shtml)  - Question 8.).


well in the link you indicated they say the problem was with version 1.4
and that version 1.6 use interger based numbers
so the problem is finiched with (and GNUcash is business ready!)

---

### Post by Sporkman on 2008-04-19
I'd like to say that I use Ubuntu Server for my website, and I'm very happy with it. It's perfectly stable, even under big surges of activity such as from stumbleupon, etc...

---

### Post by russh on 2008-07-13
> **DarkOx said:**
>  
So, first of all: are Sugar and CATS the best FOSS applications for these tasks? Does anyone have any experience using them?


Hi, you may have seen (I've not done the SEO thing just yet) that the Open Source effort for CATs has moved to [OpenCATS.org]("http://www.opencats.org"). Stop on by and download the source code, contribute etc, etc. 

If you want the SaaS version (hosted) by all means visit the orignal developers who closed the code and continue to develop it on a commercial basis.

---

### Post by marcelo.matos on 2008-08-08
I don't know if I should ask this here or if i should create a thread to ask this. Since it's a question about free software powering a small business I'll try here first.

I'm working on a small law office, and we are looking for something to control the cases we are working on.

It would be something like a mix of a CRM and a Project tool. I've searched the web and found some options but they are a little "supportless" to install and use.

If someone know any software to suggest, I would appreciate.

Thanks.
Marcelo.Matos

---

### Post by dca on 2008-08-08
You can take a gander here:
 
[http://www.debian.org/devel/debian-lex/software](http://www.debian.org/devel/debian-lex/software)
 
...the only one I know of off the top of my head is proprietary and it runs on Windows (they could've changed, it's been a long time).
 
[http://www.case-track.com/](http://www.case-track.com/)
 
... I have consulted for law firms in the past but it never dealt w/ case management, more for hardware, FTP sites to connect satellite offices, etc.

---

### Post by jonabyte on 2008-08-08
> 

* Some Accountants will only work with QB.

I support an accounting firm, and they spend a lot to make sure they support the majority of their clients, meaning they will work with a number of accounting software packages.
If your accountant only supports one package, you would be better off finding another one.

---


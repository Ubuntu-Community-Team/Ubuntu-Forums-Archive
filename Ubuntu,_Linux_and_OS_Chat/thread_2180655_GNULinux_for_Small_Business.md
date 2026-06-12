---
title: "GNU/Linux for Small Business"
date: 2013-10-14
forum: Ubuntu, Linux and OS Chat
---

### Post by mcglowca on 2013-10-14
Hi all,

I was wondering if there is an all-in-one solution for small business owners looking into linux. I understand that they can install Ubuntu and set it up but how many business owners have the know-how, time, patience, or contacts to do it. From what I understand now there are technologies available for business owners but they are scattered and not well known. My thought is this, Is it viable to create a derivative of Ubuntu that focus on providing a stable platform aimed solely for small to medium business owners? It could be based on LTS versions of Ubuntu and provide packages specific for business owners. There should be a desktop and server version that communicate as flawless as possible to store and encrypt business documents. Of course this would be difficult because you would have to identify what most businesses would need and find a solution that can be packaged in linux. I do believe that this can be a great opportunity for linux to be exposed to more people and be present in a market that may need such a platform. Many small businesses still use Windows XP for various reasons ranging from dislike of Vista/7/8 to cost of upgrading. I think there should be a discussion on how to turn Linux more into a business solution for a market that may need such a solution.

I will admit that I am no small business owner but I am friends and family to some. I think the first thing we should look at is what are some of the types of programs they may need.

Here are some obvious ones I can think of off the top of my head:

[LIST]
[*]Office Suite ([LibreOffice]("http://www.libreoffice.org/"))
[*]Financial Accounting software ([Gnucash]("http://www.gnucash.org/"))
[*]Email ([Thunderbird]("http://www.mozilla.org/en-US/thunderbird/"))
[*]Calendar ([Lightning]("http://www.mozilla.org/projects/calendar/lightning/"))
[*]Project Management (This one is kinda hard because the software I've looked into either lack features or are old and almost unsupported but here's what I found, [GanttProject]("http://www.ganttproject.biz/") and [ProjectLibre]("http://www.projectlibre.org/"))
[*]Publishing ([Scribus]("http://www.scribus.net/canvas/Scribus"))
[*]Invoices ([FusionInvoice]("https://www.fusioninvoice.com/") and [SimpleInvoices]("http://www.simpleinvoices.org/"))
[*]Note taking ([EverNote]("https://evernote.com/"))
[*]Customer Relationship Manager ([SugarCRM Community Edition]("http://www.sugarcrm.com/community"))
[*]Timesheets ([eHour]("http://www.ehour.nl/"))
[*]Encryption and security software
[*]Business related templates for business cards, brochures, resumes, etc.
[*]Retail Management ([uniCenta]("http://www.unicenta.com/"))
[/LIST]

I'm sure I'm missing alot of important things but that is why I'm opening this topic to all of you. Is it possible to gather all these software together into one easy to use Linux based OS like Ubuntu and market it to small business owners? With the recent NSA mess brought on by Mr. Snowden and slow adoption of Windows 8 this could be prime time for such an OS. One of the features you can tout is no NSA backdoors. I know alot of work would be needed in packaging and maintaining the packages but once it gets started I think the community can only make it better. There would also need to be available an easy to use and understand tutorial on how to use this software that comes with the OS. 

Please share your thoughts on this idea. I admit that I am not a small business owner at this time though I frequent them often. :) I also admit that I have limited time and resources to undertake this project right now but look forward to the discussions that can come from this and hope to undertake it in the future. Also I apologize in advanced for my late replies since I have limited internet access.

---

### Post by josgeluk on 2013-10-14
I run a small business on a couple of Linux boxes using some of the software you mention, and have done so for years.
A few points. Gnucash is good for accounts keeping but it does not do quotations. If you send a quotation to a customer, once you make the sale, you will have to reenter all the data into Gnucash. I have found no easy way to do this.
Also, the invoices side of Gnucash is not very versatile, and as far as I can tell, FusionInvoice and SimpleInvoices do not get their data from Gnucash or its backend database. What you want is to enter the invoice data into Gnucash (once) and generate a printed invoice from that. Currently I use some Perl to generate a LibreOffice document, that I can convert to PDF and then send to the customer.
A separate CRM module may be a good idea but again I don't see how that integrates with Gnucash. This may need a lot of "glue" before the CRM screen can tell me, for example, how much revenue customer X has generated for me, data that should be easily available from the accounting software.
For project planning and time management, I have built a couple of simple tools in Perl that run on an Apache webserver. Again, these tools use the Gnucash data wherever possible. So perhaps Apache should be in your list as well.

I wouldn't focus too much on security. In my opinion, of all the troubles that vex small business owners, government snooping is not the most important.

---

### Post by mcglowca on 2013-10-14
josgeluk,

It looks like communication is a big problem for you when it comes to the software. I'm glad you replied because I suspected that it would be an issue. So the problem that needs to be solved is how to get all the software to "talk" to each other and use the same database. It can be rather difficult if all of them use their own unique formats. Maybe a few email requests to the developers with some modified code attachments and cash could be enough to get some unity. Having an ecosystem where everything is in harmony and stable would be important for a business owner. I'm interested in hearing other problems or needs from business owners.

---

### Post by mastablasta on 2013-10-14
different businesses have different requirements. some of which you wrote are useless.

i am not sure what this would accomplish. one size won't fit all. businesses even now install windows and then add things they like or need.

also it depends on business size.

---

### Post by ssam on 2013-10-14
would it be worth having a ubuntu-business-desktop meta-package, so that the above packages could be installed in one go. From there its easy to make a custom install cd that uses that meta-package. Likely you will need a few like ubuntu-accountant-desktop, ubuntu-admin-desktop ...

---

### Post by grahammechanical on 2013-10-14
Canonical has already tried this

[http://www.omgubuntu.co.uk/2012/02/ubuntu-business-remix-launched-by-canonical](http://www.omgubuntu.co.uk/2012/02/ubuntu-business-remix-launched-by-canonical)

But

[http://www.ubuntu.com/business/desktop/remix](http://www.ubuntu.com/business/desktop/remix)

Yet click on the links at the bottom of the page and any business leader with a head for business would learn a lot about what Canonical has to offer.

Desktop management

[http://www.ubuntu.com/desktop/management](http://www.ubuntu.com/desktop/management)

Systems Management

[http://www.ubuntu.com/management](http://www.ubuntu.com/management)

I think that the OP is touting for business. It is another form of cold calling.

Regards.

---

### Post by mcglowca on 2013-10-14
It seems that the Canonical version is for large corporations that can afford dedicated people to customize the packages for their business. I'm thinking something along the lines of [CAELinux]("http://www.caelinux.com/CMS/"). It uses Ubuntu as a base and have various packages preinstalled and configured that are specific for computer aided engineering. The problem is creating a list of packages that are useful for most small businesses. Like mastablasta pointed out every business is different but at the same time at some level every small business have a set of basic needs, like accounting and customer relationship management, that they all have in common. If we can identify and address those needs then we can build a package and offer it to them.

---

### Post by mastablasta on 2013-10-15
the thing is if you have for example webshop - invoicing, CRM and such is available wihtin that tool. and some are very good at this. add a few plugins and it's good to go.

but for example we have accounting on i think windows (i dont' know now anymore all i know is that it's web based) - a proprietary programme. however that programme gives output for yearly and monthly tax report, and i can use some of output to import it directly into online back to do the necessary tax payments (i know the bank is windows locked, but it is very easy to use). the output in various accounting porgrammes available is more tailored for american market and more or less useless. sure we could modify them to fit our needs, but it would porbably cost quite a bit.

---

### Post by Docaltmed on 2013-10-18
**[SIZE=5]VERY IMPORTANT GNUCASH WARNING FOR SMALL BUSINESS!!!!!!!![/SIZE]**

I've been using Ubuntu to run my practice since 8.10. For a long time, I ran quickbooks in a VM for my accounting needs, but then I decided to simplify things by going with GnuCash.

[B][I]What nobody tells you is that GnuCash cannot produce reports on a cash basis, only an accrual basis. So if you are in the USA, and use GnuCash for AR and AP, and you file taxes on a cash basis (as most small businesses do) you are royally screwed. You, or your bookkeeper or your accountant ($$$) has to go through and manually produce the reports. 
[/I][/B]
[SIZE=3]***[COLOR="#FF0000"]HEED MY ADVICE: DO NOT use GnuCash if you file taxes on a cash basis![/COLOR]***[/SIZE]

I cannot even tell you how many thousands of dollars this mistake cost me. It makes me cry every time.

Otherwise, it's a nice program. Does my home finances just fine.


EDIT: I've never done a post with so much formatting. Kind of fun, even if it does make me look like a crazy cat lady. But, seriously, I wish someone had warned me about this.

---

### Post by ian-weisser on 2013-10-18
This subject has been discussed several (many!) times before.

"Business" covers a huge variety of organizations and needs.
No single business metapackage or distro can cover enough of that variety to be useful, and the blowback from ill-fitting business packages will harm Ubuntu's reputation more than it attracts business users.

This iteration of the discussion did not start with looking at those needs. Merely throwing a bunch of already-existing applications into a tin, and labelling that tin to be "business-friendly" is not a substitute for researching the needs of the target communities.

Docaltmed's point is a great example of free software not yet meeting a business need. In this case, there are a couple really good reasons why free cash-basis bookkeeping and accounting is not available for Ubuntu.

---

### Post by davem1946 on 2013-10-21
Since I write the software and for small to large businesses, let me state an ipinion?

accounting is accounting and size is just how much is put in.  One makes a chart of accounts to start a company off and the accountant can add to that base as needed.  Reports for that are numerous and have to be able to access the added chart accounts and a thourough manner.  Those reports are really for internal use.

CRM is, in some cases, where you keep track of clients and make your invoices as well as reports to show what they have done in the past.  Totalling reports that can take in geographical locations(small or large) and produce reports are derived off the crm side.  for simplicity, i am including sales into the crm.

CRM is generally software created by programmers with the specific nature of the company built in.  accounting can be used for any business of any size. 

it is wonderful to have the crm feed information into the accounting system at the close of a transaction.  It makes the accountants job easier. 

Wanna make money?  Create some of this software(easy part) and sell it(hard part).

---

### Post by mcglowca on 2013-10-21
> **ian-weisser said:**
> This subject has been discussed several (many!) times before.

"Business" covers a huge variety of organizations and needs.
No single business metapackage or distro can cover enough of that variety to be useful, and the blowback from ill-fitting business packages will harm Ubuntu's reputation more than it attracts business users.

This iteration of the discussion did not start with looking at those needs. Merely throwing a bunch of already-existing applications into a tin, and labelling that tin to be "business-friendly" is not a substitute for researching the needs of the target communities.

Docaltmed's point is a great example of free software not yet meeting a business need. In this case, there are a couple really good reasons why free cash-basis bookkeeping and accounting is not available for Ubuntu.

I understand the broad implications of the term "business" but what I wanted to learn and discuss was what are the common basic needs of businesses. I tried to aim the discussion to small and medium scales, mom and pop shops, to reduce the complexity of the resources needed. What I really wanted to talk about is the feasibility of creating an ecosystem that is friendly to these business owners. 

As for looking at the needs of small businesses, I knew that I wasn't addressing alot of the needs in my first post. Thats why I asked for a discussion in this area. I now realized that this discussion may encompass more than just US businesses making the project more unfeasible. "How can I address the needs of a Chinese business owner when I'm in America?" I suppose the best route to take would be to try and address the needs of the community I'm a member of, city, municipality, etc. and possibly creating a business from it myself. 

However one of my main questions may still be valid for discussion. Where does open source and free software fall short in addressing the needs of business owners? The Gnucash example is something I was looking for. Since the problem is identified, the way gnucash issues its reports for taxes, is there a simple solution to fixing it, like making a simple plugin, or will it require more work, like modifying the source code.

---

### Post by mastablasta on 2013-10-21
davem1946 made a very good point CRM and ERP software are the ones that need help. it's different depending on business type, region etc. so if oyu want to help it is indeed best to offer local support first. see how it goes...

---

### Post by ian-weisser on 2013-10-21
> **mcglowca said:**
> Since the problem is identified, the way gnucash issues its reports for taxes, is there a simple solution to fixing it, like making a simple plugin, or will it require more work, like modifying the source code.

Here's a problem with accounting and taxes showing why the tax issue is non-trivial:
Tax structures vary from country to country, and among state/provinces/departments, and among cities/counties/regions.
Taxes may vary among goods and services bought, sold, produced, destroyed, in inventory, and components.
Taxes may be collected on number or type of employees, members, partners, contractors, and/or on the amount paid. Multiple taxes and perhaps mandatory witholding on each, too.
And each of those taxes may be paid to a different taxing authority, and each tax is subject to change at any time. That's thousands of tax tables to be updated annually in the United States alone.

Now add in the liability for penalties if software not designed for that location or industry calculates the tax wrong. Who pays that penalty?

It's simply easier and more reliable for a business owner to locate an accountant familiar with the industry and local tax requirements, and to have the accountant set up the bookkeeping system so all tax-relevant data gets captured. The accountant sets it up in whatever system they feel most comfortable and productive with (like QuickBooks). There *are* comparable linux-native or web-based bookkeeping packages...but they are not free, and many accountants are less familiar (unproductive) with them. 

In this example, it's not really a code problem. It's an accountant-training problem.

---

### Post by davem1946 on 2013-10-21
One must simply(simplify) what a business needs most now(right now) and what will be the next step.


Now:
IF a business has inventory and sells from the inventory, then the sales application needs to have inventory where it maintains levels(or not).  If the business sells time, then no inventory is really needed. If manufacturing, the end product(s) are sold and keeping up with the inventory used to make the product needs to be accounted for.  That all being said, then the part of the sale and follow up(crm) is needed with the ever popular math portions.  

Generally it is the crm/sales/inventory type app needed most and this extends from the mom&pop to fortune 100 companies.  This is pretty much universal around the world and I have programmer friends from china headed east to Germany/Italy  I even know a couple in India.  These things are the same.  

Next on a Maybe:
The accounting thing has to be dealt with in most countries(all that I know of) and is really a basic mathematical exercise.  Again, it all comes from a chart of accounts where one side is added and one is take-away.  The few static are for a different reason.  Just basic boring stuff.

Remember:  A very small mom and pop can get by with ink and paper until the math starts killing them and the customer base gets too large.  

To me, a Linux server is a great plus because one can create a database application and have it sit on a web space anywhere or on a lan if needed.  That would be a good repository for all data and very secure if done right.   I have been using them for years.

---

### Post by davem1946 on 2013-10-21
> Now add in the liability for penalties if software not designed for that location or industry calculates the tax wrong. Who pays that penalty?


It is the business owner, but if he was supplied bad tools, he is not going to be happy at the least.  

When I give a client a piece of software, it is up to the business to insert the rates into the tables and to keep up with them.  It is that simple, but it is like and extra piece of software I have to make.

---


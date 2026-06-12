---
title: "Software Recommendations for Small Business"
date: 2011-04-26
forum: The Cafe
---

### Post by marl30 on 2011-04-26
We are starting a small family business that will involve buying and selling goods to different companies. We will be making the deliveries where necessary. Some of what we will be selling will be bought online, while more urgent stuff will be purchased locally. 

Since I will be managing the business, I've made the decision to use Linux in our office. I'm yet to decide on what Distro I'll go with. Certainly not Ubuntu 11.04 with Unity, or anything with Gnome Shell. Perhaps I'll check out Opensuse or go with Debian (KDE), well, only if it's not true that Wine refuses to work in Debian. 

Anyway, I would like some suggestions as to what free Linux software I could use for the following task.

* Manage all the accounting needs of the business (Check account, credit card, payroll, petty cash, etc).

* A software that I can use to keep a stock inventory

*  Something for doing up pay stub to show tax deduction, etc

Any suggestion will be welcomed. So far I have been looking at GNU Cash, Kmymoney, and Homebank. We'll have a staff of four. 

I've worked in management before, so I know the power of having the right software. Where I used to work, they had a custom software (for Windows) that they got developed to run every aspect of the business. It made things easy and didn't require us to hire an accountant.

---

### Post by HermanAB on 2011-04-26
The serious version of all those is SQL-Ledger.

---

### Post by Zlatan on 2011-04-26
> **marl30 said:**
> We are starting a small family business that will involve buying and selling goods to different companies. We will be making the deliveries where necessary. Some of what we will be selling will be bought online, while more urgent stuff will be purchased locally. 

Since I will be managing the business, I've made the decision to use Linux in our office. I'm yet to decide on what Distro I'll go with. Certainly not Ubuntu 11.04 with Unity, or anything with Gnome Shell. Perhaps I'll check out Opensuse or go with Debian (KDE), well, only if it's not true that Wine refuses to work in Debian. 

Anyway, I would like some suggestions as to what free Linux software I could use for the following task.

* Manage all the accounting needs of the business (Check account, credit card, payroll, petty cash, etc).

* A software that I can use to keep a stock inventory

*  Something for doing up pay stub to show tax deduction, etc

Any suggestion will be welcomed. So far I have been looking at GNU Cash, Kmymoney, and Homebank. We'll have a staff of four. 

I've worked in management before, so I know the power of having the right software. Where I used to work, they had a custom software (for Windows) that they got developed to run every aspect of the business. It made things easy and didn't require us to hire an accountant.

[Opentaps]("http://www.opentaps.org")
try [demo]("http://www.opentaps.org/products/online-demo")
[available on cloud]("http://www.opentaps.org/cloud")

---

### Post by jonathonblake on 2011-04-26
> **HermanAB said:**
> The serious version of all those is SQL-Ledger.

The current version of SQL-Ledger is closed source SAAS.

LedgerSMB ([http://sourceforge.net/projects/ledger-smb/files/ledgersmb/1.2.21/](http://sourceforge.net/projects/ledger-smb/files/ledgersmb/1.2.21/)) is free libre open source software.

Both of those programs require an accountant to setup. I'm not quite at the point of saying that you have to be an accountant to use either of them.

There are at least a dozen other accounting packages for Linux, for SOHO and SMB organizations. Some of those other packages are arguably, off the shelf, much more appropriate for what Marl described, than either SQL-Ledger or LedgerSMB.

Both _PeachTree Accounting_ and _QuickBooks Enterprise Edition_  are much easier for non-accountants to setup, customize, and use, than anything in the Linux world is.

Three other points of consideration:
* Accounting packages tend to be web based, or in the cloud, usually Amazon's;
* Pricing is usually on a Software as a Service basis;
* The vendor might claim the product is open source, but the things that make it useful, and as often as not, usable, are closed source/propriety;

jonathon

---

### Post by marl30 on 2011-04-26
Hey guys, thanks for the reply. I'm going to be looking into those software suggested. Thanks for your input, Jonathan.  For now, I can only focusing on free software. A lot of money has already gone into other areas. When things take off I can probably go with something commercial. In the mean time, I may have to use Libreoffice Spreadsheet and Database to make up where the free software fall short. 

I'll be updating in the future as to how things turnout running our business with Linux. :)

---

### Post by andrewabc on 2011-04-27
[OpenERP](http://openerp.com/) - [demo](https://demo.my.openerp.com/?db=demo_1303844555&user=demo&password=demo&login_action=login) - natty has old version in repository.
[SugarCRM](http://www.sugarcrm.com/crm/) - got some video demos to watch, got rid of online demo to try, so you pretty much have to install to see (I would use VM)
[Compiere](http://www.compiere.com/) - seem to be douchebags that don't have easy access to demo or open source download
[webERP](http://www.weberp.org/HomePage) - [demo](http://www.weberp.org/weberp/index.php)
[Zimbra](http://www.zimbra.com/) - [Zimbra Desktop](http://www.zimbra.com/products/desktop.html)
[vtiger](http://www.vtiger.com/) - [demo](http://demo.vtiger.com/)

If all 4 of you will be wanting to input sales, contact info etc, you would probably want something that all 4 can connect to over local lan.

I don't know how well how these programs would help, but those with demos you should definitely click around in them, and those that don't have demos watch a couple videos.
Some of these programs might not fit your criteria, but I thought I'd include them as I'd been following their progress for a couple years.

EDIT:
[BitNami](http://bitnami.org/) is good place to install stuff from, makes installers easy. Example: [SugarCRM installer](http://bitnami.org/stack/sugarcrm), I've installed this from here before and was as easy as double clicking installer (or at least in terminal sudo run the installer).

---

### Post by marl30 on 2011-04-29
> **andrewabc said:**
> [OpenERP]("http://openerp.com/") - [demo]("https://demo.my.openerp.com/?db=demo_1303844555&user=demo&password=demo&login_action=login") - natty has old version in repository.
[SugarCRM]("http://www.sugarcrm.com/crm/") - got some video demos to watch, got rid of online demo to try, so you pretty much have to install to see (I would use VM)
[Compiere]("http://www.compiere.com/") - seem to be douchebags that don't have easy access to demo or open source download
[webERP]("http://www.weberp.org/HomePage") - [demo]("http://www.weberp.org/weberp/index.php")
[Zimbra]("http://www.zimbra.com/") - [Zimbra Desktop]("http://www.zimbra.com/products/desktop.html")
[vtiger]("http://www.vtiger.com/") - [demo]("http://demo.vtiger.com/")

If all 4 of you will be wanting to input sales, contact info etc, you would probably want something that all 4 can connect to over local lan.

I don't know how well how these programs would help, but those with demos you should definitely click around in them, and those that don't have demos watch a couple videos.
Some of these programs might not fit your criteria, but I thought I'd include them as I'd been following their progress for a couple years.

EDIT:
[BitNami]("http://bitnami.org/") is good place to install stuff from, makes installers easy. Example: [SugarCRM installer]("http://bitnami.org/stack/sugarcrm"), I've installed this from here before and was as easy as double clicking installer (or at least in terminal sudo run the installer).

Most of them seem Cloud related. Since we will be operating from one location and only need the internet to order goods, the only use I'll have for Cloud is backing up important files. Dropbox will be used for that. 

Nonetheless, I'll still take note of all the software mentioned in this thread. As soon as things get off the ground, I'll see which is worth investing in. Planning to keep things native (Linux) though. I want our business completely free of Windows dependency. That means, no VM, or if I use Wine, it will only be for some game I might take to play when I stay back after work. 

Thanks to all.

---

### Post by Artemis3 on 2011-04-29
I don't see where you got that Wine refuses to work with Debian, thats not true. The only problem is the outdated versions in the official repos, so you need to use a third party repository or even fetch the debs from Ubuntu's PPA...

If you go with Ubuntu, stick to LTS. If Debian, stick to Stable. For the Desktop, I'd say go with XFCE for a classic, fast and stable desktop.

---

### Post by jonathonblake on 2011-04-29
> **marl30 said:**
> Most of them seem Cloud related.

You'll probably end up running your own in-house cloud server.  
Everything I've seen for SOHO or larger is based on a client/server model.

> As soon as things get off the ground, I'll see which is worth investing in. Planning to keep things native (Linux) though.

In comparing the features of the various FLOSS packages with Quickbooks and PeachTree Accounting, your investment will be in either writing code, or paying somebody to write the code.


jonathon

---

### Post by marl30 on 2011-04-29
> **Artemis3 said:**
> I don't see where you got that Wine refuses to work with Debian, thats not true. The only problem is the outdated versions in the official repos, so you need to use a third party repository or even fetch the debs from Ubuntu's PPA...

If you go with Ubuntu, stick to LTS. If Debian, stick to Stable. For the Desktop, I'd say go with XFCE for a classic, fast and stable desktop.

Well, it's something I see coming up over and over. I was even trying to help someone in the Wine section getting Wine running on Debian some time ago. Every version, including the development version, failed to get software installed.

Yeah, XFCE seems like a nice choice. I think if I were to choose that, I'd go with Linux Mint XFCE Debian, since it is a rolling distro, plus the other person who will be using the computer along with me is a Windows user, so using Mint should make most things seem familiar. 

> **jonathonblake said:**
> You'll probably end up running your own in-house cloud server.  
Everything I've seen for SOHO or larger is based on a client/server model.



In comparing the features of the various FLOSS packages with Quickbooks and PeachTree Accounting, your investment will be in either writing code, or paying somebody to write the code.


jonathon

I don't really need cloud outside of backing up. It's not one of those types of businesses that will require linking with other companies and constantly sharing information. It's just a simple delivery business where the local orders will be done over the phone and then the goods we're selling are picked up and stored. The online side of things just involves going to certain sites and order certain items we're selling that we can't get locally. The computer is mainly needed for storing data and keeping track of things. 

Basically what you're saying is that Linux is not a great choice when it comes to business software? 

I know those you mentioned are some of the best, but even if they work flawlessly in Wine, my thing is, I'd rather not have to use Wine. It tends to develop issues especially if you fiddle too much with it. Since using Linux, I've often had to reinstall Wine because something stop working how it use to. Staying native will avoid such headaches.

---

### Post by Artemis3 on 2011-04-29
I don't think you should use a rolling distro for production...

---

### Post by jonathonblake on 2011-04-29
> **marl30 said:**
> I don't really need cloud outside of backing up.

The issue is what is available. If you don't want a client/server package, or a cloud based package, you'll have to use a stand-alone Windows product. One that might work under CrossOver.

> Basically what you're saying is that Linux is not a great choice when it comes to business software? 

Linux software is written with the assumption that the end-user is somebody that knows what, why, and how they need to do things.

Windows software is written with the assumption that end-user does not know what, why, and how they need to do things.

That difference in programming philosophy means that the Linux product is more useful to the person who can program, and has complete comprehension of the field that the software is targeted for. However, it also means that it has a much steeper learning curve than the equivalent Windows software.

jonathon

---

### Post by User235 on 2011-05-30
> **jonathonblake said:**
> 
Linux software is written with the assumption that the end-user is somebody that knows what, why, and how they need to do things.

Windows software is written with the assumption that end-user does not know what, why, and how they need to do things.

That difference in programming philosophy means that the Linux product is more useful to the person who can program, and has complete comprehension of the field that the software is targeted for. However, it also means that it has a much steeper learning curve than the equivalent Windows software.

jonathon

This is a really interesting proposal - so if I understand you right, you're saying if one is willing to put in the time/effort, Linux can be a useful OS for business purposes.  

I, for one, am all for Linux.  However, even though I have years of software (programming) experience, I am reluctant to commit that time when Windows offers many solutions not yet available from Linux. 

I'm not one for re-inventing the wheel, I have a company to run.  But I am hopeful that someday I can run this company on Linux and see the benefits in the long run.

---

### Post by jonathonblake on 2011-05-30
> **User235 said:**
> This is a really interesting proposal - so if I understand you right, you're saying if one is willing to put in the time/effort, Linux can be a useful OS for business purposes.  

a) Rephrasing:
[LIST]
[*]Windows software is written for trained monkeys that neither know, nor care about what they are doing;
[*]Linux software requires one to commit to learning why they need to do what they want to do;
[/LIST]

> I am reluctant to commit that time when Windows offers many solutions not yet available from Linux. 

[LIST]
[*]Windows solutions are restricted to what the programmer/designer thinks are viable solutions;
[*]Linux solutions are restricted to those that the user can conceive of;
[/LIST]
> 
But I am hopeful that someday I can run this company on Linux and see the benefits in the long run.

You can reap the benefits of Linux as your business OS today, [COLOR="DarkRed"]if[/COLOR] you are willing to commit to educating your employees in the area that they were hired for.

jonathon

---

### Post by Dustin2128 on 2011-05-30
I say ubuntu lucid or debian stable. Both should run fine.

---

### Post by katykat on 2011-05-30
Unix was designed from the start as an OS for large corporations and academic institutions.

However, inventory and accounting programming was normally done in house by the IT departments and never meant to be publicly releassed. 

As an online vendor my accounting needs are very simple, and mostly done on paper. Simpler than data entry. 

What I would do in this instance is talk to an accountant and see what they will accept. 
They may very well have a spreadsheet template that they prefer. Or a software recommendation - and if there is a choice go for the simplest. Wine works well on Gnome, but may need some addtiional support such as Crossover (feeware) or Playonlinux (free). 

Especially as a startup business, the accountant is infinitely more important than accounting software, and so should be consulted first on the choice.

---

### Post by kufanindustries on 2011-07-04
if you use a debian based os like xubuntu, you can use incoPOS from vladster without needing wine to emulate windows. 
you will also need the mySQL-server.deb package from the debian repo installed BEFORE you install incoPOS.

ubuntu forums won't let me describe the features or link the download page, accused spamming advertisment. 
sorry ](*,)

for a business setup like what you are describing, Artemis3 is right, you need a stable version so that you can keep getting updates long after the os version is released.
this is so that you won't have to constantly update every couple of months and likely loose program support and stability.

---

### Post by juancarlospaco on 2011-07-04
How is the business going OP ...?  :)

---

### Post by Bandit on 2011-07-04
> **marl30 said:**
> Hey guys, thanks for the reply. I'm going to be looking into those software suggested. Thanks for your input, Jonathan.  For now, I can only focusing on free software. A lot of money has already gone into other areas. When things take off I can probably go with something commercial. In the mean time, I may have to use Libreoffice Spreadsheet and Database to make up where the free software fall short. 

I'll be updating in the future as to how things turnout running our business with Linux. :)

Dont forget you can use MySQL and MYSQL Admin to build your databases and simple PHP scripts to produce reports.

---


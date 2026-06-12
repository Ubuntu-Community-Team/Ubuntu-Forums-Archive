---
title: "To all those whose only impediment to using linux is Microsoft Office..."
date: 2010-11-20
forum: The Cafe
---

### Post by user1397 on 2010-11-20
If you have a legitimate copy of Microsoft Office, and you want to use linux as your sole OS, but OpenOffice doesn't cut it for you, it is really simple to install MS Office in linux (specifically ubuntu here of course).

It is as simple as installing wine through the repos, putting the MS Office install CD in the CD tray, going to the setup.exe file in the CD, and opening it with wine.

Of course, if you have a netbook and don't have a CD drive, you have to install using an .iso image file.  To make an .iso image of your MS Office CD, use a program like [imgBurn]("http://www.imgburn.com/") on Windows.

Mounting an ISO in ubuntu is exceedingly simple using the Furius ISO Mount app available in the repos.

Then it is just as simple as the steps above.

There are some post-installation instructions which might make certain programs work better, for example if you are installing MS Office 2007 go [here]("ttp://appdb.winehq.org/appview.php?iVersionId=4992") and scroll down to the post installation instructions.

---

### Post by beew on 2010-11-20
Many people who claim that openoffice doesn't cut it for them never give it a chance, they are just too used to MSO, peroid. Many people who say that must have MSO are using it for simple spreadsheets and words. It is a psychological rather than real need.

What really kils me is that I read quite a few people trying to install Office 2003 or even Office 9x in Wine because they want better compatibilty with MS formats.

---

### Post by Hippytaff on 2010-11-20
Thanks for that...Maybe the mods can put your words of wisdom in the tutorials sub-forum

For everyone to be able to call upon :-)

---

### Post by user1397 on 2010-11-20
> **beew said:**
> Many people who claims that openoffice doesn't cut it for them never give it a chance. Many people who say that must have MSO are using it for simple spreadsheets and words. It is a psychological rather than real need.

What really kils me is that I read quite a few people trying to install Office 2003 or even Office 9x in Wine because they want better compatibilty with MS formats.

I completely agree, this post is meant more for those people whose job or school or whatever really requires MS office for whatever reason, and they need to have it.

---

### Post by Hippytaff on 2010-11-20
I know where your coming from...to behonest Oo works really well for me :-)

but I understand the neesd for Wine, dual boot with windows and a a virtual  effort

Mods  can this be a tutorial?

hello?

---

### Post by user1397 on 2010-11-20
> **Hippytaff said:**
> I know where your coming from...to behonest Oo works really well for me :-)

but I understand the neesd for Wine, dual boot with windows and a a virtual  effort

Mods  can this be a tutorial?

hello?
well i would be willing to make it into a real tutorial if there was enough demand for it.  my post here is hardly a tutorial, i just outlined how there aren't that many steps to get ms office working correctly in linux.

---

### Post by TheNessus on 2010-11-20
I don't fully trust Wine. Things are unstable running on Wine. 

To use MS office I run Windows XP in Virtual Box, made solely to run Office 2010 (2010 doesn't work on Wine anyway, only 2007 and under). I put it in its own workspace, and it has access to my Documents folders on the linux host. Its virtually like using it on Linux, and it runs stable and good. I don't only use it for MS word, but for OneNote and other things that have no suitable linux alternative.

---

### Post by dtfinch on 2010-11-20
A lot of small businesses use MS Access, which has no practical substitute.

Office is generally a lot faster than OpenOffice, but I've grown to prefer OOo Calc over Excel for its better text import (more flexibility, and being able to paste tab delimited text without saving to a file first), block drag/drop (vs having to cut/paste to move blocks in Excel), and less crashy solvers (separate download). And Office generally supports much fewer formats and now requires registry hacks to open files saved in much older versions, under the false guise of security.

Then there's the xml based Office documents which usually don't show up right in OpenOffice, but I can open them in 2003 and save them again in the old binary formats and after that they usually look just fine in OOo.

I don't understand what people like about Outlook, or Exchange. They're both an IT support nightmare, usually mandated by higher ups who know nothing about how bad it is and choose it because it's made by Microsoft.

---

### Post by Crusty Old Fart on 2010-11-20
> **beew said:**
> Many people who claim that openoffice doesn't cut it for them never give it a chance, they are just too used to MSO, peroid. Many people who say that must have MSO are using it for simple spreadsheets and words. It is a psychological rather than real need.

What really kils me is that I read quite a few people trying to install Office 2003 or even Office 9x in Wine because they want better compatibilty with MS formats.
Sorry lads, I couldn't disagree more. There's only one application that I use in MSO and that's Excel. I would LOVE to use Calc instead. I hate Microsoft and all their crap code more than you could possibly imagine. However, Excel still blows the doors off of Calc. Just try running Calc on a spreadsheet that has over a thousand lines in it and you'll see what I mean. It's dog slow. And when it does its periodic auto-saves, it takes ten to fifteen seconds to complete and you can't do jack with it while it's saving. Excel auto-saves so fast that I never notice it happening. If you attach comments to cells, which is a feature that I NEED, Calc "notes" will do it, but don't expect the note to point to the correct cell, I've had it be more than eight cells off. Its offset isn't consistent either. While notes will stay in the correct column, they seem to have a mind of their own in terms of what row they're going to land on. I've given Calc a chance, and I will continue giving it more chances in the future because I want to get completely away from EVERYTHING Microsoft. But Calc just isn't ready yet for anyone who has serious work to do on large spreadsheets.

---

### Post by Kdar on 2010-11-20
I just use LaTeX now. No need even for OpenOffice. Its intalled only to view other's doc files.

---

### Post by zorocke on 2010-11-20
I love how I need Microsoft Excel for my entry level engineering lab at my university. While we are not doing anything that Open Office can't do, the test questions reflect microsoft. "How do you create a scatter plot in excel, where on the ribbon would you find this function?" 

Just my rant against being forced to buy a product that is unnecessary. 

PS> The course is a joke as far as I'm concerned.

---

### Post by weasel fierce on 2010-11-20
The stuff I publish online I do in PDF, and I don't need spreadsheets, so MS office has absolutely zero value to me.
For heavy excel users, it'd be worthwhile of course.

As far as compatibility, I haven't run into trouble opening MS documents in OO, but I rarely open stuff with a ton of macros. We constantly have issues at work though, since we use two different versions of Office at the moment.

---

### Post by marl30 on 2010-11-20
I read that Go-OO (the fork of OOO) is actually the best alternative for MS Office out of OOO and other Office suites that are based on it. They say it offers better support for MS Formats. What do you guys think?

I'd gladly use only Openoffice; however, there are a few reasons holding me back from doing so. 1. I need Ms Office for school, since I'm actually learning more about Excel and Access... I have to use MS Office to do school work relating to it. 2. I'd love to do some of my Access database assignments in Openoffice Base, but I can't seem to get it to work with Access format. 3. Writer lacks a decent grammer checker that compares to the one in Ms Word, even with different grammer extentions like After The Deadline and others, it was not near to Word. (If anyone knows of any other good grammer extension for Writer apart from Ligthproof, After The Deadline, and Language Tool, please do let me know.)

Apart from those everything else with OOO is great. If only I could resolve those issues, I would have less reason to use Ms Word, well at least for none school stuff.   

> 5. Go-OO office suite

Unless you've been living under a rock for the past few years, you probably already know about OpenOffice.org, the open source (and therefore free-of-charge) office suite. This keeps getting better with each release and is now a definite contender for lighter-weight office tasks. If you haven't looked at it recently, it's well worth a trial.

I find it very useful for those upgrading from an older version of Office and who are confused by the ribbon-based user interface, found on recent releases of Microsoft Office.

However, it's been a busy time in the world of OpenOffice.org, and Oracle's acquisition of Sun--owners of OpenOffice.org--has dropped a bomb from which the dust is still settling. The LibreOffice project has picked-up the reins but is still in beta testing stage, so at the moment I recommend the existing version of Go-OO as the best free-of-charge office suite around. Based on OpenOffice.org with some useful tweaks here and there, its chief advantage is support for Microsoft's newer XML-based file format (such as the DOCX, XLSX, and PPTX file extensions), which is the default in all recent releases of Microsoft Office.[http://www.pcworld.com/businesscenter/article/210411/5_awesome_free_tools_for_small_businesses.html](http://www.pcworld.com/businesscenter/article/210411/5_awesome_free_tools_for_small_businesses.html) 

---

### Post by czr114 on 2010-11-20
From what I've found, most people use only the basic functionality, for which either suite will be fine. Switching from one to the other is mostly an issue of becoming comfortable with the interface, especially if switching to/from MSO2k7 or newer (with the ribbon).

OO calc has issues, so OO + Gnumeric would be a good substitute for heavy spreadsheet users.

MSO still has a place, with all its plugins, merge integration, macro functionality, and MS Access.

Most people don't need one or the other. Those who need MSO should know right away.

---

### Post by Shining Arcanine on 2010-11-20
> **ubuntuman001 said:**
> If you have a legitimate copy of Microsoft Office, and you want to use linux as your sole OS, but OpenOffice doesn't cut it for you, it is really simple to install MS Office in linux (specifically ubuntu here of course).

It is as simple as installing wine through the repos, putting the MS Office install CD in the CD tray, going to the setup.exe file in the CD, and opening it with wine.

Of course, if you have a netbook and don't have a CD drive, you have to install using an .iso image file.  To make an .iso image of your MS Office CD, use a program like [imgBurn]("http://www.imgburn.com/") on Windows.

Mounting an ISO in ubuntu is exceedingly simple using the Furius ISO Mount app available in the repos.

Then it is just as simple as the steps above.

There are some post-installation instructions which might make certain programs work better, for example if you are installing MS Office 2007 go [here]("ttp://appdb.winehq.org/appview.php?iVersionId=4992") and scroll down to the post installation instructions.

Even better, just buy a copy of CrossOver Professional:

[http://www.codeweavers.com/](http://www.codeweavers.com/)

Purchases of crossover help fund the salaries of many of the WINE developers, including Alexandre Julliard.

> **beew said:**
> Many people who claim that openoffice doesn't cut it for them never give it a chance, they are just too used to MSO, peroid. Many people who say that must have MSO are using it for simple spreadsheets and words. It is a psychological rather than real need.

What really kils me is that I read quite a few people trying to install Office 2003 or even Office 9x in Wine because they want better compatibilty with MS formats.

I tried open office for several months and it was a disaster for me. I could not do plot histograms for my assignments and although there is supposed to be a way, it is by no means easy to access.

Doing word processing is also a pain. Making multilevel ordered/unordered list requires moving your hands from the keyboard and obtaining anything other than the default formatting will take a significant amount of time away from typing.

Honestly, Open Office is like a bad clone of Microsoft Office 97 and ignoring the problem by making excuses for the project is backwards. The difference between Open Office and Microsoft Office is like the difference between GNU Nano and vim. There is simply no contest and if this was a few decades ago, it would be considered good, but by today's standards, it is poor.

---

### Post by marl30 on 2010-11-20
> **Shining Arcanine said:**
> Even better, just buy a copy of CrossOver Professional:

[http://www.codeweavers.com/](http://www.codeweavers.com/)

Purchases of crossover help fund the salaries of many of the WINE developers, including Alexandre Julliard.



I tried open office for several months and it was a disaster for me. I could not do plot histograms for my assignments and although there is supposed to be a way, it is by no means easy to access.

Doing word processing is also a pain. Making multilevel ordered/unordered list requires moving your hands from the keyboard and obtaining anything other than the default formatting will take a significant amount of time away from typing.

Honestly, Open Office is like a bad clone of Microsoft Office 97 and ignoring the problem by making excuses for the project is backwards. The difference between Open Office and Microsoft Office is like the difference between GNU Nano and vim. There is simply no contest and if this was a few decades ago, it would be considered good, but by today's standards, it is poor.
If Openoffice was so far off from being close to Ms Office, Ms would not have seen the need to put out a recent Office 2010 ad that specifically targeted Openoffice, which encouraged people to choose Office 2010 over OOO.

---

### Post by holiday on 2010-11-20
All my home machines are Ubuntu, but I have to run MS Office because my employer uses many complicated templates and macros and OO doesn't cut it. Sure, OO can do everything that MS Office does, but some of those things don't translate all that well. We also have to use Cisco VPN client, and Enterprise Architect. Sure Unix offers functional substitutes, but we're locked down and use of non-approved software is considered a security breach.  

My solution is VirtualBox. VB obsoletes Wine. It's no good for gaming, but we're talking about Office apps, right?

---

### Post by witeshark17 on 2010-11-20
> **beew said:**
> Many people who claim that openoffice doesn't cut it for them never give it a chance, they are just too used to MSO, peroid. Many people who say that must have MSO are using it for simple spreadsheets and words. It is a psychological rather than real need.

What really kils me is that I read quite a few people trying to install Office 2003 or even Office 9x in Wine because they want better compatibilty with MS formats. Just wanna put my +1 here :KS

---

### Post by smellyman on 2010-11-20
I hope someday we can say "why can't MS office open Ooo documents..."

---

### Post by user1397 on 2010-11-20
> **holiday said:**
> My solution is VirtualBox. VB obsoletes Wine. It's no good for gaming, but we're talking about Office apps, right?In my opinion, Wine obsoletes VB...why run an entire OS in a virtual machine just to run one program, when you can use Wine, just a compatibility layer, to do the same thing.  It uses less resources, I can guarantee that.

---

### Post by czr114 on 2010-11-20
> **ubuntuman001 said:**
> In my opinion, Wine obsoletes VB...why run an entire OS in a virtual machine just to run one program, when you can use Wine, just a compatibility layer, to do the same thing.  It uses less resources, I can guarantee that.

Wine is not a perfect solution. Many applications do not run well in Wine. VirtualBox will run anything properly, limited only by certain graphics-heavy operations which run with poor efficiency.

---

### Post by marl30 on 2010-11-20
> **ubuntuman001 said:**
> In my opinion, Wine obsoletes VB...why run an entire OS in a virtual machine just to run one program, when you can use Wine, just a compatibility layer, to do the same thing.  It uses less resources, I can guarantee that.

Wine still unable to run Access. That's one of the main reason I have to run Xp in VB. I really wish I didn't have. I hate having to boot up another OS just to get my work done.

---

### Post by 73ckn797 on 2010-11-20
I have MS Office 97 running in Wine. It works just fine and is required for some documents my wife has to work with. The original documents have graphics and some watermarks. When opened in OO the formating is completely fouled up. The effort needed to straighten all of this out is not worth it since the documents have to be sent back in the MS doc format.

Otherwise OO is great for my needs.

---

### Post by wilee-nilee on 2010-11-20
If a person has a Word License then they probably have a MS OS license as well, run it in windows where it should be dual boot or go virtual as suggested. If you want stability that is what I would do. I have W7 with Word 2007 never user either though except to help those that do.

---

### Post by Khakilang on 2010-11-20
I have use Microsoft for years since Office 97. Since I converted my computer to Linux. Not only I need to learn OpenOffice but Linux as well. After a few months of tinkering. Now I am at home with Linux and all the software. To me patience is the virtue in learning new things.

---

### Post by jrusso2 on 2010-11-21
> **ubuntuman001 said:**
> If you have a legitimate copy of Microsoft Office, and you want to use linux as your sole OS, but OpenOffice doesn't cut it for you, it is really simple to install MS Office in linux (specifically ubuntu here of course).

It is as simple as installing wine through the repos, putting the MS Office install CD in the CD tray, going to the setup.exe file in the CD, and opening it with wine.

Of course, if you have a netbook and don't have a CD drive, you have to install using an .iso image file.  To make an .iso image of your MS Office CD, use a program like [imgBurn]("http://www.imgburn.com/") on Windows.

Mounting an ISO in ubuntu is exceedingly simple using the Furius ISO Mount app available in the repos.

Then it is just as simple as the steps above.

There are some post-installation instructions which might make certain programs work better, for example if you are installing MS Office 2007 go [here]("ttp://appdb.winehq.org/appview.php?iVersionId=4992") and scroll down to the post installation instructions.

I did this but each time I launch office I have to put the whole key in again.

---

### Post by beew on 2010-11-21
> **dtfinch said:**
> A lot of small businesses use MS Access, which has no practical substitute.

Office is generally a lot faster than OpenOffice, .

That is not true. MSO is a lot faster than OO in Windows (who would be surprised?) but OO is faster in Linux than MSO in Windows.

Small businesses are exactly the ones who don't need to pay for MSO, well at least many don't have to but for their fear of the unknown.

---

### Post by beew on 2010-11-21
> **Crusty Old Fart said:**
> Sorry lads, I couldn't disagree more. There's only one application that I use in MSO and that's Excel. I would LOVE to use Calc instead. I hate Microsoft and all their crap code more than you could possibly imagine. However, Excel still blows the doors off of Calc. Just try running Calc on a spreadsheet that has over a thousand lines in it and you'll see what I mean. It's dog slow. And when it does its periodic auto-saves, it takes ten to fifteen seconds to complete and you can't do jack with it while it's saving. Excel auto-saves so fast that I never notice it happening. If you attach comments to cells, which is a feature that I NEED, Calc "notes" will do it, but don't expect the note to point to the correct cell, I've had it be more than eight cells off. Its offset isn't consistent either. While notes will stay in the correct column, they seem to have a mind of their own in terms of what row they're going to land on. I've given Calc a chance, and I will continue giving it more chances in the future because I want to get completely away from EVERYTHING Microsoft. But Calc just isn't ready yet for anyone who has serious work to do on large spreadsheets.


Well I don't use EXCEL or Calc for anything over a thousand lines and I suspect many people don't. I have to work with large datasets at work but I use professional softwares not Office Suites for such purposes.

---

### Post by wilee-nilee on 2010-11-21
> **beew said:**
> That is not true. MSO is a lot faster than OO in Windows (who would be surprised?) but OO is faster in Linux than MSO in Windows.

Small businesses are exactly the ones who don't need to pay for MSO, well at least many don't have to but for their fear of the unknown.

OO runs and opens at pretty much the same speed as word in W7 you just have to know how to set it up this is without the quick start in OO. I also have Java off I just write papers for college classes.
[ATTACH]176152[/ATTACH]

---

### Post by beew on 2010-11-21
> **73ckn797 said:**
> I have MS Office 97 running in Wine. It works just fine and is required for some documents my wife has to work with. The original documents have graphics and some watermarks. When opened in OO the formating is completely fouled up. The effort needed to straighten all of this out is not worth it since the documents have to be sent back in the MS doc format.

Otherwise OO is great for my needs.

Have you tried open a docx file in Office97? I don't believe that Office97 is that compatible with Office 07 and 10.

---

### Post by HermanAB on 2010-11-21
Hmm, it depends. If you only produce new documents, then OOo is in many ways better than MS Office.  Problems arise when you are working in a collaborative environment and need to edit documents that were created in MS Office.  In that case OOo is not a good solution.

My solution is Codeweavers and MS Office 2007.  I have been using that combination for the past two years and it works perfectly most of the time.

---

### Post by TheNessus on 2010-11-21
> **ubuntuman001 said:**
> In my opinion, Wine obsoletes VB...why run an entire OS in a virtual machine just to run one program, when you can use Wine, just a compatibility layer, to do the same thing.  It uses less resources, I can guarantee that.

my xp VB uses exactly 97 mb of RAM when it loads. I have nothing, absolutely nothing on it, except office 2010, and then it takes just 110 mb. I still give the VB around 200 as a limit. It runs very smooth; too smooth even!

---

### Post by alaukikyo on 2010-11-21
> **beew said:**
> Many people who claim that openoffice doesn't cut it for them never give it a chance, they are just too used to MSO, peroid. Many people who say that must have MSO are using it for simple spreadsheets and words. It is a psychological rather than real need.

What really kils me is that I read quite a few people trying to install Office 2003 or even Office 9x in Wine because they want better compatibilty with MS formats.

Totally agree.
the same also goes for gimp and photoshop

---

### Post by 73ckn797 on 2010-11-21
> **beew said:**
> Have you tried open a docx file in Office97? I don't believe that Office97 is that compatible with Office 07 and 10.

I do not think this is the case. There have been no problems loading the documents being received. I also have Office XP but it is not loaded so I would not know if there are problems with docx files. I probably will install Office XP and replace 97. OXP will run in Wine perfectly.

I may eventually reload Windows XP in Virtualbox on both desktop systems.

I personally use OO for all of my business documents. Being self-employed I only need OOWriter and Calc and they do a great job.

---

### Post by randumnumber on 2010-11-21
I need Excel and Word for school, I have had to goto the library in the past I'm going to try this tonight and see if i can get it to work on my laptop....Horrah

---

### Post by marl30 on 2010-11-21
> **randumnumber said:**
> I need Excel and Word for school, I have had to goto the library in the past I'm going to try this tonight and see if i can get it to work on my laptop....Horrah

If you only need those two, they work perfectly under Wine. It's just Access that won't run on Wine.

---

### Post by holiday on 2010-11-21
> **ubuntuman001 said:**
> In my opinion, Wine obsoletes VB...why run an entire OS in a virtual machine just to run one program, when you can use Wine, just a compatibility layer, to do the same thing.  It uses less resources, I can guarantee that.

Good point. 

I had trouble getting EA to run in Wine, and just went looking for something to prove my point, but instead I found an article on how to install EA into Wine. 

I'll give it a try.

---

### Post by Shining Arcanine on 2010-11-21
> **marl30 said:**
> If Openoffice was so far off from being close to Ms Office, Ms would not have seen the need to put out a recent Office 2010 ad that specifically targeted Openoffice, which encouraged people to choose Office 2010 over OOO.

The difference between Open Office and Microsoft Office is the difference between manual tools and power tools. You can do things manual tools, but you can never do them as quickly as you could with power tools. Talking about how you can do the same things is beside the point because the concern is not about the ability to do the same things but the ability to do them faster.

Try not to read too much from Microsoft's advertising. It rarely reflects reality.

---

### Post by beew on 2010-11-21
> **Shining Arcanine said:**
> The difference between Open Office and Microsoft Office is the difference between manual tools and power tools. You can do things manual tools, but you can never do them as quickly as you could with power tools. Talking about how you can do the same things is beside the point because the concern is not about the ability to do the same things but the ability to do them faster.

Try not to read too much from Microsoft's advertising. It rarely reflects reality.


Good analogy. I know this guy who built a canoe with scrapped wood, table cloths and other discarded material using hand tools. The product was impressive, he hitched it to his bicycle, took it down to the lake and went for hours of canoeing through out the summer.

I also knew a yuppie guy who was interested in building a canoe so I introduced them to each other. The yuppie guy told my other friend that he had a workshop in his house with all the power tools and he was looking for the right tools and material. He estimated the project would cost him about $3000 to $4000.He asked the other guy how much did it cost him to build his. The other guy thought for a moment and said, probably around 80 bucks.

The expression on my yuppie friend's face was priceless.

---

### Post by forrestcupp on 2010-11-21
> **ubuntuman001 said:**
> 
It is as simple as installing wine through the repos, putting the MS Office install CD in the CD tray, going to the setup.exe file in the CD, and opening it with wine.Will that work with 2010?  The last time I checked into installing 2007 with wine, it was possible, but it was a major pain in the butt.  It took more tweaking than just installing it like you described.  It worked well with pre-2007 versions, though.

> **beew said:**
> Many people who claim that openoffice doesn't cut it for them never give it a chance, they are just too used to MSO, peroid.
Some people are used to MSO, they already own it, and they don't see the need to learn something new.  Also, we could come up with a very long list of reasons that OOo doesn't measure up to MS Office.  There are plenty of threads on here that do just that.  I agree that OOo is suitable for most stuff, but some people really need MSO instead of OOo.

---

### Post by beew on 2010-11-21
> **forrestcupp said:**
> 

Some people are used to MSO, they already own it, and they don't see the need to learn something new.  Also, we could come up with a very long list of reasons that OOo doesn't measure up to MS Office.  There are plenty of threads on here that do just that.  I agree that OOo is suitable for most stuff, but some people really need MSO instead of OOo.


I don't disagree that some people do need MSO's power features, all I was saying was that many people who claim that they must have MSO because OO doesn't measure up never need those features. They don't even know how to use these features,--or even know about them! I know tons of people like that.Try telling some secretary about EXCEL macros. They are simply parroting what they are told.

---

### Post by KiwiNZ on 2010-11-21
> **beew said:**
> I don't disagree that some people do need MSO's power features, all I was saying was that many people who claim that they must have MSO because OO doesn't measure up never need those features. They don't even know how to use these features,--or even know about them! I know tons of people like that.Try telling some secretary about EXCEL macros. They are simply parroting what they are told.

It is _very_ important for secretaries or Executive assistants to MS Office as they are usually handling documents hourly from internal and external sources that have a 99% probability of being MS Office in origin. And a great many of the E.As  and Secretaries I have hired and who have been my E.A's and Secretaries have been very highly skilled in the advanced features of MS Office including Macros, VB etc.

---

### Post by weasel fierce on 2010-11-22
> **KiwiNZ said:**
> It is _very_ important for secretaries or Executive assistants to MS Office as they are usually handling documents hourly from internal and external sources that have a 99% probability of being MS Office in origin. And a great many of the E.As  and Secretaries I have hired and who have been my E.A's and Secretaries have been very highly skilled in the advanced features of MS Office including Macros, VB etc.

I dont disagree but I don't think they are the "average user" that's being discussed in the thread.

---

### Post by Evil-Ernie on 2010-11-22
I feel really dirty for saying this but I am going to admit that I love Excel, it is one thing the MS got completely right and nothing gets even close to it.
 
It is simply the most useful office tool out there, Ive used it to create visual maps with a pan and zoom tool using VBA and Forms and created whole databases with it. 
 
The rest of the MS Office suite of progams can easily be replaced by open source alternatives but Excel is the only one that is irreplaceable.
 
I admire Calc and what its trying to do and I do use it on my Ubuntu machines but put it next to Excel and it is blown away.

---

### Post by HermanAB on 2010-11-22
Howdy,

You should try Gnumeric.  It is almost better than Excel.

---

### Post by Evil-Ernie on 2010-11-22
Gnumeric is good and and accurate, I would say if you are looking for a 'traditional' spreadsheet program then it could fit the bill, but still Excel has got VBA and nice wizards for the less technical users.

---

### Post by 73ckn797 on 2010-11-22
The way Open Office is described in Synaptic creates the impression of being a fully functional replacement for MS Office but, the word "near" seems to be missed. That tells me that it knows it has limits to being exactly like MS Office.
 [HTML]OpenOffice.org is a full-featured office productivity suite that provides a near drop-in replacement for Microsoft(R) Office.[/HTML]

---

### Post by forrestcupp on 2010-11-22
> **beew said:**
> I don't disagree that some people do need MSO's power features, all I was saying was that many people who claim that they must have MSO because OO doesn't measure up never need those features. They don't even know how to use these features,--or even know about them! I know tons of people like that.Try telling some secretary about EXCEL macros. They are simply parroting what they are told.

I agree that the average user could get along just fine with OOo.  But realistically, there are even some average users that *could* get along with OOo, but they are familiar with the MSO interface and they don't want to learn a new interface.  

My grandma is one person like that.  Trying to get her to even learn copy/paste is like pulling teeth.  Somehow she learned to use Word and Powerpoint.  There's no way in the world I'm going to throw OOo on her computer and go through weeks of torment trying to get it through her head that they basically work exactly the same but the interface is just slightly different.

---

### Post by fcomstoc on 2010-11-22
Hey there everyone 
I am a college student, so i have to use some office products, I have switched to using oo products for most stuff but i cannot get access to work in wine or any other product by that matter, I have to have access for a class, I am currently running ubuntu 10.10, I have every version of office, and I was interested to find out if anyone has had any luck with getting access to work
thanks

---

### Post by wilee-nilee on 2010-11-22
> **Evil-Ernie said:**
> I feel really dirty for saying this but I am going to admit that I love Excel, it is one thing the MS got completely right and nothing gets even close to it.
 
It is simply the most useful office tool out there, Ive used it to create visual maps with a pan and zoom tool using VBA and Forms and created whole databases with it. 
 
The rest of the MS Office suite of progams can easily be replaced by open source alternatives but Excel is the only one that is irreplaceable.
 
I admire Calc and what its trying to do and I do use it on my Ubuntu machines but put it next to Excel and it is blown away.

Use the theremin on the guitar man get to the stream of consciousness you wont feel dirty there.;)

---

### Post by forrestcupp on 2010-11-22
> **fcomstoc said:**
> Hey there everyone 
I am a college student, so i have to use some office products, I have switched to using oo products for most stuff but i cannot get access to work in wine or any other product by that matter, I have to have access for a class, I am currently running ubuntu 10.10, I have every version of office, and I was interested to find out if anyone has had any luck with getting access to work
thanks

I think Access is the main thing that will not work no matter what.  You'll probably either have to dual boot or run it in a Windows virtual machine.

---

### Post by Dargo101 on 2010-12-26
The office install seems to work, but when I try to use any of the office products, every one of them fails to even start.  Nothing happens at all.  All products (word, etc.) are listed in the applications/wine drop down menu, but all of them refuse to start.  I have even tried locating the files, right-clicking, and selecting to run with wine, but to no avail.  All of the posts that I have read indicate that it is so easy, the office products just work via wine.  Unfortunately, this is not true.  In fact, I can't get a single windows application to work via wine.  I have tried the wine that is installed via the ubuntu application installer, and I have tried downloading a new version of wine, but nothing works.  What could be wrong?  I installed Ubuntu 10.10, but it says that it is 11.4 maverik maven, or some such name.  I don't know how this can be, since april 2011 is still months away.  I am currently writing this from a cursed windows machine, since I have work that must be done for my job.  If I could get this stuff working, perhaps I could break away from windows, finally.  Any help would be greatly appreciated.

---

### Post by Spr0k3t on 2010-12-26
Dargo101, it sounds like you have a different problem.  Try running 'wine notepad' from a terminal and see if you get any errors.  If you do, create a new thread in the WINE forum to hammer out the issues.

---

### Post by jshepherd on 2010-12-26
> **HermanAB said:**
> Hmm, it depends. If you only produce new documents, then OOo is in many ways better than MS Office.  Problems arise when you are working in a collaborative environment and need to edit documents that were created in MS Office.  In that case OOo is not a good solution.

Couldn't agree more. I use OOo to produce documents but have to save them as .doc files for others at work to see. Almost all work produced documents open poorly in OOo though. In fact my employer has just started an Office 2010 partner program in which all employees are encouraged to download MS Office 2010 at a hugely reduced price. And I mean HUGE reduction. As for Calc, I've said on these forums before, is way short of Excel.
To be honest I dual boot Windows 7 just to use Office 2007. Well that and video conversion which is again much easier in Windows.

---

### Post by cap10Ibraim on 2010-12-26
isn't there a way to port Microsoft Office Mac to Linux ?

---

### Post by jerenept on 2010-12-26
> **cap10Ibraim said:**
> isn't there a way to port Microsoft Office Mac to Linux ?

Nope. sorry.

---

### Post by IWantFroyo on 2010-12-26
MS Office and Open Office depend on your needs.
Open Office is much faster
Can open both OO and MS formats
Can be modified to use .docx

MS Office has so much graphic decoration that it slows it down.
You don't have to modify it to use .docx (obviously)
IT LOOKS PRETTY!!!

---

### Post by jerenept on 2010-12-26
> **IWantFroyo said:**
> MS Office and Open Office depend on your needs.
Open Office is much faster
Can open both OO and MS formats
Can be modified to use .docx

MS Office has so much graphic decoration that it slows it down.
You don't have to modify it to use .docx (obviously)
IT LOOKS PRETTY!!!

I don't understand...... I have OpenOffice 3.2 and 3.3 and they can both open and save in Office Open XML (.docx etc)

In my experience, MS Office is fast, and efficeient with the Ribbon UI. (It can also open OpenDocument (.odt files))

---

### Post by IWantFroyo on 2010-12-26
In my experience, MS Office tends to be slow. My OO 3.2 works faster than any other office I've used, opening MS Office on others' computers just seems laaaaggggyyyyy
What I mean about modifying OO is that I can't save in .docx
It can be annoying...
*Warning, personal opinions contained*

---

### Post by majikins on 2010-12-31
This howto for Office 2007 worked perfectly for me [http://www.mikesouthby.co.uk/2009/11/ubuntu-9-10-installing-microsoft-office-2007](http://www.mikesouthby.co.uk/2009/11/ubuntu-9-10-installing-microsoft-office-2007)

kudos

---


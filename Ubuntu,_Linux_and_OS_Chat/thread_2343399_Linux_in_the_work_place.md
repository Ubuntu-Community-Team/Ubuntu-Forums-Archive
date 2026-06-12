---
title: "Linux in the work place"
date: 2016-11-15
forum: Ubuntu, Linux and OS Chat
---

### Post by tazz4vr on 2016-11-15
I work for a company that deals with multiple clients, which means we also deal with extensive data sheets, line items can range from 20 to well over 100,000.  I have used a Linux desktop environment for many years, with very little issue.  Work wise however we use Windows based programs and the functionality of these programs.. well, moss grows faster.  Could someone please direct me to information on using Linux for the workplace?  I would like to read up on it and then if I believe it will benefit the company, which I am sure it will, present the information to management.

Thank you.

---

### Post by QIII on 2016-11-15
Not a support request.

Moved to Ubuntu, Linux and OS Chat.

---

### Post by tazz4vr on 2016-11-15
Thank you.

---

### Post by Bucky Ball on 2016-11-16
What would be convincing is if you could demonstrate how you can do what you are doing in Windows on a Ubuntu box. This would mean hunting down Linux alternatives to the Win programs your office is now using. That may be easy in some case, not so in others. There is always the possibility of have a Win box or two around for those essential but non-negotiable Win apps, but if they know the majority of the tools and apps required are available, reliable and stable, what's not to like?

If you can demonstrate that your workflow is as efficient or better on Ubuntu box you'd be halfway there. I'd go for that stuff first before trying to convince them with 'the wonders of Linux and open-source' or anything like that (best NOT to come across as a crazed Linux zealot!). :)

Linux could save them a lot of money over the years by not having to licence Windows for an office environment (an enterprise license or some such? don't remember much 'Windows' stuff now ...). It would be remiss of you, though, if you did not mention that all office hardware would need to be researched thoroughly before purchase to make sure it will work with Linux; printers, scanners, overhead projectors, etc.

There are some very Linux friendly manufacturers around now, though, so I tend to buy the same brands pretty much exclusively.

---

### Post by mastablasta on 2016-11-16
> **tazz4vr said:**
> I work for a company that deals with multiple clients, which means we also deal with extensive data sheets....

if you are exchanging data excel then you are likely stuck with MS office. 

if you have some other data processing (e.g. ERP) then you have more options. if you deal with databases then there are plenty in linux that can handle form small nimble and fast databases to large corporation size ones.

depending on data exchange you might also look into EDI methods and standards. ofter many things can actually be automated. then processed on server and in the end you autmatically get the output you need.

---

### Post by SeijiSensei on 2016-11-16
> **mastablasta said:**
> if you are exchanging data excel then you are likely stuck with MS office.

Not necessarily.  Both OpenOffice and LibreOffice read and write .xlsx files.  However they do not support files with Excel macros.  For pure data exchange, .csv is the best choice since everything supports that.  OO and LO also do not produce identical looking documents when compared to their MS cousins because of proprietary features in MS Office.  That matters more for written documents than spreadsheets, of course.

Along with the inventorying of applications and devices discussed above, I'll toss out another potential roadblock -- retraining your staff.  If you want to try Linux in the workplace, I'd start with a single, small department staffed with competent and flexible people willing to participate in the experiment.  

Another important question is whether you use services like Active Directory to manage your organization's network.  That enables administrators to manage all the computers on the network from a central location.  If you're on an AD-based network now, transitioning to Linux would be much more difficult.  The same advice applies if you're using Exchange for messaging or Microsoft SQL Server for databases.  It's not just the desktops that matter, but the entire network infrastructure.

---

### Post by tazz4vr on 2016-11-16
My idea was to introduce the possibility of something better than Windows to the company and use a staff of approximately 3 - 5 people, initially.  However, we do use Excel Macros and from what I have read, it sounds like this will not be a possibility for us at this time.  However as I am not that computer inclined when it comes to the back-end of processes, I can't say that it wouldn't work.  Is there some form of written information that I can get a copy of that details what Linux can do for a company?

---

### Post by Bucky Ball on 2016-11-16
> **tazz4vr said:**
> However as I am not that computer inclined when it comes to the back-end of processes, I can't say that it wouldn't work.

This is something else I was going to mention in my first post but didn't: whose going to oversee this nest of Linux boxes when something goes wrong or something needs to be changed or tweaked? There are times when you're probably going to need to go 'under the hood'. You will having a staff of 3-5 people, presumably with Linux boxes. Are you confident you can administer these boxes and get the users up to speed with an entirely new OS?

Judging by your level of expertise (no offence intended, but if you can't find information about this without help:

> Is there some form of written information that I can get a copy of that details what Linux can do for a company?  

... not sure how you're going to go if one of the machines won't boot. Not trying to offend, just trying to be realistic. You know what they say, time is money, and that's possibly what your boss will say when you tell them how long it might take to 'transition' and get back up to speed again.

What happens if things go pear-shaped and you tell the boss all work will have to cease until you get a reply back on the forums that will hopefully fix the issue? A reply that might not come for 48 hours or ever?

What Linux can do for a business depends on the needs of the business. Maybe sit down with a pen, paper and beverage (and maybe your boss or not) and make a comprehensive list and notes of *exactly* what you are going to need these boxes to do (try not to leave anything out) then post the gist of it here. We can't give you much help about 'what Linux can do for your business' if we have no idea of your business or what it needs an OS to do apart from Excel macros.

There are quite a few 'alternatives for Win program' sites you might want to dig up that give examples of to Win programs.  

Just further food for thought. Not intended to dissuade. Good luck with it. :)

---

### Post by tazz4vr on 2016-11-17
Absolutely no offense taken.  The company has an IT department that handles such tasks as problems, resolving, tweaking, etc... what I am trying to do is search for the possibility that there is something much better than the programs we use now.  Currently the programs we use can take any where from 30 minutes to several hours just to run prior to the work being created.  Once the work is created, there is usually additional time consuming tasks that are repetitive.  The great thing about my company is that they are very open to suggestions and would not hesitate to look into something that would help make the company more efficient.  What I don't know is enough about Linux based systems to approach them, that's why I have asked for help.  I have done a few searches such as, 'Linux in the workplace', 'Intro to Linux', etc... and so far I am directed to forums.

---

### Post by Bucky Ball on 2016-11-17
Try hitting us with some of the tasks you are going to need to do in the office and we could perhaps see if anything fits.

Note: many open-source apps are cross-platform, meaning they can run in both Linux, Win and sometimes Mac. Something like Libreoffice, for instance, you can install in Win right now and try out. It will work pretty similar in Ubuntu but the interface may look slightly different. Not being sure what you need, not sure what else to suggest, but keep the cross-platform thing in mind. You might be able to do a fair bit of research on the apps themselves before you even install Ubuntu or another Linux distro. ;)

---

### Post by mastablasta on 2016-11-17
it really does depend on what you intend to do or what you need it to do. Linux or Ubuntu is just an OS. it can run many apps but not all. if you need to run Excel then it's better to stay on windows. if you could actually pull that data and process it in another app (maybe een more effieiently) then perhaps linux could do that. it really depends what you are doing.

for example - we deal with quite a lot of data and cusotmers. but we use ERP for that. sure there is still manual tasks where excel is used to inpiut the data. but even that is being moved either to EDI method, or a web app. plent yo her tasks moved to server apps as well. those are system agnostic and only need a browser. 

i still use excel for data analysis, word i rarely use, but we do have some forms in it and store some basic customer data in a presentable format in it. but that's about it. all this could easilly be done in libre office. but with office 365 it is much more convenient to do it in office since it has more apps connected.

of MS apps we also use exchange for emails, the use AD for administering computers (arround 5 or 6  thousand of them across all contintents), MS Sharepoint for colaborative work and as an internal web portal, One drive for sharing data, common folders (ran on windows server)... now most of these have some form of linux alternative. not sure if all is connected as well as with MS and if you can actually get good support for those things and at the same price. support is probably fragmanted just as the OS. for example apache support good and fast, samba support bad and slow or something like that. 
owncloud for example is quite similar to one drive, but their andorid app is quite lame and you need to pay for it. 
we get office 365 on our mobile phones, so everyhting is rather connected. which to me is funny as i bet if someone stole my mobile they could easilly penetrate the whole company and take it down. nayway we get office andorid apps which enable us to do somewhat descent work while traveling. or at leats to reply to some crucial emails.

anyway as i understand we also use linux on servers. various web apps run on apache, then there is the ERP which i think also runs on SUSE or Redhat, backup servers... not sure what is running the company websites. it could be linux or windows server.

then there are 3rd party apps, closed source mostly. but we do have some opensoruce stuff on desktops installed. they are open totesting it and if it's good they install it. for example PFD maker, i have Gimp and Inkscape installed for preparing a bit nicer offers of rather mundane items.

When we still had XP there was serious talk and testing about desktop linux move. but now... well i guess MS improved a few products. went forward and i can't say i blame them for choosing to stick with MS. we never had Vista (AFAIK), we did have 7, some still do. while i was moved directly from xp to 8.1 like most of my colleagues. i think it would be very very hard for our IT to move to linux at the moment. MS effectivelly locked them in and i think costs would be too big to move.

---

### Post by tazz4vr on 2016-11-17
Thank you all very much for the feedback, I think the best thing for me to do at this point is bring it up to our IT department and find out what tools they use to run the programs, perhaps they will provide more insight as to something that would be similar to a Linux program.  I am definitely interested in learning more about it myself and will check out some of the apps already out there.  I currently use a desktop version on my home computer, but have never tried doing similar things done at work with it.  Basically once the words Bootstrap, CSS, LESS, etc.. come into play, for me, that's pretty much where I check out, not a clue how it works or its purpose.  However I am hoping to change that.

---

### Post by tazz4vr on 2016-11-17
Just a quick update.  I brought up the idea of Linux to the IT department, one of the developers will be looking into it and stated that it was a thought of his a while back however he did not know anyone familiar with it and pretty much let it go.  After much discussion, I will be sitting with him as he reviews the material that he finds and will possibly be one of 3 people who will get to do a trial run to test it's capabilities with what we would need it for.  :)

---

### Post by Bucky Ball on 2016-11-18
The ball is rolling. Well done and hope it all works out for the best, whatever that may be. :)

At least you have someone in IT dept. who is 'on your side' and your business is open to change. We've seen others approach their IT mob and it is more like approaching a brickwall, or worse (derogatory things to say about an OS they know little about, generally; the sort of stuff that is not allowed on these forums about ANY OS) so you're lucky! ;)

---

### Post by SeijiSensei on 2016-11-18
I'd start by working with the IT person on the infrastructure side.  How do you manage your network now?  Is it centrally-managed with something like Active Directory? Do you rely on Exchange or Sharepoint?  All of these proprietary Microsoft technologies will place obstacles into moving to Linux in a major way.  

mastablasta talks about moving applications to the cloud.  That can make sense for many organizations as long as you have good methods for maintaining local backups.  I wouldn't trust any cloud provider, even Microsoft, to hold the only copies of critical business data.  

Can you give us an example of some task that fits this description?

> Currently the programs we use can take any where from 30 minutes to several hours just to run prior to the work being created.

Not knowing what kind of business your firm is engaged in, it's hard to imagine what might take that long.  Maybe some high-tech manufacturing or genetic engineering?  If these are long computational processes that happen before something gets done, moving to Linux might not make all that much difference.  For that, faster hardware would be a better investment.  It might also mean rewriting the programs themselves.

However if your organization does have large computational needs, you might look into some of the "clustering" technologies that Linux offers like [Beowulf]("https://en.wikipedia.org/wiki/Beowulf_cluster") and its offspring.

---

### Post by tazz4vr on 2016-11-18
Yes, I am extremely happy that the suggestion is being considered.  So for now, I think I can close this thread, unfortunately I did not see the option via the Thread Tools, any idea how to close this thread?

---

### Post by wildmanne39 on 2016-11-18
You can not close threads but please use thread tools and mark the thread solved.
Thanks

---

### Post by tazz4vr on 2016-11-18
When using the Thread Tools menu in the upper right corner, there is no option for me to mark the thread as solved.

---

### Post by QIII on 2016-11-19
This is a chat sub-forum, so "Solved" is not an option.

---

### Post by Bucky Ball on 2016-11-19
... so leave as is and enjoy. :)

No doubt it will be closed in a spring clean some [s]decades[/s] time in the future. ;)

Sure we'd all be interested to hear how you go with this anyhow, even if it's in a month's time.

---

### Post by tazz4vr on 2016-11-20
Absolutely will provide an update as things progress.  So far the IT guy has a meeting on Monday after Turkeyday to request use of 3 computers for this idea.  I wish it were as simple as just taking them off desks and doing what he does, but he has to provide a bid of sorts to get permission.  I believe highly that authorization will be given, but still have to wait for the higher ups decision.  Ugh!  Patience is not my virtue!

---

### Post by Bucky Ball on 2016-11-20
> **tazz4vr said:**
> So far the IT guy has a meeting on Monday after Turkeyday to request use of 3 computers for this idea ... he has to provide a bid of sorts to get permission.

One of the reasons you are lucky to have one of the IT team onboard. Without them, this would probably still be in the 'pipedream' category. How long since you get this rolling? You got to this point pretty quick so your patience shouldn't be too worn ... yet. :)

---

### Post by tazz4vr on 2016-11-20
Once I brought up Linux and learned he was familiar with it already, it kind of took off on it's own.  It would have been nice to leave the office on Friday with a definite 'Yes' you can run a trial and have use of 3 puters, but that didn't happen.  At this point there is a meeting scheduled for the 28th to submit a proposal, this will be done on the IT side, nothing to do with me.  We are both hoping that the outcome will not take too long to determine and also that it goes in our favor.  However per IT guy, he was going to be doing some research this weekend to go along with his proposal/presentation next week, so I am meeting with him first thing in the morning to have a peek-see at what he found.

---

### Post by tazz4vr on 2016-12-06
Update... Update.

After 3 days of meetings, the IT guy and I received the okay to do a trial run using Linux.  Although we are not slated to start it until after the New Year, the fact that we got the okay is completely awesome.  So extremely excited for this opportunity with him, there is no doubt in my mind that I will be an IT geek-ette by the time we are done.

---

### Post by Bucky Ball on 2016-12-06
Great news and good luck with it. :)

---

### Post by Habitual on 2016-12-06
I'm inspired.
When I got to General Atomics, Aeronautical Systems, Inc.  in San Diego as a "temp",
they only had Win9x installed and using "shares". It was painful.

I was "Bench Support" for 200 Windows systems and The United States Air Force
and as long as my "work" got done, it didn't matter what I used. The other guys certainly were curious about "what I did 'after' work".
Certainly didn't need Windows to run ghost on a bootable CD (at that time was all we had, and PXE boot) since the re-imaging
required a reboot.

A year after introducing it to GA-ASI, I was offered a permanent position as a "Salaried Oracle DBA Admin".
When I asked the Air Force 'guy' why he wanted me to manage the environment for a $75 Million database, he said
"You fixed my Outlook on your first day here. Every one else said it could not be done."

Never regret small beginnings.

Nod to Bill Larkin and Budd, The Air Force 'guy'

---

### Post by tazz4vr on 2017-03-04
Well finally have an update on this... after a good attempt from the IT guru at work, it doesn't appear that what is available will work with what we need at work.  So for now, Linux in the work place has come to an end, well really more like a suspension for further review.  :(

The IT guru will do further research when he is able to and we will go from there.

---

### Post by kurt18947 on 2017-03-05
I started a new position the first of the year. I am not working in the core functions of the company but in more of an support function. I am set up with Outlook Web Access, the rest is .pdf, simple .xlsx and web forms. I have Windows available but so far haven't needed it.

---

### Post by Bucky Ball on 2017-03-05
> **tazz4vr said:**
> Well finally have an update on this... after a good attempt from the IT guru at work, it doesn't appear that what is available will work with what we need at work.  So for now, Linux in the work place has come to an end, well really more like a suspension for further review.  :(

The IT guru will do further research when he is able to and we will go from there.

Can't say you didn't have a 'red hot go' at it. Maybe some open-source apps have crept in somewhere along the chain in the process even if the whole shebang couldn't switch to Linux? 

Anyhow, good effort and you got lucky with the tech person. ;)

---


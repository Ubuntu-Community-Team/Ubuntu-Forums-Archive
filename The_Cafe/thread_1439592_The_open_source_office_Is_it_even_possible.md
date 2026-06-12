---
title: "The open source office: Is it even possible?"
date: 2010-03-26
forum: The Cafe
---

### Post by Vunutus on 2010-03-26
I'm the sysadmin for a small office (under 10 people). Wherever possible, I have tried my best to go with a Linux/open source solution. I'm finding this to be very difficult, however. Despite my best efforts, we still have no option but to use Windows for workstations and Microsoft Office.

Our main software system clients only run on Windows (heavily .NET so not much hope of Wine working). Before we selected it I did extensive research and there was absolutely no Linux alternative (although server side it just needs a MySQL database so our server is Linux). After this compromise, I tried to use OO.O to no avail. The software requires Word and Excel 2007 to generate the hundreds of letters we have it do every day. It's not a matter of OO.O not having the functionality (it does mail merge just fine), the software simply does not work unless MS Office is installed.

I was just curious if anyone around here has actually been able to go completely (or mostly) open source in their office? Even with such a small office, I couldn't do it. I imagine it only gets harder as the office gets bigger.

---

### Post by koenn on 2010-03-26
well, you've found why it's at the same time easy and hard to run en entire office on linux: 3th party apps that somehow depend on "something microsoft", be it .Net, Internet Explorer, MS Word Macros or some other VBA contraption, an MS Access runtime, or (in the really bad cases) the presence of an entire MS Office suite. 

So, it's hard, because there's usually no way you'll get those to run on Linux.
It's also easy because you know what it takes to fix it : get rid of that software. ((actually doing that might be less easy)

So you've also learned that next time you have to purchase or order software, you have better checked their system specs for requirements and silly dependencies like these.

---

### Post by Roasted on 2010-03-26
I work in IT support for a large school district. There are about 6 of us in the tech department, covering a decent amount of servers and about 1,800 workstations.

All of them are currently Windows, but all of the elementary schools are now running OpenOffice. We haven't had any issue, and plan to implement more of OpenOffice out there. I do however go into the OpenOffice settings and default the save type to Microsoft standards, just so there's no confusion when documents are passed in between each platform.

---

### Post by samalex on 2010-03-26
One suggestion is to get a Windows server and install your software using MySQL along with MS Office, then purchase 10 TS CAL's and 10 Office CAL's.  Your clients could then use Linux workstations and Terminal Services to connect into the app which could be setup to run seamlessly on Linux.  The reports output from your software could be saved to the local Linux workstations and Open Office could take over from there.

The Pro here is you're not out of the costs to maintain 10 Windows workstations, which would detail having to buy Windows 7, virus scanners, etc.  You could run Linux on older PC's as well, so you'd get longer live out of your hardware.

That's the beauty of terminal services is that there's really no reason not to run Linux on the desktop because a TS CAL from Microsoft is always cheaper then Windows 7 and the headache of maintaining a large number of Win workstations.

Just a thought -

Sam

---

### Post by prodigy_ on 2010-03-26
> **Vunutus said:**
> Our main software ... heavily .NET ... simply does not work unless MS Office is installed.
Conclusion: crapware.

---

### Post by madnessjack on 2010-03-26
Possible- yes, but for the love of all things, please don't :P

---

### Post by prshah on 2010-03-26
> **Vunutus said:**
> I was just curious if anyone around here has actually been able to go completely (or mostly) open source in their office? 

Well, it's working out just great for me. We are running a small office with less than 10 computers (8 to be exact) and running totally on opensource. Ubuntu / Openoffice / Tally (Accounting program) in Wine / GnuCash / Evolution / Korganizer. (OK Tally is not an opensource program but it works fine in Wine).

We also have our own mailserver and soon-to-be-public webserver.

It took a long while to release the shackles of Microsoft, but persistence (and transparent macro handling in office documents since OpenOffice 3.2) paid off.

btw, we do a lot of mail-merge operations to customize end-of-exhibition followup letters, special offers, etc, and we've never run into any problems.

In India, I'd estimate that more than 90% of the businesses run pirated and out-of-date (and consequently insecure) software. I'm happy not to be one of them.

Note that though our office is small, our business is not; in fact, we are within the top 10 companies in our field in India.

So I'd suggest you persevere. However, even that advice is valid only upto a point; there is no sense in trying to force an idealogy; use that which works for you from all angles: convenience, financial and realistic.

---

### Post by phrostbyte on 2010-03-26
It's much easier for new businesses. It looks like you are already locked-in hard to Windows.

One thing you could try is perhaps this software only requires 1 machine to do it's thing, you could convert the rest of the office to Linux.

If that wouldn't work, you could try virtualization. It's not really getting off of Windows but it's a step in that direction.

---

### Post by Vunutus on 2010-03-26
> **koenn said:**
> So you've also learned that next time you have to purchase or order software, you have better checked their system specs for requirements and silly dependencies like these.

Unfortunately whether or not it supported OO.O could not have made an impact on my decision. This company's startup was funded out-of-pocket by the two owners (who aren't particularly wealthy). The software is industry-specific. It ran us about $2000 for all machines, the next lowest priced package was about $12,000 (and even it would not have been Linux friendly).

---

### Post by beniwtv on 2010-03-26
Yes, it is possible...

...if you have time to investigate the best solution and are ready to change how certains 'things' work/are done. It's not going to be the same as with Windows.

We do use Linux in our office. Not only Linux, because after all we need to test our products in Windows too. But mostly all is done on Linux. However, it needs time to first set it all up, just like if you would set it up on Windows from scratch without knowing. After that, you can get a new office running in what it takes to install your computer hardware and firing it all up.

And for those that wonder how we interact with customers: By using document formats that are compatible and free. Hint: They are not formats from Microsoft.

Cheers,

---

### Post by koenn on 2010-03-26
> **Vunutus said:**
> Unfortunately whether or not it supported OO.O could not have made an impact on my decision. This company's startup was funded out-of-pocket by the two owners (who aren't particularly wealthy). The software is industry-specific. It ran us about $2000 for all machines, the next lowest priced package was about $12,000 (and even it would not have been Linux friendly).

Been there, etc. Where do you think i got those examples of ways in which software can depend on MS stuff ? 

Just saying, if you're buying Windows programs, or software that depends on Windows programs, you're going to be running Windows. 
Nothing wrong with that, if it's a conscious decision.

---

### Post by qalimas on 2010-03-27
I'm a manager at an IT Firm.  I've been on board about a year there now, and when I got on it was ALL Microsoft.

In a year I've managed to get us off of a domain, get rid of Microsoft Office (OOo and Symphony), get rid of Exchange and Outlook (Zimbra), and change all but a couple machines to Fedora.  All servers are now Linux and virtualized using vbox-ose.

The only thing we use that we can't get an open source alternitive to is viruses/malware.  We use a commercial AV for Linux.  (We need to be able to fix Windows machines for customers).


I do believe it is possible, but at the same time, it may not be the best.  There exists a perfect harmony between FOSS and Commercial Software, you just have to find it.

Edit
Forgot to add: Although some of the software we used could only be run on Windows, it was only a database program.  I managed to learn Ruby on Rails and make a better web application than the existing solution they had.

So if you can't get the software, write it :D

---


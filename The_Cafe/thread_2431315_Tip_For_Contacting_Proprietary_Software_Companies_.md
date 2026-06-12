---
title: "Tip For Contacting Proprietary Software Companies Sitting on Abandonware?"
date: 2019-11-14
forum: The Cafe
---

### Post by jetsam on 2019-11-14
Has anyone ever tried to get a company to release source code and open the license for an old abandoned project?

Here's two recently "abandoned" code bases that would be huge gains for OSS if we could get our hands on them:
[Picasa 3 (Google, natch...)]("https://support.google.com/picasa/?hl=en#topic=6247492")  You can still download Picasa, but it's some obscure cloud drive link and seems dodgy, but it works.

and

[Micro-Cap 12 (Spectrum software)]("http://www.spectrum-soft.com/index.shtm")  Site has a download link.  This is quality software.

How should I write them an email were I to do that?  I don't know any of them personally, but enjoy using both programs.

---

### Post by TheFu on 2019-11-15
Releasing software that was once proprietary under some approved F/LOSS license isn't free.  You'll need to find someone to champion the idea of wasting $20K in developer and legal time to make it happen. 

The company may not have the source code any more.  Dead projects aren't usually retained.
Or they were written in languages that don't exist.
Or they were written in languages that have changed in the last 10 yrs, using proprietary compilers that aren't available anymore.
Or some parts of the internal code has been morphed into some new, patented, solution.
Or the software has dependencies on 3rd party tools which are proprietary, so giving access to just their code will be worthless.

In short, unless the CEO of the company has some personal love of F/LOSS, it won't be released.

The idea that a company can just take the code and throw it onto GitLab just isn't realistic.

I worked on some cross-platform code that was built for the govt.  That means it couldn't have any patents and the rules about copyright were a little different.  It was fairly general purpose, so not under any ITAR restrictions.  Think - Adobe Acrobat, but 10x faster with layered annotations on a per-user basis that could be shared or not with a publish/subscribe methodology.  But that applied only to the code we wrote.  Underneath it, were 2 proprietary tools:
* file-based DBMS -  $$$ per developer license per platform
* cross-platform code, builder, and Look-and-feel system - $$$$$ per developer license, per platform.

Anyways, you can probably find the code on the govt website where all their non-classified tools get released, but without that DBMS and the cross-platform development tool, it will be worthless.

Worked at a different company which wanted to take their Windows-only software into the world of cross-platform software. Mainly, they needed to run on Unix back-end servers.  Through other work, they'd gained expertise with a terrible, but expensive, cross-platform development tool. It was a hack and not elegant, but was still $$$$ per developer per platform license.  They used the RogueWave libraries too, which was also licensed per developer per platform.  When I left the company in 1999, they'd almost finished ripping out Rogue Wave and switched to the new-fangled STL.  The STL basically killed an entire industry, which was fine with me.
The cross-platform GUI tool was still integral to the software.
And we used a 3rd party network license manager too which ensured only the number of licenses purchased could be run. "Western" company begged for that ability.  Asian companies were less happy.
At that company, I'd worked on a F/LOSS project related to a DBMS driver manager.  The original programmer said it was "public licensed", meaning it could be used anyway we wanted, but at the time, that sort of license wasn't working in the courts.  He gave the software to the GNU foundation and RMS said it was GPL licensed, which effectively broke the software at about 20 companies. That specific software needed to be LGPL to be useful for anyone.  We all wrote emails to RMS with reasons why LGPL was needed, but didn't hear anything back for months.  One of the companies which was much more depended on the software than others, decided their company couldn't wait and re-implemented the software, releasing their version under the MIT or BSD license (I vaguely recall).  [https://en.wikipedia.org/wiki/Open_Database_Connectivity#Release_and_continued_development](https://en.wikipedia.org/wiki/Open_Database_Connectivity#Release_and_continued_development) A few months after that happened, RMS decided the LGPL was necessary, but we'd all moved to working on the newer uDBC code with a company behind it.  I contributed a tiny bit of code to handle locating the DB connection and driver configuration file using the expected Unix hierarchy - environment variable, userid HOME directory, then system directory.

Anyways, it ain't easy.

---

### Post by jetsam on 2019-11-15
Darn.  I was really hoping Micro-Cap could be liberated, but it has a 20 or 30 year development history all the way back to the DOS days.  The code base must be extremely complex with many many authors of the code.

Thanks for your reply.

Edited to add:  OMG.  I think I use an OBDC driver in our database config...  It works OK, but it feels pretty "non Windows" when you're setting it up.  It helps translate between an Access database and a Filemaker one, and gets active use every time someone does an import to translate the database between one format and the other.  I doubt the one I use is open source, though, but I'll have to check.

Cheers,
...jetsam

---

### Post by TheFu on 2019-11-15
MS-Access is slow and should never be allowed to connect to any enterprise DB.  

One place I worked, we had to block 99% of ODBC connections from 6000 end-users because they were using too many resources just to have a spreadsheet-like view of the data.  It was bringing a $2M server to it's knees.  We ended up showing them how to run queries, usually just 5 sec of clock time, that dumped the data they needed into CSV files, which they could import into either Access or Excel as they liked. The DB server was much happier after that change.  The users didn't like it, but any change is usually an issue for end users. "Too many steps" was the most common complaint because they had to learn to use sftp too.

---

### Post by jetsam on 2019-11-15
Yeah...  I'd like to ditch Access, but my resources are pretty limited.  My problem is that it's too much work to debug a development project that's really going to serve maybe two people.

Filemaker is acceptable to work with, but it's still too much work to make it a daily client solution for us.  We use a proprietary but free database that allows us to process sales and acts as middle-ware between external eCommerce sights for us.  It's inventory tracking, and our inventory is stupidly complex for it's low monetary value.  Each item is unique... it's books, and they all have minor flaws that must be identified and described, then advertised as such to the punters via bookselling sites.

It's a gig, but not a living...  :rolleyes:

New Windows 10 upgrade hopefully won't cause too much pain.  We use much too much old and unsupported software and have to run it in legacy mode.

---

### Post by mörgæs on 2019-11-17
Though there might be problems getting the source code released it's a good idea and I hope you will proceed. 

Try to get personal face to face (or at least phone) contacts rather than e-mail. The latter is easier to turn down.

---


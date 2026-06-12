---
title: "Ubuntu 8.04 Server feasibility"
date: 2009-06-13
forum: Server Platforms
---

### Post by jd8001 on 2009-06-13
All,
    I work for a small business in a sort of "Do it all" role (IT, Operations, etc). Anyway we're about to install a file/print server to service several windows XP machines. I've been trying to setup a test server on my laptop running a partition with ubuntu server 8.04. I've got SAMBA sharing files, and I don't think I'll have problems sharing printers. We have a piece of software called Taxworks that runs a SQL database server on one of the computers on the network. First, is it possible to move the SQL server to the ubnuntu box with MYSQL? I apologize for the generality of that question, but my ignorance on the topic precludes me from providing more information. Is there a book (Not wikipedia) that I can reference? Lastly, how should I go about sharing outlook calendars, contacts, and tasks? Am I genuinely screwed or is possible to do this w/o going to Microsoft Small Business Server? Any help is greatly appreciated,


-JD

---

### Post by quixote on 2009-06-15
If I were you I wouldn't dream of moving any program with "Tax" in the name from one database program to another without doing a complete dry run and test in some kind of non-production setup.  MySQL has documentation, but I understand it's over 1500 pages printed out, so I'm not sure life isn't too short for that.  Somewhere in there might be something about importing from SQL.

As for sharing contacts and all the rest, Evolution is supposed to be the Linux-side answer to Outlook.  I don't know how seamlessly it would work for people.  Again, I'd say let people try it before any actual switch over.

Make sure your coworkers -- and your boss! -- are really motivated by the advantages of open source and free, so that they're willing to put up with the learning curve of any new software, free or not.  

I realize this isn't a lot of help, except that I'm saying "Be careful!"

---

### Post by gtdaqua on 2009-06-15
I agree with post #2. Linking databases BY YOURSELF could be very complex. But of course, you could ask the vendor if they would support MySQL as the backend instead of MS-SQL. Most vendors do, and I assume this is not a complex job for the people who program these all these stuff.

You could use [Zimbra]("http://www.zimbra.com/") to share email contacts. Its a Collaboration Suite. Thunderbird would come in handy as an email client for Linux users. The Zimbra Desktop (an email client) is out for both Windows and Linux users, a perfect alternate to Outlook and its simply superb in sharing and collaboration.

---

### Post by jd8001 on 2009-06-15
All
Yea after spending a day setting up a test server on my laptop, I've decided to go with a microsoft solution. The bottom line is most people in the office are technologically illiterate and have consequently made poor technogy decisions. In order to accomadate those decisions a ms small business server is really the only option. I was really hoping to go Linux for several reasons namely monatary and hardware savings. It's so much lighter that we could save $500 or more on hardware and not buying small business would save another $500+. I'm just so excited about the obligatory reboots slow start ups and virus software

---

### Post by quixote on 2009-06-15
Zimbra!  Of course.  Why didn't I remember that?  (I haven't used it myself, is probably why.)

jd8001: yeah, spending bags of money to get less is always so satisfying.  Not.  In any case, good for you for thinking of doing something about it.  Even if going with M$ is a good idea for now, that doesn't mean you have to give up.  Get something like Zimbra going on a couple of computers and just keep showing people how much more they could be getting for less money (i.e. your time, which they're paying for anyway).  Get or keep Apache for the servers.  Mention how much the M$ server software costs, and how much less stable and more virus-prone it is.

May the Force be with you! :D

---


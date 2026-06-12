---
title: "Windows Question - Best Free Backup Software?"
date: 2009-03-09
forum: The Cafe
---

### Post by Roasted on 2009-03-09
At work, we have several hundred computers. In fact, we have almost 2,000 programs.

For those with laptops (about 800 or so) they often take them home, so synchronizing documents is a must, whereas the desktops have their my documents folder directly routed to their share on the server.

Up until now, we've been using SyncToy, but teachers don't like to open it and hit the run button. We've been trying to find a free alternative that automatically does the job.

I came across Syncback V3, the freeware edition. But there's 1 minor issue with this, despite it being completely awesome and exactly what I need. In order for this to work, the user's password must be put into Syncback for authentication purposes.

The problem? Every 3 months, passwords change for all users. That's a lot of passwords to change for your synchronization tool to work.

I'm looking for something that'll automatically transfer documents from point A to point B with no password issues, and... is also free. :) :)

Any ideas? Or am I stuck with passwords no matter what free program I find?

---

### Post by frrobert on 2009-03-09
I have not worked on a Windows server for about 3 years so I am rusty.  You did not mention what server you are on but I am assuming this is a Windows 2003 server with windows clients.

Is there a reason that you can not use folder redirection with Redirected Folders automatically made available offline,, by default is is turned off.

here is a technet article about it

[http://technet.microsoft.com/en-us/library/cc778976.aspx](http://technet.microsoft.com/en-us/library/cc778976.aspx)

If that is not what you need, could you just create a script that runs at login that compares the files in the 2 locations and copies the changed files.

Hope this helps

---

### Post by bashveank on 2009-03-09
You could write a batch script to run SyncToy automatically.

 -R runs SyncToy headless, so just put that on a scheduled programs list.

---

### Post by albandy on 2009-03-09
Amanda, works with windows, linux, and others:

[http://www.amanda.org/](http://www.amanda.org/)

---

### Post by mips on 2009-03-09
[http://www.techsupportalert.com/best-free-backup-program](http://www.techsupportalert.com/best-free-backup-program)
[http://www.techsupportalert.com/best-free-folder-synchronization-utility.htm](http://www.techsupportalert.com/best-free-folder-synchronization-utility.htm)

Bookmark that site, it really is brilliant with good freeware recommendations.

---

### Post by Roasted on 2009-03-09
> **frrobert said:**
> I have not worked on a Windows server for about 3 years so I am rusty.  You did not mention what server you are on but I am assuming this is a Windows 2003 server with windows clients.

Is there a reason that you can not use folder redirection with Redirected Folders automatically made available offline,, by default is is turned off.



Yeah... unfortunately we have a Windows environment with Server 03 + 2k Pro/XP Pro machines.

We've tried the offline files thing within Windows. I don't mean to be all negative, but to say it sucks is an understatement. 

We moved to SyncToy which performs much better, but we're finding that some teachers aren't backing up at all despite the ease of use it has.

If I could just get SyncToy, but automated, that'd work nicely. And I thought about a batch script and even tried it as a test on my laptop, but I couldn't get it working. I figured I'd invest time in finding a free program since I also want to find a free program of this nature for home use on my own LAN as well. So it's a combination of what I want + what I could use at the district. 

I'll check out these links. Thanks!

---

### Post by mips on 2009-03-09
SuperSync can do commandline unattended syncs.

Two more references I came  across.
[http://www.filetransit.com/freeware.php?name=File_Synchronization](http://www.filetransit.com/freeware.php?name=File_Synchronization)
[http://www.all-freeware.com/browse/freeware/folder-synchronization.html](http://www.all-freeware.com/browse/freeware/folder-synchronization.html)

---

### Post by blueturtl on 2009-03-09
Try [Cobian Backup]("http://www.educ.umu.se/~cobian/cobianbackup.htm").

It can be run with user privileges as well as a service, so it should do well in your case. As an added bonus, it's open-source.

---

### Post by Roasted on 2009-03-09
> **blueturtl said:**
> Try [Cobian Backup]("http://www.educ.umu.se/~cobian/cobianbackup.htm").

It can be run with user privileges as well as a service, so it should do well in your case. As an added bonus, it's open-source.

Codian looks really attractive, but the thing I was REALLY hoping for was that the synchronizing run automatically upon user log on/off. We have a big district here, and there will be times teachers will be traveling from one building to another that won't be on the network. I don't want to have to actually schedule every single laptop. I was hoping to just switch to to when they log on/off and then it takes care of it then.

I'll tinker with Codian more. I tried using it last night and testing it with my Samba machine being the testing grounds of where I'd sync to, but I got nothing but errors. I'll test it again now that I'm at work.

---

### Post by HermanAB on 2009-03-09
Simply use Synctoy -R in a shutdown script:
[http://www.windows-help-central.com/windows-shutdown-script.html](http://www.windows-help-central.com/windows-shutdown-script.html)

[http://www.mydigitallife.info/2008/01/01/schedule-synctoy-to-run-and-automatically-and-repetitively/](http://www.mydigitallife.info/2008/01/01/schedule-synctoy-to-run-and-automatically-and-repetitively/)

Cheers,

Herman

---

### Post by Roasted on 2009-03-10
We really  need the users to auto-sync upon log on/off, so that way it guarantees that they'll sync every day and more than likely at a different time. Even if we would schedule random times for all laptops, there's no telling whether or not they will be connected at the time of the sync schedule.

I really just need a free synchronizing program that doesn't require user authentication (due to our passwords changing every so often) and also can run upon system log on/off... either one (or both) would work.

Any more ideas?

---

### Post by joeinbend on 2009-03-16
Hey Roasted -- I might suggest doing the opposite in your environment: You can install Cobian on the clients, and have them "push" back to the central backup server. This is best achieved via FTP, so that even if your laptop users are outside of your WAN, you can have them backup over the Internet. Create a task for the backup you need, set your bandwidth throttling so it doesnt destroy your WAN links when it fires off, and you should be good to go.

The ticket to making this work since you have so many client PC's/Laptops, is having a way to push it... SMS, LANDesk, logon script, GPO.. something. Obviously you're not going to run around and manually install this on all clients!

Regarding command-line scripting and logon/logoff triggering, take a look at this post on the Cobian website:
[http://www.educ.umu.se/~cobian/cobianbackup_faq.htm#22](http://www.educ.umu.se/~cobian/cobianbackup_faq.htm#22)

This is an interesting topic to me, I'd be more than happy to lend a hand in this! With some fairly basic scripts for executing the backup, and some basic routing on your WAN's DMZ so that the central backup server is accessable via internet, as well as the appropreate DNS entries so it resolves to the same URL inside your WAN, I think you could build a highly automated, highly reliable backup mechanism, with minimal impact on your users' experience!

---

### Post by ksennin on 2009-03-16
I have been using Cobian for over a year at my office, an engineering firm with multiple draftsmen accessing a central storage of 75gb of Autocad files.  Never had any trouble with it.

---

### Post by DonaldJ on 2009-03-17
Windows Question - Best Free Backup Software...


I don't think there are any...  I tried to find one for seven years...  I tried them all...  I got a CD of Nero with a new CD RW, but even it was useless as a backer-upper...  This is one of the reasons I switched to Linux...

To get a back up for Windows you must spend a couple hundred bucks...

---

### Post by TVC15 on 2009-03-21
Hello,

For me, the best backup utility in linux is RSYNC.  This works very well with Windows shares.
Even better: now there is a GUI for rsync, called grsync.  You can find it in the Ubuntu repositories.
In practice it works very similar to Syncback.


Give it a try!

---


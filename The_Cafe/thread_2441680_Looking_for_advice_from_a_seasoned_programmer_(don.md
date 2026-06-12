---
title: "Looking for advice from a seasoned programmer (don't know where to post this!)"
date: 2020-04-25
forum: The Cafe
---

### Post by rocket57 on 2020-04-25
Folks,

Maybe this is not appropriate for the Forums, but the good advice and sharp minds here I trust, and I hope someone who knows programming could tell me what would be a good way to start learning a useful language, and a good language to concentrate on. Many years ago, before Windows, I could program in Basic and Fortran, nothing fancy, though. I can read and think logically, and I am willing to work at it. If you (moderator) determine this post is "bad" - could you direct me to a trusted site for advice? There is too much vested interest and self promotion out there, at least IMHO...

Thanks, and apologies, if I have erred!
Rocket

---

### Post by DuckHook on 2020-04-25
> **rocket57 said:**
> …If you (moderator) determine this post is "bad"…
Not at all bad. It's a good question. I'm sure many here are willing to help. However, not a technical support request, so…

*Thread moved to **The Cafe** as the more appropriate forum.*

---

### Post by TheFu on 2020-04-25
This is a very, very common question here.
i learned BASiC and FORTRAN66 in high school too.  Used FORTRAN in college, but never again.

Anyway, my answer is here: [https://blog.jdpfu.com/2011/10/19/how-to-learn-to-program](https://blog.jdpfu.com/2011/10/19/how-to-learn-to-program)
All free, no-hassle links, nothing commercial.

Be certain to search these forums for answers too.  There must be 10 good discussions.

The short answer is - learn python first, then learn C, then learn whatever pays.   When i say "learn" that doesn't mean to become an expert or even intermediate skilled.  Those will take years, each.

---

### Post by rocket57 on 2020-04-25
TheFu,
Thanks for your advice and for the link to your blog; you suggest Python, but there is more than one Python: 2, 3, etc.  Which would be preferable?
- and what about jumping to C first?
Rocket(19)57 (a retired PhD Analytical Chemist turned H.S. Chemistry and Physics Teacher wanting to maybe change careers again, ergo programming at a desk job level?)

---

### Post by TheFu on 2020-04-25
You need to learn both pythons since you will see both for years to come.  The specific version you learn depends on the book or whatever else you use to learn. There will be a specific python version - use that to start.

C isn't as productive as python and many people get frustrated without having some quick successes.

While I hope this doesn't happen to you, but in my part of the world, programmers over about 45 are considered too old to hire new.  That means if I wanted to go back to programming, it is highly unlikely I'd ever get a job offer due to my age and I'm younger than you.  The only way you'll get work is by proving your capabilities, gaining 1 client, who tells others, who tell others until you have 10-20 clients for whatever sort of programming you end up doing.  

IBM won't hire you. Apple won't hire you.  Microsoft won't hire you. .... or me to be a programmer.  They might hire me to manage programmers or as an enterprise architect.

Small programming companies usually need to specialize in a specific area.  C would be for enrichment only if you become a website programmer.  While the knowledge would be useful, the detailed skills probably would not.  OTOH, if you are an embedded systems developer, then C would be pretty common for micro-controllers, but with tiny computers being much more capable today, python and java are pretty common on those devices too.  It just depends.

So, what you should learn really depends on where you want to work, what that industry will actually pay you to do, and hopefully, the job won't be soul sucking.  One of the quickest ways to a well-paying job in most larger companies is to get trained in project management - a PMI cert can open lots of doors, but it requires a special sort of attitude.  Age usually isn't an issue with the PM role, assuming you can get around.  Sitting at a desk all day isn't great.  I did that far too many decades.  In the IT infrastructure world, corporations tend to follow something called ITIL. There are all sorts of classes about that too and certs.  A PMI and a few ITIL certs will go somewhere. Those methods can work in any company of any size, even a 1-man company. 

Of course, anyone can do anything in programming if they work at it hard enough and have an idea that others appreciate.  Do you have an itch?  

My last non-trivial itch was a TV recording system for Linux. Spent about 3 days creating it. Once a week, I have to run a few scripts to convert schedule data into a useful format, search the schedule for programs we like, then schedule to recordings for the channel, duration, start time so a recording will happen.  Doing the recording was solved about 2 yrs ago thanks to my tuners being on the network and the recording is literally a wget from a specific URL for a specific duration.  A few weeks ago, I updated the recording script to use multiple tuners by looking at the error from the first tuner. Certain errors mean the all the recording/playback slots on the tuner are in-use, so the script hits a second tuner device.  No drivers needed. Nothing other than a few commonly available CLI tools.

There are more complete solutions, but those were all 1000x more complex than necessary - mythtv and tvheadend come to mind.  Every Sunday ... or Monday, I spend about 5 minutes and that's it for the week.  Schedule changes ARE an issue for me.  Tonight I was expecting 1 program to be recorded, but a Prince Special was broadcast instead.  Frustrating.  The system doesn't pull new schedules daily.  When I get frustrated enough, I'll fix that ... so give me a few years. ;)  I really need to handle getting schedule data in a better way. Getting higher quality data would be nice too, so that searches for actors could be handled.  Really wish the schedules broadcast with the video streams were good here.  There's no law mandating them, so none of the broadcasters do it and if they do, it is often wrong and only for 2-3 hours in advance. The standard supports over 3-14 days of schedule data.  Clearly, Gracenote has paid someone in the FCC off.

---

### Post by Skaperen on 2020-04-26
Python 2 went end of life on 31 Dec 2019, ten years after it was announced it would do so.  Python 3 is "the Python" now.  that said, i definitely suggest Python and the other advice is "get started ASAP.  i personally learned many mainframe languages decades ago (Fortran, Assembler. PL/1, COBOL). then got onto DECsystem-20 where i encountered C.  then i crossed over to VAX and BSD 4,3 Unix.  DOS, Windows, and finally Linux.  i picked up Python about 10 years ago.  if i go for another it would likely be Node-JS.

---

### Post by TheFu on 2020-04-26
There was a python2 release last week (4/20/20). It is claimed to be the last-ever, python2 release.
[https://pythoninsider.blogspot.com/2020/04/python-2718-last-release-of-python-2.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+PythonInsider+%28Python+Insider%29](https://pythoninsider.blogspot.com/2020/04/python-2718-last-release-of-python-2.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+PythonInsider+%28Python+Insider%29)

---

### Post by EuclideanCoffee on 2020-04-26
Learning a programming language is not like learning a language. You can write many programs without being "fluent," and it's often required. This is why documentation is written. To learn any "programming language," you read the documentation that provides you examples and ideas on how to implement the language to meet a goal. Without a goal, without a reason to write, then you won't find programming satisfying.

---

### Post by rocket57 on 2020-04-26
This is principally to TheFU:
I thank you for your well thought post - and your informative links! I actually started watching the MIT class last night, and I'm going to try and keep up with it (I loved school). What I am really looking for is enough knowledge, in the right area, to get a "Help Desk Support" position, for many reasons, one being that I have a messed up and painful foot and can't do jobs where I will be on my feet more than 4-5 hours (part of the reason I retired from teaching - I was an active and involved teacher and spent a lot of time on my feet helping kids, like a good classroom teacher should, IMO). I am now trying to get informed about what skills the "IT" help desk support types need - perhaps you could give me some pointers here??  I am also considering online chemistry tutoring from home - another thing I need to investigate more. 
I loved what little programming I did in Basic and in Fortran - back then there was no GUI, and green letters on a black screen was cool (but rolls of punched tape and taking stacks of punchcards to the mainframe wasn't that cool!). I still want to learn some programming, and maybe I should get familiar with the command line in Linux as a start - it will probably help me to understand some of the things I fear, like snaps vs. flatpaks vs apt - which is more secure really demands a lot more understanding of how Linux works - do you know a good source to learn about whats "behind the curtain" of our desktops?
Any way, thank you so much for taking the time to give me a good answer and things to think about. I am going to stick to Ubuntu MATE 18.04 for awhile, I'm not one to try a little of this and a little of that - if something is good and I like it I tend to stick with it (like I have oatmeal and scrambled eggs every morning - sometimes fried eggs and turkey sausage now and then...).
Again, many thanks. Live long and prosper.
Rocket

---

### Post by EuclideanCoffee on 2020-04-26
Programming will not help you with a help desk position. Saying you know how to program may confuse someone, especially if you bring up your MIT class.

If you wish to learn skills for IT, you can take classes for free on Plural Sight until the end of April.

If you are serious, please direct message me. I can instruct you further if you can provide me a resume or some sort of assessment on where you are today. I've hired IT people before and can tell you what I'm looking for in a candidate

I began working help desk many years ago and now am a systems engineer. I've climbed my way up through help desk, networking, and now I'm programming daily.

---

### Post by TheFu on 2020-04-27
I never had a help desk job, so I'm not the best resource for that.  My personality doesn't go well to deal with computer illiterate people, let's just say.

I don't see how programming has much to do with a help desk position.  In all my years dealing with corporate help desks, they come, say "hummmm", take the equipment, wipe it, and return it the next day with all the local data gone. If I was lucky, they'd reinstall the special programs for my role, but usually not. This was Windows help-desk.  At most of my jobs, we didn't have any help-desk to call.  When we needed networking, a few of us would order the equipment, run the wired in the ceiling, and make the connections in each office as needed. It was only in my consulting role for about 9 yrs at a huge company where they had "desktop support" that I dealt with the dreaded help-desk and came to understand why the complete wipe was used almost always.
* It solved most issues.
* It got the latest OS, patches, and drivers loaded, with minimal IT effort.
* It provided negative feedback because of the 2+ days of hassle due to lost time as we had to reload programs, search for our data, etc.
BTW, I've never had a job that wasn't "IT" post-college, but we never called it that until I started consulting for huge companies.  Everywhere I worked, everyone except the office manager and sales people were "IT." Every group I was in did our own IT. Networking, computer purchasing, OS selection, tool installs. Every once in a while we'd be called in to help other groups do some major upgrade to their computing stuff, but most of the time we were programmers writing software for outside clients.

I've been out of eggs almost a week.  ;(

---

### Post by sdsurfer on 2020-04-27
I have programmed for over 25 years, if there is one answer to this question . . . . 

Don't learn a language for the sake of learning it (with one exception below.) If you learn French and never go to France in your life, what did you do?

Whatever language you learn it should be ***task-based.*** Figure out what you need to do, and then find the most appropriate language to achieve it. For example, other than learning the structural aspects of programming in general, it does you no good to learn something like .NET if you want to do front end browser-based GUI tasks in which case HTML/CSS/Javascript and related frameworks are what you need to learn.

It is very likely that once you get your head around basic programming concepts, you will want to integrate several languages. For example right now my working suite is Mysql, PGSql, PHP, a little Perl, Jquery, Javascript, CSS, HTML, and various frameworks in those languages. Five years ago it was a different suite entirely.

The exception I mentioned: if your goal is to pursue a stable career using a long term language, then by all means, start with the recruiting web sites and see what has the most activity and what suits you the best. I see tons of dot-net requests and second to that, Java in close competition with C/C#. With dot-net, you will always be programming for Windows, the other two are platform independent and their applications are far more diverse. Front end stuff is huge but there is a huge employee base as well, driving the salaries down in a lot of cases. Plus front end technologies change very quickly, it seems like every month there is some new Javascript framework that is the hot item - you will constantly have to be re-learning technology just to keep up.

Right now mobile application development is real hot, but IMO it's one of those technologies that is very specific and if it ever goes away (like . . . FORTAN or COBOL) you are back to square one. What if phones are eliminated for communication implants or . . . . ?

Speaking of COBOL - look at this, the Oregon Employment Division never upgraded to the 21st century and is requesting retired programmers come out of retirement. Is that mind blowing or what?

[https://www.oregonlive.com/news/2020/04/oregon-enlists-retired-computer-programmers-to-aid-beleaguered-employment-department.html](https://www.oregonlive.com/news/2020/04/oregon-enlists-retired-computer-programmers-to-aid-beleaguered-employment-department.html)

---

### Post by Skaperen on 2020-04-27
i wonder if i qualify.  i'm retired and took 2 COBOL classes way back when i was in college.  i wrote a grand total of ONE (1) program in COBOL after finishing the 2nd class just to prove i could do it (it read tapes and produced a list of files on it for a backup format used by the IBM CMS system).  but i will not move to Oregon, so i will need to telecommute.  and i have tested negative for *SARS-CoV-2*.

---

### Post by sdsurfer on 2020-04-29
^ ^ Haha . . . I imagine in this strange time they would be open to working remote, but it seems to me implementation of remote COBOL code on aging hardware would present difficulties. Do you have access to 5 1/2" floppy disk drives? :-D

---

### Post by TheFu on 2020-04-29
> **sdsurfer said:**
> ^ ^ Haha . . . I imagine in this strange time they would be open to working remote, but it seems to me implementation of remote COBOL code on aging hardware would present difficulties. Do you have access to 5 1/2" floppy disk drives? :-D

Mainframes have full VPN capabilities with secureID for 2FA and have had that since the early 1990s.
Yes, I have a 5.25inch floppy available.  It isn't connected, but I kept a MB+CPU+RAM+IDE HDD should it ever be needed.  I worked on mainframes as a programmer a few different places, but never touched COBOL.  Mainly programmed in languages that nobody has ever heard of, even in the mainframe world, though we used TSO/ISPF, JES3, JCL, PL1, and Rexx too.  Just before I left my last job using mainframes, I was coding utilities in C++ on the system when Rexx wasn't sufficient.  The main language used on our contract was: [https://en.wikipedia.org/wiki/HAL%2FS](https://en.wikipedia.org/wiki/HAL%2FS) if anyone is interested.  It is a real-time, avionics flight control language with 255 threads, though we only used 3 main threads and didn't call them threads. The exact same issues that modern multi-threaded programs have are the problems we had. The system was designed in the mid-1970s.

---


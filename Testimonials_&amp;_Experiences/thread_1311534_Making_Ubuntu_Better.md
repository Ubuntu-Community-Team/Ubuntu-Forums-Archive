---
title: "Making Ubuntu Better"
date: 2009-11-02
forum: Testimonials &amp; Experiences
---

### Post by Leslie Viljoen on 2009-11-02
Hi people!

Whenever I reinstall Ubuntu (I upgrade or install with every release!) - I try to put on my novice cap so I can get an idea of what Ubuntu would be like for the average-type people I constantly evangelize it to.

Well unfortunately Karmic has given me a day's worth of challenges! I will put my notes and issues (and how I avoided or solved them) below. Most of the problems I experienced were with different apps that I installed and not the Karmic base at all.

I'm interested to know:
1. Is every package in Main tested on a new release before it is released?
2. Is anything in Universe or Multiverse required to be tested before a release?
3. If only packages in Main are required to be tested, how do more apps get moved into Main?
4. DO packages get added to main?
5. Is it just packages specifically marked as "applications" that get into Software Center versus Synaptic?

I spend a lot of time racking my brains on how Ubuntu (and all distros) can be made better. This is because I spend so much time and effort promoting it, and every fault makes ME look bad too! :-)

I guess because of the quick releases the quality just cannot be perfect, and I have noticed that NO bug seems to delay a release, no matter how serious. I am always dithering between "wait for stable" and "I need that feature"!

Here are some of my (crazy?) ideas for addressing the stability problem:

1. Have a post-release snapshot ISO when certain stability milestones have been met (this will help when the release includes buggy drivers that make installation hard)
2. Try to write add some kind of unit testing to the basic package build mechanism - so that package builds break if the tests fail
3. Have links to LaunchPad pages (or whatever bug tracker) for packages in "Software Center"
4. Perhaps while Software Center downloads a screenshot it can somehow determine a "level of functionality" for a package from remote bug trackers and display that. I often go through download-install-try-fail loops for many packages before I find one stable enough to use.
5. If more apps can't go in Main, or Main doesn't imply "tested", perhaps there can be a "feedback" area for each package in Software Center. A person who has tried an app can then go back to the package's page and rate a package out of 5 in categories such as "Featureful <-> Simple", "Reliable <-> Broken", etc. This info could be uploaded and then other users could sort the packages by ratings. Nothing leaves a bad taste in a new user's mouth like going through buggy app after buggy app looking for one that works.

I'm not saying all this should (or could) be done, just thinking out loud. And of course I am always willing to try and make things better myself.

Any comments on all this?



NOTES FROM MY FIRST DAY OF KARMIC

TASK: Install some software

software center
no idea how much data I am committing to download (I'm in Africa!)
no idea how functional a program is (besides the canonical supported apps)
can get to website directly, but not launchpad/other bug tracker?

rubygems 1.3.5 (downloaded and installed from source)
"gem install" freezes if libopenssl-ruby not installed

TASK: Extract and crop audio from an FLV video

kdenlive 0.7.5-1ubuntu1
playback freezes

mplayer
works great for dumping flv audio!

gnusound 0.7.5-2
crashes x completely

jokosher 0.11.3-1
jokosher doesn't know that it needs to restart after a plugin is downloaded
very slow, cannot shift-click to select, cannot double-click to split
won't exit properly, has to be killed

audacity 1.3.9-6
file menu too wide, annoying drag into submenus
otherwise worked very well!

TASK: Install some useful apps

virtualbox 3.0.10 r54097
package doesn't update menu until next session - so need to log in again to see it

firefox
found a site that needs flash, clicked 'get flash', downloaded 'deb', opened it,
installed it, reopened firefox, no flash. I hadn't noticed that the 'downloads' 
window was open somewhere, a bit confusing.

TASK: Install a mind mapper program

labyrinth 0.4.0-0ubuntu1
does not start, from command-line:
  Traceback (most recent call last):
    File "/usr/bin/labyrinth", line 45, in <module>
      import utils
  ImportError: No module named utils

found bug report: [https://bugs.launchpad.net/ubuntu/+source/labyrinth/+bug/86503](https://bugs.launchpad.net/ubuntu/+source/labyrinth/+bug/86503)

freemind 0.7.1-6ubuntu4
crashed twice within five minutes of use, trying to download later version
downloaded Debian package for 0.8.1 - does not work on Ubuntu
downloaded "all operating system" version of 0.8.1
seems to be stable after five minutes

TASK: Get my Ruby database access program running (uses ODBC)

installed iodbc
no menu icon for iodbcadm-gtk
added data sources with a +- 10 segmentation faults in between (memory corruption!)

tried my ruby ODBC program, got:
DBI::DatabaseError : INTERN (0) [RubyODBC] Cannot allocate SQLHENV
found:
[http://stackoverflow.com/questions/1419397/rubyodbc-cannot-allocate-sqlhenv](http://stackoverflow.com/questions/1419397/rubyodbc-cannot-allocate-sqlhenv)
tried to follow instructions but 'sql.h' missing when compiling
no mention of a -dev package in README
searched on: [http://packages.ubuntu.com](http://packages.ubuntu.com)
found I had to install: libiodbc2-dev

Now, running my program produces:
/usr/lib/ruby/gems/1.8/gems/dbd-odbc-0.2.4/lib/dbd/odbc/statement.rb:41: [BUG] Segmentation fault

went back and removed libiodbc2-dev and tried unixodbc-dev (recompiled ruby-odbc)
now the program works!

TASK: General

Nautilus won't let me size the first column in the right-hand pane smaller than half my screen width.

---

### Post by P4man on 2009-11-02
Hi there,


Interesting post. 

I cant really help with the questions though (im curious to see the answers as well).

Id just point out that your suggestions here may never get to the right places. Perhaps after getting some clarification you want to submit your thoughts to brainstorm or on some of the appropriate mailing lists. The people that could actually implement your ideas dont tend to read much on this forum.

> **Leslie Viljoen said:**
> 
Here are some of my (crazy?) ideas for addressing the stability problem:

1. Have a post-release snapshot ISO when certain stability milestones have been met (this will help when the release includes buggy drivers that make installation hard)

They have done this for LTS releases I believe, but not for regular releases and I think that makes sense. However I would argue the issue is simply that more time is needed between a beta / RC / release. The schedule is insane. I reported a few show stopper bugs in the beta (like no boot with 2 monitors connected) and no dev even checked it out until after the release. There is just no appropriate amount of time to test and implement (and test!) fixes IMHO.

I work in software development and our products are not anywhere near are complex as an OS, but we take 6 months between a beta or RC and releasing.  Canonical adds brand new features a few weeks before release. That can never work. Perhaps they should adopt the Google approach and call everything beta, or everything except a 1 year old LTS ;)

> 3. Have links to LaunchPad pages (or whatever bug tracker) for packages in "Software Center"
4. Perhaps while Software Center downloads a screenshot it can somehow determine a "level of functionality" for a package from remote bug trackers and display that. I often go through download-install-try-fail loops for many packages before I find one stable enough to use.

Software centre is very much work in progress. I suspect such features will be added later, this is barely more than a preview, and if anything, a regression from the gnome add/remove applications. Heck you cant even copy/paste text from software centre to google on it.

---

### Post by Leslie Viljoen on 2009-11-03
I see Software Center is in Python, so I may do some hacking on it.
Wow, LinuxMint might already have some of the things I was suggesting! I am going to take a look at it.

---

### Post by slakkie on 2009-11-03
> **Leslie Viljoen said:**
> 
I'm interested to know:
1. Is every package in Main tested on a new release before it is released?
2. Is anything in Universe or Multiverse required to be tested before a release?
3. If only packages in Main are required to be tested, how do more apps get moved into Main?
4. DO packages get added to main?
5. Is it just packages specifically marked as "applications" that get into Software Center versus Synaptic?


In theory all packages are tested, provided all packages are used by the ones who test the development release (lucid for the coming 6 months). As you will understand this is hardly possible. If you want to make sure everything you run is tested, my advice is to jump on the band wagon and start running the Lucid development release. This way you can tackle problems early on and get those bugs solved.

For your questions regarding main packages, have a look here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

> 
1. Have a post-release snapshot ISO when certain stability milestones have been met (this will help when the release includes buggy drivers that make installation hard)

I know this is done with LTS releases at every point release. I don't know if this is done for regular releases. I don't use the normal installers, the network install will provide me the latest and greatest at any given moment.

> 
2. Try to write add some kind of unit testing to the basic package build mechanism - so that package builds break if the tests fail


I've asked this question to a developer, this was the answer:

> 
dholbach	<slacker_nl> QUESTION: are there automated testtools for package testing, eg tests for regression testing? or should that be provided by upstream?
dholbach	slacker_nl: great question
dholbach	there's a number of upstream developers (which means software authors) that provide us with test suites and very often they are run during the build to directly find out if things got broken in the new release
dholbach	there's tools like pbuilder for safe test-building and there's tools like lintian that can check your packaging for you


So this is implemented partially.

> 
3. Have links to LaunchPad pages (or whatever bug tracker) for packages in "Software Center"

Nice idea, something like this already exists in Debian: apt-listbugs. It is present in Dapper and Hardy. Perhaps Lucid will also include it (since it is also LTS). 

[http://packages.ubuntu.com/hardy/apt-listbugs](http://packages.ubuntu.com/hardy/apt-listbugs)

> 
4. Perhaps while Software Center downloads a screenshot it can somehow determine a "level of functionality" for a package from remote bug trackers and display that. I often go through download-install-try-fail loops for many packages before I find one stable enough to use.


Maybe have a look at the popularity-contest package.

> 
5. If more apps can't go in Main, or Main doesn't imply "tested", perhaps there can be a "feedback" area for each package in Software Center. A person who has tried an app can then go back to the package's page and rate a package out of 5 in categories such as "Featureful <-> Simple", "Reliable <-> Broken", etc. This info could be uploaded and then other users could sort the packages by ratings. Nothing leaves a bad taste in a new user's mouth like going through buggy app after buggy app looking for one that works.


Main has nothing to do with how well a package has been tested. Packages in main are supported by Canonical. Unlike packages in the other sections.

Regarding software center, I think they took the approach, release early, release often, so in Lucid it will be improved. Add wishlist items to launchpad for your ideas regarding Software Center. See also [http://www.ubuntu.com/news/spotlight/uds](http://www.ubuntu.com/news/spotlight/uds)

---


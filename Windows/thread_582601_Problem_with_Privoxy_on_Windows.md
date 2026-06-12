---
title: "Problem with Privoxy on Windows"
date: 2007-10-20
forum: Windows
---

### Post by blackhole54 on 2007-10-20
Hi All,

I use Privoxy on Linux w/o problems.  I have created a CD based on Portable Firefox that  I can use on public computers running Windows.  I have also added Tor and Privoxy and added a batch file that sets everything up which is fired by autorun when the disk is inserted.  And it  works.

Except that, nearly as I can figure out, the filters in Privoxy are not working.  I first noticed that a filter that is supposed to eliminate the Microsoft "Get the Facts" adds on Linux Today was not working.  A little toying with the filter and config files led me to suspect that none of the filters were working.   Yet I know Privoxy was doing something as some of the ads were removed.

First, I should explain that I have the batch file copy everything related to Privoxy to the hard drive, and the program is run from there.  This allows me to change the filter and config files, and it was simpler to put everything else on hard drive than figure out how to split it up.  (Yeah, I am lazy.  :-P )  To simplify testing, I created a very simple test filter which simply replaced a string that was known to be on the page with another string:

```

FILTER:  test test this
s/<known string>/<something goofy>/g

```

I tried this both in *user.filter* and *default.filter*.  I looked at these respective files through Privoxy's web interface to make sure the changes were being read.

I performed this test on Linux Today.  I enabled the filter for the website.  I checked the source of the web page to make sure I had the <known string> right, including spaces.    I used the "which actions apply to a URL" function of Privoxy to verify that this filter was enabled and I refreshed the Linux Today page.  The expected substitution did _not_ take place.  To double check my method, I tried the same sort of thing on a setup where Privoxy was running under Linux, and I had the expected result.  I've wondered if this was a bug in Privoxy, but unless there is something unusual in my setup triggering this, this would be such a glaring bug, surely it would have been reported by now.

I tried to use the access times of the filter files to observe whether these files were read when I refreshed the LT page.  I did this from the command line because simply looking at the "properties" page from the GUI alters the access time.  I eventually demonstrated that this test was meaningless because the access time is not changed simply by reading the file the way it is in Linux.  (If this is not standard Windows behavior, it may have been a result that this machine is running *Deep Freeze*.)

I am totally baffled as to what could be going on.  Does anybody have any ideas? Please be aware that I do not own a Windows box to test this on, so I will have to do any testing on a public computer.  This means that there could be delays in my trying  suggestions.

Thanks in advance.

P.S.  Both the Linux and Windows versions are Privoxy 3.0.6.

---

### Post by blackhole54 on 2007-12-09
I have now seen instances where the "Get the Facts" filter works from my CD on WinXP, although most of the time it doesn't.  I still don't have a clue about this.:confused:

---


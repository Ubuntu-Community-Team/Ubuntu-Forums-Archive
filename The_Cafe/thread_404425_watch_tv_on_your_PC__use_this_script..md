---
title: "watch tv on your PC?  use this script."
date: 2007-04-08
forum: The Cafe
---

### Post by Andre_44 on 2007-04-08
I don't have cable TV at home, so my computer is my main source of entertainment.  i use TV-Out on my laptop to keep something playing on the TV most of the evening.  the most annoying thing about this kind of set up is having to choose what to watch every time a show is over.  so, as an experiment in ruby programming, I've come up with randomShow.rb.
this program manages an sqlite3 database of videos on your computer and will choose random ones to play. it tracks the last time the show was played, and whether or not it was skipped.

the package can be downloaded here: [randomshow-0.9.tar.bz2]("http://liquidmm.com/~andre/randomshow-0.9.tar.bz2")
the dependencies are:
-sqlite3
-sqlite3-ruby
-gnome-osd
-mplayer

all of which are installable through the ubuntu repositories.  

install instructions are included in README.txt, but here's a run down:

-extract files.
-run mkdb.sh to create the db
-configure the script (open randomShow.rb in your fav editor and change the 4 config values at the top)
-copy to /usr/local/bin
-add media to the library:
 (randomShow.rb scan /path/to/media)

if you are using this script, please let me know, and if you have modified it in any way, your contributions would be appreciated.

---


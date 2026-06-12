---
title: "winamp libary for linux aka mp3 library i have created"
date: 2008-08-28
forum: The Cafe
---

### Post by sgf on 2008-08-28
For those of us who prefer oldschool mp3 players like audacious (eg no big fancy itunes styled GUI), there still is no real mp3 library that matches the functionality of winamp's media library. I wrote this script to teach myself perl and some sql, and thought it might be useful to other users, and useful for myself to get some feedback. 

How to use:
install MP3::Tag and DBI for perl. DBI is in the ubuntu repo's iirc. MP3::Tag can be installed by typing "perl -MCPAN -e shell" then typing "install MP3::Tag" in the interactive shell. sqlite is also required (for the database).

open scanMusic.pl with your favorite editor and edit the line @dirsToScan to the appropriate things, ex: my @dirsToScan = ("$home/Music","$home/Downloads","$home/temp");



after it's done scanning, run linampLibrary.pl . Note: feature #2 is not implemented yet. Note: if you do NOT use audacious, edit the very last line of linampLibrary.pl to reflect your favorite mp3 player.

I am very new to perl, so any tips or suggestions about my code is greatly appreciated.

---

### Post by StOoZ on 2008-08-28
cool! thanks , gonna give it a try :guitar:

---


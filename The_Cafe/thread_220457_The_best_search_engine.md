---
title: "The best search engine?"
date: 2006-07-21
forum: The Cafe
---

### Post by jordilin on 2006-07-21
Ubuntu fellows, what do you think of the (optional in ubuntu) Gnome search engine, Beagle?
What do you prefer Beagle, the gnome-search-tool, or you prefer going to the command line and type find or locate?
It's interesting because finding files over your Desktop is extremely important for me.

---

### Post by reacocard on 2006-07-21
beagle, because of its intergration with deskbar.

beagle + deskbar >= spotlight

---

### Post by ComplexNumber on 2006-07-21
i rarely use beagle. i just use gnome-search-tool. it does the trick for me. locate and find are command line tools. the 'locate' command needs 'updatedb' to be run every now and again because when you ad dor delete stuff, it doesn't automatically keep track of where things are. it only knows where things are according to whats in its database (somewhere in /var). 'find' is better in that respect, but its also not as fast as 'locate'.

---

### Post by FISHERMAN on 2006-07-21
gnome-search-tool

---

### Post by jordilin on 2006-07-21
I didn't say it, but I love Beagle. It searches everything in just a moment. This is very important for the future of Linux as Microsoft will address this feature in the forthcoming Vista. M$ is considering this feature as an extremely important one.

---

### Post by Engnome on 2006-07-21
I have an index of my files stored in my brain that I search in using my own homemade search engine.;) 

(what I mean is I don't search, I store them smartly)

---

### Post by scxtt on 2006-07-21
i use **(s)locate** and when i'm looking for more than just a name, **find** fits the bill nicely ...

---

### Post by ComplexNumber on 2006-07-21
> **Engnome said:**
> I have an index of my files stored in my brain that I search in using my own homemade search engine.;) 

(what I mean is I don't search, I store them smartly)
yes, but search tools have other uses ;). for example, if you want to delete all the 'README' files from a large directory, its very time consuming to just go through every single directory deleting them individually. a much better and quicker way is to do a search for the README files, then delete all those found in one operation.

---

### Post by fluffington on 2006-07-21
> **Engnome said:**
> I have an index of my files stored in my brain that I search in using my own homemade search engine.;) 

(what I mean is I don't search, I store them smartly)

Ditto.

---

### Post by benplaut on 2006-07-21
> **Engnome said:**
> I have an index of my files stored in my brain that I search in using my own homemade search engine.;) 

(what I mean is I don't search, I store them smartly)

d-d-d-ditto!

---

### Post by bruce89 on 2006-07-21
You missed out tracker - [http://freedesktop.org/wiki/Software/Tracker](http://freedesktop.org/wiki/Software/Tracker), It'll be in Gnome 2.18 possibly.

---

### Post by Lord Illidan on 2006-07-21
Beagle slows down my computer to a crawl.

---

### Post by richbarna on 2006-07-21
> **bruce89 said:**
> You missed out tracker - [http://freedesktop.org/wiki/Software/Tracker](http://freedesktop.org/wiki/Software/Tracker), It'll be in Gnome 2.18 possibly.

Nice link !! I was using beagle but it slowed my computer down, not good if you've got a couple of things on the go.

I  see that tracker uses only 1MB RAM, that is definitely worth looking into.

Thanks

---

### Post by matthew on 2006-07-21
> **Engnome said:**
> I have an index of my files stored in my brain that I search in using my own homemade search engine.;) 

(what I mean is I don't search, I store them smartly)I do the same...I put a lot of time and effort into my filesystem in /home and it pays off when I need to find something. I use good, descriptive names for folders and it's quite easy.

Now, if I want to do as a previous poster mentioned and search for all the readme files, that's a different story. I hate doing stuff like that. :)

---

### Post by richbarna on 2006-07-21
Ok, got the deb and installed, the search is fast :) I just tested it with .txt files, which I have a lot of.

For anyone else who is interested this is how to get it running at start up, and some other info.
> RUNNING TRACKER


To run tracker, you need to manually start the tracker daemon trackerd. 
By default trackerd will index your entire home directory.

You can also pass a directory root to be indexed as a command line parameter 
if you dont want your entire home directory indexed. EG

"trackerd /home/jamie/Documents"

You can make sure that tracker only indexes a subset of your home directory 
and also specify folders not in your home directory by editing the tracker.cfg 
file in ~/.Tracker (which is created when you first run trackerd) and setting 
WatchDirectoryRoots to a semicolon delimited list of directories (full path required!) 

EG: 

WatchDirectoryRoots=directory1;directory2;directory3

On the first run, Tracker will automatically create a new database and 
start populating it with metadata by browsing through the user's home 
directory (or the root folder(s) specified).

On subsequent runs, Tracker will start up much much faster and will only 
ever incrementally index files (IE files that have changed since last index).

If installed correctly, the tracker daemon (trackerd) can also be started 
automatically via Dbus activation.


Tracker And Nautilus Search

Once you have installed Tracker and have some indexed contents, you should 
now compile Nautilus (ver 2.13.4 or higher) which should auto detect that 
tracker is installed and automatically compile in tracker support. You are 
now ready to appreciate a powerful and super efficient c based indexer in 
all its glory... happy hunting!

To make sure trackerd always start when you login to Gnome, you will need to 
add it to Gnome-session (select sessions from preferences menu, select startup 
program tab and then add /usr/bin/trackerd). For non-gnome installations, see 
the desktop docs for how to auto start an application for your particular desktop.

Tracker and Deskbar applet

Tracker is also integrated in GNOME's deskbar applet. Please see that applet 
for more info.



COMMAND LINE TOOLS

Tracker comes with a number of command line apps that you can use:

"tracker-extract FILE" - this extracts embedded metadata from FILE and prints to stdout

"tracker-search SEARCHTERM" - this perfoms a google like search using SEARCHTERM to retrieve 
all matching files where SEARCHTERM appears in any searchable metadata

"tracker-query" - this reads from STDIN an RDF Query that specifies the search criteria for 
various fields. It prints to STDOUT all matching files. You can see some example queries in 
the RDF-Query-examples folder. You can run the examples as "tracker-query < RDFFILE"


   


Thanks Bruce89

---

### Post by Engnome on 2006-07-21
I just realised that I used to search alot in windows (windows search engine is really good after telling that dog to "Piss off!") But in linux I only have home (were I stove away useless crap) and the desktop were I've organised everything into folders. Neat!

Windows on the other hand is a mess, they have so many default places to put stuff (my documents, my music, my videos, desktop) wich is really confusing as you spend alot of time looking for files. Also you have to mess around with stuff in c:\program files\ searching for config files that might be in the program folder, application data wich is a hidden folder only accesible from C:\dokument and settings\username\application data or some other obscure place like the nightmarish register. why?

Also it's kinda weird that if you go up from root (c:\) you come to my computer wich i some sort of virtual folder, if you go up from that you get into C:\dokument and settings\username\desktop\ but you can't go up from that bc that is root according to some weird logic.#-o

</rant>

Windows bashing is fun:D

---

### Post by Carrots171 on 2006-07-21
I prefer to use locate because of the speed. No waiting for your search results to appear, and no computer slowdown. That may change when I give Beagle a try, though.

---

### Post by AndyCooll on 2006-07-21
I like the deskbar-applet which searches in lots of ways. I think part of it uses Beagle.
However Beagle doesn't seem to do a thorough search. So, when I want to look for "icons" for instance for an app that hasn't got one in Applications, Beagle does a crap job finding anything system related. Maybe it's not designed to search in this way? Anyway, I end up back at the command line. 

Like others, I too have found that Beagle can bring my box to a crawl too. And when I go to the System Monitor there is a long list of "beagled-helper". I end up killing these just to get my computer back to speed.

:cool:

---

### Post by Randomskk on 2006-07-21
I just use find :P

---

### Post by adam.tropics on 2006-07-22
I think I will start keeping my files in better order. I was going to say Beagle, just having just been inspired to check its memory use, forget it, it's gone!

---

### Post by IYY on 2006-07-22
Don't know which is best, but I use 'locate' most often.

---

### Post by croak77 on 2006-07-22
(s)(r)locate

---

### Post by DoktorSeven on 2006-07-22
I don't use desktop search solutions, and I disabled the slocate updater (wasteful to catalog my whole system when I don't need to find something everywhere), so find rules.

---

### Post by chajuram on 2006-10-03
beagle does not catalog everything for me.

---

### Post by Franko30 on 2007-07-03
> **chajuram said:**
> beagle does not catalog everything for me.

Same here.

And tracker still is missing in the poll on page one, although tracker rocks!

Cheers

Franko30

---

### Post by MedivhX on 2007-07-03
> **reacocard said:**
> beagle, because of its intergration with deskbar.

beagle + deskbar >= spotlight

Same here.

---

### Post by brim4brim on 2007-07-03
I use gnome-search-tool because I think Beagle uses too many resources for a search engine.

---

### Post by Franko30 on 2007-07-10
Hi,

MetaTracker is still not part of this survey - why?

Franko30

---


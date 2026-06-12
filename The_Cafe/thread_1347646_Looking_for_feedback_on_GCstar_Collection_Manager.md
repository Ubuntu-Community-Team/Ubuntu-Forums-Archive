---
title: "Looking for feedback on GCstar Collection Manager"
date: 2009-12-06
forum: The Cafe
---

### Post by zombiepig on 2009-12-06
I'm one of the developers for GCstar Collection Manager ([http://www.gcstar.org](http://www.gcstar.org)) which is an open source program for tracking collections of dvds, books, comics, games, and heaps more. I'm interested on any feedback people have about the program, so I can get a better idea of where we stand and how we can improve. (I'm really committed to making gcstar the best collection manager available, so feedback is important :P) 

Have you ever tried gcstar? Do you use any similar programs? Have you tried gcstar in the past but something turned you off? Most importantly, how can we improve the program? ;)

You can install gcstar through the normal ubuntu channels, but a much more recent version is available in our ppa ([https://launchpad.net/~gcstar/+archive/ppa](https://launchpad.net/~gcstar/+archive/ppa)). 

Any feedback would be appreciated!!

---

### Post by lovinglinux on 2009-12-06
> **zombiepig said:**
> Have you ever tried gcstar?

Yes and I do recommend it for anyone looking for a video catalog application. GCStar is the best IMO.

> **zombiepig said:**
> Do you use any similar programs?

I was a fan of Ant Movie Catalog on Windows, but was very pleased with GCStar when I switched to Ubuntu Hardy Heron. I haven't used it lately, because I have developed a [Firefox extension]("http://fmc.isgreat.org") for managing my stuff. I feel comfortable mentioning it here, because it's not a competitor. It is designed for a different purpose, which suit my needs better. Nevertheless, I have been thinking about adding some sort of export feature that would allow my users to import data into GCstar.

> **zombiepig said:**
> Most importantly, how can we improve the program?;)

I will have to test it again to give you a decent feedback.

---

### Post by cariboo on 2009-12-06
I currently use Griffith, it works well form me, I've installed Gcstar and will start adding DVD's to it later this week. 

The one thing I didn't find was IMDB wasn't in the list of search sites.

---

### Post by g63marty on 2009-12-07
I found the version prior to 1.5.0 not usable with IMDB. Too many bugs in program and scripts. This one seems much better already, so I am trying it again using Karmic Kubuntu (64 bit).

It will be used for a digital movie collection. I like the import from folder. Optioned to chose from the list of results at end of the import. Seems to be much better at title matching now. 

I set IMDB as the default db in the preferences. But the first thing it asked me on a folder import was which resource to use again. Seems like it should set the one from preferences first or ask to set it at the preference if one has not been selected before.

Using import a folder, it takes all files in the folder, regardless of type. This would be ok except that there is some art and thumbnails I don't want to remove (dual boot with Win 7).
The previous version had a filter by file extension option. Is there a way you could categorize import to match the collection type? In this case I selected a movie collection, so the import would include only video files. Music would include music types, and so on.

On the Details of a movie entry it is totally cool to be able to add any tag to any text field. But how do you change/remove typo's? For example. I add a Location "Libary". Can it be corrected? 
 
On the "Select an Item" search results list I like that it can sort by title/date by clicking on the appropriate bar. But there seems to be no way to get back to the original relevance sorting. 

Also on the "Select an Item" list, the buttons are preview, cancel and ok. If I don't want to add a file to the database, it seems there should be a Skip button. I found it currently uses cancel, but for me cancel means to quit the entire operation. I suggest this because there is no way to cancel all the way out of a batch import. I tried cancel, X, alt-f4, etc... but it just goes to the next movie on the list.

These may be IMDB specific issues:
- The Select return results list are sometimes ambiguous. That is because there is a video game or perhaps a TV show with the same title as the movie.
For example. "Harry Potter and the Sorcerer's Stone". Both have same date, so they appear as a duplicate entries on the results. But in IMDB, the video game is distinguished with suffix (VG).
- IMDB also adds a roman numeral after the year if there happens to be two movies with the same title in the same year. E.G. "Shooter". The one I have is with Mark Wahlberg. IMDB shows title as "Shooter (2007/I)". This causes another ambiguity in the Select an Item list.
- There was an issue with the Director name not filled in, but after a gcstar -u it grabbed a new plugin for imdb and the director field now poplulates. Is there a way to Re-fetch all the information for any/all entries in the db?
- I use a year (yyyy) in the file name so that the lookup would be more correct. But the filename parser removes dates. Great that the parser removes junk, but dates are useful for use with IMDB searches. 

And finally a bit on the wish list.
- Ability to attach and tag other images or media to a collection entry. 
- Import by (selected) File names not just folders.
- Primary and sub entries for handling TV series. Have just one "Stargate SG-1" entry in left column than can expand to show all the episodes in the collection. 
- Person information (Picture, short bio?) with actor/director links on General page linking to person info.

I hope this is more critique than critical. I think this software is an excellent tool. Plus the price is right ;-)

Happy Holidays!

---

### Post by Uncle Spellbinder on 2009-12-07
@ zombiepig

I'm currently logged into Windows 7 at the moment and need to get to sleep. But I've e-mailed myself this page. I *really* need to try this . Sounds like just what I've been looking for.

Cheers!

---

### Post by Uncle Spellbinder on 2009-12-07
Have downloaded it now. Will configure this weekend and test (long workweek ahead). 

Seems odd that it appears in "Office". Seeing as it seems geared towards film and music, it would bee in "Sound & Video".

Look forward to testing this out.

---

### Post by mlippert on 2009-12-08
Hi,
I just installed GCStar yesterday. I added the PPA and got version 1.5.0.

One thing I think would really help is a getting started tutorial. There are a lot of options and it's a little overwhelming.

I know that some people like to just dive in, but I like to get an understanding of what all the pieces are so that I can try to do it right the 1st time.

I've only added a couple of my DVD's so far.

I know I'm going to have a bunch of questions.

The ones I have right now are:
1) I've got lots of TV Series DVDs which tend to be packaged by season. How would I enter say "Terminator: The Sarah Conner Chronicles" Season 2 into my movie collection?

Under details I see a field labeled Series and one labeled Rank, are they for this purpose?

Or I saw some mention of a different collection type for TV Series, but the only one currently listed seems to require individual episodes be entered, so it doesn't seem appropriate.

2) I have several DVDs with multiple movies on them. How would you suggest those DVDs be entered? If the DVD has 4 movies, do I have 4 entries in the database? Is there a way to indicate that these 4 entries share a DVD?

3) Lastly for now, I had a MS Access DB which I created to store my DVD collection, but I haven't updated it in quite a while, which is part of what prompted me to look for and try out GCStar. Is there a text format I can write even just the titles to, which I can then import, and use the fetch facility to update other information?

Thanks for a nice tool, after I get my DVDs dealt with, I will start on my Science Fiction collection :D.

Mike

---

### Post by g63marty on 2009-12-08
Hello again.

I've had a bit more time to play and have also installed the windows version in addition to the debian package. They both seem to look the same. That's a big plus in the consistency department.

I do have a few other issues.

1) I would highly recommend an automatic check for plugin update tool at startup. On the windows side I don't think anyone would think to run the update.bat in the directory or the start menu. There is no feedback from this so one does not know if it completed successfully. 

As others may have done, I installed the base 1.5.0 but did not run the update before adding or importing items. So the Director entry is blank. After the gcstar -u -n, the Director entry fills in properly. But this leads to request 2.

2) In addition to the Fetch button, could you have an "Update Missing Information" button? Using the Fetch button twice retrieves another image from the web, but does not remove the old image... A batch version of Update Missing for Selected or All movies would be great too.

3) Have a tool to cleanup or remove unused images in the downloaded pictures folder. Add the tool to the menu somewhere.

I tried using the Import Folder with a TV Series collection, but it hangs, so not sure what may be going on here. 

Thanks for all your hard work!

---

### Post by JohnJackson on 2009-12-29
I think GCStar has the best user interface out of the ones I've used (Tellico and Griffith come to mind).

Any chance of an SQLite backend?

---

### Post by aktiwers on 2009-12-29
Is there anyway to add a folder (say my Movies folder,) let it scan the files and import them?

Some of them might have strange titles, with release date/year and so on in them, but searching IMDB often gives the right results. Maybe it could try to guess the name of movies with dots and numbers or small incorrect info in the title? It would take forever to add them all manually.

---

### Post by trixman on 2009-12-29
> **zombiepig said:**
> I'm one of the developers for GCstar Collection Manager ([http://www.gcstar.org](http://www.gcstar.org)) which is an open source program for tracking collections of dvds, books, comics, games, and heaps more. I'm interested on any feedback people have about the program, so I can get a better idea of where we stand and how we can improve. (I'm really committed to making gcstar the best collection manager available, so feedback is important :P) 

Have you ever tried gcstar? Do you use any similar programs? Have you tried gcstar in the past but something turned you off? Most importantly, how can we improve the program? ;)

You can install gcstar through the normal ubuntu channels, but a much more recent version is available in our ppa ([https://launchpad.net/~gcstar/+archive/ppa](https://launchpad.net/~gcstar/+archive/ppa)). 

Any feedback would be appreciated!!

i love it, m friend would like to know f you can install it on the mac

---

### Post by cgb on 2009-12-30
I like the program a lot.  Seems to work good.  One thing I would like to see personally would be some type of Shift Switcher for the movie posters possibly on top and the description below while switching.  I use the program mainly as a file browser to play video files on a HTPC and it would be nice to have a more graphical display.  I used to use XBMC but have other issues with it and trying to now use a stand alone app for file browsing and playing movies through VLC. 

Image of Shift Switcher used by Compiz:
[IMG]http://wiki.compiz.org/Plugins/Switcher?action=AttachFile&do=get&target=shiftshot.png[/IMG]

---

### Post by tuhatom on 2010-01-20
First off, thank you for all your efforts!  I have only started using GCstar on linux, but it seems pretty damn good...

I have one small feature that I think it could use, unless it already exists and I was just not able to find it via a quick google search and poking around in the app.... a keyboard shortcut to add a new movie!

I click the + icon to add a new movie, and then its hands on keyboard:  type the name of movie, hit enter... likely the IMDB search has the correct one highlighted already, and I hit enter again.. perfect, movie added!  ...except now I have to reach for the mouse again to click the + icon.

I know it seems like a small thing, but I am trying to catalogue a couple of hundred movies for the first time, and that one small step repeated over and over adds up =)

Thanks again for this excellent software!

---

### Post by Volynda on 2010-02-16
I tried GCStar and Tellico but I think I like Tellico because it gathers more information. I get the polt summary and the complete cast of my movies. It also has a place for me to give the movie a personal rating and a few other items that I didn't find on GCStar. I can import from other programs my lists of collections and it has a function called "Generate Report" that gives a list of all my collections in a couple of different formats.

---

### Post by ottabaub on 2010-06-03
> **zombiepig said:**
> 
Have you ever tried gcstar? Do you use any similar programs? Have you tried gcstar in the past but something turned you off? Most importantly, how can we improve the program? ;)

Any feedback would be appreciated!!

I installed GCstar yesterday and today I imported my *Ant Movie Catalog* database. I am very impressed with the program. I like the interface much better than AMC.

I observed two things I don't like:
1. Some of the movie images didn't come through.
2. "Titles" and "Alternative Titles" got swapped. For example, Clint Eastwood's film "The Good, The Bad & The Ugly" was titled "Bo, el lleig i el dolent, El..." (trimmed). Not much good to me. With 588 titles, it will take me quite a while to swap them.

---

### Post by MakOwner on 2010-09-09
> **zombiepig said:**
> I'm one of the developers for GCstar Collection Manager ([http://www.gcstar.org](http://www.gcstar.org)) which is an open source program for tracking collections of dvds, books, comics, games, and heaps more. I'm interested on any feedback people have about the program, so I can get a better idea of where we stand and how we can improve. (I'm really committed to making gcstar the best collection manager available, so feedback is important :P) 

Have you ever tried gcstar? Do you use any similar programs? Have you tried gcstar in the past but something turned you off? Most importantly, how can we improve the program? ;)

You can install gcstar through the normal ubuntu channels, but a much more recent version is available in our ppa ([https://launchpad.net/~gcstar/+archive/ppa](https://launchpad.net/~gcstar/+archive/ppa)). 

Any feedback would be appreciated!!

I have posted this in the bug report forum on the Gcstar web site but it doesn't seem to be attracting much attention:

I'm on Ubuntu 10.4.1 LTS with gcstar 1.6.1 with whatever updates running gcstart -u as root provides.
At some point in the past, gcstar stored the actual imdb web page for each movie in the Main Items:Web Page field (As identified by the export to csv function).  As of 172 entries ago in my collection, it started storing the actual search query used to find the page, as opposed to the actual page.

So of 592 entries that have the correct url stored, 172 have the search term.  And no way to actually edit this in the user interface, other than hitting fetch information, and editing it there (I haven't tried this, and won't do it for 172 items anyway...)

Any way to fix this?
Will the value stored in this field ever be the actual page again, or is the new thing the search term?

---


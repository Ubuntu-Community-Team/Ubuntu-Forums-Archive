---
title: "Tracker Alternative?"
date: 2011-03-05
forum: The Cafe
---

### Post by pt123 on 2011-03-05
is there a Tracker alternative? I tried installing Tracker on Maverick, it just an awful piece of software, ignores all the config settings, and started indexing the whole / folder. 

Support for it seems dead
[https://bugs.launchpad.net/ubuntu/+source/tracker](https://bugs.launchpad.net/ubuntu/+source/tracker)
[http://ubuntuforums.org/showthread.php?t=1667061&highlight=tracker](http://ubuntuforums.org/showthread.php?t=1667061&highlight=tracker)

I just need an application to index a folder with PDFs (300 or so) (not the content inside).

---

### Post by Quadunit404 on 2011-03-05
You can try Beagle, although that's kinda dead too.

---

### Post by DZ* on 2011-03-06
> **pt123 said:**
> I just need an application to index a folder with PDFs (300 or so) (not the content inside).

If you don't need to index content, why not just use "locate"?

Unlike Beagle, Tracker development is very active and they seem to be responsive. Try their mailing list:
[http://news.gmane.org/gmane.comp.freedesktop.tracker](http://news.gmane.org/gmane.comp.freedesktop.tracker)

---

### Post by pt123 on 2011-03-07
with locate you can't limit it to certain folders, then you have to cut and paste the address to open the file it is cumbersome,

mailing list, I might try that, the application is renown for it's bugginess and the developers continue to ignore it

---

### Post by DZ* on 2011-03-07
> **pt123 said:**
> with locate you can't limit it to certain folders, then you have to cut and paste the address to open the file it is cumbersome,

mailing list, I might try that, the application is renown for it's bugginess and the developers continue to ignore it

You can post to it as if it was a newsgroup by pointing a newsreader to news.gmane.org and selecting gmane.comp.freedesktop.tracker.

I mostly use KDE which now has a similar functionality integrated, and only use tracker occasionally on wife's netbook with Gnome. It does have bugs but it's been improving IMO (previous stable version, 0.6 was barely usable). 

Another application you may try is recoll. It can run as a daemon but I use it in its default mode where it indexes only when you tell it, i.e. manually or via a cron job at night. It can search for either file names or content. I'm very impressed with recoll. For example, it does instant search inside attachments to emails (such as pdf and doc) in offline IMAP folders.

---

### Post by pt123 on 2011-03-08
KDE seems to be on shakey ground with the way QT is being kicked around.
This page had a good comparison of the applications.
[http://www.wikinfo.org/index.php/Comparison_of_desktop_search_software](http://www.wikinfo.org/index.php/Comparison_of_desktop_search_software)

There is an app called Pino which looked promising, but it can't be installed because of a package conflict with LibreOffice PPA, screenshot below

---

### Post by DZ* on 2011-03-09
> **pt123 said:**
> KDE seems to be on shakey ground with the way QT is being kicked around.
This page had a good comparison of the applications.
[http://www.wikinfo.org/index.php/Comparison_of_desktop_search_software](http://www.wikinfo.org/index.php/Comparison_of_desktop_search_software)

The page needs some corrections. 

1. KDE desktop search is based on strigi and it definitely implements full text search as well as exact phrase search; you can search through dolphin interface starting from any directory, for full text or file names.

2. Tracker also has these features but it's a bit trickier to search for a phrase than to simply quote it. You either have to do it from nautilus (it's currently integrated with Tracker in 10.10) or to prepend a phrase with a letter character in the search tool, e.g. x"some_word1 some_word2".

3. Recoll supports regular expressions.

If I followed the news correctly, KDE is not on shaky grounds in legal terms, only corporate support for Qt is not certain. If so, the worst that can happen to KDE development is that it will lose some focus and become... well, a lot like GNOME :-)  (that is, I see nothing to worry about)

---

### Post by David Andersson on 2011-03-13
> **pt123 said:**
> with locate you can't limit it to certain folders, then you have to cut and paste the address to open the file it is cumbersome

*Catfish* can be used as a graphical frontend to *locate*, where you can restrict the search to a specific folder, and open a found file with double-click. (My problem with it is that it does not remember what folder I want to search in, so I have to re-select it every time.) (Package: catfish)

EDIT: > I just need an application to index a folder with PDFs (300 or so) (not the content inside).
(Only 300 files and only search in names, not in content? Searching 100000 files for parts of file names takes ca 0.2 seconds with *locate* and ca 0.4 seconds with *find*. No indexing needed. The find-method is also available in Catfish.)

---

### Post by ternyk on 2011-04-18
I needed a way to categorize my documents (books/manuals/etc) to subjects (one doc -> many subjects). It was reasonable to do it with some tagging software. 

After a whole day hacking/tweaking with Tracker I surrender. It seems that it's not completed and not usable for me at least.
Critical bugs for me:
1. Cannot search or browse files by tags - it's funny but true
2. Cannot skip monitoring hdd partitions even if the directory is in the ignored dirs list and disabled removable/optical devices
3. Cannot disable indexing at all - because I don't need full text search, only searching by tags which I associate with files manually

I'm still looking for solution to tag my files. I know that I can use e.g. Calibre for docs, id3 for music, Shotwell for photos but I wanted to have tags integrated with the system or at most one application (and Tracker should fit it well if it was usable for me)

---


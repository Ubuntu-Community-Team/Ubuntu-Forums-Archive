---
title: "program that does mass HTML saving?"
date: 2007-07-27
forum: The Cafe
---

### Post by Polygon on 2007-07-27
Ok, so i help run a forum that is run by one of those sites (proboards.com if you must know) that does not allow the users to make backup of the databases....  Im sure they keep their own backups but i know that one of these sites similar to proboards got hacked and the database got jacked and 100's of boards lost huge amounts of posts, and that would be really bad as there is a lot of artwork and stories on this forum and it would suck to lose it all

So im asking for suggestions on how to make a backup of it? i was thinking of some program that could like traverse links in a web page and then just save the html of the current page, then go on to the next one, save the html etc, but I have no idea if this exists

or there is the manual way where i go to each page in each topic and save the html manually, which works but will take a insanely huge amount of time.

Any suggestions on how this can be accomplished? Preferably not the manual way? :D

---

### Post by mcduck on 2007-07-27
wget can do that, but I don't remeber what switches you needed for it to work that way. Check 'man wget' ;)

---

### Post by vanadium on 2007-07-27
HTTrack is more specifically designed to mirror websites, although indeed wget can also do the job to a large extend. I am not sure how well it will work with a database-driven website, though. It might download the same page multiple times and you will not be able to use search functionality. Be prepared for a very lengthy download that needs lots of disk space.

---

### Post by popch on 2007-07-27
The product you are looking for would be a  _[web crawler]("//http://en.wikipedia.org/wiki/Web_crawler")_, I think

---

### Post by super breadfish on 2007-07-27
I had the exact same problem with Proboards. I tried using wget, but there were so many pages it was going to take days, and most of the what is was downloading was not usable anyway. Most of the pages it downloaded were things like the post new message page over and over again, and the few actual posts it did download needed heavy editing to be able to use properly. I gave up in the end.

To get it right you would need a tool that would only download the pages with posts in, or somehow configure wget to do it, but I have no idea how you would go about that.

---

### Post by B0rsuk on 2007-07-27
Sounds like you're looking for [curl](http://en.wikipedia.org/wiki/CURL).

---

### Post by Polygon on 2007-07-28
I think wget is the program to do it, and i read the man page and im running:

wget -r -p -np -k --load-cookies ~/.mozilla/firefox/ys0b8nnf.default/cookies.txt WEBSITEURL\

But when i try to open the pages in firefox, its giving me a XML error. Any suggestions?

---


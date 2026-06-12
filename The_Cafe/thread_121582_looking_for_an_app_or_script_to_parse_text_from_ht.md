---
title: "looking for an app or script to parse text from html"
date: 2006-01-25
forum: The Cafe
---

### Post by soonindallas on 2006-01-25
I'm a job seeker.  I want to make a mailmerge file from text that I could get from a website's pages by parsing stuff out of their html.

On the site I'm looking at, each company has a profile page containing information I want: the company's mailing address and the name of the guy I want to write to behind a predictable title.

If I can also parse some information out of links in an "index" page I can automate the generation of urls to pass to the parser.

This information appears in the html source when I ask firefox to display it.

Would anyone with experience of this kind of task please give me some recommendations ?

---

### Post by stream303 on 2006-01-26
I often use Lynx to parse out html.

You could use Lynx to actually navigate to the site/page, and then issue the "print" command, which will prompt you to save to a local file.  This "printed" file is stripped of html.

I'm sure there are other ways, but Lynx has always been one of my favorite browser/tools on the command line..

---

### Post by soonindallas on 2006-01-26
thanks stream.  I used Lynx as you suggested.  It does help strip the tags and I went ahead with it.

I was looking for a way to filter the text and automate the task for 100 or so webpages at predictable urls.

I'm about half way done.  If anyone can chip in with another idea I would appreciate it.

---

### Post by sapo on 2006-01-26
This sounds like spamming stuff :rolleyes:

---

### Post by Kerberos on 2006-01-26
PHP can do it pretty well.  I made a script for fetching wow items and parsing the info (similar thing).

$remotefilename = http://wow.allakhazam.com/db/item.html?witem=' . $itemno;
$externalinfo = file2string ( $remotefilename );

Then just use string functions on $externalinfo to filter out the bits you want.  Write it to MySQL if your feeling exotic. :)

---

### Post by Kerberos on 2006-01-26
double post.  are these forums running on windows server or something?

---

### Post by soonindallas on 2006-01-27
kerebos: thanks for the suggestion.  I'll look into that for fetching the pages.

yesterday I manually fetched 40 or so web pages and saved the text with Lynx.  Then with grep -f keywords * >> foobar compiled a file foobar with eveything I need.

should have thought of grep before...

---


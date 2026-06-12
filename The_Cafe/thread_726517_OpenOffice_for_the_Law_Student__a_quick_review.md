---
title: "OpenOffice for the Law Student:  a quick review"
date: 2008-03-16
forum: The Cafe
---

### Post by Brunellus on 2008-03-16
(This originally appeared as a post on my blog, [here.]("http://ouij.livejournal.com/261380.html"))

OpenOffice.org is not ready for my desktop. There, I said it. Flame me, O my Free Software-using comrades.

I've managed a semester and a half so far without having to resort to proprietary software. I use Firefox for all my browsing--even for WestLaw and LexisNexis. I use vim and LaTeX to prepare my outlines. My ASUS eee PC runs Xandros. My home computer runs Ubuntu.

And, yes, up until now, I have used OpenOffice.org for my word-processing needs. OpenOffice Writer is a decent word processor--at least as good for most users as Microsoft Word or WordPerfect. OpenOffice Writer has served me well thus far in Legal Writing class: several drafts each of two memoranda, pleadings, and a motion. But the upcoming appellate brief spells the end of its usefulness.

Appellate briefs need Tables of Authorities. For the non-lawyers out there, a ToA is a kind of sectioned bibliography for lawyers: it indexes all the various citations used in a document by type of authority (constitutions, statutes, regulations, case law, secondary authorities, etc.).

MS Word and WordPerfect have table-of-authority builders built right into the program. Essentially, the ToA builder goes through the whole document, looking for anything that might look like it's a citation. Once it finds a possible citation, it stops: the user can then mark the citation and add it to an index. In the end, you end up with something that looks like this:

```

TABLE OF AUTHORITIES

BROWN V. BOARD OF EDUCATION, 273 U.S. 177, 93 F.2d 14
(1953)...................1, 2

```


There, you see Brown, its full citation in Blue Book format, and the pages where it's cited.

Now, OpenOffice and LaTeX should be able to do a simple trick like this--and do it better. But they're structurally different programs. Instead of treating the document like one long stream of text, they use a "structured document" model.

Theoretically, the structured document should be better: you define the logical parts of your document and let the program deal with all the fiddly character-by-character design issues. To make this work, you need to have a separate bibliographic database, and then insert tagged references into the document as you go. Sounds good, right?

Wrong. In OpenOffice, as in TeX, it's the bibliographic package (bibtex or some such) that generates the formatted citation. And, wouldn't you know it--there aren't any style files out there for legal citations.

Sure, TeXheads, tell me about jurabib or biblatex. But all the style files kicking around are mathematics, sciences, or engineering. I'm lucky if I find a regular humanities style file--never mind actually find anything useful for us lawyers.

And I really don't have the time or the inclination these days to break down and really learn any of the bibliographic systems in *nix to make them work for lawyers.

So this is what I'm reduced to. I'm going to have to crawl back to Microsoft Office for an appellate brief. Luckily, Word 97 runs very well in WINE.

Still, I feel a bit annoyed at having to go back to Microsoft for this. What do I have to do to get decent ToA support out there in OO.o or TeX? Where do I post the bounty?

* * * 

POSTSCRIPT:  I suppose I should be happy that OO.o is such a capable piece of software for general use.  After all, how many lawyers are there that use Free Software, anyway?  But as things stand, I'm more than a little annoyed that I'm going to have to go crawling back to Microsoft.  

Maybe I'll e-mail the Software Freedom Law Center and ask how they do it in-house over there.   *sigh*

---

### Post by Daveski on 2008-03-16
Our legal dept at work swears that most firms use Workshare Professional (used to be called DeltaView): [http://www.workshare.com/products/wsprofessional/](http://www.workshare.com/products/wsprofessional/)

Is there a functional equivelant for OOo? Have you seen this Brunellus?

---

### Post by Brunellus on 2008-03-16
> **Daveski said:**
> Our legal dept at work swears that most firms use Workshare Professional (used to be called DeltaView): [http://www.workshare.com/products/wsprofessional/](http://www.workshare.com/products/wsprofessional/)

Is there a functional equivelant for OOo? Have you seen this Brunellus?
The document comparison functions are taken care off natively in OOo.  There is a "Compare Documents" tool built-in.  

I was alwas amused at work when people needed DeltaView--the output was essentially the output of ```
diff
```.

What I'm looking for really is a way/means to get my citations and indexing right, which is a real pain.  I'm trying to get in touch with the guys at the Software Freedom Law Center to see what they do.  If anybody knows how to do it, they will, and maybe I can get some of their "best practices" out there in general circulation.

---

### Post by Atomic Dog on 2008-03-17
My issue with OpenOffice is the slight differences when a document is opened in Word.  I can't take the risk.  If I am writing a document to print on paper then I use OpenOffice.

---

### Post by Brunellus on 2008-03-17
the difference in document conversion are certainly an issue.  OOo (as well as Abiword and Kwrite) make up for this, though:  the direct export to PDF has been extremely helpful.

Again, put positively, OOo seems to be well-suited for most users.  I would say that for certain users--academic users outside the legal field-- it's probably much better out of the box than MS Word.  But as a law student, I still find it somewhat lacking.  

What I have not yet found is whether the shortcoming is inherent to the software or my inability to use it .

---

### Post by quinnten83 on 2008-03-17
I hate to sound this naive, but have you tried contacting the OO.o devs?

---

### Post by 50words on 2008-03-17
I am an attorney, and I use OOo for everything. I also teach appellate writing at the University of Minnesota Law School.

Word's ToA wizard is garbage, and my students who try to use it inevitably go back to doing it by hand--or just take a reduced grade on formatting. You have to check the ToA by hand in the end, anyway, because the wizard will always miss quotations that split pages, for example. You also have to go through the ToA and edit all the citations, as inline citations are not what should be showing up in your ToA.

It takes almost no additional time to do the page numbers yourself.

Exactly how many appellate briefs are you writing, anyway? Most law students only write two or, at most, three, during three years of law school. I hardly think saving perhaps 10-15 minutes (at the most) on the job is doing much for your study time.

While it would be nice to see a ToA wizard in OOo, that hardly makes it inadequate for legal work.

---

### Post by jonathonblake on 2008-03-19
> **50words said:**
> You have to check the ToA by hand in the end, 

This question really belongs on the OOo forum.   There is a way to create a ToA within OOo, but I don't remember how/what was done.   My guess is that it was a specific extension, in combination with specific styles.

xan

jonathon

---

### Post by fjf on 2008-03-20
I am no lawyer, but I write papers (biomedicine) and the lack of a reference manager-type of software that is easy to install and use is a real problem in my field.  I know there are linux alternatives, but I was not able to even make them run.  Maybe I am not geeky enough ;)

---

### Post by hyper_ch on 2008-03-20
I've used OOo in my final two years at law school... wrote my master thesis with it... formatting the whole thing (well, while writing alread assigning proper formating blocks for paragraphs, citations, ...) took me about 3h. Some of my buddies formatted their thesis 2 or 3 days because in M$O the footnotes were sometimes on the wrong page, the formatting was not consistent through their thesis' and other things like that...

The only thing I missed was not to have the cite-while-you-write capability from EndNote... however you can use EndNote with OOo...

---

### Post by Brunellus on 2008-03-20
> **50words said:**
> I am an attorney, and I use OOo for everything. I also teach appellate writing at the University of Minnesota Law School.

Word's ToA wizard is garbage, and my students who try to use it inevitably go back to doing it by hand--or just take a reduced grade on formatting. You have to check the ToA by hand in the end, anyway, because the wizard will always miss quotations that split pages, for example. You also have to go through the ToA and edit all the citations, as inline citations are not what should be showing up in your ToA.

It takes almost no additional time to do the page numbers yourself.

Exactly how many appellate briefs are you writing, anyway? Most law students only write two or, at most, three, during three years of law school. I hardly think saving perhaps 10-15 minutes (at the most) on the job is doing much for your study time.

While it would be nice to see a ToA wizard in OOo, that hardly makes it inadequate for legal work.
Doing the ToA by hand isn't a big deal if I already know, somehow, that the brief is "done."  

I guess I'm also complaining becasue OOo makes it trivial to generate accurate tables of contents:  define your section-heading style appropriately and use that for all your point headings, and the ToC generates itself.  Fantastic!

So it's not necessarily the time saved, but the aggravation.  I understand that back in the day we'd compose briefs with goose quills and iron gall ink, and that we kids ought to be grateful--but surely we can find a way to use the computer in a way that saves us the time and bother of the old way?

according to [this bug report]("http://www.openoffice.org/issues/show_bug.cgi?id=32712"), ToAs can be done in the indexing system of OOo, but there are a number of outstanding issues that make the auto-indexing inadequate:

```

A few more experience notes:

A legal document can require multiple sections in the ToA -- for reference, this
can be emulated by using "Cases", "Statutes", and "Treatises" as index "keys,"
if you can accept the alphabetical sort those categories get.  It does require
painfully editing every index entry anchor in the document once you realize
this, of course.


You can make as many "user-defined" indexes as you want, but as of 2.0.2
user-defined indexes cannot be sorted alphabetically and do not inherit the
options to 'combine' keys and do page number ranges.  This is a huge drawback to
the index feature and recent documentation suggests it hasn't changed in later
versions.


The alphabetic sort naturally doesn't have the intelligence to numerically sort
statutory references like the below properly (predictable, but an annoyance):

C.G.S. §55-555(a)(1)	
C.G.S. §55-555(a)(11)
C.G.S. §55-555(a)(6)

```

Sigh.

---

### Post by frisket on 2008-03-20
> **Brunellus said:**
> (This originally appeared as a post on my blog, [here.]("http://ouij.livejournal.com/261380.html"))

[...]
Sure, TeXheads, tell me about jurabib or biblatex. But all the style files kicking around are mathematics, sciences, or engineering. I'm lucky if I find a regular humanities style file--never mind actually find anything useful for us lawyers.

But Jurabib *is* for law citations...and humanities. i use it all the time, and there aren't any math/sci style files for jurabib that I know of. And there's Harvard, and Oxford, and Kluwer, and a bunch of other humanities .bst files.

The problem with Humanities bib styles is that they're different for every discipline, so you need to change some of the jurabib parameters. Fiddly, I admit, but not hard.

For capturing citation data from web pages, look at Zotero for Firefox, which can export BIBTeX.

P

---

### Post by Brunellus on 2008-03-20
> **frisket said:**
> But Jurabib *is* for law citations...and humanities. i use it all the time, and there aren't any math/sci style files for jurabib that I know of. And there's Harvard, and Oxford, and Kluwer, and a bunch of other humanities .bst files.

The problem with Humanities bib styles is that they're different for every discipline, so you need to change some of the jurabib parameters. Fiddly, I admit, but not hard.

For capturing citation data from web pages, look at Zotero for Firefox, which can export BIBTeX.

P
Jurabib is for legal citations--in German.  I'm not a German advocate;  I'm studying (and intend to practice) in the United States.

---

### Post by freebeer on 2008-03-20
> **Brunellus said:**
> but surely we can find a way to use the computer in a way that saves us the time and bother of the old way?


If you think about it, the academic world hasn't kept up.  The whole point of citations is to create a standard means of reference to supplementary material.  In the days of pen and paper, it would be far too burdensome to copy all the references, so citations became an "index" (of sorts) to the referenced material.  With today's technology you should be able to create a hyperlink directly to copy/pasted supplementary documentation and submit your document by suitable electronic means.

---

### Post by 50words on 2008-03-20
Tables of authority are for more than just reference. It gives readers an at-a-glance look at the sprinkling of authority throughout a brief and a different way to navigate the text.

Hyperlinks are making their way into legal briefs. In the USDC Minnesota, for example, you can now link to any document in the electronic case filing system (every filed document from the last few years, at least). The same will come for cases, law review articles, etc.

But we will never need to stop citing sources. Hyperlinks are not citations, although they can be useful supplement to citations.

---

### Post by Brunellus on 2008-03-21
> **freebeer said:**
> If you think about it, the academic world hasn't kept up.  The whole point of citations is to create a standard means of reference to supplementary material.  In the days of pen and paper, it would be far too burdensome to copy all the references, so citations became an "index" (of sorts) to the referenced material.  With today's technology you should be able to create a hyperlink directly to copy/pasted supplementary documentation and submit your document by suitable electronic means.

That's a horrible world.  Think about the ridiculous burden on storage and bandwidth!  

Moreover, many things are not yet available electronically, but are fodder for academic and legal writers.  Manuscript and archival collections, for instance, are still largely paper, and will probably remain so for a very long time--there simply isn't the capacity to digitize the information already out there.  

> **50words said:**
> Tables of authority are for more than just reference. It gives readers an at-a-glance look at the sprinkling of authority throughout a brief and a different way to navigate the text.

I hadn't thought of it that formally but now that you put it like that, yes, that works.  

>  Hyperlinks are making their way into legal briefs. In the USDC Minnesota, for example, you can now link to any document in the electronic case filing system (every filed document from the last few years, at least). The same will come for cases, law review articles, etc.



I love electronic case filing.  

> But we will never need to stop citing sources. Hyperlinks are not citations, although they can be useful supplement to citations.

A good citation is more reliable than the most reliable "permalink."  It's also easily-discoverable.  Hyperlinks are useful, but I'd hate to have to navigate to every hyperlink to find out where someone pulled useful language . . .

---

### Post by Jenda on 2008-11-09
Don't generalize &#12484; I'm a third year law student, and I've never needed a ToA... probably because it isn't a standard in my country.

Admittedly, however, I've found this thread while searching for complaints about OOo's Compare Document feature. I am updating an old translation of an updated document, and it seems to me it stops working at the first change it finds (i.e. instead of recognising that one word was added, it will remove the entire paragraph and add it again with the added word). I'm still looking for a solution.

---

### Post by brunovecchi on 2008-11-09
> **fjf said:**
> I am no lawyer, but I write papers (biomedicine) and the lack of a reference manager-type of software that is easy to install and use is a real problem in my field.  I know there are linux alternatives, but I was not able to even make them run.  Maybe I am not geeky enough ;)

I'm in the molecular biology field, and I found that there are many choices for bibliography management.
I currently use Bibus, which plays nicely with Open Office to insert and capture citations in the text. There are many bibliography styles, and you can even create your own, it's really easy to do.

---

### Post by andrewabc on 2008-11-09
Thanks for the tip with Bibus.
Now if only ubuntu would come with OOo3 I would be set.
Too scared to install the 100 files worth 190mb of OOo3 from calcs PPA.

---

### Post by johnnybirdman on 2008-12-17
I've been a lawyer for a little over 5 years and have done 3 or 4 appeal briefs and 1 state supreme court brief. TOA cost more time and effort than writing the actual briefs sometimes.  Citations are a general PIA to dictate and for your secretary but, of course, we need them.  Hopefully better tools will develop.
Best of luck in school.
J.

---

### Post by lukjad on 2008-12-17
I don't mind if you use Word, I find it to be quite good. I took a course in it, and so I know my was around it. If you find that it is easier, or more familiar, or just works better for you, I don't care if you use it or OpenOffice. If you told me that I had to use it instead of OpenOffice, that is where you and I would have problems. Have fun, and I hope you do well in your course. :D

---

### Post by javyn999 on 2009-07-19
Don't mean to resurrect such a dead thread, but thought I'd throw my 2 cents in with a little pointer.

I'm a paralegal that spends much of my time preparing TOCs and TOAs for federal filings online.  The built-in generators in both Word and WordPerfect are total CRAP.

I've found the best way is to scan the brief for authority, pasting it into a Spreadsheet.  Each "sheet" in the spreadsheet is for a type of authority.  Sheet 1 is for cases, 2 for statutes, 3 for rules.   I paste each instance of authority with a corresponding page number in the brief into a cell creating a list down the column.

Then when done, I highlight my list and sort it alphabetically.  Then I copy it back to a TOA template doc I generated with the tabs and whatnot set in the correct format.  

I combine my TOC and TOA doc with the brief and cover page after converting to PDF.  

OpenOffice is not what is going to keep lawyers away from Ubuntu.  A total lack of a decent PDF editor is what is going to keep them away.  pdfedit just doesn't cut it.  More and more lawyers and paralegals are needing full featured PDF editors such as Acrobat or NitroPDF (my favorite - it even Bates stamps!).

---


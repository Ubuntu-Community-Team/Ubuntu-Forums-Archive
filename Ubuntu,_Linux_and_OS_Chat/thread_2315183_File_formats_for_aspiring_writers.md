---
title: "File formats for aspiring writers"
date: 2016-02-26
forum: Ubuntu, Linux and OS Chat
---

### Post by t0p on 2016-02-26
I write fiction, and I'd like to be published some time.  I use LibreOffice, and my documents are .odt format.

If I sent an .odt file to an editor (magazine or book publisher) would it get read?  Or would it be filed 'unreadable' or 'clueless writer'?  What format would be best (remember, I'm using LibreOffice!).

Another idea is self-publication of e-books, using, for instance, Amazon as an outlet.  I believe that is done by some writers.  What format should I use?

Is it all still .doc (or even .docx - obviously I haven't sent anything to a publisher in many years... and does LibreOffice even do .docx, or is that strictly owned by Microsoft?).

As these questions make clear, I know nothing about sending typescripts in electronic document file form.  The last time I sent an MS to a would-be publisher it was a hard copy.  Sending MSS as email attachments was still science fiction back then!  I had a 'word processor' which was a machine that looked like an electric typewriter with a 3-line LCD "monitor".  So, I know nothing.  Please be gentle.  I'm not a virgin... but it's been a while.  :)

---

### Post by pauljw on 2016-02-26
If it were me, I'd look into a desktop publishing software i.e. Scribus.  These programs will import text and graphics and format them in the proper layout suitable for publishing.  As I understand it, and that's not very well, you can upload the file to a publisher and he can import it directly to the printing machinery and publish your work.  Pamphlets, newspaper articles, ad copy to books.  Scribus is in the repostitories so installation is easy.

Here's a link to the Scribus wiki page:

[https://wiki.scribus.net/canvas/Scribus](https://wiki.scribus.net/canvas/Scribus)

Good luck with your work.

---

### Post by grahammechanical on 2016-02-26
Libreoffice File menu has an option to Export as PDF and PDF is an electronic file format. You might want to examine Calibre

[http://manual.calibre-ebook.com/faq.html#what-formats-does-app-support-conversion-to-from](http://manual.calibre-ebook.com/faq.html#what-formats-does-app-support-conversion-to-from)

Regards

---

### Post by pauljw on 2016-02-26
Also, having just spent some time reading up on Scribus, it's rather complex.  The repos also have a program called Calligra Words that seems a bit less intimidating.  As you can see, there are several options to accomplish your goal.

---

### Post by t0p on 2016-02-26
Thanks everyone for the suggestions.  And if there are any more out there, please keep 'em coming!  It's all helpful!!  :)

---

### Post by Graeme_Pietersz on 2016-02-27
You may want to use Scribus for self-publishing, but not to submit something to a publisher.

You could write in a format like Markdown that is easily converted to any format. latex (using Lyx for example) is another possible, although the easiest conversion to .docx is probably via HTML. Plain text may be enough.

Also consider using something like Focus Writer - much nicer for writing fiction. It can save in .odt or plain text, which you can then covert as required.

---

### Post by Bucky Ball on 2016-02-27
You would send any and all sample articles to a publisher (or anyone) as PDFs in the first instance. Simply keep working in Libreoffice then File> Export> PDF.

Different publishers will have different and very specific requirements for your submissions. They'll soon tell you what they require. Don't bother sending if you haven't checked.

In other words, don't ask us, as them, the publishers. Give a publisher you might want to approach in future a ring or an email. They'll be happy to tell you what format you'd be required to submit your work in. 

If you actually get far enough to get a deal and they want to tamper with your work, then they will request a .doc file or something like it. Until then, protect your work and .pdf it is. Don't hand over your work in a format anyone can change without securing some form of agreement with a publisher first. 

Good luck in the literary world.

---

### Post by coldraven on 2016-02-27
Bucky Ball: > If you actually get far enough to get a deal and they want to tamper  with your work, then they will request a .doc file or something like it.  Until then, protect your work and .pdf it is. Don't hand over your work  in a format anyone can change without securing some form of agreement  with a publisher first.
Check out the Security tab after doing File>Export as PDF. There you can make the file non-editable or even non-printable. I've never used it so maybe best to experiment on a dummy file in case it all goes wrong :)

---

### Post by Bucky Ball on 2016-02-27
> **coldraven said:**
> Bucky Ball: 
Check out the Security tab after doing File>Export as PDF. There you can make the file non-editable or even non-printable. I've never used it so maybe best to experiment on a dummy file in case it all goes wrong :)

Exactly. :)

* Just tried it and you need to use a password to encrypt. That would work out fine. You come to a happy arrangement, you give the publishing hacks the password to the PDFs! :D

---

### Post by SagaciousKJB on 2016-02-28
MS Word documents are so widely supported and honestly it may look unprofessional to send some kind of "weird" format. Just save as and choose a 2000 or above MS Word document and virtually every word processing software under the sun will be able to read it.

If you're REALLY in doubt Rich Text Format is still pretty much universal too.

---

### Post by 1clue on 2016-02-29
While I've been out of this for a long time (10 years or so), I seriously doubt that a traditional word processor file is going to go unmodified.

Disclaimer:  I never published a book. I worked internal corporate software documentation for awhile, which used the same requirements as the O'Reilly publisher.

Publishers want their story in a consistent format from end to end.  Every paragraph needs to be exactly the same style as every other paragraph.  Every chapter heading must be identical.  This is almost impossible with Word.  Word lets you change the look of "this particular" section of text without changing its named style, I used to do it inadvertently.

This is extremely not OK for publishers.  Back when I knew something about this, publishers generally wouldn't accept a Word document at all.  Now I expect they would export a plain text file and then have their editors go through it and apply formatting.

Back when I did this, we used some variant of latex. Latex is not an editor, it's a markup language. It's a bit cryptic but probably still used in forum sites like this one, behind the gui editor.  If your book has lots of mathematical equations you'll still probably have to dive into this if something else isn't available.  If you grew up on O'Reilly books for computer topics, then you're familiar with the output of latex.

Markdown dialects would probably be acceptable. Markdown is easy to learn, there are several widespread dialects tailored to something specific (e.g. MultiMarkdown, Github Flavored Markdown) and it does not support crazy mid-document changes of style. More importantly it can be easily converted to pretty much anything else.

I would strongly recommend that you contact one or more publishers you might like to work with and see what they recommend.

<endorsement type="non-free software plug">
For latex or markdown, I would recommend the sublime-text-3 editor ([https://www.sublimetext.com/3](https://www.sublimetext.com/3)), which is **not free** but which IS a fantastic lightweight highly extensible gui editor that runs on Mac, Windows and Linux and has a one-license-per-human eula, any number of machines.  You can download and try for free (There is a PPA for Ubuntu at [http://www.webupd8.org/2013/07/sublime-text-3-ubuntu-ppa-now-available.html](http://www.webupd8.org/2013/07/sublime-text-3-ubuntu-ppa-now-available.html)) The unlicensed code just pops up a message every so often.  Paste in your license and you're done, no more nagging. Add plugins for language support and extra features you want.  I write software for a living, so a fantastic editor with only the features I want is worth the price.
</endorsement>

There are also other editors which understand and properly highlight latex and markdown, some of which are free.

One thing to keep in mind here, if you use latex or markdown or something similar, you can easily convert it to almost any format a publisher might want.  So part of this exploration is to find something you find comfortable, so long as it can be converted to something acceptable and which does not support bad habits.

Markdown and the like were created so that non-technical people could write documentation. While this wasn't really prevalent when I wrote documentation it almost certainly is the way you want to go.

---

### Post by Bucky Ball on 2016-02-29
> **1clue said:**
> I would strongly recommend that you contact one or more publishers you might like to work with and see what they recommend.



Agreed and exactly what I mentioned earlier. You can have your questions answered in a few minutes. What format you should be using for publisher X is something we could only answer by contacting publisher X and asking them, which you can do right now (or in the morning, depending on the timezone). :)

---

### Post by 1clue on 2016-02-29
This is interesting:

[http://www.r-bloggers.com/retrospective-writing-an-oreilly-book/](http://www.r-bloggers.com/retrospective-writing-an-oreilly-book/)

---

### Post by Bucky Ball on 2016-02-29
[Read here]("http://www.baen.com/submit") under the heading 'Electronic Submissions'. [Here's another]("https://global.oup.com/academic/authors/?lang=en&cc=au"). Both very different as not sure what you're aiming at.

That's two. Research the ones you want to approach.

---

### Post by Buntu Bunny on 2016-03-22
> **t0p said:**
> I write fiction, and I'd like to be published some time.  I use LibreOffice, and my documents are .odt format.

If I sent an .odt file to an editor (magazine or book publisher) would it get read?  Or would it be filed 'unreadable' or 'clueless writer'?  What format would be best (remember, I'm using LibreOffice!).

For magazines, just ask them for their submission guidelines. I've used LibreOffice and converted to .doc or .docx as requested. That makes it easy for them to copy and paste.

Depending on the book publisher (for print books) they may accept .doc, but you will likely need to submit in PDF/X-1a format, which LO can't do. So far only Scribus Trunk can do that (1.5 or 1.5.1) Scribus is a desktop publisher, so it's perfect for page and cover design, but you need your text ready to go (and then there's the learning curve of figuring it out). 

> **t0p said:**
> Another idea is self-publication of e-books, using, for instance, Amazon as an outlet.  I believe that is done by some writers.  What format should I use?

Is it still .doc (or even .docx - obviously I haven't sent anything to a publisher in many years... and does LibreOffice even do .docx, or is that strictly owned by Microsoft?).

Yes, still .doc. I publish eBooks through both Amazon and [Smashwords]("https://www.smashwords.com/") and that is the best format (*not* .docx). Kindle Direct Publishing has an online viewer so you can preview how your book looks in their various devices, make adjustments, and upload new files if needed. (In fact, one of the nice things about eBooks is that they can be updated even after publishing). Smashwords will convert your file to epub, mobi (Kindle), pdf, rtf, lrf, pdb, txt, and html formats, and get you into B&N Nook and iTunes, etc. However, their file converter (the infamous "Meat Grinder") is a bogga-bear. (Suggest downloading Mark Coker's free [Smashwords Style Guide]("http://www.smashwords.com/books/view/52"), helpful for Amazon too.)

> **t0p said:**
> As these questions make clear, I know nothing about sending typescripts in electronic document file form.  The last time I sent an MS to a would-be publisher it was a hard copy.  Sending MSS as email attachments was still science fiction back then!  I had a 'word processor' which was a machine that looked like an electric typewriter with a 3-line LCD "monitor".  So, I know nothing.  Please be gentle.  I'm not a virgin... but it's been a while.  :)

You can do it! If you're still interested in doing print books, check out [CreateSpace]("https://www.createspace.com/"). It's all free, they do a good job of explaining how to do things, and the community it tops for questions. For eBooks, Amazon is more popular and easier to get started with, but Smashwords gives you broader distribution and higher royalties.

---

### Post by t0p on 2016-03-22
Thanks a lot to everyone who shared in this thread!  Much food for thought.  Now, I'm gonna get on the phone and see how my possible target publishers prefer to receive MSS in this new-fangled electronic world...

In the meantime, I'm also looking at possible self-publication for some stuff that might have too small a niche readership (anyone for SF poetry?).  I know a couple of forum users self-publish, and I'd *love*&#8203; to know how they go about their self-publication (I'm reading up all this on the web too, so please don't imagine I'm being lazy and require your info.  I just thought, the more the merrier, yeah?  Especially the experiences of Free software users like myself).

---

### Post by Bucky Ball on 2016-03-23
Science-fiction poetry??? Count me in, if only out of curiousity! Can't imagine there's too many science-fiction poets about, but I'm not in the game so ...

Good luck with it all.

---

### Post by Buntu Bunny on 2016-03-23
> **Bucky Ball said:**
> Science-fiction poetry??? Count me in, if only out of curiousity! Can't imagine there's too many science-fiction poets about, but I'm not in the game so ...

Hey, I've heard of Amish sci fi, so why not poetry. :)

> **t0p said:**
> In the meantime, I'm also looking at possible self-publication for some stuff that might have too small a niche readership (anyone for SF poetry?).  I know a couple of forum users self-publish, and I'd *love*&#8203; to know how they go about their self-publication

Good suggestion, t0p. I would love to hear from other Indie authors and publishers too. Sharing stories is the best way to pick up new tips. 

Indie publishing is perfect for niche writing. I started with a paperback and didn't even entertain submitting manuscripts to publishing houses, because I didn't think any of them would be interested in my niche (homesteading). I was determined to do it all open source (including fonts), however, which presented it's own challenges because almost everyone uses Adobe Acrobat and InDesign. 

What I like about self-publishing is having complete control over the final product, as well as the costs. If one is game, one can do all their own formatting and interior and cover design work, or hire someone to do it. It's work, but for those who like that sort of thing it's a lot of fun. I did it all myself and had huge learning curves with the software (especially Scribus for the book design and Inkscape for my publishing logo). Basically I just use gedit for writing, gimp for images, Scribus 1.4 for formatting and design, and Scribus 1.5 for pdf conversion. After that, it's a simple upload to the printer.

Self-publishing with Print on Demand (POD) means there are no huge printing costs to deal with, and no minimum orders for the author. By going through a seller like Amazon, the books are printed as they are ordered, so all I have to do is collect the royalties. They subtract printing costs, their share, and the rest is mine. Plus authors get paid monthly. Or, you can order your own copies and sell them from your own website or any place you can make them available. Since the author price is only the print costs and shipping, royalties are better that way than through a seller. 

There are a lot of POD companies out there, but I think the big 3 are IngramSpark (the self-publishing branch of Lightning Source), Lulu, and CreateSpace (the self-publishing branch of Amazon). For print books, Lulu pays the lowest royalties. Before Lightning Source created IngramSpark, most indie authors went with them. There are book set-up fees and an annual subscription fee per title to stay in their catalogue, but you could set your own wholesale discount and receive the best royalties. That changed with the creation of IngramSpark and the wholesale discount is now set too high to make it attractive (to me anyway, especially after other costs.) I went with CreateSpace (CS) because it's all free unless you hire services. (Obviously at least an editor is a must). Most POD printers offer free ISBNs, but I recommend buying your own from [Bowker]("https://www.myidentifiers.com/"). That names you as publisher (instead of them) so you can always switch printers if you wish. (But don't buy the barcodes from Bowker. CS, for example, will create and add those to your book cover for free).

Now the downside. Self-publishing means self-promotion. In fact, most self-published books can only expect to average 200 copies sold in the book's lifetime. A traditional publisher will do the promotion for you, because they have a vested interest in making a profit. If you self-publish you're on your own. I credit the success of my first print book to my homesteading blog, which had become surprisingly popular. That meant I had a ready-made target audience. With giveaways for those who helped spread the word, I've been blessed with really good sales. My first book has sold about 6000 copies. Second book hasn't done as well, but sales are steady. 

Another downside is that most brick-and-mortar book stores won't stock self-published works. If they do and they don't sell, they can return them. You pretty much have to focus on online sales, but that's what most of us want anyway. 

eBooks. Not a fan, but I got into them just to see how to do it. Since they need the doc format for submission, I use LibreOffice for that. Not an LO fan either, because it does weird things on me sometimes, but it's what I've got. I've [already mentioned]("http://ubuntuforums.org/showthread.php?t=2315183&page=2&p=13458931#post13458931") Smashwords versus Kindle Direct Publishing, but there are others too. One of the biggest problems with eBooks is that folks don't want to pay anything for them. They know there are no print costs, and for some reason they seem to think we authors like to work for free. :roll:

Okay, so now that I've babbled on and one, I'd be interested in hearing someone else's story, although if you have questions, please ask.

---

### Post by mastablasta on 2016-03-23
e-books are usually in e-pub format, if you go Amazon you need Mobi or AZW3.

you can also just do PDF.

---

### Post by Buntu Bunny on 2016-03-23
> **mastablasta said:**
> e-books are usually in e-pub format, if you go Amazon you need Mobi or AZW3.

you can also just do PDF.

That's why I like Smashwords. They give you epub, mobi, pdf, rtf, lrf, pdb, txt, and html from the same doc file.

---


---
title: "Think you could host a collaborative textbook on github?"
date: 2011-10-14
forum: The Cafe
---

### Post by ninjaaron on 2011-10-14
*note:  I realize that this is a crazy idea on the level of those ideas that one guy is always posting.  Just sick of 'business as usual' in Academia.*

I want to work on writing a free textbook in my feild that people can use or modify of their classrooms.  I want it to be forkable.  I want it to be written by community collaboration.  I want anyone to be able to use the work for anything, and to be able to print and publish with freedom.  Essentially, I want to write a textbook for my field that has all of the qualities of Open Source software (with some naming rights reserved).

Is there any reason that this would not be possible through github?  It would require teaching humanities nerds to use git, which would be problematic, but I see it as a very viable option for hosting text-based, open, collaborative projects beyond code.

In addition, any ideas about a licence that might be appropriate for a project like this?

---

### Post by dniMretsaM on 2011-10-14
Sound plausible to me. I like the idea of a collaborative, free (as in freedom) book. You could use the GPL for the book, obviously it's not ideal, but it could work. I would recommend you look into the Creative Commons licenses. My personal recommendation would be the CC-BY-SA license:
> 
           [IMG]http://i.creativecommons.org/l/by-sa/3.0/88x31.png[/IMG]         
**               CC BY-SA             **           
                         This license lets others remix, tweak, and build upon your  work even for commercial purposes, as long as they credit you and  license their new creations under the identical terms. This license is  often compared to &#8220;copyleft&#8221; free and open source software licenses. All  new works based on yours will carry the same license, so any  derivatives will also allow commercial use. This is the license used by  Wikipedia, and is recommended for materials that would benefit from  incorporating content from Wikipedia and similarly licensed projects.
[COLOR=#000000][View License Deed]("http://creativecommons.org/licenses/by-sa/3.0")               | [                 View Legal Code]("http://creativecommons.org/licenses/by-sa/3.0/legalcode")[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]All the othe CC licenses can be found [here](http://creativecommons.org/licenses/).
[/COLOR]

---

### Post by el_koraco on 2011-10-14
> **ninjaaron said:**
>   It would require teaching humanities nerds to use git, which would be problematic, but I see it as a very viable option for hosting text-based, open, collaborative projects beyond code.


Yeah, but you'd have to teach humanities to use git. And what would the format they send the texts in be, .doc, .tex, .odf?

---

### Post by dniMretsaM on 2011-10-14
> **el_koraco said:**
> Yeah, but you'd have to teach humanities to use git. And what would the format they send the texts in be, .doc, .tex, .odf?

I would say have a PDF version and an OpenDocument version for starters and if someone wanted to add a new format, they could. Obviously there would have to be people who keep each format the same, but it could work.

---

### Post by el_koraco on 2011-10-14
> **dniMretsaM said:**
> I would say have a PDF version and an OpenDocument version for starters and if someone wanted to add a new format, they could. Obviously there would have to be people who keep each format the same, but it could work.

How are you gonna merge PDF documents into one?

---

### Post by dniMretsaM on 2011-10-14
> **el_koraco said:**
> How are you gonna merge PDF documents into one?

PDFtk can merge PDF's. And you can edit them easily in LibreOffice Draw (add pages, replace pages, change page content, etc.).

---

### Post by ninjaaron on 2011-10-14
> **dniMretsaM said:**
> Sound plausible to me. I like the idea of a collaborative, free (as in freedom) book. You could use the GPL for the book, obviously it's not ideal, but it could work. I would recommend you look into the Creative Commons licenses. My personal recommendation would be the CC-BY-SA license: [...]

Yeah, I like the idea of something like that for a textbook too.  Share-Alike isn't really what you would want for something like a work of fiction or a monograph or an article, but when I think about something like a textbook, it seems like the ideal way to do it, really.  It's also listed as a license that fits the Debian Free Software Guidelines, so it's possible to market the book as "Open Source" without being to far off the mark.

> **el_koraco said:**
> Yeah, but you'd have to teach humanities to use git. And what would the format they send the texts in be, .doc, .tex, .odf?

First Choice: Plain Text
I was thinking that the "source" could be maintained as unicode plain text (it's "a universal interface," after all), and various other formats could be maintained as branches.  In my opinion, plain text can be formated to have just as clear a layout as anything else, and it's the best for tracking changes.

However, there is a possible issue: bi-directional text (Biblical Hebrew textbook).  Direction isn't encoded in plain text (obviously), so it would be dependent on whatever text-editor is being used.  Abiword and LO/OO can handle bi-directional text perfectly.  Gedit also does a pretty friggin' good job, and all of those programs are cross-platform, so I think that would be ok.

The other thing would be difficulty with using tables, which you often need in language textbooks.  Tables can be made in plain text, but they aren't very portable.  Images would also be an issue, if they were ever deemed important (and they might be in a chapter about the history of the script or something).  This leads me to choice #2, which I think is the best option right now...

Second Choice: HTML
HTML is also basically plain text, so tracking changes would be pretty easy, even if it is slightly less accessible than plain text.  Basically every modern wysiwyg editor can read and write HTML like any other document format.  It makes it easier to format text, and tables and images are a breeze.  I was originally thinking about RTF, but it's proprietary, and I think it's less universal than HTML, and they do about the same thing (in terms of formating text).  It can also be easily ported to other formats.  text direction and rendering would depend on the browser, but browsers generally do a better job at rendering weird scripts than any other class of program, so it's not a big worry.

Third Choice: ODF
ODF can give professional layout options.  However, it is less universal than HTML, and it's a compressed archive, which makes tracking changes yet more difficult.  Anyone who has ever looked inside of a ODF archive knows that, while it's all XML, and it is technically "Human Readable,"  It's not exactly something a human wants to read.

Fourth Choice:  Google Docs
Google docs is awesome for collaborative document editing and change tracking, one of the best out there.  However, the framework isn't ideal for taking full advantage of an open-source development model and license, which is sort of the point.

---

### Post by dniMretsaM on 2011-10-14
> **ninjaaron said:**
> First Choice: [realtalk]

It would probably be the best for formatting and stuff, as its an extremely powerful platform (for lack of a better term) that can easily handle multiple languages, pictures, table of contents, etc. It's also completely universal. What computer do you know of that doesn't come with a web browser. And most e-readers support HTML now too. And it's super easy to print from a web browser, so those who want a printed version can easily do that. It would obviously require someone with HTML experience to write though.

---

### Post by ninjaaron on 2011-10-14
Oh yeah.  TeX should also get honorable mention.  I like the idea of tex a lot, and in many ways, its the best option for doing a book, but it's much better adapted to maths and natural sciences than linguistics.  This has kept me personally from using it for my work.  However despite certain benefits of tex for working with a book, HTML is is still a much more widely used format.  I think, as long as each chapter was consistently laid out, automated conversion to tex with a script shouldn't be exceptionally difficult for someone who knows the format better than I do.

> **dniMretsaM said:**
> It would probably be the best for formatting and stuff, as its an extremely powerful platform (for lack of a better term) that can easily handle multiple languages, pictures, table of contents, etc. It's also completely universal. What computer do you know of that doesn't come with a web browser. And most e-readers support HTML now too. And it's super easy to print from a web browser, so those who want a printed version can easily do that. It would obviously require someone with HTML experience to write though.

I'm no wiz in HTML, but I know the basic tags for text formatting, images, tables, etc.  It's a matter of an afternoon to figure that stuff out.  But, even someone who doesn't know any HTML will be able to work with it on almost any wysiwyg editor.

Anyway, I can probably handle tidying up contributions until it grows beyond me, if that ever happens.

---

### Post by ki4jgt on 2011-10-14
> **ninjaaron said:**
> *note:  I realize that this is a crazy idea on the level of those ideas that one guy is always posting.  Just sick of 'business as usual' in Academia.*

Awwe I feel loved LOL. There's nothing wrong with a crazy idea though LOL. That's how most modern inventions (technologies) came to be. As for your book, I would Google Doc it. (That's just me) It's easier to collaborate b/c you can actually see what others are writing (while they're writing it) which may not be as important on source code, but would allow you to expand on each others ideas better.

That's just my two cents.

---

### Post by doorknob60 on 2011-10-14
If I had to vote, I'd go with HTML, since it a plaintext open standard format, that supports all the formatting and images you may need, and can be viewed easily with any browser (unlike something like ODF or even PDF), and git would be able to handle it well since it's plain text (unlike PDF).

---

### Post by sujoy on 2011-10-15
IMO make it an org document. So now you can track changes, export to pdf/html/ etc etc.

---

### Post by matthew.ball on 2011-10-15
I do this with a graduate student in computer science (I am in the humanities). We both use emacs and (as sujoy suggested) just use org-mode to export to PDF when we want to view the final document (we could export to HTML or ODF, but just choose PDF). There is some specific LaTeX code in there (mainly for tableaux proofs and sequent calculi), but this is obviously not essential for a collaborative textbook. We basically make our own edits and do weekly pushes/pulls (this works, because we are each working on different topics within the greater topic).

I was introduced to this idea by a friend who did this "style" of editing with his advisor and his Honours thesis. It works pretty effectively I think.

---

### Post by ninjaaron on 2011-10-15
This org thing looks better in terms of readability.  However, it requires emacs, which not everyone will want to learn (and I'm a member of the cult of VI, so I can't hardly endorse a emacs-only format).  It also requires the use of a simple markup, which, while apparently simpler than HTML, must still be learned, whereas it is possible to edit HTML documents in almost any modern wysiwyg editor, which lowers the bar for participation.

So basically, while the format might be better, the fact that the user-base for this format is small (by comparison) means it's probably not as good for this project.

---

### Post by ninjaaron on 2011-10-15
> **ki4jgt said:**
> Awwe I feel loved LOL. There's nothing wrong with a crazy idea though LOL. That's how most modern inventions (technologies) came to be.I almost mentioned you by your monkier, but I didn't want to get an infraction (I get infractions for everything these days).
:p
> As for your book, I would Google Doc it. (That's just me) It's easier to collaborate b/c you can actually see what others are writing (while they're writing it) which may not be as important on source code, but would allow you to expand on each others ideas better.

I'll agree that Google Docs is the obvious choice for collaborative document creation (until LibreOffice Online hits, or so I hope), but I don't see simultaneous editing as a big thing here.  Github also has a complete toolset for cloning the docs locally, branching, forking, version control, et al.  That is, github allows me to make the most out of having an open license, where Google Docs isn't really designed for something like that.  In addition, github is based on open-source technologies itself and Google Docs is at least partially closed.  That's not such a big deal, but I prefer an open platform when I have the option.

---

### Post by ssam on 2011-10-15
one of the kernel developers is writing a book on multithreaded programming in latex, and using a public git to host it.
[http://paulmck.livejournal.com/tag/perfbook](http://paulmck.livejournal.com/tag/perfbook)

There are a couple of other text markup languages that might be more suitable than latex.

[https://secure.wikimedia.org/wikipedia/en/wiki/Markdown](https://secure.wikimedia.org/wikipedia/en/wiki/Markdown)
[https://secure.wikimedia.org/wikipedia/en/wiki/ReStructuredText](https://secure.wikimedia.org/wikipedia/en/wiki/ReStructuredText)

another solution would be to host a wiki. there are many wiki systems that are not to hard to run. quite a few people are familiar with the syntax. if it is generally useful book then you could host it on wikibooks. [http://www.wikibooks.org/](http://www.wikibooks.org/)

---

### Post by Thewhistlingwind on 2011-10-15
HTML

Just, HTML.

That or TeX.

HTML in particular now has the benefits of video and audio.

I mean, if your going to do something crazy, may as well make it REALLY crazy!

---

### Post by tgalati4 on 2011-10-15
I would do a shotgun approach.  Post an outline of the book on several services:

wikipedia or wikibooks

google docs

github (text or html)

PDF drafts on various subject-matter websites.

Then sit back and wait to see which one gets the most hits and activity.  After a while it will become clear which method to continue with and abandon the others.

---

### Post by ki4jgt on 2011-10-15
> **tgalati4 said:**
> I would do a shotgun approach.  Post an outline of the book on several services:

wikipedia or wikibooks

google docs

github (text or html)

PDF drafts on various subject-matter websites.

Then sit back and wait to see which one gets the most hits and activity.  After a while it will become clear which method to continue with and abandon the others.

If you use this method, be sure to include the idea within each of the projects as you would have readers who were waiting for updates in each project and would soon grow tiresome as no updates would be made. Also, using this method would lose readers, as when you dropped all the other services, a minority of readers using them would drop interests.

---

### Post by lykwydchykyn on 2011-10-15
Any plain-text markup format would be ideal

 - Tex/LaTex would be best, but they have a steepish learning curve
 - HTML is widely known, but it's cumbersome to type in
 - RST or markdown are very simple to learn, but don't have all the features of the others.

In any case... why not just use a wiki?  It's a collaborative, version-controlled text-development platform -- pretty much ideal for what you're trying to do.

---

### Post by dniMretsaM on 2011-10-15
> **ninjaaron said:**
> (and I'm a member of the cult of VI, so I can't hardly endorse a emacs-only format).

Of all the despicable...[FONT=Arial][SIZE=1]mumblemumblemumble... [/SIZE][/FONT] Tried Vim, found it very unintuitive. Emacs is SO much better. Anyway, another reason to use HTML would be because you could have like video demonstrations built right into the book (assuming you used HTML5). Seriously, how cool would that be? Of course, you might have to have a separate "printable" version with links to online versions of the videos.

---

### Post by ninjaaron on 2011-10-15
> **dniMretsaM said:**
> Of all the despicable...[FONT=Arial][SIZE=1]mumblemumblemumble... [/SIZE][/FONT] Tried Vim, found it very unintuitive. Emacs is SO much better.

This thread is now officially about the text-editor war. :mad:

:lolflag:

---

### Post by Copper Bezel on 2011-10-15
Another vote for the wiki method. I'm in the humanities, and I don't want to learn to use git; most of the other people I know who are also in the humanities would be even less inclined, even if you explained it to them in little words. A wiki is as easy to edit as a forum post. 

I'd also love to see any attempt to tilt at the state-industrial complex that is the modern textbook industry succeed in every way imaginable.

---

### Post by ki4jgt on 2011-10-16
> **Copper Bezel said:**
> Another vote for the wiki method. I'm in the humanities, and I don't want to learn to use git; most of the other people I know who are also in the humanities would be even less inclined, even if you explained it to them in little words. A wiki is as easy to edit as a forum post. 

I'd also love to see any attempt to tilt at the state-industrial complex that is the modern textbook industry succeed in every way imaginable.

With Google Docs out I'm afraid wikis have my vote too.

---

### Post by matthew.ball on 2011-10-16
> **ninjaaron said:**
> This org thing looks better in terms of readability.  However, it requires emacs, which not everyone will want to learn (and I'm a member of the cult of VI, so I can't hardly endorse a emacs-only format).  It also requires the use of a simple markup, which, while apparently simpler than HTML, must still be learned, whereas it is possible to edit HTML documents in almost any modern wysiwyg editor, which lowers the bar for participation.

So basically, while the format might be better, the fact that the user-base for this format is small (by comparison) means it's probably not as good for this project.
Yeah, I wasn't really saying you had to learn emacs to use this method, sort of just "proof-of-concept" so to speak.

I was really just saying I think it works well for me.

---

### Post by earthpigg on 2011-10-16
(Haven't read the thread, only the OP)

Use wiki software (not github) and do not embrace Wikipedia's "consensus" stuff.

Strongly encourage people to copypasta into new sup-pages/forks, and strongly encourage "-stable" contributors to copypasta from those sub-pages/forks back into "-stable".

---

### Post by Biber on 2011-11-06
I was thinking about using git as well and remembered Scott Chacon developing a work flow system with git: [https://github.com/schacon/git-scribe](https://github.com/schacon/git-scribe) The repository is online, the web site currently not.

---


---
title: "Review: Free OpenOffice.org Writer surpasses Microsoft Word under the hood"
date: 2009-02-03
forum: The Cafe
---

### Post by ubuntu27 on 2009-02-03
[http://www.nwprogressive.org/weblog/2009/01/review-free-openofficeorg-writer.html](http://www.nwprogressive.org/weblog/2009/01/review-free-openofficeorg-writer.html)

Sunday, January 11, 2009
**Review: Free OpenOffice.org Writer surpasses Microsoft Word under the hood**

These days, whether for work, home, or school, most people in America use a computer for word processing.

The era of the typewriter ended long ago, and typing speed is considered by many people to be more important than good penmanship.

For over a decade, the king of word processing has been Microsoft Word, perhaps the most well known and widely used component of Microsoft Office.

Microsoft Word is everywhere: on library workstations, on school/college machines, and in workplaces large and small. New computers built by major manufacturers like Dell or Hewlett Packard (HP) often come bundled with Microsoft Works Suite, a cheaper version of Office that includes Word.

Most installations of Word can be found on machines running Windows, but the software is also available for Mac. (Word is not offered for Linux, though it is possible to install and run it on Linux using [Wine]("http://www.winehq.org/")).

Like millions of other users, I have the latest version of Microsoft Office running on my computer, and while I like the interface, I've become more and more dissatisfied with Word's performance.

This weekend, I was preparing a thank-you card to send to a friend who has long been a source of inspiration and strength for myself and the rest of the Northwest Progressive Institute team.

The card, which I created in Word, included several lines of text on the front, plus a photograph taken by an NPI staff member and a high resolution [SVG]("http://en.wikipedia.org/wiki/Scalable_Vector_Graphics") I had illustrated in [Inkscape]("http://www.inkscape.org/") and exported to [PNG]("http://en.wikipedia.org/wiki/Portable_Network_Graphics").

When I printed the document, I was annoyed to see that the photograph was fuzzy and the lines on the graphics rough.

I knew that Word's image compression must be to blame, because I can get sharp and beautiful photo prints using Adobe software.

I could have sent the card anyway, but it just wasn't crisp enough for me.

I exported the document to portable document format using Microsoft's [Save As PDF Add-In for Office]("http://www.microsoft.com/downloads/details.aspx?FamilyID=4d951911-3e7e-4ae6-b059-a2e79ed87041"). Then I tried to print it from Adobe Reader to see if the quality would be any better. The graphic came out more smoothly, but predictably, the photograph looked even worse.

Frustrated, I wondered how another word processor would compare to Microsoft's. So I fired up [OpenOffice.org's Writer]("http://www.openoffice.org/") and recreated my thank-you card there.

OpenOffice.org is a free suite of productivity tools developed by Sun Microsystems with assistance from the open source community. OpenOffice.org can be installed on all major operating systems, including Linux, Mac, and Windows, but also FreeBSD, Irix, and Sun's own Solaris. It's truly multiplatform.

OpenOffice's user interface is not as sleek as Microsoft Word's. From my perspective, Word 2007's intuitive ribbon and glitzy appearance take first prize in the design category, but that's almost where the superiority ends. When it comes to performance and quality, OpenOffice.org beats Word, hands down.

My first test of OpenOffice was printing that thank-you card. I ran it off, unsure of what to expect. When I picked it up from the printer tray, I was pleasantly surprised. Not only did the photograph on my card look much better, but the graphic did, too. (The text looked identical to the Word printout).

Pleased, I authored a handwritten note on my card, put it inside an envelope, stamped it, and set it aside to be mailed.

Next, I wondered how OpenOffice.org would fare against Microsoft's Save As PDF Add-In. I often need to export documents to PDF, and I've noticed that Word tends to produce PDFs that are considerably large in size.

So I created a two page document as a test. The first page was a fake memo with several paragraphs of Wall Street gibberish (corporate mumbo jumbo) generated using David Powers' fabulous Lorum Ipsum extension.

The second page contained a table. The table shows the outcome of Washington gubernatorial races from 1998-2008. It lists the year, Democratic candidate, and the Republican opponent who was defeated.

The PDF produced by Word was about 196 kilobytes in size. The PDF produced by Writer was about 45 kilobytes in size.

Not only was the Writer PDF four times more compact, but it correctly exported the table on the second page, whereas Word somehow messed up the table borders. (The border widths in the PDF produced by Word are not all the same, but they're supposed to be. The PDF produced by Writer has a flawless table).

Compared to Word, Writer also seems to use slightly less memory. Since I started comparing Writer and Word, I've pulled up Task Manager in Windows to check memory use at regular intervals. For example, while I was writing this post, Winword.exe clocked in at around 104,500 K, while soffice.bin (Writer) clocked in at 99,100 K. Each processor had the same three documents open simaltaneously.

How does Writer compare to Word with other features that I often use? Pretty well. I found that creating documents for Avery label templates was a snap, and Writer's mail merge was easy to use. Writer doesn't yet have as many built in wizards for document types as Word does, but there are a few basics available - letters, faxes, and agendas, for example. Writer also lacks Word 2007's SmartArt, but drawings and graphics can be easily inserted from other programs.

I use bullets and numbering frequently in my documents, and I've long had trouble changing my lists in Word. The 2007 version improved Word's handling of lists, but Writer gives me absolutely no trouble when I want to make changes. Writer's autocorrect functionality is also far less intrusive and annoying than Word's.

What about crash recovery? I purposely terminated OpenOffice.org to see what would happen to a document if the program was suddenly shut down. To my delight, all the data I had entered was promptly recovered when I restarted Writer.

Perhaps the best thing about Writer, though, is that it doesn't default to proprietary file formats. Documents are saved in .ODF (Open Document Format). ODF files can be opened with online collaboration tools like Google Docs or Zoho, as well as the latest version of Corel WordPerfect and IBM Lotus Symphony. (Symphony is based in part on OpenOffice.org).

Microsoft has announced it will add ODF support to Office 2007 in the first half of this year with Office Service Pack 2. When that occurs, Word 2007 users will be able to save and open ODF files and even make ODF the default file format.

Saving in ODF is a really good idea because it allows for ultimate portability. An ODF file can be opened by different word processors on any major operating system, whereas support for proprietary Microsoft formats is more limited.

Just a few months ago, however, Microsoft succeeding in getting the [Office 2007 file formats]("http://en.wikipedia.org/wiki/Office_Open_XML") approved as an open standard. Naturally, Microsoft would prefer that its own file format be the dominant worldwide standard, as opposed to ODF, which is vendor neutral, but that doesn't mean we all have to do what Microsoft wants.

[As Edward Macnaghten explains]("http://www.freesoftwaremagazine.com/articles/odf_ooxml_technical_white_paper?page=0%2C10"):

    Standards exist for interoperability, and office document format standards should not be different. The goal is that someone in country A working for company B using product C can interchange documents with someone in country D working for company E using product D without any thought as to what precisely A, B, C, D, E or any other letter actually is. It simply works. There is no need to worry if any single vendor would continue in the office suite business or not, as any other vendor could be used.

    ODF was created using existing standards with this interoperability in mind, using long public consultation and design periods to achieve this. The benefits of this are evident when examining the resulting formats themselves.

    It has been implemented by a large number of office products and the list is growing.

    OOXML was designed by a single vendor, Microsoft, with no extensive public consultation or design input. It was largely designed to co-exist with their legacy formats using their own products.

Interoperability and standards are a key part of NPI's position on technology policy. Without standards, we're all stuck using proprietary formats that serve as barriers to the free exchange of information.

Imagine if web pages were offered in proprietary formats. We all might have to buy browsers with various support for different formats. It would be a disaster - the Internet simply wouldn't be the accessible medium that it is.

OpenOffice.org is a terrific product that should be considered a must-have for Windows and Mac users. (It's already included by default with many Linux distributions, like Ubuntu). OpenOffice.org is free, completely interoperable, and its Writer word processor beats Microsoft Word where it really counts.

# Posted by Andrew : 2:45 PM 

Original: [http://www.nwprogressive.org/weblog/2009/01/review-free-openofficeorg-writer.html](http://www.nwprogressive.org/weblog/2009/01/review-free-openofficeorg-writer.html)

---

### Post by ProgramErgoSum on 2009-02-04
As far as size of exported PDF is concerned, here is a test that can be performed. In OOo, goto File -> Export as PDF... In General tab, under Images, check 'Lossless compression' instead of 'JPEG compression'. I would expect the resulting PDF to be of slightly larger size.

---

### Post by ubuntu27 on 2009-02-05
wow! After one day, there is only one reply :D I was expecting something along the lines of "Yeah! Go OpenOffice!"

---

### Post by CrazyDesi on 2009-02-05
I like OpenOffice, but until it gets Outlining and a Grammar/Style checker, I am still going to have to switch to Wine every now and then.

---

### Post by halovivek on 2009-02-05
I exported a PDF file to word file using some software. it came around 24 to 30 MB. while tried to open that document it got failed in microsoft word.
But i can able to see it, open, edit in Openoffice. it is really doing good. 
I am using open office for more than 3 years. it fits for me.

---

### Post by Twitch6000 on 2009-02-05
> **CrazyDesi said:**
> I like OpenOffice, but until it gets Outlining and a Grammar/Style checker, I am still going to have to switch to Wine every now and then.

I am not trying to be a fanboy here,but I am pretty sure open office has a spell checker.

I know my Open Office has one and works pretty well.

I also heard that Open Office 3.1 comes with a new and improved one.

As for outlining I wouldn't know what that is as I have never used it lol.

---

### Post by yabbadabbadont on 2009-02-05
> **Twitch6000 said:**
> I am not trying to be a fanboy here,but I am pretty sure open office has a spell checker.

I know my Open Office has one and works pretty well.

I also heard that Open Office 3.1 comes with a new and improved one.

As for outlining I wouldn't know what that is as I have never used it lol.

Spell checker != Grammar/Style checker

;)

---

### Post by SunnyRabbiera on 2009-02-05
still I am not shocked, I absolutely loathe office 2007, @#$%^ ribbon!!!!!!!

---

### Post by Corfy on 2009-02-07
> **ubuntu27 said:**
> wow! After one day, there is only one reply :D I was expecting something along the lines of "Yeah! Go OpenOffice!"

Yeah! Go OpenOffice.org! :D

(Sorry, I would have responded sooner, but I just now saw the thread).

> **CrazyDesi said:**
> I like OpenOffice, but until it gets Outlining and a Grammar/Style checker, I am still going to have to switch to Wine every now and then.

I don't know about outlining, but as for grammar/style checker, it has it, at least for some languages. You just have to install it separately.

[http://extensions.services.openoffice.org/project/languagetool](http://extensions.services.openoffice.org/project/languagetool)

Part of the problem is OpenOffice.org comes in so many different [languages](http://wiki.services.openoffice.org/wiki/Languages), it is hard to have a grammar checker for all of them.

---

### Post by Thirtysixway on 2009-02-08
Openoffice is nice.  I recommended it to one of my friends who is not very tech savvy, she was able to install it and write her papers.  Before, she had to go to the library just to type a paper! :|

---

### Post by karellen on 2009-02-08
no thanks :). for me ms office is the best option

---

### Post by Mohamedzv2 on 2009-02-08
I can't say I like Office 07's interface. I like OOo's and Office 03's interace much better. I've still had problems with both of them however, so I can't say I like either one. My current needs aren't much though, just .docs, and a processor that gets my school work done.

---

### Post by Rokurosv on 2009-02-08
I think the interface and options in MS Office are better, I do like the fact that OO can open docx files, cause sometimes people send docx even when you tell em not to send it in docx....

---

### Post by andrewabc on 2009-02-08
I just tried the language tool grammar checker, but it will not install.
I don't see anyone with similar problem when looking around google.

Also, it requires java to be enabled? With java disabled I get different errors.

I have openoffice 3.0.1 (calcs PPA), and trying to install LanguageTool-0.9.6.oxt

I have java installed (openjdk6)

---

### Post by TWO on 2009-03-06
Really?

OK, so the latest layout changes in Microsoft Office are not brilliant HOWEVER, the grammar checking facility of OpenOffice is absolutely **diabolical**. 

I've just installed the **Language Tool **add on. 

I write in French for my studies and sometimes the tool will tell me there is a grammar error, but not give me a suggestion. It also missed other errors that were picked up on when I used Word to double check the document.

I solely depend upon OO when I am at home, but for the first time, I'm actually seeing sense in splashing out on an office suit that isn't going to cost me several grade boundaries... 

I cannot see this is a viable alternative for anyone in a student/ business environment.

---

### Post by mamamia88 on 2009-03-06
i love word 07 but it's kinda slow under crossover so i use open office for all my college papers

---

### Post by ArtF10 on 2009-03-06
> **TWO said:**
> Really?...I cannot see this is a viable alternative for anyone in a student/ business environment.

Agreed.  For mission critical situations, you want 100% compatibility with "whatever everyone else is using" and MS Office is the only way to guarantee this.

---

### Post by Grez on 2009-03-06
> **ArtF10 said:**
> Agreed.  For mission critical situations, you want 100% compatibility with "whatever everyone else is using" and MS Office is the only way to guarantee this.

Not really. Only if everyone has the latest version (which they don't!)

---

### Post by bakedbeans4life on 2009-03-06
Open Office is a fine piece of software, not perfect, but still very capable. To say that Open Office is at least the equal of Microsoft Office, in any way, invites ridicule.

Most people would never use half of the options available provided by either package. Open Office is free, Microsoft Office is not (unless you believe in piracy as a means to an end).  

Just as Office 2000 and Office 2003 (even Office '97) provide what most people need in a modern IT environment, so does the latest Open Office (with a few exceptions).

What people seem to neglect is to ask the question "Why do we always need to upgrade to the latest version of Microsoft Office {insert latest version here} to remain compatible? Once Office {insert latest version here} opens my latest CV (resume, for our American friends) and I press save, why does my other computer with Office {insert previous version here consigned to history} balk at my request?

Industry as a whole got along without Microsoft Office being judged the standard for many years. The fact that this now seems to be the case is a tragedy.

I know many people that **NEED** Office 2007 and that new "Ribbon" interface will climb down my throat and examine my tonsils over my viewpoint.  

I suspect that the latest version of Open office is more compatible with previous versions of Microsoft Office (previous to 2003) than Office 2007.

This I can see from my own experiments. The bigger picture is something I am missing. What makes Office 2007 superior to previous generations of Microsoft Office?

It is my lot in life to get many Microsoft people telling me that I lack vision and morale fortitude (that last remark was not made up, in case you ask).

So do you judge Microsoft Office on it's quality, or it's ubiquity?

---

### Post by cb951303 on 2009-03-06
I don't use MS office but I also don't think open office is that great. I used it on daily basis for my latest project (after failing with latex :() for a month and I think it needs a lot of improvement in linux. As always (*me points to mozilla) while the windows version works great, linux version is ugly, glitchy and buggy.

---

### Post by bakedbeans4life on 2009-03-06
> **cb951303 said:**
> I don't use MS office but I also don't think open office is that great. I used it on daily basis for my latest project (after failing with latex :() for a month and I think it needs a lot of improvement in linux. As always (*me points to mozilla) while the windows version works great, linux version is ugly, glitchy and buggy.

So it is a question of aesthetics, not functionality?

---

### Post by lykwydchykyn on 2009-03-06
Did anyone else notice that the article originates from Redmond, WA?  I thought that was kind of ironic and amusing.

---

### Post by hessiess on 2009-03-06
Im sticking with LaTeX untill someone mackes a word prosessor that produces eaven half decent typesetting, and does *not* need a mouse.
Also, I have found the spell checker in Vim to be vastily supirior to the one in open office, and even MS word.

---

### Post by cb951303 on 2009-03-06
> **bakedbeans4life said:**
> So it is a question of aesthetics, not functionality?

especially in office applications the gui design and quality is very important. if you want to call it aesthetics then do it but know that I'm not talking about eye candy. Also other then "ugly" I said two other things. Have you read them? Or you just didn't read because you couldn't wait to reply just because I didn't like an open source application.

---

### Post by bakedbeans4life on 2009-03-06
> **cb951303 said:**
> especially in office applications the gui design and quality is very important. if you want to call it aesthetics then do it but know that I'm not talking about eye candy. Also other then "ugly" I said two other things. Have you read them? Or you just didn't read because you couldn't wait to reply just because I didn't like an open source application.

I could not care if you use a commercial, freeware or "open source" application.But I think this is not what you took afront to. You use Microsoft Office (2003 or 2007)vintage do you not?

---

### Post by cb951303 on 2009-03-06
> **bakedbeans4life said:**
> I could not care if you use a commercial, freeware or "open source" application.But I think this is not what you took afront to. You use Microsoft Office (2003 or 2007)vintage do you not?

quoting from myself
> 
I don't use MS office but I also don't think open office is that great....


---

### Post by andras artois on 2009-03-06
In my eyes OpenOffice is brilliant much better MS Word. The only place I really see OpenOffice lacking in is in Presentation. I got my Dad using OOo and he was quite pleased with it and it did everything he wanted but in Presentation it wouldn't display some of the MS Powerpoint slides correctly.

The spell checker in Writer is lacking a bit though, that is one of things that could do with some improvement.

I can see OpenOffice becoming much more popular, especially in large companys.

---

### Post by bakedbeans4life on 2009-03-06
> **cb951303 said:**
> quoting from myself

So is life, move on I am told.

---


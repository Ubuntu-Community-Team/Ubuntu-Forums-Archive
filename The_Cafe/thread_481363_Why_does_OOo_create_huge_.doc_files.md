---
title: "Why does OOo create huge .doc files?"
date: 2007-06-22
forum: The Cafe
---

### Post by hellmet on 2007-06-22
I've noticed this a few times that a .doc file is much larger, about 3 times bigger than its respective .odt file. Why is this so? The same file on MS Office is much smaller, usually half the OOo .doc size? 

  Am I doing something wrong? Is there some setting for this too?

I was not sure where to post this thread. Please move it to the appropriate forum.Thanks

---

### Post by init1 on 2007-07-24
> **hellmet said:**
> I've noticed this a few times that a .doc file is much larger, about 3 times bigger than its respective .odt file. Why is this so? The same file on MS Office is much smaller, usually half the OOo .doc size? 

  Am I doing something wrong? Is there some setting for this too?

I was not sure where to post this thread. Please move it to the appropriate forum.Thanks
Same thing happened when I made an excel spreadsheet. I don't know why.

---

### Post by DC@DR on 2007-07-24
It might be because OO converts the .odt files to .doc format, which will have to put some extra *stuffs* to make it compatible with M$ .doc files (which means it could be read by M$ Word). Since it's reverse-engineering (and then I think you should not blame OO for this issue, but point it to Redmond, since they use proprietary format, kinda vendor lock-in sh*tty), it's not optimal and I hope now you got the idea :-)

---

### Post by Tundro Walker on 2007-07-24
It could be for the same reason that MS Office Word HTML files are so bloated.  What MS Word does when you "save as" HTML is use an MS Word XML code that bloats the web-page to high-heaven so it's still backwards compatible to return to .doc format if you so choose.  If you use their (extra) HTML cleaner add-on, the resulting stripped down web-pages are usually 1/10 the size of the retro-gradable ones.

I'm thinking OOo does the same thing.  They keep enough open source code in it to let it retro-grade back to an .odt if necessary w/o losing any features.

Of course, this is just a guess.

---

### Post by init1 on 2007-07-24
> **Tundro Walker said:**
> It could be for the same reason that MS Office Word HTML files are so bloated.  What MS Word does when you "save as" HTML is use an MS Word XML code that bloats the web-page to high-heaven so it's still backwards compatible to return to .doc format if you so choose.  If you use their (extra) HTML cleaner add-on, the resulting stripped down web-pages are usually 1/10 the size of the retro-gradable ones.

I'm thinking OOo does the same thing.  They keep enough open source code in it to let it retro-grade back to an .odt if necessary w/o losing any features.

Of course, this is just a guess.
Yes, MS file formats are incredibly bloated. An empty MS Word file takes up about 15K. RTF is much better. Even HTML takes up less space, and that was designed to be readable, not tidy. I also notice HTML made by MS products is bloated. Besides, I prefer pure text editors for my scripting.

---

### Post by kamaboko on 2007-07-24
> **hellmet said:**
> I've noticed this a few times that a .doc file is much larger, about 3 times bigger than its respective .odt file. Why is this so? The same file on MS Office is much smaller, usually half the OOo .doc size? 

  Am I doing something wrong? Is there some setting for this too?

I was not sure where to post this thread. Please move it to the appropriate forum.Thanks

Are you down to your last 100K of hard drive space?

---

### Post by init1 on 2007-07-24
> **kamaboko said:**
> Are you down to your last 100K of hard drive space?
Sounds like MS's philosophy.

---

### Post by Turboaaa2001 on 2007-07-24
I agree with the previous posts. But even then I personally don't care since storage is so cheap. Right now you can get a Petabyte worth of storage for $1 Million USD (roughly $480K British Pounds). If you filed it with music your master play list would loop every 100 years.

Or you could just buy a single Hitachi 1TB drive for a couple hundred.

---

### Post by Peyton on 2007-07-24
Well, he didn't say it was a *problem*.

---

### Post by kamaboko on 2007-07-24
> **init1 said:**
> Sounds like MS's philosophy.

Not at all.  I don't care if one is using Apple, Linux, or MS.  Most people I know have GB's of hard drive space available.  What's even 1MB for a file when one has 50 or more GB of space?  It's just strikes me as whiny.  It's up there with complaining that the pickle one got with their sandwich isn't big enough.  God...be quiet and eat the sandwich.

---

### Post by Tundro Walker on 2007-07-25
This kinda goes to the debate other threads have gone on about...where just because we have the power and space these days, does that mean we shouldn't be as interested in optimized software or condensed files?

My personal feeling is optimization should still be a goal...but then again, I'm an...optimist..?...LOL!  I'm for doing the most with the least.  But, tons of folks are cranking out tons of software, and sometimes don't have the time or inclination (or sheer know-how) to make it as efficient as possible.

I always go back to the "writing a book" analogy.  Some folks will write one sentence and it's all you need to know.  Others (like me) will write a few paragraphs.

Anyways, until someone more familiar with OOo clears up the "why", I still vote for my theory that OOo is creating Word.doc files with embedded OOo code so it can retro them back to .odt format if needed.


SIDE NOTE - I'm forced to use MS Word as a web-page tool at work, and it's really annoying.  On the one hand, it can do quite a bit (fairly WYSIWYG).  But, it likes to assume your bold text should be a certain style when it shouldn't, it's difficult to do Style Sheets in it (you have to use Templates, and even then, it's a real pain in the neck).  I'm all for a "unified" document format, but I still think there's so many formats that one tool can't do everything.  MS Word tries to do it all, and as a Jack of All Trades / Master of None, it's lackluster in the secondary functions (IE: HTML editor).

When I took over a project, there was about 1mb of web-pages I decided to clean up.  I first ran then through MS Words HTML Filter add-on, then HTML Tidy, then hand-tweaked the end result.  When I was done, it all fit in 100k of space.  A 1000% reduction in size.  There's no accounting for hand-crafted quality!  LOL!

The ironic part was, after I got it all done, folks were amazed at how quickly the pages came up over the intranet at work.  But, if you tried opening them to edit in MS Word going forward, it screwed up the files (MS Word thought it was it's version of HTML, so would get all screwy, misinterpret the HTML and bloat the document up again).  I was using Nvu to edit the docs going forward, but others who helped maintain the things didn't know enough about HTML to use Nvu (even though it's a really easy program).  So, I got to turn ALL those docs back into MS Word HTML again...  Essentially, I created a lot of extra work for myself with nothing to gain in the end.  Sad.

---

### Post by Turboaaa2001 on 2007-07-25
I do agree with working for efficiency. I believe that if people would put a little effort (like you did) into their web content we could improve the net's performance.

What i see is there is a need for optimization in different areas. I will admit I skimmed this thread before posting so I don't know if you mentioned this being used for a the web.

In any case, sounds like you should offer to train your colleagues, for extra pay that is, to improve performance.

---

### Post by init1 on 2007-07-25
> **kamaboko said:**
> Not at all.  I don't care if one is using Apple, Linux, or MS.  Most people I know have GB's of hard drive space available.  What's even 1MB for a file when one has 50 or more GB of space?  It's just strikes me as whiny.  It's up there with complaining that the pickle one got with their sandwich isn't big enough.  God...be quiet and eat the sandwich.

Well, first of all, OP didn't sound like whining. And second of all, I was joking. But really, I once thought I had more space than I needed, and now I am running out. There is no need to waste space, like with MS products.

---

### Post by init1 on 2007-07-25
> **Tundro Walker said:**
> This kinda goes to the debate other threads have gone on about...where just because we have the power and space these days, does that mean we shouldn't be as interested in optimized software or condensed files?

My personal feeling is optimization should still be a goal...but then again, I'm an...optimist..?...LOL!  I'm for doing the most with the least.  But, tons of folks are cranking out tons of software, and sometimes don't have the time or inclination (or sheer know-how) to make it as efficient as possible.

I always go back to the "writing a book" analogy.  Some folks will write one sentence and it's all you need to know.  Others (like me) will write a few paragraphs.

Anyways, until someone more familiar with OOo clears up the "why", I still vote for my theory that OOo is creating Word.doc files with embedded OOo code so it can retro them back to .odt format if needed.


SIDE NOTE - I'm forced to use MS Word as a web-page tool at work, and it's really annoying.  On the one hand, it can do quite a bit (fairly WYSIWYG).  But, it likes to assume your bold text should be a certain style when it shouldn't, it's difficult to do Style Sheets in it (you have to use Templates, and even then, it's a real pain in the neck).  I'm all for a "unified" document format, but I still think there's so many formats that one tool can't do everything.  MS Word tries to do it all, and as a Jack of All Trades / Master of None, it's lackluster in the secondary functions (IE: HTML editor).

When I took over a project, there was about 1mb of web-pages I decided to clean up.  I first ran then through MS Words HTML Filter add-on, then HTML Tidy, then hand-tweaked the end result.  When I was done, it all fit in 100k of space.  A 1000% reduction in size.  There's no accounting for hand-crafted quality!  LOL!

The ironic part was, after I got it all done, folks were amazed at how quickly the pages came up over the intranet at work.  But, if you tried opening them to edit in MS Word going forward, it screwed up the files (MS Word thought it was it's version of HTML, so would get all screwy, misinterpret the HTML and bloat the document up again).  I was using Nvu to edit the docs going forward, but others who helped maintain the things didn't know enough about HTML to use Nvu (even though it's a really easy program).  So, I got to turn ALL those docs back into MS Word HTML again...  Essentially, I created a lot of extra work for myself with nothing to gain in the end.  Sad.
That's why I like to do raw HTML editing. I have complete control.

---

### Post by hellmet on 2007-07-25
> **kamaboko said:**
> Are you down to your last 100K of hard drive space?
Uhh. I've no *problem*. Its the online job portals that don't accept .docs greater than 100k in size. 
Btw, why did this topic so much attention so late? :D

---

### Post by hellmet on 2007-07-25
> **kamaboko said:**
> Not at all.  I don't care if one is using Apple, Linux, or MS.  Most people I know have GB's of hard drive space available.  What's even 1MB for a file when one has 50 or more GB of space?  It's just strikes me as whiny.  It's up there with complaining that the pickle one got with their sandwich isn't big enough.  God...be quiet and eat the sandwich.
Would you please SHUT UP ? If you don't like the original post, just go away. Just don't increase my BP.

---

### Post by Tundro Walker on 2007-07-26
> **init1 said:**
> That's why I like to do raw HTML editing. I have complete control.

I agree with you on that one, but I've learned that "complete control" can sometimes turn into a nightmare, especially if you're the only one who knows how to do whatever it is you do.

I've gotten burned in the past at jobs where I optimize something which, in the short-term is more complicated, but has longer-term benefits (like raw-coding HTML for optimization).  Then I need to go on vacation, or switch jobs, and someone comes in and doesn't have the foundation skills necessary to do what I've done.  So, they either screw something up (which I later have to fix), or they have to scrap everything I've done and re-do it in a fashion they can maintain (especially true at jobs where I've automated things.)

I've learned over time to temper optimization and automation with the ability for others (co-workers) to do it in my place.  At my current job, I've done quite well...I've automated data runs and such, but they can always be ran manually if need be.  It's just a shame that so many folks in an office environment use a computer day in and day out, yet don't want to learn more about using it beyond email or word processing.  

I treat my computer like a co-worker, and always try to automated process when possible.  Before I show up to work in the morning, my computer's already ran about 4 man-hours worth of mundane work which I've automated, from double-checking systems to make sure there's no errors, to running data or reports for metrics.  That leaves me with more time to automate more stuff.  It's a shame more folks don't operate like that.  Instead, they want to have meetings and "talk" problems to death, or fire off endless emails that don't get much done...and they call that "work".

---


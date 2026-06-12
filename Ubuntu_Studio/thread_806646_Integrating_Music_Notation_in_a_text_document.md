---
title: "Integrating Music Notation in a text document"
date: 2008-05-25
forum: Ubuntu Studio
---

### Post by angelsguitar on 2008-05-25
Hi all.

What's the best way to integrate music notation (fragments of a musical score) in a text doc (for example, an OpenOffice text doc)? Is there a music scoring program that offers an export graphics option (like Finale or Sibelius)?

I've heard of several tools, like OooLilypond, and of course, there's the option of grabbing it directly from a screenshot, although not a very elegant option.  Just checking if there are other options I'm not aware of.

Frankly speaking, I'm used at exporting graphics with Sibelius (as easy and quick as copy and paste; don't even need to use export and import graphics commands) and was wondering is there is a similar tool in Linux

---

### Post by spiderbatdad on 2008-05-25
Not sure if this is the option you're looking for, but "convert" will allow you to convert "screenshots," ie. gifs, jpegs, etc. into pdf docs. For example:```
convert sheetmusic.jpeg sheetmusic.pdf
```Of course if the file name has spaces in it, it must be put into quotation marks.

---

### Post by angelsguitar on 2008-05-25
> **spiderbatdad said:**
> Not sure if this is the option you're looking for, but "convert" will allow you to convert "screenshots," ie. gifs, jpegs, etc. into pdf docs. For example:```
convert sheetmusic.jpeg sheetmusic.pdf
```Of course if the file name has spaces in it, it must be put into quotation marks.

Thanks for your reply, but not quite what I'm looking for.  Maybe I didn't explain myself well, sorry.  I want to be able to embed or integrate musical fragments into a text document.

---

### Post by spiderbatdad on 2008-05-25
of course rosegarden will export notation to a pdf. Uses lilypond as a tool, but you avoid the command line with rosegarden.

---

### Post by Stochastic on 2008-05-25
I'd say the best tool around is the OooLilypond tool that you already know about.  Then again I write all my music in lilypond code, so that tool works quite well for my needs.  I've used it many times with good results (though I haven't needed to install it into my Hardy system yet so I can't vouch for it's compatibility with the latest OpenOffice).

Lilypond's manual also explains how to go about writing a book in TeX (or is it LaTex) with music excerpts incorporated into the text, but that doesn't really seem to be what you're after.

What program are you using for your score writing?  That makes a difference for which method is easiest.

---

### Post by angelsguitar on 2008-05-26
> **Stochastic said:**
> I'd say the best tool around is the OooLilypond tool that you already know about.  Then again I write all my music in lilypond code, so that tool works quite well for my needs.  I've used it many times with good results (though I haven't needed to install it into my Hardy system yet so I can't vouch for it's compatibility with the latest OpenOffice).

Lilypond's manual also explains how to go about writing a book in TeX (or is it LaTex) with music excerpts incorporated into the text, but that doesn't really seem to be what you're after.

What program are you using for your score writing?  That makes a difference for which method is easiest.

Well, to be really sincere, I'm still using Sibelius 5 on Windows.  What I do is that I make the musical examples in Sibelius, open the text document (I use OpenOffice in Windows, by the way), select the musical fragment in Sibelius and copy it to the clipboard, then paste it on the OpenOffice text document as a graphic.

I'm just looking for a way to make that in Linux.  I think this is one of the few things that is stopping me to switch completely to Ubuntu, 'cause I use this feature a lot to produce materials for my music classes.

I've been experimenting with MuseScore and really like it; it's very similar to Sibelius in a lot of ways and does most of the things I need, although a step behind Sibelius in terms of features.  As far as I know, MuseScore does not seem to have a way to export musical fragments as Sibelius does (maybe this would be a good suggestion for a future feature...)

Anyway, seems the best way to integrate music into a text document is using Lilypond, either with Ooolilypond or Tex (or LaTex?? I don't know either).  I'm somewhat familiar with the Lilypond syntax, just was trying to avoid having to code to produce a musical score or fragment.

Thanks to all for the suggestions so far.  Is there any other way I'm not aware of?

---

### Post by Stochastic on 2008-05-27
With Muse score you're able to "save as" then in the file type dialog, select lilypond format (.ly) at the bottom of the drop-down menu.  From there copy and paste the code from a text editor into the OooLilypond plugin.  I know this is a bit more work than Sibelius, but it's also a bit less work than the screenshot/crop/save/import route.

There are also other GUI frontends that will give you a lilypond code output.  I've heard mixed reviews about denemo, you may want to tinker with that.

I personally prefer to code straight into lilypond as it allows for extremely flexible scores (especially when you want to do things like spatial notation, modern notation, baroque notation, chord names, complex time, etc... the list goes on) but at the same time it takes a while to get used to (you'll need to sit with the manual pdf open as you code the first while).

Sibelius is a wonderful program though - I'd spend the money for it if it would run natively on linux.

---

### Post by angelsguitar on 2008-05-27
> **Stochastic said:**
> With Muse score you're able to "save as" then in the file type dialog, select lilypond format (.ly) at the bottom of the drop-down menu.  From there copy and paste the code from a text editor into the OooLilypond plugin.  I know this is a bit more work than Sibelius, but it's also a bit less work than the screenshot/crop/save/import route.

There are also other GUI frontends that will give you a lilypond code output.  I've heard mixed reviews about denemo, you may want to tinker with that.

I personally prefer to code straight into lilypond as it allows for extremely flexible scores (especially when you want to do things like spatial notation, modern notation, baroque notation, chord names, complex time, etc... the list goes on) but at the same time it takes a while to get used to (you'll need to sit with the manual pdf open as you code the first while).

Sibelius is a wonderful program though - I'd spend the money for it if it would run natively on linux.

Thanks for your ideas on this matter, Stochastic.  I think I'll take out the Lilypond manual again, and start coding.  I understand that there are some advantages in coding in Lilypond than using a GUI scoring program, specially in terms of layout.  I'll give it a try.

I see you're well versed in audio recording in Linux.  I'm experimenting with all those tools now; as I stated, my intentions are to move completly to Linux in some point.  Anyway, this is really a topic for another post, and I don't want to brake the rules, but I'm glad to finally know someone who actually uses Linux to compose, score, record and arrange music.  Thanks for your help! :guitar:

---


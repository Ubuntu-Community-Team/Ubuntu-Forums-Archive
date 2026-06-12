---
title: "So I made a new &quot;programmer font.&quot;"
date: 2011-09-19
forum: The Cafe
---

### Post by ninjaaron on 2011-09-19
Current version: 0.9.2 (download below)  [changes]("http://ubuntuforums.org/showpost.php?p=11272466&postcount=45")

pic:
(left to right: sample with code, Latin charset examples, Hebrew charset samples + gtk widget)

[[IMG]http://ubuntuone.com/1TOnCr7UFgGBTPuidSe8Rq[/IMG]]("http://ubuntuone.com/0ypofivRRrMKAFR1wrK69U")


Note: there is a tl;dr version at the bottom for the incompetent.  There are also pictures and downloads down there, but first, I've got a lot to say, and I'm going to say it, even if nobody reads it.

Programmers tend to have very specific needs and strong opinions when it comes to fonts.  Because they spend so much time looking at text, they need fonts to be very readable with good distinction between each number and letter.  Fonts for coding generally need to be monospaced as well.  Finally, many programmers also like very small fonts, so they can see a lot of lines at once without scrolling.

Small and "easy to read" don't tend to go hand in hand.  Normal vector fonts (such as OTF and TTF) get very blurry or sometimes distorted at small sizes (though good hinting can help).  However bitmap fonts do not get blurry. The pixel is either on or off.  Though bitmap fonts are not as pretty as vector fonts, they are ideal for readability in a small package.

Though not a professional programmer, as someone who spends a lot of time working with text myself, I eventually came to appreciate these features in a font, after some coaxing, but I couldn't get over how jaggy  bitmap fonts tend to be, so I set out to create my own.

Initially, my main inspiration was one of my favorite fonts, the old OCR-A font that they used when computerized character recognition was just getting started.  At first, I just used this font in the terminal for fun, cause it's quirky and looks cool, but I had another profile setup with a different font for serious work.  I eventually ended up switching all of the profiles to this font.  The Characters are designed to look different so that a computer can read them correctly, but it turns out that this also helps Humans read them too.  

I started out trying to copy the OCR font as closely as possible. Sometimes it looked good.  Other times it looked downright bad.  I eventually realized that the shapes I didn't like were happening around diagonal edges.  Two undesirable things happen with diagonal lines on a bitmap:  First, you see the sharp edge of every pixel.  It's impossible to give the illusion of smoothness without anti-aliasing on anything other than a strait line up or down.  The other problem is that diagonal lines get extremely thin when they are one pixel wide, appearing much thinner than strait lines.  This lead me to embrace the fact that the pixel is a square, and to try to use strait lines as often as possible.  I did use some diagonals to produce greater variation of shape in the letters (and thereby improve recognition), but when I have used diagonals, they are, as a rule, two pixels wide instead of one.  This makes them a little bit thicker than the normal vertical and horizontal strokes, which isn't ideal, but I find it to be better than thinner, and you have to choose one of the two when working with a bitmap.

I've ended up with a font that is rather different than the OCR-A font, but some letters still look quite similar (almost all of the numbers), and I've tried to retain a similar sort of feeling, even when the actual glyphs are quite different.

So that's the story of the font.  Now on to the files.  There are two files.  One, the one that I expect most people will have more use for, covers all characters for western encoding (aka: iso-8859-1, ascii 256, Latin-1).  This means it will work with just about any program as an XFT font or a X core font, and is also suitable for most western European languages.  The "bitocra-full" file contains all of these glyphs, plus a lot more.  As of version 0.9.2, it contains all of the Latin Extended-A charset, which means it should work for every living language with a latin-based alphabet (as far as I know).

It also many extra characters that I need for my work (grad student in Biblical and Ancient Near Eastern Studies; refer to pic for listing). In addition, it has a complete Hebrew character-set with niqqud (vowel points). These things are not especially interesting unless you happen to be involved in semitic linguistics, or are Israeli.

BUGS:  The extra Unicode characters in bitocra-full seem to make programs that are expecting a normal X core font freak out sometimes.  If you use rxvt-unicode as your terminal, you will need to call it with an xft code to take advantage of the extra glyphs.

There is no bold yet. If you call it as an xft, freetype will automatically generate bold characters. Sometimes they look bad, but they don't mess up the alignment (except maybe Æ and &#338;, the two widest glyphs. I haven't tested them).

I guess that's about it.  Constructive criticisms are welcome.  Inversely, complements are also welcome. I hope to get some of both. :D

TL;DR VERSION:

I made a very small, readable bitmap font.  It supports full Western encoding. The "full" version also has a complete set of Latin Extended-A glyphs, Hebrew glyphs and characters for the transcription of Semitic and Ancient Near Eastern languages.

Pics:

v0.9.2 (Current)

[[IMG]http://ubuntuone.com/1TOnCr7UFgGBTPuidSe8Rq[/IMG]]("http://ubuntuone.com/0ypofivRRrMKAFR1wrK69U")

v0.9.1 

[[img]http://ubuntuone.com/5RTA2DJcsQp3dfcPdVHEb3[/img]]("http://ubuntuone.com/3MEFx7NxNI2ZI3PCw73WcE")

v0.9

[[IMG]http://ubuntuone.com/1hkPqAWQ1VlS45Lv23GxCx[/IMG]]("http://ubuntuone.com/1ukJJmVADriUCNb1pKUTt8")


bitocra and bitocrafull are now licensed under the SIL Open Font license v1.1. Font freedom for all!

Latest version is now available at github - [https://github.com/ninjaaron/bitocra](https://github.com/ninjaaron/bitocra)


Files:

---

### Post by IWantFroyo on 2011-09-19
When you think it's ready for production use, do you think you'll make a ppa for it?

---

### Post by ninjaaron on 2011-09-19
> **IWantFroyo said:**
> When you think it's ready for production use, do you think you'll make a ppa for it?

I don't know how to do that.  I don't even know how to build a package.  I'll probably need help.

Anwyay, I think it's ready for production use now.  I probably should have slapped a CC licence in that archive.

---

### Post by Legendary_Bibo on 2011-09-19
> **ninjaaron said:**
> I don't know how to do that.  I don't even know how to build a package.  I'll probably need help.

Anwyay, I think it's ready for production use now.  I probably should have slapped a CC licence in that archive.

If it's a ttf you shouldn't need to package it, unless you plan on updating it.

---

### Post by el_koraco on 2011-09-19
downloading, will get back to ya tomorrow.

---

### Post by Famicube64 on 2011-09-19
The font is unreadable.

---

### Post by ninjaaron on 2011-09-19
> **Legendary_Bibo said:**
> If it's a ttf you shouldn't need to package it, unless you plan on updating it.

It's a bdf.  Still shouldn't require packaging, but I don't really know what the point of a PPA is without a packages that automatically install in the correct directory.

---

### Post by disabledaccount on 2011-09-19
I would say that the most important factors affecting readibility are color and contrast -  font / background and monitor / ambient. Next is syntax highlighting and then finally the font.
I'm using vector fonts in editors if it's only possible, because this allows me to easily zoom-in/out when I want to focus on some portion of text or when I'm getting tired. Currently I'm using Monospace8 as sytem default and Monospace9 Bold for window captions, subpixel smoothing, hinting=none.

For long time I've used black bg and green-gray fonts, but now I prefer dirty-yellow bg (like: 0xFFFFDD) and black font.

---

### Post by ninjaaron on 2011-09-19
I just realized that the Hebrew letter zayin is backwards.

/facepalm

Will upload the fix tomorrow, not that anyone is going to be using the Hebrew.  In related "nobody cares" news, I also fixed the proportions on &#7717;.

---

### Post by Copper Bezel on 2011-09-19
> In related "nobody cares" news,
This is one of the most appealing segues I've ever experienced.

I have nothing else to add - I don't code. = )

---

### Post by IWantFroyo on 2011-09-19
Downloaded it. I actually quite like it. It's readable (despite what Famicube33 posted), and I look forward to using a finished version. I use small fonts, and so far I've been using Times New Roman. Not the most readable font for programming.

Keep up the good work! :)

---

### Post by Famicube64 on 2011-09-19
> **IWantFroyo said:**
> Downloaded it. I actually quite like it. It's readable (despite what Famicube33 posted), and I look forward to using a finished version. I use small fonts, and so far I've been using Times New Roman. Not the most readable font for programming.

Keep up the good work! :)
That's Famicube*64* to you, good sir.

):P

---

### Post by ninjaaron on 2011-09-19
> **IWantFroyo said:**
> Downloaded it. I actually quite like it. It's readable (despite what Famicube33 posted), and I look forward to using a finished version. I use small fonts, and so far I've been using Times New Roman. Not the most readable font for programming.

Keep up the good work! :)

You should tell me what you would look for in a finished version.  At this point, I'm just doing minor tweaks.  I'm quite satisfied with it, so if you want it to improve, I need some suggestions.

As far as "readability", I'm not exactly sure what he means either. I'm using it for everything right now, including GTK apps (which I don't especialy recommend), just so I will notice things that bother me more quickly.  I'm not having trouble reading anything.

So, Famicube64, is it that you simply don't like the font, or are really having trouble distinguishing characters?  If you are going by the picture, my first suggestion for taking care of the 'readablity' issue is reading only those texts that appear in languages you understand. ;)

---

### Post by IWantFroyo on 2011-09-19
I really don't see what more there is to change. The font is quite brilliant as it is. I would suggest checking it over for accuracy one last time, possibly rounding out the c's and q's a bit (just my view- ask some other people on this), and packaging it.

[QUOTE=Famicube64]That's Famicube64 to you, good sir.[/QUOTE]
Ahh... Sorry.
This is what happens when I Go Advanced and get too lazy to scroll down and check the spelling.
I'm using Go Advanced less and less. I'm just putting in the BB tags manually, now.

---

### Post by Spice Weasel on 2011-09-20
I can't read it without my eyes hurting.

---

### Post by el_koraco on 2011-09-20
The regular letters are awesome, IMO they exhibit none of the weaknesses that one finds in the artwiz fonts, like a too large spacing, or unreadability in certain letters (m and w in lime as an example). Nice job, wouldn't change a thing!

I find certain things to be lacking in the capital letters, but I'm not a 100% on how those things should be corrected, it mostly comes to design decisions. The curve to the left in Q, A, C is not bad in itself, but I seem to be annoyed by some inconsistencies (say, you have the curve in Q, but not in O, even though the tail in Q is the only real difference). I'm also not sold on the tilt in C and S, it seems a little out of place. 

I would also make some adjustments either to the O, or to the D, because they are a little too similar. Also, the V looks like somebody chopped it up and put it back together. The W is awesome, though, as is the B, but the P looks like it's misaligned.

I'm not sure what to do, whether to give up on the tilting, or just style it a little differently. It's completely up to you as the designer. 

The charset is sweet, but the square brackets are weird, I get the feeling they're part of a sobriety test or something.

All in all, i give it 6,5 out of 10, but I'm pretty sure you could bring it up to 9.  

P.S. don't feed the trolls.

---

### Post by kaldor on 2011-09-20
> **ninjaaron said:**
> You should tell me what you would look for in a finished version.  At this point, I'm just doing minor tweaks.  I'm quite satisfied with it, so if you want it to improve, I need some suggestions.

As far as "readability", I'm not exactly sure what he means either. I'm using it for everything right now, including GTK apps (which I don't especialy recommend), just so I will notice things that bother me more quickly.  I'm not having trouble reading anything.

So, Famicube64, is it that you simply don't like the font, or are really having trouble distinguishing characters?  If you are going by the picture, my first suggestion for taking care of the 'readablity' issue is reading only those texts that appear in languages you understand. ;)

I took a look at the font and found the same issues. The font *looks* very nice, but I could never imagine myself using it. The letters feel too small and too "boxy" and make my eyes hurt a little bit due to straining/squinting at the characters. 

It may depend on the resolution or type of screen, but for me there's no way I could ever use it. That's not to say it isn't a good job though, of course. It's obvious a lot of work was put into it, and that for some people it will be great.

---

### Post by el_koraco on 2011-09-20
> **kaldor said:**
> I took a look at the font and found the same issues. The font *looks* very nice, but I could never imagine myself using it. The letters feel too small and too "boxy" and make my eyes hurt a little bit due to straining/squinting at the characters. 


If you're straining your eyes on this font, it's probably because you don't have the font engine set to full bitmap rendering.

---

### Post by ninjaaron on 2011-09-20
> **el_koraco said:**
> The regular letters are awesome, IMO they exhibit none of the weaknesses that one finds in the artwiz fonts, like a too large spacing, or unreadability in certain letters (m and w in lime as an example). Nice job, wouldn't change a thing!

I find certain things to be lacking in the capital letters, but I'm not a 100% on how those things should be corrected, it mostly comes to design decisions. The curve to the left in Q, A, C is not bad in itself, but I seem to be annoyed by some inconsistencies (say, you have the curve in Q, but not in O, even though the tail in Q is the only real difference). I'm also not sold on the tilt in C and S, it seems a little out of place. 

I would also make some adjustments either to the O, or to the D, because they are a little too similar. Also, the V looks like somebody chopped it up and put it back together. The W is awesome, though, as is the B, but the P looks like it's misaligned.

I'm not sure what to do, whether to give up on the tilting, or just style it a little differently. It's completely up to you as the designer. 

The charset is sweet, but the square brackets are weird, I get the feeling they're part of a sobriety test or something.

All in all, i give it 6,5 out of 10, but I'm pretty sure you could bring it up to 9.  

P.S. don't feed the trolls.

Thanks for the criticisms and the complements.  A lot of the things you brought up are bugging me also.  I've actually already made some adjustments to P, D, and K.  As far as "the tilted letters" I'm in a quandry about them myself.  When I take them out, some of the letters begin to look very similar, but they definitly do look a little out of place at times.  It will probably stay in A for sure, and most likely in the Q, since those letters don't bug me in the least, but I'll have another go at some of the others.

I'm quite fond of the quirky brackets.  They were one of my favorite carry-overs from the orignial OCR-A, but if I get a lot of negative feedback about them, I suppose I can just keep them on my computer and make normal brackets for everyone else.

---

### Post by ninjaaron on 2011-09-20
> **kaldor said:**
> I took a look at the font and found the same issues. The font *looks* very nice, but I could never imagine myself using it. The letters feel too small and too "boxy" and make my eyes hurt a little bit due to straining/squinting at the characters. 

It may depend on the resolution or type of screen, but for me there's no way I could ever use it. That's not to say it isn't a good job though, of course. It's obvious a lot of work was put into it, and that for some people it will be great.

Yeah, I know what you mean.  Working with fonts like this is an adjustment, though I've found it's more in you head than your eye.  The shapes are clear, but your mind isn't used to reading something so small at first.  The nice thing, as el_koraco would constantly remind me, is how much you can fit on the screen with a font at this size, but it's definitly a "niche market."

I've thought about making a larger version, but I have trouble seeing the point, since vector fonts look better in larger sizes (in my opinion).  There will never be a less boxy version, however.  There are plenty of excellent bitmap fonts with more rounded edges (Terminus, Dina, MonteCarlo, Profont, Tamsyn, etc.).  I happen to like boxy fonts for monospace contexts, and I feel like the "boxy approach" presents certain advantages when working with bitmaps because the pixel is, well, a box.

But for sure, it's not intended to be a font for all people or all uses.

Thanks for giving it a look.

---

### Post by Spice Weasel on 2011-09-20
> **el_koraco said:**
> P.S. don't feed the trolls.

You disagree with me, therefore you are a troll.

---

### Post by sffvba[e0rt on 2011-09-20
> **Spice Weasel said:**
> You disagree with me, therefore you are a troll.

No trolls around here... 

@OP awesome for creating your own font... :guitar:


404

---

### Post by BeRoot ReBoot on 2011-09-20
If it isn't Terminus, it isn't a 'programmer font'.

---

### Post by gutterslob on 2011-09-20
Downloaded. Will give em a go later and get back to ya.

---

### Post by undecim on 2011-09-20
It's not bad, considering that the characters are only 8 pixels tall

But that's the problem: the characters are only 8 pixels tall. That's alright if you need to read 80 lines of code at once, but for general use, it's a killer on the eyes. I would love to see a scalable version of this font, or perhaps a larger one.

---

### Post by BrokenKingpin on 2011-09-20
The font has a retro feel to it, which I like. I couldn't use it full time.

---

### Post by ninjaaron on 2011-09-20
> **BeRoot ReBoot said:**
> If it isn't Terminus, it isn't a 'programmer font'.
Go tell it to Profont! :mad:

> **gutterslob said:**
> Downloaded. Will give em a go later and get back to ya.
Never fails.  See, there's going to be an update in just a couple of minutes.

> **undecim said:**
> It's not bad, considering that the characters are only 8 pixels tall

But that's the problem: the characters are only 8 pixels tall. That's alright if you need to read 80 lines of code at once, but for general use, it's a killer on the eyes. I would love to see a scalable version of this font, or perhaps a larger one.

I'm using it for general use at the moment, and it's fine for me.  I ultimately created the font to satisfy my needs and desires.  Howerver If there is enough demand for a larger/scalable version, I'll see what I can do after I get this one how I want it.

If you like the design, This probably won't be my last font (I've done some in the past);  probably nothing too revolutionary though. There are already a many excellent daily-use  serif and san-serif fonts.  I have a couple of thoughts for some novelty TTF fonts, and a few Greek and Hebrew fonts based on the gyphs as they appear in their most ancient forms.  If I ever do anything serious for the general user, it would probably be an organic sans-serif (think Linux Biolinum).


Alright.  I've got to go get the update tar'd and upload the sample image.  Back in a few with fresh glyphs.

---

### Post by sanderd17 on 2011-09-20
I think I'll make an AUR package for it, but could you put your font on a place where it can easily be tracked and downloaded?

Like google code or github?

Making a script that downloads something from forums is asking for problems.

BTW: if you make a ppa on launchpad, that will also work.

---

### Post by ninjaaron on 2011-09-20
Ok, update is posted.  We're just going to call the first one v0.9, so this is v0.9.1

Changes:[list]
[*]Made the more severely tilts softer
[*]moved the the bottoms of letters extending below the line on px higher.
[*]Tweaked the capitol D, V, K, and R, as well as both big Z small z. 
[*]Adjusted mistakes in several derived glyps, as well as the height of the Hebrew zayin
[*]found and added the unicode glyph for Hebrew yud+hiriq
[*]moved all Hebrew letters up by one pixel so the niqqud (vowel points) would be more usable.
[*]Made the slash a little more "normal."
[/list]
Pics and files in the OP.



> **sanderd17 said:**
> I think I'll make an AUR package for it, but could you put your font on a place where it can easily be tracked and downloaded?

Like google code or github?

Making a script that downloads something from forums is asking for problems.

BTW: if you make a ppa on launchpad, that will also work.

Eh... I'm flattered at the offer, but two things.

1.  I need to figure out the licence first, whether a GNU or a CC licences is more appropriate for a font.

2.  I don't have any experince with being anywhere except on the reciving end of software distribution.  I would be happy to do any of the things you suggested, but I haven't the slightest idea where to begin.  Any suggestions for a starting point?

(I'm attracted to github, cause it seems like a universal sort of medium, and then anyone who likes can make a package based on that for any distro)

---

### Post by el_koraco on 2011-09-20
Nice job on the V, D and tilts. I'm still not a 100 percent sold on the A and Q, they seem a little too rugged, but that's your prerogative. 

Since you're going for a full set of characters, maybe you should include &#353;, &#269;, &#263;, &#273; and &#382;. Those are used in a bunch of Slavic languages, and you just need to add hyphens on s, c, d and z.

---

### Post by whiskeylover on 2011-09-20
Any chance you can upload a font file that Windows can read?

---

### Post by el_koraco on 2011-09-20
[http://bdf.software.informer.com/download-bdf-font-viewer-windows/]("http://http://bdf.software.informer.com/download-bdf-font-viewer-windows/")

---

### Post by ninjaaron on 2011-09-20
> **el_koraco said:**
> Nice job on the V, D and tilts. I'm still not a 100 percent sold on the A and Q, they seem a little too rugged, but that's your prerogative. 

Since you're going for a full set of characters, maybe you should include š, &#269;, &#263;, &#273; and ž. Those are used in a bunch of Slavic languages, and you just need to add hyphens on s, c, d and z.

I did, in fact, make the A and the Q softer, but the tilt is still there.  I feel like it makes them more recognisable... I'll keep looking at them, but I'm quite statisfied with them at present.

I think your right.  Adding the Eastern european characters has to be next, along with the Euro sign.

I can't do Cyrillic though, as I can't read it, so I can't really be the judge of whether a character looks right.

[edit]
check out these titls.  They do anything for you?

---

### Post by forrestcupp on 2011-09-20
> **Spice Weasel said:**
> I can't read it without my eyes hurting.

That was my thought, too. When I code and I'm staring at text and really concentrating for a long period of time, I need a font that is really easy on the eyes. This one is pretty harsh on my eyes.

But that's just my opinion. I'm sure there are many people who would like it.

---

### Post by aaaantoine on 2011-09-20
> **ninjaaron said:**
> 
Eh... I'm flattered at the offer, but two things.

1.  I need to figure out the licence first, whether a GNU or a CC licences is more appropriate for a font.

2.  I don't have any experince with being anywhere except on the reciving end of software distribution.  I would be happy to do any of the things you suggested, but I haven't the slightest idea where to begin.  Any suggestions for a starting point?

(I'm attracted to github, cause it seems like a universal sort of medium, and then anyone who likes can make a package based on that for any distro)

1. Generally speaking, if there is a source file required* to make the final product, then use GPL and make that file available.  Otherwise, CC.  

*I don't know enough about font creation to know if this is the case or not.

2. Popular hosting options are: [GitHub](https://github.com/), [SourceForge.net](http://sourceforge.net/), and [GNOME-Look.org](http://gnome-look.org/).  For something like this, you probably want something simple like GnomeLook.  I don't know how complex GitHub is.  SourceForge is actually rather involved, and probably not well suited for a font.

---

### Post by ninjaaron on 2011-09-20
> **aaaantoine said:**
> 1. Generally speaking, if there is a source file required* to make the final product, then use GPL and make that file available.  Otherwise, CC.  

*I don't know enough about font creation to know if this is the case or not.

2. Popular hosting options are: [GitHub](https://github.com/), [SourceForge.net](http://sourceforge.net/), and [GNOME-Look.org](http://gnome-look.org/).  For something like this, you probably want something simple like GnomeLook.  I don't know how complex GitHub is.  SourceForge is actually rather involved, and probably not well suited for a font.

BDF, which I'm using at the moment, is a non-compiled format.  You can read it in a text editor, though the glyphs themselves are represented by numbers that I don't fully understand, but the names and all the info about each glyph is there in plain text.  They can also be compiled into PCF binary format, but there are free decompression tools to turn it back into BDF.  It's not like C or something, where I could compile it and nobody could ever get to the source.

Fonts are more like books or paintings.  What you see is what you get.  If a computer can render it, then it can open it in an editor, unless there is some kind of DRM or something, but I've never heard of that for a font, yet.

I was thinking CC might be more appropriate because it is more like art.  I'll have to do some reading and maybe start a thread about it.

I'll look into gnome-look and github.  I'm pretty sure git-hub has more sophisticated version control, which is attractive for something that people what to package.  I watched Linus give a talk about it on Youtube. I had no idea what he was on about most of the time, but I guess some of it got into my head somehow.

---

### Post by el_koraco on 2011-09-20
> **ninjaaron said:**
> 
check out these titls.  They do anything for you?

Nice. That's an 8,5 now. I'll probably have more feedback for you when I start using these for a longer period of time, but I'm pretty committed to MonteCarlo at the moment. The only thing I do notice is, even though the P is much better than in the original, it leaves a little too much space behind. But that's pure nit-picking, awesome job all in all.

---

### Post by ninjaaron on 2011-09-20
> **el_koraco said:**
> The only thing I do notice is, even though the P is much better than in the original, it leaves a little too much space behind. But that's pure nit-picking, awesome job all in all.

Thanks.  I think the thing with the "P" may be an optical illusion. It's 4px wide, the same as most of the other letters.  It probably has to do with the fact that it has nothing on the bottom-right, and you usually have kerning to sort of nestle the smaller letters in there. I could try to move the whole glyph one pixel to the right.  This would create extra space on the left, obviously, but as it is a capitol letter, it will generally follow a space anyway.  The only time it should be noticable is in a context with all caps (which does happen pretty often in the console).

I'm playing with a solution right now that moves the P over one pixel, and offsets the loss by adding a serif to it's left side.  I can't decide of the serif is cool or silly.  I'm leaning towards cool at the moment, but I'm not sure if it actually fixes the gap created by moving the whole character to the right.  Perhaps I'll post a shot tomorrow.

And I won't be mad or something stupid if you stick with Monte Carlo.  Your nit-picking is helping to make a better font for me and anyone else who might choose to use it later. So far, your're the only one offering any constructive criticism, which was the whole point of this thread.  I wish more people were nit-picking!

---

### Post by ninjaaron on 2011-09-20
> **whiskeylover said:**
> Any chance you can upload a font file that Windows can read?

I'm not sure what windows uses for bitmap fonts.  Can it read PCF?  I can post that.

---

### Post by undecim on 2011-09-20
> **ninjaaron said:**
> 1.  I need to figure out the licence first, whether a GNU or a CC licences is more appropriate for a font.

How about a license specifically made for fonts? [http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&id=OFL](http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&id=OFL)

(NOTE: The FSF considers it to be an open source license.)

---

### Post by kaldor on 2011-09-21
> **ninjaaron said:**
> I can't do Cyrillic though, as I can't read it, so I can't really be the judge of whether a character looks right.

If you decide to do Cyrillic and need confirmation on anything, I can help.

---

### Post by ninjaaron on 2011-09-21
> **kaldor said:**
> If you decide to do Cyrillic and need confirmation on anything, I can help.

I appriciate the offer, but working with scritps one doesn't know well is quite problematic.  You probaly recognise Cyrillic letters in a wide variety of fonts and handwriting styles and probably understand "what makes them what they are."  If I were to try, the best I could aim for is to copy exactly what I see, which is sort of impossible on a bitmap font, especially at this size, where "e" and "s" are the difference of one pixel.  It's compounded by the fact that this is a stylized type-face, so a certain level of distortion on the expected shapes is desireable.  If I try to stylize cyrillic letters, I run a high risk of making them unreadable, or worse, look like another letter altogether.  It happened quite often with this font that I would be working on the shape of a letter, and I would move a couple of pixels, and it would looks like something else.  I can recognize this immediatly in Latin and Hebrew scripts, but wouldn't know in Cyrillic unless someone pointed it out.

Now, my feeling is that these sorts of blunders would probably happen quite often, given the font in question (It would be easier with vector fonts, for example).  There are two main solutions.  One would be to make the font with someone who knows the script in the room as a source of constant feedback.  The other would be to communicate the deisign principles of the font to someone who does know, and have them design the charset.

Having said all of that, I do think it would be fun to try my hand at Cyrillic, despite all of the reasons that it's a bad idea, and if I do, I'll probably message you (don't hold your breath).  On the other hand, if you would like to try doing the cyrillic characters, I would be happy to tell you the "rules" of the font

---

### Post by kaldor on 2011-09-21
> **ninjaaron said:**
> Having said all of that, I do think it would be fun to try my hand at Cyrillic, despite all of the reasons that it's a bad idea, and if I do, I'll probably message you (don't hold your breath).  On the other hand, if you would like to try doing the cyrillic characters, I would be happy to tell you the "rules" of the font

I can't promise anything, but if you have any information then you can give it to me. If/When I have some time, I'll take a look into it.

Cyrillic isn't extremely hard to learn though. It's an alphabet that works pretty much identically to latin. The only problem is variations between some other languages that use different characters. Italics in Russian are sometimes written differently in some other Slavic languages, for example. Overall, Cyrillic follows the same sort of flow as the latin alphabet.

Edit with an image just for reference.

[img]http://ubuntuone.com/3qNrbGK52UNyd0Qp7JQIPt[/img]

---

### Post by ninjaaron on 2011-09-21
> **kaldor said:**
> I can't promise anything, but if you have any information then you can give it to me. If/When I have some time, I'll take a look into it.

Cyrillic isn't extremely hard to learn though. It's an alphabet that works pretty much identically to latin. The only problem is variations between some other languages that use different characters. Italics in Russian are sometimes written differently in some other Slavic languages, for example. Overall, Cyrillic follows the same sort of flow as the latin alphabet.

Edit with an image just for reference.

Well, I'll take some shots at it, send them along to you, and if they are terrible, I'll give you some ground rules about the font and you can try your hand if you like.  I know Greek, so that should help a bit.

---

### Post by ninjaaron on 2011-09-21
BIG Update: v0.9.2

Pics and files in the OP.

Changes: [list]

[*]EXPERIMENTAL SUPPORT FOR LATIN EXTENDED-A CHARSET.  If you use a language with a latin-based alphabet, your languages is probably supported now. I don't personally use most of these glyphs, so opinions on their shapes from people who do would be highly appriciated.  There are bound to be some mistakes and problems.
[*]Many glyphs have been "trimmed down" to give a slightly slimmer appearance.
[*]Capitol P has been moved one pixel to the right with a small tail added. this is to provide better kerning.  Opinions welcome.
[*]various minor fixes to mistakes in the previous versions.
[*]added the Euro sign.
[/list]

---

### Post by sanderd17 on 2011-09-21
Sorry to push you, but have you decided on what version control or hosting service you will use?

[s]Maybe one char I'm missing (at least I don't see it on the screenshot, don't have installed the new version) is the c-cedilla: [https://secure.wikimedia.org/wikipedia/en/wiki/C-cedilla](https://secure.wikimedia.org/wikipedia/en/wiki/C-cedilla)

It's used a lot in French for regular words like garçon (boy[/s]

Forget about that. It was in regular latin things.

---

### Post by ninjaaron on 2011-09-21
> **sanderd17 said:**
> Sorry to push you, but have you decided on what version control or hosting service you will use?

[s]Maybe one char I'm missing (at least I don't see it on the screenshot, don't have installed the new version) is the c-cedilla: [https://secure.wikimedia.org/wikipedia/en/wiki/C-cedilla](https://secure.wikimedia.org/wikipedia/en/wiki/C-cedilla)

It's used a lot in French for regular words like garçon (boy[/s]

Forget about that. It was in regular latin things.

No. I will make that my next priority, before cyrillic or bold or anything.

---

### Post by el_koraco on 2011-09-21
Yup, the P is pretty awesome now. There's even a pattern forming, P and D have the uppermost pixels extending over the rest of the letter. All in all, I like your lovechild more than the artwiz fonts now.

---

### Post by ninjaaron on 2011-09-21
Get back to nit-picking. :mad:

But thanks!

[edit]
If anyone actually downloaded the latest version, there is a tiny, tiny mantinance update.  The character spacing had secretly grown by one px, but it's back to normal now.

Not sure how this happened.  I still haven't totally figured out the software I'm using.

---

### Post by ninjaaron on 2011-09-23
Latest version is now available at github (same as what's already here).

[https://github.com/ninjaaron/bitocra]("https://github.com/ninjaaron/bitocra")

---

### Post by ninjaaron on 2011-09-24
bitocra and bitocrafull are now licensed under the SIL Open Font license v1.1.  Font freedom for all!


To the mod who moderates this:  As I'm currently on the UF naughtly list, I cannot edit my posts.  If you would be so kind as to add the license info and the github link from the previous post to the OP, I would be much obliged.  If not, well, that's that's the price of being naughty, I guess.;)

---

### Post by sffvba[e0rt on 2011-09-24
> **ninjaaron said:**
> bitocra and bitocrafull are now licensed under the SIL Open Font license v1.1.  Font freedom for all!


To the mod who moderates this:  As I'm currently on the UF naughtly list, I cannot edit my posts.  If you would be so kind as to add the license info and the github link from the previous post to the OP, I would be much obliged.  If not, well, that's that's the price of being naughty, I guess.;)

Added them to the bottom of the OP.


Regards
404

---

### Post by ninjaaron on 2011-09-25
> **not found said:**
> Added them to the bottom of the OP.


Regards
404

Cool. Thanks.

---

### Post by Foxcow on 2011-09-25
This may be a dumb question but how do you install the font?  I'm taking several programming classes right now and would love to try it out.  Like all other fonts I've installed, it wasn't just a click and install.

Thanks.

---

### Post by el_koraco on 2011-09-25
> **Foxcow said:**
> This may be a dumb question but how do you install the font?  I'm taking several programming classes right now and would love to try it out.  Like all other fonts I've installed, it wasn't just a click and install.

Thanks.

Move them to .fonts, cd to the ~/.fonts/bitocra folder, run 

```
mkfontdir
fc-cache-fv
```Log out and back in (or restart X if you don't have a DM. If you want to use it with the long code in obscure window managers, xterm, urxvt and so on, you need to add the fontpath to .xorg.conf. Get back if you need that, I'll give you instructions.

---

### Post by Foxcow on 2011-09-25
> **el_koraco said:**
> Move them to .fonts, cd to the ~/.fonts/bitocra folder, run 

```
mkfontdir
fc-cache-fv
```Log out and back in (or restart X if you don't have a DM. If you want to use it with the long code in obscure window managers, xterm, urxvt and so on, you need to add the fontpath to .xorg.conf. Get back if you need that, I'll give you instructions.



Thanks, I'm getting a command not found for the second command though.

---

### Post by whiskeylover on 2011-09-25
> **Foxcow said:**
> Thanks, I'm getting a command not found for the second command though.

Try 
```
 fc-cache -fv
```instead of 
```
 fc-cache-fv
```

By the way, I tried that, and still can't see the new fonts. Am I missing something?

---

### Post by el_koraco on 2011-09-26
> **whiskeylover said:**
> Try 
```
 fc-cache -fv
```instead of 
```
 fc-cache-fv
```By the way, I tried that, and still can't see the new fonts. Am I missing something?

Yeah, typo. Did you run mkfontdir in the .../bitocra folder? Just for kicks, add 

```
xset fp rehash
```

---

### Post by sanderd17 on 2011-09-26
ninjaaron is also working on a deb file/apt repo. This should make installation better for Debian based distros.

---

### Post by ninjaaron on 2011-09-26
Just did a quick search.  As it turns out, Ubuntu has bitmap fonts disabled by default. 

You have to delete a config file to get it to work.

```
sudo rm /etc/fonts/conf.d/70-no-bitmaps.conf
```

After running this command, the instructions given by the other should work.

Weird.

---

### Post by whiskeylover on 2011-09-26
> **el_koraco said:**
> Yeah, typo. Did you run mkfontdir in the .../bitocra folder? Just for kicks, add 

```
xset fp rehash
```

Yes, did the mkfontdir and xset fp rehash. 

By the way, I put the font files in .fonts instead of a folder of their own. Do you think that could have been the problem?

---

### Post by el_koraco on 2011-09-26
> **whiskeylover said:**
> 
By the way, I put the font files in .fonts instead of a folder of their own. Do you think that could have been the problem?

Most likely, Try to put them in a bitocra folder, put that one to .fonts, mkfontdir, fc-cache -fv. That should be enough if you're using the fonts in GTK applications. If you want xfontsel to recognize the fonts, you have to add the path to the xorg configuration file.

---

### Post by maever on 2011-09-26
kudos nice work

---

### Post by Foxcow on 2011-09-26
Thanks, trying it out now.

---

### Post by ninjaaron on 2011-09-27
Apparently bitmap fonts are disabled by default in many distros.

Debian contains the say file as Ubuntu.  Fedora appears to have a similar file by the name of '/etc/fonts/conf.d/25-no-bitmap-fedora.conf'.

I guess I wasn't the only one dissatisfied with the available bitmap fonts.  :lolflag:

---

### Post by sanderd17 on 2011-09-27
> **ninjaaron said:**
> Apparently bitmap fonts are disabled by default in many distros.

Debian contains the say file as Ubuntu.  Fedora appears to have a similar file by the name of '/etc/fonts/conf.d/25-no-bitmap-fedora.conf'.

I guess I wasn't the only one dissatisfied with the available bitmap fonts.  :lolflag:

I think users complain if they get fonts that aren't resizeable. So to avoid complaints ...

---

### Post by el_koraco on 2011-09-27
Oh, yeah, I forgot, the easy way to enable bitmap fonts on Ubuntu is to run as root

```
dpkg-reconfigure fontconfig-config
```

And answer *Yes* to the third question.

---


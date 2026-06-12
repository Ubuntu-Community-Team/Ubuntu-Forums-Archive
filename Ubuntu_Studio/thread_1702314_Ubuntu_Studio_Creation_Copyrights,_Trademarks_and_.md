---
title: "Ubuntu Studio Creation: Copyrights, Trademarks and License Fees?"
date: 2011-03-07
forum: Ubuntu Studio
---

### Post by billdotson on 2011-03-07
Does Ubuntu Studio have anything in it by default that is copyrighted or trademarked (images, fonts, etc.) Does Ubuntu Studio have any codecs, file formats (h.264, Xvid, DivX, etc) that require licensing fees?

I am asking this in regards to commercial use as well as non-commercial/personal use.

If you know, or have a pretty good idea please separate comments about them. Ex:

"Commercial use: be careful of 'x', you may have to do 'y' with it"

"Non-commercial use is ok" 

I've considered doing a small media editing business and don't really know a ton about legal issues. One of the things I think I be doing is taking people's 18mm films, VHS tapes, DVDs (non-copyrighted) and doing one of the following (but probably image editing as well):
Converting them to .mp4's .avi's, or something else
Putting them on DVD and giving them the option of having DVD menus put on 
    there (probably use QDVDAuthor for this)

What would I need to know about this sort of thing? There seem to be a lot of potential issues.
For example:
Say a home video has the radio playing in the background and its a copyrighted song or someone is watching a movie or TV show in the background (also copyrighted). What would you do there? 

Would you have to pay a licensing fee if you used any of the video containers (mp4, avi, mpeg2, etc.), video codecs, audio codecs, image formats?

Or, for image editing. What if you were editing a photo and there was a trademarked something in the background, like a Coke ad or something?

What if you were designing a DVD menu or a design, how do you know if the font you used is copyrighted or not? How do you deal with that? I've looked for open fonts and they seem to be limited.

Are the fonts included in Inkscape or any of the other editors free to use for any purpose?

Thanks.

---

### Post by cfhowlett on 2011-03-07
First: consult an intellectual property attorney.  You should be able to get a free 15 - 30 minute consultation.

Music: stick with creative commons licensed content and you should have no worries.  Google "podsafe music" or check out [www.jamendo.com](www.jamendo.com).

The default fonts in Ubuntu Studio are Creative Commons licensed.  ADDED fonts may not be, e.g. Microsoft Core Fonts.

---

### Post by cchhrriiss121212 on 2011-03-07
For what you are planning to do, I can't see much of this being an issue. Changing the format of an existing home video would not require you to alter it's contents (ie remove images or songs), given that there will be no wider distribution. Changing the format of any media is perfectly legal in most countries I know of.

Anything like fonts included in Ubuntu will be free to use for whatever, but as far as codecs go, I am not as certain. Ubuntu does not include any non-free codecs with the OS, they must be downloaded separately in the restricted-extras package.
The only codec I am aware of that requires royalty payments is h264, but all the examples I have seen on that indicate it only applies for those who distribute or broadcast media. I think there is some kind of potential market threshold that dictates whether any payment should be made.

---

### Post by billdotson on 2011-03-08
Ultimately, yes, I can't see any other way to approach this other than talking to an IP attorney.

However, just from what you people know, if the fonts in Ubuntu Studio are used, what has to do done? Are all of them under the same Creative Commons license? Are they allowed to be used commercially? Do you have to attribute the creator of the font in a way as to degrade the media that you're creating with it?

Also, there are two things I can think of that I think may be an issue when talking to an IP lawyer. First, how much is something like a consultation going to cost (obviously only respond if you have an idea)?

Secondly, since there is some FUD surrounding open source media (open source implementations of codecs, open source containers, programs, etc.) would it be likely for an attorney to question my use of open source software? For example, say I tell an IP attorney I want to try out a media business. I tell them I am going to use the fonts, codecs, containers, and programs included in Ubuntu Studio. The attorney then tells me that I shouldn't use that because the legality is dubious and the "open source people probably infringed on software patents when making the codec (or whatever)". I know the Xvid codec is particularly questionable as a codec; the last time I looked they wouldn't even offer binaries of it, only the source. However, I just saw that Apple allowed an Xvid player app in its store: [http://itunes.apple.com/us/app/id384098375?mt=8](http://itunes.apple.com/us/app/id384098375?mt=8)  Another potential codec that could be questioned is x264. What if a lawyer questioned me even having x264 or Xvid installing on my computer (even if included in a software program)?

cchhrriiss121212: the market threshold thing you're saying sounds like it may be correct. Here is a link where someone is saying that for mp4 you don't have to pay anything if there are less than 50000 users involved. However, he does say something about the vendor of mp4 encoding tools having to pay a license. In Ubuntu Studio's case, who would have paid that license? I'm going to assume that nobody did and an open source mp4 encoding tool is used.
Thanks.

---

### Post by billdotson on 2011-03-08
If anyone has answers (or even comments) regarding the material in my last post please post. Thanks.

---

### Post by cchhrriiss121212 on 2011-03-08
mp4 is a container, the royalty threshold thing applies to h264 which is a codec. The licence has this to say about royalty payments (emphasis mine):
> For (b) (1) where an End User pays directly for video services on a Title-by-Title basis 
(e.g., where viewer determines Titles to be viewed or number of viewable Titles is 
otherwise limited), royalties for video greater than 12 minutes (there is no royalty for a 
Title 12 minutes or less) are (beginning January 1, 2006) the lower of 2% of the price 
paid to the Licensee (on first Arms Length Sale of the video) or $0.02 per Title 
(categories of Licensees include Legal Entities that are **(i) replicators of physical media**, 
and (ii) service/content providers (e.g., cable, satellite, video DSL, internet and mobile) 
of VOD, PPV and electronic downloads to End Users).

So you would owe them money: 2% of what you charge your customer. Of course you do not have to use h264. Xvid is more complicated, found this on the doom9 forums:
> No. In most countries, you can't use xvid for commercial purposes. To be legal commercially, an MPEG-4 codec needs a patent license bought from MPEGLA. DivX would take care of this if you paid for their codec. But the GPL under which xvid is released effectively forbids you from buying any patent licenses. Ergo, you can't use xvid legally in a commercial application :( .

The best tool for encoding on Linux will be [FFmpeg]("http://en.wikipedia.org/wiki/FFmpeg") which will not be in the main repository for legal reasons.

You should definitely contact a professional, all this stuff is way to complex for the average business person to know with any certainty. Make sure you are prepared beforehand and it shouldn't take more than an hour or so to learn what is what.

---

### Post by billdotson on 2011-03-08
What do you mean by "being prepared?"

Anyway, on a side note: all of this stuff is exactly why I think open formats are key to enabling creative freedom. Also, this kind of stuff is why I am against software patents. Why the heck should the payment system for this stuff be so complex that even some lawyers don't completely understand? Not just patents, but copyrights as well. How utterly ridiculous is it that for every little creative/media related thing you do you have to track down the owners, ask them if it is ok, pay some fee, etc. I can't think of anything else that I've EVER dealt with that is so friggin confusing. 

It is even more silly to think that programs like Final Cut Pro, Avid, etc. say in their license terms that they can only be used for personal or non-commercial use (ads count as commercial use too). Yeah, I read an article earlier that said that that wasn't always the case, and there were exceptions where people could do commercial stuff with their programs, but come on, if someone pays hundreds of dollars for a video (audio or image) editing program the licensing should be included in the product and be VERY clear. 

If there is a cheap product (Roxio creation software or something) that does video editing, then the license should clearly state: you can not use this software for commercial purposes. For software like Final Cut Pro, the license should CLEARLY say: "You can use this for any commercial purpose." (I'm not saying the license says you're allowed to modify the program or anything, just that whatever you do with the media is covered)

It is also ridiculous that if I distribute content that I made, that I have to pay 2%. Yeah, that 2% really adds up for the MPEG LA (talking video codec patents here), but for your "average business person" it seems like a huge, annoying barrier to entry to have to pay a lawyer to tell you how many pennies you have to pay out to the MPEG LA. If the MPEG LA insists on charging royalties, then the very least they could do it make it easy to pay them, instead of having a hundred different exceptions. 

god, I hope that Google wins the battle against MPEG LA over the VP8 codec and we get a truly patent and royalty free video codec that is a standard. I hope the same thing happens for an audio format (is there something going on with audio like this now?) Ogg theora is great and all, but if you have video in ogg theora it won't play on barely anything. The same is true for .flac or .ogg. The number of media devices that can play .flac or .ogg is probably less than a hundred. If open formats were more of a standard and patented/proprietary stuff wasn't built into every consumer video camera, DVD player, TV, etc. then what would people choose? Even if the proprietary video format was better, is your average consumer really going to notice that much of a difference? No. They will get the open one (unless a group has licensed the proprietary thing for free for a few years to get people used to it and then starts charging for it, like MPEG LA is doing right now)

---

### Post by billdotson on 2011-03-08
I thought FFMPEG was included in Ubuntu, but a limited version. [http://en.wikipedia.org/wiki/FFmpeg#Legal_status_of_codecs]("http://en.wikipedia.org/wiki/FFmpeg#Legal_status_of_codecs")

This talks like its pretty common in a limited sense.

---

### Post by cchhrriiss121212 on 2011-03-08
> What do you mean by "being prepared?"
Just meant that you should be clear about everything you might want to do before asking advice. Specify exactly which software or codecs (eg h264) you plan to use and take a copy of their licence with you for the lawyer to interpret.

> I thought FFMPEG was included in Ubuntu, but a limited version.
I'm not sure how the Ubuntu version differs from the one in the Medibuntu repository, I have always used the latter.

I think everyone pretty much has the same opinion you do regarding the complexity of proprietary codecs and such. On this note:
> if someone pays hundreds of dollars for a video (audio or image) editing program the licensing should be included in the product and be VERY clear. 
It seems that this is an area where open source makes things more confusing. Take a look at [Reaper]("http://www.reaper.fm/purchase.php") (proprietary audio software) for example:
> There is only one version of REAPER. We offer two licenses, depending on how you use it. 

$150: full commercial license.
$40:   discounted license.

You may use the discounted license if any of the following is true: 

You are an individual, using REAPER only for personal use.
You are an individual or business, using REAPER for commercial use, and the yearly gross revenue does not exceed USD $20,000.
You are an educational or non-profit organization.
The necessary licence fees are covered when the individual pays for the software in simple terms. 

With open source there is no point of sale, so it is up to the individual to figure out for themselves. Most open source programs are covered by the GPL, but this only covers software, not art or entertainment produced by said software.

---

### Post by billdotson on 2011-03-09
Yeah the whole thing about not having a point of sale for open source software does make things more complicated for sure. However, I shouldn't have to buy some expensive media creation software to do some media editing and/or creation (although if I do I expect it to have the licensing and everything taken care of for me and explain to me in very clear terms what I have to do to distibute the video).

 For open source stuff the situation could still be made easier than it is. For an open source encoder it could be as simple as:"if you want to use x264 for commercial purposes, you need to pay $50 for a license. If you want to use ffmpeg to do mpeg2, you need to pay $15 for a license. Every media you distribute in physical form you need to pay 2% of the cost. You can pay that at this website: example.com"
If MPEG LA wants its patent money it needs to make it easy to do. If they arent willing to make it easy then that seems like their true motive is just to spread FUD and annoy the heck out of people who are actually trying to produce something instead of just collecting royalties. I'm not even completely against the idea of paying to use some technology that took a fair amount of work to make, I'm just saying that if you insist on people paying you then you have to make things clear to them. However, seeing as software algorithms are basically math and reasoning, it seems silly to allow software patents. I could see someone who had no idea how software was developed think that there was some ingenious process involved, but it just comes down to logic and math.

The way I would envision an environment in which media creation was encouraged:
1) Open and royalty free video, audio and image technologies
2) Copyright laws reworked so that the length they protected work is shorter (70 years or so is ridiculous)
3) Software patents are thrown out as nonsensical or are reworked to a maximum of 5 years (if 1 didn't happen at least this restriction would kind of take care of it the anyway)
4) Copyrighted media was more clearly defined. Everything is assumed copyrighted but how many people don't care if someone used it?Ever try finding Creative Commons images for something? There aren't all that many out there, a lot of people simply aren't aware of the issue so they never even think of licensing it somehow.

The website you linked about Reaper is how commercial media software should be done. The terms are extraordinarily clear and fair. If I needed an audio editing package for commercial use I would seriously consider supporting them.

For open source stuff, namely ubuntu studio, it would be nice if some group had all the codecs, etc. legally analyzed and then made a clear, precise howto on the legal stuff you need to do for personal use, and a guide for commercial use. Since Canonical already licensed h.264 that would be great if they did that. I for one would gladly pay them for clearing up all the questions people have. Doing so would enable a lot of people, in my opinion.

---

### Post by cchhrriiss121212 on 2011-03-09
> For open source stuff, namely ubuntu studio, it would be nice if some  group had all the codecs, etc. legally analyzed and then made a clear,  precise howto on the legal stuff you need to do for personal use, and a  guide for commercial use.That would be nice, but I can't see it happening. Personal use is easy: you can use whatever codes you like, so there is no real dilemma there. The difficulty is commercial application, for the following reasons:

[LIST]
[*] Diversity - there are so many different codecs out there all with different owners and patents
[*]Complexity - some codecs have numerous patents (mp3 for example)
[*]Localisation - different countries have different laws on patents and how they are applicable
[/LIST]
Generally speaking, "clear and precise" and "legal stuff" do not often coincide, Law is a profession that benefits from making things as complex as possible.

Possibly bad advice follows:
If I were in your position I would just go ahead and use whatever codecs I needed to provide my service best, then look into the legal situation when I had the time.
It is extremely unlikely for a small business venture such as yourself to be reprimanded for something like this, at worst you would just be asked to stop using the codec or retroactively pay a fee. That's under the unlikely assumption one of your customers would directly inform the owner of the patent about your business.

---

### Post by cchhrriiss121212 on 2011-03-09
Just found this on the mp3 wikipedia page:
> Additionally, patent holders declined to enforce license fees on free and open source decoders, which allows many free MP3 decoders to develop.[citation needed]
I know there is no citation for this claim, but it could be indicative of the other major patent holders' attitude towards FOSS. 
Perhaps they don't want the negative publicity of demanding money from non-profit organisations, or perhaps they just don't consider FOSS to be big enough to care about. Good news either way.

---


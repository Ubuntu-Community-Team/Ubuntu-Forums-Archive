---
title: "Brasero not burning tag information"
date: 2008-11-21
forum: Ubuntu Studio
---

### Post by nbakewell on 2008-11-21
Hey all,

I've been trying to burn some audio CDs with Brasero, but every time I do and then proceed to play the audio CD in another program/location, all the tracks come up as "Unknown - Unknown" even though when I right-click > properties > audio on the MP3 files themselves they have all the appropriate audio tags, and looking at them through EasyTag shows all the correct information too.  Any idea to why Brasero is not keeping the tags with the files when it burns them?

Thanks

---

### Post by kstarkey1 on 2008-11-29
Are we the only ones with this problem, or is this a problem for everyone (that can't be can it?)?

I've had the same problem for a while now and been meaning to post.  I was just about to post this exact problem.  I have this problem regardless of what program I use to burn CDs with.  I just burned a CD a couple of minutes ago, to make sure I still have the problem.  I rarely burn CDs, but when I do, it's quite frustrating.

It seems like this should be a basic fix.

Hopefully someone will be able to help us with this.

---

### Post by kstarkey1 on 2008-11-29
I decided to pose this question to my local LUG, thru email, and I got a good response.

K3b.

It demands that the songs be wav.  No biggie.  Sound Converter does this quite easily.  Maybe K3b can do this, but I'm pretty much clueless in this regard.  Once your songs are wav, add them and then hit the 'burn' button.  Then you get an 'Audio Project - K3b' window.  Make sure you select the 'CD-Text' tab and click the box for 'Write CD-Text', and then I typed in the Title & Performer names.  After that I just hit 'Burn' and in no time it was finished.  I closed down K3b and then popped the CD back in and it opened in Rhythmbox.  It took a few seconds before all of the song titles appeared and the Artist & Album values.

Hope this helps someone.

This is kind of ridiculous if you ask me.  This is pretty basic stuff.  It should really just work.  You shouldn't have to convert the songs first, it should just do it for you.  Oh well.

---

### Post by don_m on 2009-05-01
I did install K3B along with the library to access mp3 files with it.

I did select the CD text option, but the tracks still come up with no lables. 

I am using a Memorex DVD ROM/CD Writer Model # MRX48244816AJI with firmware KWH8.

Also tried a Philips DVD/CD reader/writer with same result of no track labels.

---

### Post by babarosa on 2009-05-01
Hi guys,

take a look at gnomebaker (it is in the repo for v9.04 and can be downloaded for v8.10 and 8.04 on [www.getdeb.net](www.getdeb.net)).

I never had luck with brasero while gnomebaker works like flawlessly for me.

Regards, Michael

---


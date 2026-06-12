---
title: "a/v files with both a space(s) &amp; a ' can't be opened from context menu"
date: 2012-09-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-09-15
Seeing this here with all players, audo & video files. Seems only with nautilus but version doesn't matter, happens with both the default 3.4 & newer 3.5

Ex.
I'll be around.flac - doesn't open from context menu
Ill be around.flac -  opens
I'll-be-around.flac - opens

From the Aug. 15th live cd session there is no issue with both spaces & ' in a file name.
With todays live image session there is.
Curious if anyone can see the same before trying to figure out what caused this, if just here well so be it

---

### Post by effenberg0x0 on 2012-09-15
> **mc4man said:**
> Seeing this here with all players, audo & video files. Seems only with nautilus but version doesn't matter, happens with both the default 3.4 & newer 3.5

Ex.
I'll be around.flac - doesn't open from context menu
Ill be around.flac -  opens
I'll-be-around.flac - opens

From the Aug. 15th live cd session there is no issue with both spaces & ' in a file name.
With todays live image session there is.
Curious if anyone can see the same before trying to figure out what caused this, if just here well so be it

You're right. 

- The context menu shows me rhythmbox and vlc for all 3 flac files.
- rhythmbox always starts, for all files. I have killed all rhythmbox instances before testing for each file.  
- It immediately starts playing the files, except for the first one ("I'll be around.flac").

I tested it really quick because of something I'm doing here so I copy/pasted what I did below.

```

[17:10:49] ahsl@AL-DESK01:[~]: mkdir dev/mc4man-test %% cd dev/mc4man-test
[17:10:52] ahsl@AL-DESK01:[~/dev/mc4man-test]: cp /mnt/home-office/nas/public/media/music/Weezer/Weezer/Weezer_Deluxe_Edition_2004_Blue_Album/07.Say.it.ain\'t.so.flac source.flac
[17:10:55] ahsl@AL-DESK01:[~/dev/mc4man-test]: cp source.flac "I'll be around.flac"
[17:10:57] ahsl@AL-DESK01:[~/dev/mc4man-test]: cp source.flac "Ill be around.flac"
[17:11:01] ahsl@AL-DESK01:[~/dev/mc4man-test]: cp source.flac "I'll-be-around.flac"
[17:11:03] ahsl@AL-DESK01:[~/dev/mc4man-test]: ls -la
total 115992
drwxrwxr-x  2 ahsl ahsl     4096 Sep 15 17:07 .
drwxrwxr-x 19 ahsl ahsl     4096 Sep 15 17:05 ..
-rwxrwxr-x  1 ahsl ahsl 29690685 Sep 15 17:07 I'll be around.flac
-rwxrwxr-x  1 ahsl ahsl 29690685 Sep 15 17:07 I'll-be-around.flac
-rwxrwxr-x  1 ahsl ahsl 29690685 Sep 15 17:07 Ill be around.flac
-rwxrwxr-x  1 ahsl ahsl 29690685 Sep 15 17:06 source.flac
[17:11:10] ahsl@AL-DESK01:[~/dev/mc4man-test]: sudo killall -s KILL rhythmbox
[sudo] password for ahsl: 
[17:11:13] ahsl@AL-DESK01:[~/dev/mc4man-test]: xdg-open .

```
[ATTACH]224192[/ATTACH]

Regards,
Effenberg

---

### Post by mc4man on 2012-09-15
I've tracked this down to a change in glib. Whether if affects any FM other than nautilus don't know, I have pcmanfm on my other install & it is unaffected.

Guess I'll file a nautilus bug & see where that goes

(didn't find exact glib source where this went south due to the extreme pita if trying to downgrade glib
Works fine with  glib2.0 (2.33.8-1), likely breaks with glib2.0 (2.33.12-1)

---

### Post by effenberg0x0 on 2012-09-15
> **mc4man said:**
> I've tracked this down to a change in glib. Whether if affects any FM other than nautilus don't know, I have pcmanfm on my other install & it is unaffected.

Guess I'll file a nautilus bug & see where that goes

(didn't find exact glib source where this went south due to the extreme pita if trying to downgrade glib
Works fine with  glib2.0 (2.33.8-1), likely breaks with glib2.0 (2.33.12-1)

Look at my screenshot, it's Marlin :) Sorry I forgot to actually mention that on text, it would be more intelligent of me. Anyway, Nautilus and Marlin are affected at least. 

Regards,
Effenberg

---

### Post by mc4man on 2012-09-15
To make it a little more confusing - 
If the apostrophe is in the word directly preceding the .ext there is no issue
(or maybe in any word where there are no spaces after

So then this is ok
Ill be around's.flac

Edit: in any event audio & video often comes with spaces & apostrophe's, would be a pain to have to alter though I can see a response of one shouldn't have spaces in names

---

### Post by effenberg0x0 on 2012-09-15
> **mc4man said:**
> To make it a little more confusing - 
If the apostrophe is in the word directly preceding the .ext there is no issue
(or maybe in any word where there are no spaces after

So then this is ok
Ill be around's.flac

Edit: in any event audio & video often comes with spaces & apostrophe's, would be a pain to have to alter though I can see a response of one shouldn't have spaces in names

You're right again.

But I just realized something:

xdg-open I\'ll\ be\ around.flac does not work (rhythmbox opens but won't play)
xdg-open Ill\ be\ around\'s.flac works!

So, any file manager is definitely cut from the bug. This is glib, you were right!

Let me know where to +1.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-09-15
> **mc4man said:**
> Tin any event audio & video often comes with spaces & apostrophe's, would be a pain to have to alter though I can see a response of one shouldn't have spaces in names

<ot>
I had all kinds of problems with spaces, apostrophes, accents and international characters in my (large) media library that is shared via smbfs and later cifs throughout many years. I have some bugs about it that are still opened in LP. So I always used some small scripting to replace spaces for underline, ç for c, à for a, etc...
</ot>

Regards,
Effenberg

---

### Post by mc4man on 2012-09-15
> **effenberg0x0 said:**
> <ot>
I had all kinds of problems with spaces, apostrophes, accents and international characters in my (large) media library that is shared via smbfs and later cifs throughout many years. I have some bugs about it that are still opened in LP. So I always used some small scripting to replace spaces for underline, ç for c, à for a, etc...
</ot>

Regards,
Effenberg,

Ultimately that may be something users will have to do, at the very least underscore their media files. 
I'll go ahead & file on glib a bit later

(also see the same on gvfs-open & the new kid - 
gtk-launch <app> <url>

Really ot - 
Something about FF/12.10 & this forum is driving me crazy - I guess I'm the only one that see text in the middle of a reply disappearing at times, restored thru a scroll up/down

Oh & some ancient history?
[https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/929366](https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/929366)

---

### Post by effenberg0x0 on 2012-09-15
> **mc4man said:**
> ,
Ultimately that may be something users will have to do, at the very least underscore their media files. 
I'll go ahead & file on glib a bit later

Have a look at this, from 2008 :) [https://bugs.launchpad.net/gvfs/+bug/195798](https://bugs.launchpad.net/gvfs/+bug/195798)
They recently decided it was critical, but then it became invalid again. The company I was working for back then created a policy for file names to avoid the bug lol. I think my first shell script to "normalize" safe file names is dated from 2008 or so. It has been a constant for me. I have no idea how ordinary users would handle that though.
> **mc4man said:**
> 
(also see the same on gvfs-open & the new kid - 
gtk-launch <app> <url>

Totally glib then, you nailed it.
> **mc4man said:**
> 
Really ot - 
Something about FF/12.10 & this forum is driving me crazy - I guess I'm the only one that see text in the middle of a reply disappearing at times, restored thru a scroll up/down

Actually, I'm glad you mentioned it. You're on Nvidia too right? I'm getting some square screen areas not properly repainted and some artifacts when scrolling large documents real fast (like holding page down in a 50 page document). This started in 304.43 and is still here in 304.48. It is unusual for me, I don't think I ever had these sort of problems with this hardware. I am blaming the new OpenGL stuff, as the "Framebuffer Object" and "Vertex Object". 

Go to ccsm / OpenGL and rover "FrameBuffer Object" / "Vertex Buffer Object" to get a pop-up definition. My rationale: If someone bothered to write pros and cons (first time I see it), it means glitches are very likely...
> **mc4man said:**
> 
Oh & some ancient history?
[https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/929366](https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/929366)
Ah I remember that one. Actually I got used to just using F6 since that :) And I use class=tilda in "Place Windows" and "Windows Rules" to overcome that other bug we talked about back in PP about Tilda showing up in primary/Secondary monitors erratically and not being able to understand viewport coordinates on multimonitor setups... 

Regards,
Effenberg

---

### Post by mc4man on 2012-09-15
[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/1051447](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/1051447)
feel free to edit bug title or descrip if appropriate

---

### Post by effenberg0x0 on 2012-09-15
> **mc4man said:**
> [https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/1051447](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/1051447)
feel free to edit bug title or descrip if appropriate

+1'd, this was a nice catch.

Thanks!
Effenberg

---

### Post by mc4man on 2012-09-15
The results are considerably worse with a text file depending on how many spaced words are after the '

---

### Post by mc4man on 2012-09-16
found an [upstream fix in glib]("http://bazaar.launchpad.net/~registry/glib/trunk/revision/12621"), rebuilt glib (what a pita), & all fixed
So hopefully 12.10 gets a new glib - if not the gnome3 ppa, if going to the next nautilus release this week, [will need a new glib to build]("https://bugzilla.gnome.org/show_bug.cgi?id=684149")

---


---
title: "Ripping DVD's? Help please"
date: 2007-01-16
forum: Windows
---

### Post by atarileaf on 2007-01-16
I'm a newbie when it comes to working with DVD's. I burnt (or authored) a DVD of home movies a few weeks ago and wasn't smart enough to back up my work when my hard drive crashed so I can't make more copies.

Can I take my existing DVD and rip it into windows and make more copies that way? Will all the menu's and chapters, etc show up when I make copies? I have a version of Nero (not sure which one) that came with my DVD burner. Does it have software for ripping and burning DVD's?

Thanks

---

### Post by edward4130 on 2007-01-16
As far as ripping DVD's, I have two commands/scripts that may help.  Both are
based upon mencoder, which comes as part of Mplayer that is in the Universe/multiverse in ubuntu.

The Mplayer guys are the Hungarian prodigies that bring all media to Unix.
And have available for download all of the Windows and Real player and Apple
codecs.    They have some wonderful documentation  that you could spend the rest of 2007 reading.

Put a DVD in, and try playing it from the command line with

mplayer dvd://1

And be sure that the "1" title is the one that you want.  Sometimes it is not.
Might be dvd://2, or dvd:3.   but usually it is 1.

Once you are sure it is 1, or whatever, run this in a directory with lots of
room:

mplayer -vo xv dvd://1 -dumpstream -dumpfile outfile.mpg


That command makes a large file called "outfile.mpg".   It basically just
plays the DVD, and dumps the mpg data that it reads,  The resulting file is
called "outfile.mpg", though you could call it whatever you want, or rename
it.  It will have video and audio.

If you want to compress it, there are loits of ways, I picked this script up
in the Knoppmyth forums.  Just paste into a file, and save as "rip.sh" or
something, and chmod +x.  Note, because it is in a fourum post, you may have some
trouble with the whitespace on these and may need to do some testing on the
command line to get it right before pasting into a script.

From [http://mysettopbox.tv/phpBB2/viewtopic.php?t=12899](http://mysettopbox.tv/phpBB2/viewtopic.php?t=12899)

#!/bin/bash
THEFILE=$1
NEWFILE=`echo $THEFILE|sed 's/mpg/avi/'`
unlink frameno.avi 2> /dev/null
nice -n 19 mencoder $THEFILE -oac mp3lame -lameopts abr:br=128  -ovc
lavc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=920:vpass=1 -ofps
25 -vf pp=de,scale=720:405 -o "/dev/null"
nice -n 19 mencoder $THEFILE -oac mp3lame -lameopts abr:br=128  -ovc
lavc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=920:vpass=2 -ofps
25 -vf pp=de,scale=720:405 -o $NEWFILE unlink divx2pass.log  2> /dev/null

Actually, on the Mplayer documentation pages, I picked up an example that
works faster for me:

#!/bin/bash
mencoder dvd://1 -ovc lavc -lavcopts vcodec=mpeg4:vpass=1 -oac
mp3lame -lameopts vbr=3 -o /dev/null
mencoder dvd://1 -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell:vpass=2 -oac
mp3lame -lameopts vbr=3 -o output.avi

rm -f divx2pass.log

These do take a long time, longer than the movie took, but they are also
encoding it.  The quality is coming out great for me, better than cable tv
quality, not as good as DVD or HD of course.  The straight rip command takes
about half as long as the play time, I think, not sure.

Here is the documentation page:
[http://www.mplayerhq.hu/DOCS/HTML/en/index.html](http://www.mplayerhq.hu/DOCS/HTML/en/index.html)

hope this helps, my first reply to help somone I feel usefull :)
-Edward

---

### Post by atarileaf on 2007-01-16
Thanks but I meant in regards to doing this in Windows XP, not Linux

---

### Post by mrphd on 2007-01-16
You can try using the free DVDFab Decrypter from [http://www.dvdidle.com/free.htm](http://www.dvdidle.com/free.htm). This should do the trick. It can also remove copy protection so you can use it to backup DVD's that you own, assuming this is legal in your country ;)

---

### Post by 3rdalbum on 2007-01-17
If it's just a DVD that you originally burnt yourself, you can just use Nero's "Copy DVD" function. It's quicker than re-ripping and you won't lose quality.

---

### Post by atarileaf on 2007-01-17
> **3rdalbum said:**
> If it's just a DVD that you originally burnt yourself, you can just use Nero's "Copy DVD" function. It's quicker than re-ripping and you won't lose quality.

Thats perfect. "Copy DVD" comes with the version of Nero that was bundled with my DVD burner. One question though, how would that work if I only have one DVD drive on my computer? Does it copy everything to the hard drive first, then I put a blank DVD in and it copies back?

I do have a spare DVD player lying around that I could install into the computer if I have to but if I can do this without it, it would be easier.

---

### Post by The_Apprentice on 2007-01-17
I had a similar problem when I wanted to copy a DVD with a single DVD drive.

The absolute easiest way is to use DVDShrink to burn it to a file (ISO)
Make sure you set it to "No Compression"
Then burn the ISO using Nero.

You can get DVDShrink from - [http://www.dvdshrink.org/what.html](http://www.dvdshrink.org/what.html)
And there is a guide at - [http://www.doom9.org/index.html?/mpg/dvdshrink31-main.htm](http://www.doom9.org/index.html?/mpg/dvdshrink31-main.htm)

---

### Post by Rhubarb on 2007-01-17
All nero does when copying a DVD (if you only have one DVD drive) is:
1) Copies the DVD to a temporary image file on your hard disk
2) Burns that temporary image file to a blank DVD

DVD shrink and all that other software is great for getting around copy protection and shrinking video on dual layer DVDs to fit on a single layer DVD.

But as you burnt the DVD yourself, just use Nero (or Gnomebaker or whatever your favourite Burning program is) to copy the DVD.

Unlike the old days when you needed a source and a target audio/video tape to dub your audio / video, that's just not needed when you've got large hard drives these days.

---

### Post by atarileaf on 2007-01-17
> **Rhubarb said:**
> All nero does when copying a DVD (if you only have one DVD drive) is:
1) Copies the DVD to a temporary image file on your hard disk
2) Burns that temporary image file to a blank DVD

DVD shrink and all that other software is great for getting around copy protection and shrinking video on dual layer DVDs to fit on a single layer DVD.

But as you burnt the DVD yourself, just use Nero (or Gnomebaker or whatever your favourite Burning program is) to copy the DVD.

Unlike the old days when you needed a source and a target audio/video tape to dub your audio / video, that's just not needed when you've got large hard drives these days.

Perfect. Thats what I thought it would do but thanks for clarifying. Since its just a DVD of home movies, copy protection isn't an issue.
Thanks again.

---


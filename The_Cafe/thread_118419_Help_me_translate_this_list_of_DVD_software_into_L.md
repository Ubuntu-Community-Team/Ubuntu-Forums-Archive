---
title: "Help me translate this list of DVD software into Linux versions"
date: 2006-01-17
forum: The Cafe
---

### Post by vayu on 2006-01-17
I searched around to find out about dvd ripping and copying and became entirely confused.  I finally found an article that explained the process and made it clear to me.  It ended with a list of applications that did each part.  I was wondering if there were some parties interested in translating this list into Linux programs and bonus for K/Ubuntu programs.

Here's the article:
The basics:
[http://www.cdfreaks.com/article/117]("http://www.cdfreaks.com/article/117")
Windows centric list of software solutions:
[http://www.cdfreaks.com/article/117/2]("http://www.cdfreaks.com/article/117/2")

Here's the list to translate to Linux/Ubuntu:

**All in one solutions** (Rip, Remove/Split/Shrink, Burn):

These software packages are recommend for those who just want to make a backup of their movie, don&#8217;t want to fiddle around with settings and spend a lot of time learning. These packages will give you a perfect copy, while saving you a lot of learning time.

    * DVD x Copy Gold &#8211; Software that is currently the most popular in our downloads section and allows you to either transcode a movie, split the movie to multiple discs and/or remove content.
      Also rips the protection from the movie DVD. After that you can burn the movie to a DVD recordable with this software, a totally all in one solution and no other software is needed. Transcoding engine has been tested as one of the best in a recent article about DVD backup software by us.
    * DVD Copy Suite &#8211; Software mainly popular in Germany, is also able to rip, transcode, split and/or remove content. Besides that it also has a burning engine. Transcoding engine has not been tested by us. Also an all in one solution that does not require any third party tools.

**Ripping**:

For ripping there are currently two utilities that are very popular.

    * DVD decrypter - This software is freely available and is able to remove the DeCSS protection, it allows you to select which parts of the movie to rip and is even able to burn the files to a DVD recordable. &#8211; Freeware
    * AnyDVD &#8211; This software is able to remove the DeCSS protection, but is able to do this on the fly. Where you need to spend a lot of time with DVD Decrypter to copy the movie  to your hard disk, this software allows you to rip and burn. Insert the disc in a DVD reading device, and use your favorite software to remove content, split discs or transcode.

**Transcoding**:

    * DVD Shrink (also ripping) &#8211; This free software does a good job in transcoding and is also able to rip the contents of  the DVD. Its strongest points are the possibility to set the compression level, the ability to rip content and that it is totally free. - Freeware
    * DVD2One &#8211; This was the first transcoding engine available on the internet and is still considered as one of the best and fastest engines. Combined with AnyDVD for ripping and CopyToDVD for burning, you will have a perfect combination that is build to work together. Also allows you to select the content you want to remove.
    * DVD95Copy &#8211; Also a transcoding engine, rumors are that D-C-S is using the engine of this software. 

**Transcoding + Burning**:

    * CloneDVD &#8211; This software has been developed by Elby, the developers of CloneCD. Has one of the best looking user interfaces and a well performing transcoding engine. Of course burning is neither a problem. Also works well with AnyDVD.
    * Pinnacle Instant Copy &#8211; This software has according to our test the best transcoding engine, but has the disadvantage that it is terribly slow. Our tests showed that other software might be up to 3x faster and that&#8217;s a lot when talking about hours and not minutes.
    * Nero Recode &#8211; Rumors are that it is based on DVDShrink, because of the similiarities with that software, is included in the Nero 6 package and therefore also has the ability to burn to a DVD.

**Burning**:

    * CopyToDVD &#8211; Small tool developed by the French software company VSO-Software, creates DVD compliant discs. Its engine is also used in other products and the software is optimized to work with DVD2One. Together they are a  perfect and powerful solution.
    * Nero &#8211; Being the emperor of CD burning, this software of course also allows DVD burning. Select the files you have ripped and/or transcoded and burn them to a DVD recordable.
    * Easy CD/DVD Creator &#8211; Widely used and easy to use. When you have already installed this software, there is no need to purchase something else.
    * Recordnow Max &#8211; Popular by many, easy to use and creates perfectly working DVDs.

---

### Post by endersshadow on 2006-01-17
[dvd::rip](http://www.exit1.org/dvdrip/) can rip and then transcode DVDs pretty well.  It's just written in GTK1, so it doesn't look real sharp.  Also, it takes a long time to transcode, as it uses transcode.

[Acidrip](http://untrepid.com/acidrip/) uses mencoder, and I've never particularly liked it.

I've written a program to do rip and encode videos for the iPod Video using ffmpeg.  It seems to be quite a bit faster than dvd::rip and Acid rip, and it provides better quality, as well.  It can be found [in this thread](http://ubuntuforums.org/showthread.php?t=114946).

As for burning, [Gnomebaker](http://gnomebaker.sourceforge.net/v2/) works perfectly for me :-D

If you'd like to use a CLI interface, vobcopy does an amazing job ripping DVDs, especially if you'd like to do it in one VOB file (vobcopy -l -n <titlenum> /dev/dvd /path/to/save/vob/in).  ffmpeg does a great job encoding!

---


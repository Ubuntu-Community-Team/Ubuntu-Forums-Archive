---
title: "Gtkpod .99.2"
date: 2005-12-17
forum: Ubuntu Backports
---

### Post by punkrockguy318 on 2005-12-17
Gtkpod .99.2 fixes many bugs in the one in Breezy, and supports the new iPod video!  This would be very nice to be in Breezy.  I'm not sure if it's in universe yet, though.

---

### Post by mpbretl on 2005-12-17
Latest version in Dapper is 0.94.0.

---

### Post by punkrockguy318 on 2005-12-17
Where can people request universe upgrades?

---

### Post by dell500 on 2005-12-19
Havin' 0.99.2 would be so sweet right now.  0.94 is really buggy.  Hopefully someone puts it up for us Breezy folk.

---

### Post by arcanistherogue on 2005-12-26
I also want this.  GTKpod owns yamipod up and down the street, and thats what I have to use now.

---

### Post by Seth on 2005-12-26
I just uploaded 0.99.2-0ubuntu1 to Dapper last night. This one is a bit trickier because it introduces libgpod0 and libgpod-dev, which are needed to run and build the thing. But they're not in Breezy, so per Backports regulations, this could happen.

You'd need to ask for both packages though.

---

### Post by poofyhairguy on 2005-12-27
[QUOTE=Seth]
You'd need to ask for both packages though.[/QUOTE]

Deal. GTKpod is essential to iPod owners like myself!

---

### Post by m0biu5 on 2005-12-27
Hmm, yeah, iPod video support would be great. I really don't want to run iTunes =/

---

### Post by ember on 2005-12-28
[QUOTE=Seth]I just uploaded 0.99.2-0ubuntu1 to Dapper last night. This one is a bit trickier because it introduces libgpod0 and libgpod-dev, which are needed to run and build the thing. But they're not in Breezy, so per Backports regulations, this could happen.

You'd need to ask for both packages though.[/QUOTE]

That's great news. GTKpod didn't work too well for me in the version that is in breezy. 

I guess, I'll try a personal backport as soon as I am back home.

---

### Post by picpak on 2005-12-28
Here's some debs I made for now (right click and click save as):

[Gtkpod 0.99.2](http://samztercomix.com/kim/tech/linux/programs/gtkpod_0.99.2-1_i386.deb)
[libgpod 0.3.0](http://samztercomix.com/kim/tech/linux/programs/libgpod_0.3.0-1_i386.deb)

---

### Post by ieure on 2005-12-31
Packages aren't compiled with libmp4v2, so they cannot handle videos nor AAC audio files. If, like I, you wanted packages which would do this, don't bother.

---

### Post by punkrockguy318 on 2006-01-01
[QUOTE=ieure]Packages aren't compiled with libmp4v2, so they cannot handle videos nor AAC audio files. If, like I, you wanted packages which would do this, don't bother.[/QUOTE]

Why aren't they compiled with libmp4v2?  [https://launchpad.net/malone/bugs/6321](https://launchpad.net/malone/bugs/6321)

---

### Post by luffy on 2006-01-02
It's not like we need magic to get video support; simply install the libgpod-package found on the first page of this post, compile and install the libmp4v2-sources (mpeg4ip-1.4.1), then compile and install the GTKpod 0.99.2 sources, and voila! Video-support. My problem was getting all the depenencies to install the three separate libgpod-packages (libgpod-common, libgpod0, libgpod-dev), but the libgpod-package provided here did the trick.

---

### Post by punkrockguy318 on 2006-01-02
[QUOTE=luffy]It's not like we need magic to get video support; simply install the libgpod-package found on the first page of this post, compile and install the libmp4v2-sources (mpeg4ip-1.4.1), then compile and install the GTKpod 0.99.4 sorces, and voila! Video-support. My problem was getting all the depenencies to install the three separate libgpod-packages (libgpod-common, libgpod0, libgpod-dev), but the libgpod-package provided here did the trick.[/QUOTE]

The libmp4v2 that is included with ubuntu won't work, am I correct?

---

### Post by luffy on 2006-01-02
I did not try the one included with ubuntu, so I wouldn't know. I just compiled and installed from source.
That would be; download source from here:
[http://mpeg4ip.sourceforge.net/](http://mpeg4ip.sourceforge.net/)
extract the sources, compile and install.
It compiled without any hassle as far as I remember; all deps were in the reps.

Video-transfer is good, not flawless. For me it never says it actually transfers the files, it just "Prepares the transfer". It also does not transfer meta-tags.

---

### Post by Dr Gonzo on 2006-01-10
> **luffy]I did not try the one included with ubuntu, so I wouldn't know. I just compiled and installed from source.
That would be said:**
> http://mpeg4ip.sourceforge.net/[/url]
extract the sources, compile and install.
It compiled without any hassle as far as I remember; all deps were in the reps.

Video-transfer is good, not flawless. For me it never says it actually transfers the files, it just "Prepares the transfer". It also does not transfer meta-tags.
It does transfer the video files, and if you transfer more than one, you'll see this.

---

### Post by Edward The Bonobo on 2006-01-18
For the newbie...can you please step me through how I install these?

btw...I'm still in Hoary, if that makes a difference.

---

### Post by jetpeach on 2006-01-23
[QUOTE=Edward The Bonobo]For the newbie...can you please step me through how I install these?

btw...I'm still in Hoary, if that makes a difference.[/QUOTE]
I'm a newb too, but found this in the old UbuntuGuide
[http://ubuntuguide.org/#installuninstalldebfiles](http://ubuntuguide.org/#installuninstalldebfiles)
testing it now

---

### Post by Kid G on 2006-01-29
Hi

When I compiled Gtkpod.99.2 from the terminal it said that it had been successfully installed but it didnt appear in the applications menu.

When I tried to start the program from the terminal  I got this message:

[INDENT]*gtkpod: error while loading shared libraries: libgpod.so.0: cannot open shared o bject file: No such file or directory*[/INDENT]

Any ideas?

Thanks

---

### Post by Seth on 2006-01-29
As I said before, if you want gtkpod 0.99, you have to have libgpod >= 0.3.

---

### Post by wondering_jew on 2006-01-29
[QUOTE=picpak]Here's some debs I made for now (right click and click save as):

[Gtkpod 0.99.2](http://samztercomix.com/kim/tech/linux/programs/gtkpod_0.99.2-1_i386.deb)
[libgpod 0.3.0](http://samztercomix.com/kim/tech/linux/programs/libgpod_0.3.0-1_i386.deb)[/QUOTE]


Alright here's how I got all of this to work- I tried various things and nothing was working. Instead of using the deb for libgpod_0.3.0 I download the source from the gtkpod website. When i configured (./configure) I found that it was missing a perl module for XML parsing that it needed (probably why the deb didnt work (?)) using apt I installed libxml-parser-perl then I was able to compile and install libgpod. After that I used the deb for gtkpod0.99.2 (thanks btw) and it worked.  Hope something I said helps, I have a feeling that other people may be having problems with it completely unrelated to my own....

---

### Post by macewan on 2006-01-29
[quote=poofyhairguy]Deal. GTKpod is essential to iPod owners like myself![/quote]


and me, I'm too used to gtkpod to 'test' banshee - the chance of f'ing it up as I've done too many times before just isn't worth it
[-(

---

### Post by rickwood on 2006-02-03
[QUOTE=picpak]Here's some debs I made for now (right click and click save as):

[Gtkpod 0.99.2](http://samztercomix.com/kim/tech/linux/programs/gtkpod_0.99.2-1_i386.deb)
[libgpod 0.3.0](http://samztercomix.com/kim/tech/linux/programs/libgpod_0.3.0-1_i386.deb)[/QUOTE]

Thanks picpak!  These debs work great on my Breezy machine.

I know from experience that gtkpod 0.94 doesn't work with my shuffle if the shuffle has been updated with Apple's latest sofware.  In the past after upgrading my shuffle software, I had to subsequently downgrade it to make it work with gtkpod.  My shuffle died this week, and Apple shipped me a new one under warranty.  The new one won't let me downgrade to the last version (some message about this iPod not being compatible with the older iPod software).  So the 0.99.2 gtkpod is a lifesaver for me -- it seems to work fine with my replacement iPod.

---

### Post by patsissons on 2006-02-20
I ran into GREAT difficulties trying to compile gtkpod with video (mp4v2) support.  Turns out that the configure script was not using the root directory in its includes, very bizarre but easily fixable.
```

CFLAGS="-I." ./configure

```
that seems to do the trick.  After finally getting it compiled I decided to make a deb so that others would not have to go through that horrible ordeal that I just went through.  I couldn't get the ubuntu menu item to work properly (not sure why, I'm just using the debian directory from an earlier version of gtkpod), but the rest seems to work properly.  The deb file that I created can be accessed [here]("http://box.go.dyndns.org/dev/gtkpod_0.99.2_i386.deb").
NOTE: I used the libgpod deb that is mentioned above, but if it is not available I also have a copy of the [libgpod]("http://box.go.dyndns.org/dev/libgpod_0.3.0-1_i386.deb") deb on my server as well.

---

### Post by quietglow on 2006-02-20
Would you mind if I posted (or if you'd like to post!) the compiled GTKpod over at my iPod and OSS site (link in my sig)?

It really is a HUGE pain to compile and the last time I did it, I didn't have time to go through the process of learning to build a .deb.

Thanks for your work!

---

### Post by choffee on 2006-02-21
On breezy badger I did the following to get it working...

went to the gtkpod website and downloaded 

libgpod-0.3.0
gtkpod-0.99.2

made a tmp directory and unpacked both into it.
```
$ mkdir tmp
$ cd tmp 
$ tar -zxf libgpod-0.3.0.tar.gz
$ tar -zxf gtkpod 
```

Removed the faac stuff while we compile stuff.
```
sudo apt-get remove libmp4v2-0 libmp4v2-dev faac gstreamer0.8-faac libfaac0 libfaac-dev
```

install the mpeg4ip package from rarewares.org
```
wget http://rarewares.org/debian/packages/unstable/mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb 
sudo dpkg -i mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb

```




changed to the libgpod dir and made a basic debian package
```
$ cd libgpod-0.3.0
$dh_make
( selected single)
$ dpkg-buildpackage -rfakeroot

```
Note: At this point the configure script may bomb out with some missing deps it worked okay on mine but YMMV! Just install the required and try the dpkg-buildpackage again
Then install the deb
```
$sudo dpkg -i ../libgpop-0.3.0-1_i386.deb
```

Now do the same as the above the gtkpod package and hay presto you have a working setup!

Then just reinstall the faac stuff.

```
sudo apt-get install libmp4v2-0 libmp4v2-dev faac gstreamer0.8-faac libfaac0 libfaac-dev

```

More info can be found at: [http://doc.gwos.org/index.php/Ipod_video]("http://doc.gwos.org/index.php/Ipod_video")

---

### Post by quietglow on 2006-02-21
FWIW,

I just put a page with packages up [here]("http://www.quietglow.com/docs/ubuntu5gpod.html")

I finally managed to compile these with working video support, and figured they might help someone out.

---

### Post by souled on 2006-02-21
When trying to run gtkpod, I get this error:
```
gtkpod: error while loading shared libraries: libgpod.so.0: cannot open shared object file: No such file or directory
```

I installed libgpod-0.3, and libgpod.so.0 is located at /usr/local/lib. How can I tell gtkpod that the libgpod.so.0 is located at that spot?

---

### Post by CameronCalver on 2006-02-23
Hey Can some1 plz tell me a detailed and easy to understand way to a ipod to work on linux and be abe to add new songs on it

---

### Post by handy on 2006-02-24
Cameron, you need to learn to use the search facility of this forum, most information that you require has already been posted.  Especially for things like iPods & dial up modems.

So, you go to the **Search** link in the dark brown strip of links high on this page.  Then input **ipod** *in this case*, then scan the results.  It won't take too long, usually to find more than you need.

If after searching & reading you still need your question answered, that is the perfect time to post your question!

If you post lots of questions, without doing some research on the forum first, you may find that you don't get many answers to your questions, because many people already know that the answer is only a search away!

---

### Post by patsissons on 2006-02-24
[QUOTE=quietglow]Would you mind if I posted (or if you'd like to post!) the compiled GTKpod over at my iPod and OSS site (link in my sig)?

It really is a HUGE pain to compile and the last time I did it, I didn't have time to go through the process of learning to build a .deb.

Thanks for your work![/QUOTE]

You are more than welcome to post it at your site.  Just make sure to warn that this is fairly untested.  It worked for me, but that doesn't necessarily mean it will work for others.  I hope that this deb will solve problems but I cannot guarantee anything.  However, if problems do arise, please let me know and I will do my best to recompile the deb if you find that there are missing dependencies.

---

### Post by patsissons on 2006-02-25
[QUOTE=patsissons]The deb file that I created can be accessed [here]("http://box.go.dyndns.org/dev/gtkpod_0.99.2_i386.deb").
NOTE: I used the libgpod deb that is mentioned above, but if it is not available I also have a copy of the [libgpod]("http://box.go.dyndns.org/dev/libgpod_0.3.0-1_i386.deb") deb on my server as well.[/QUOTE]

I just recompiled a new deb file with video support from the cvs (0.99.3).  This brand spakin new deb can be found [here]("http://box.go.dyndns.org/dev/gtkpod_0.99.3-0cvs_i386.deb").  As with before, please notify me if you have any problems with this deb so that I can at least try and fix it.  Also note that the universe repo is required (for libgpod).  Finally, this deb was created **without** mpeg4ip, all that was used to make this deb was the standard deps and libmp4v2-dev.  Enjoy :)

---

### Post by Skatox on 2006-03-08
[QUOTE=souled]When trying to run gtkpod, I get this error:
```
gtkpod: error while loading shared libraries: libgpod.so.0: cannot open shared object file: No such file or directory
```

I installed libgpod-0.3, and libgpod.so.0 is located at /usr/local/lib. How can I tell gtkpod that the libgpod.so.0 is located at that spot?[/QUOTE]

move the files from /usr/local/lib to /usr/lib/

---

### Post by patsissons on 2006-03-09
[QUOTE=Skatox]move the files from /usr/local/lib to /usr/lib/[/QUOTE]
I would advise against that.  You don't want to mess up any programs that depend on the library being in /usr/local/lib .  Your best bet for the simple solution is to create a symbolic link in /usr/lib , that way you don't break anything in the process.
```
sudo ln -s /usr/local/lib/libgpod.so.0 /usr/lib/libgpod.so.0
```
However, realistically, you should reinstall libgpod and gtkpod to ensure a proper installation.  The deb files I have created (below) should be able to replace your current installation and they "should" work (no guarantees).  I recommend giving that a try, and please let me know if that doesn't work, I will try my best to fix the debs so that they will work.

[libgpod_0.3.0-1_i386.deb]("http://box.go.dyndns.org/dev/libgpod_0.3.0-1_i386.deb")
[gtkpod_0.99.3-0cvs_i386.deb]("http://box.go.dyndns.org/dev/gtkpod_0.99.3-0cvs_i386.deb")

---

### Post by pjs_flyer on 2006-03-09
Hi all

Good news and bad new with the gtkpod stuff.  The approach I took was to add the [http://spello.sscnet.ucla.edu/marillat](http://spello.sscnet.ucla.edu/marillat) sarge main repository and first load libmp4-0 and libmp4-dev through synaptic (which forced me to remove some faac and libmp4v2 files) and then to load gtkpod-aac.  gtkpod-aac works fine and finally allows me to use my ipod video...but without faac, I can't rip any more files to aac format (I do this through grip).  If I try to reinstall faac through synaptic, I can't without removing gtkpod-aac and the associated files.  Any suggestions? Not particularly tied to faac, but I don't know of anything else that rips to aac that I can get grip to use...

Cheers

P.

---

### Post by sinaen on 2006-03-10
I think that GTK-pod is an very unsimple program and i dont understan it at all.

how do you do to get it to work correctly. dont misstake me for someone who doesn´t know anything 

I have the latest releasee of gtkpod 99.2 anyway 
but i cannot figure out a simple way to use it to transfer songs on it on my computer

its almost as i want to install macos on my intel laptop. i think thats much much simpler than to understand gtk-pod :/

---

### Post by patsissons on 2006-03-12
- connect your ipod to you computer
- mount the ipod mount point (the large partition)
- set gtkpod to use whatever your mount point is (in the prefs)
- hit the read button
- add mp3's (or videos if you have the right version) with the +files button
- hit sync to apply uncommited changes (transfer the files to your ipod)

hopefully that helps.

---

### Post by jcsjcs on 2006-03-13
Just found this thread -- did nobody notize that mp4 is not required to transfer videos? So unless you also have m4a to transfer, simply compile without mp4.

JCS.

---

### Post by RyanGT on 2006-03-23
You guys rock.  When I woke up this morning, I had some new songs I could upload to my iPod because I had encoded them with the Apple AAC encoder (mp4).  But with the deb posted by patsissons, I am up and running with very little pain.  (My only pain was self-inflicted because I didn't skip to the end of the thread, but starting installing them in chronological order as I read the thread.  But instaling 4 or 5 debs is still much, much less pain than installing from source.)

Thanks again,

Ryan

---

### Post by RyanGT on 2006-03-24
I actually do have a problem.  Using the debs from post #34, I can load *.m4a files onto my iPod, but they don't actually play.  They pop up on the screen for a second with the right id3 type info and play time, but they immediately go to the next track without playing any sound.  I created the tracks using the iTunes AAC encoder.

Any thoughts?

Ryan

---

### Post by RyanGT on 2006-03-24
Sorry, it appears that the problem is that the iPod doesn't like having mp3 and m4a versions of the same song on it.  Once I deleted the mp3's I could play the m4a's.

---

### Post by Sherlock Holmboy on 2006-03-30
[QUOTE=ieure]Packages aren't compiled with libmp4v2, so they cannot handle videos nor AAC audio files. If, like I, you wanted packages which would do this, don't bother.[/QUOTE]

can somebody please post up a compiled version plz? ;)

---

### Post by RyanGT on 2006-03-30
Don't the packages in post #34 of this thread do what you want?  I know they handle AAC audio, but don't know about video.  And I think they are compiled.  They installed too quickly for my computer to have done much compiling.

---

### Post by patsissons on 2006-03-30
[QUOTE=RyanGT]Don't the packages in post #34 of this thread do what you want?  I know they handle AAC audio, but don't know about video.  And I think they are compiled.  They installed too quickly for my computer to have done much compiling.[/QUOTE]

They are also compiled to handle video (mp4 files).  Thanks Ryan, for confirming the m4a compatibility.  I am currently working on a bash script that will use ffmpeg to convert any video to ipod format (and keep the size down while preserving enough quality to view happily on the ipod).  The script still has a few bugs and my school work was piling up this week, but I'm hoping to have it done by the end of the week(end?).  Once I have it done, I will post a deb for an ffmpeg that can perform the conversion.  I also have a script that will do dvd to ipod video transcoding.  The only problem is that it requires handbrake (a dvd transcoding program).  Unfortunately, there is no deb for this program on ubuntu.  But if you can find one, or manage to compile it, this makes converting dvd movies (and even tv series dvd's) very easy.  I will also post this belwo script for anyone who is interested.

just put these somewhere in your path, I recommend /usr/local/bin
dvd2ipod
```

#!/bin/bash
# $1 - output filename
# $2 - title number
handbrake -f mp4 -i /dev/hdd -o $1.mp4 -t $2 -e ffmpeg -E faac -w 320 -r 15 -b 384 -B 48

```

dvd2ipodx (for converting multiple titles, particularily usefull when converting dvd's with multiple tv episodes)
```

#!/bin/bash
# $1 - start title
# $2 - end title
# $3 - base output file name
if [ -z "$3" ]
then
        echo -e "Usage :"
        echo -e "\t$0 start_title end_title output_name\n"
        echo -e "e.g. $0 1 4 myrips"
else
        start=$1
        end=$2
        for (( i=$start; i <= $end; i++ ))
        do
                dvd2ipod $3-$i $i
        done
fi

```

---

### Post by patsissons on 2006-03-31
Ok, so I decided to finish the script tonight (kindof).  There is an issue if you are trying to convert a video file that contains spaces.  The issue is the script doesn't work.  For the life of me I cannot figure out why, for some reason the shell just won't parse the spaces properly.  If anyone has any insight on why this does not work, please let me know because its driving me nuts!!!  However, if you type the exact same command that I am trying to invoke from the script, ffmpeg will not complain, so in such an event I provide the command when you call the script and it fails for this reason.  Anyways, as i promised, here is the script:

```

#!/bin/bash
# Filename is video2ipod
# $1 - input file

# Constants
FORMAT=mp4
VIDEO_CODEC=mpeg4
AUDIO_CODEC=aac
VIDEO_BIT_RATE=300
AUDIO_BIT_RATE=48
FRAME_RATE=15

infile=`echo $1 | sed -e "s/ /\\\\\\ /g"`
#infile=$1
outfile=`basename "$1"`
outfile=`echo $outfile | sed -e "s/ /\\\\\\ /g"`
cmdargs=`echo -e "-i $infile -f $FORMAT -vcodec $VIDEO_CODEC -acodec $AUDIO_CODEC -b $VIDEO_BIT_RATE -ab $AUDIO_BIT_RATE -r $FRAME_RATE ${outfile}.mp4"`

# Debug Info
#echo "infile  = $infile"
#echo "outfile = $outfile"
#echo "exec    = ffmpeg $cmdargs"

echo -e "Saving To '${PWD}/${outfile}.mp4'\r\n"
ffmpeg $cmdargs 2> /dev/null
if [ $? = 1 ]; then
	echo "An error occured, if your file has spaces in it run the following command"
	echo -e "ffmpeg $cmdargs"
fi

```

and the ffmpeg that will get the job done can be downloaded here:
[http://box.go.dyndns.org/dev/ffmpeg_0.cvs20050918-4ubuntu1_i386.deb]("http://box.go.dyndns.org/dev/ffmpeg_0.cvs20050918-4ubuntu1_i386.deb")

---

### Post by xerxesdaphat on 2006-04-04
Hi. Thanks very much for your hard work on the script. However, it doesn't appear to work on a *.ogm file encoded in DivX/XviD. Does the script work only on uncompressed video? Have you any clues how I might be able to turn such a file into something which I can use your script on?

Thank-you very much.

---

### Post by Bazon on 2006-04-16
[QUOTE=RyanGT]I actually do have a problem.  Using the debs from post #34, I can load *.m4a files onto my iPod, but they don't actually play.  They pop up on the screen for a second with the right id3 type info and play time, but they immediately go to the next track without playing any sound.  I created the tracks using the iTunes AAC encoder.

Any thoughts?

Ryan[/QUOTE]

[QUOTE=RyanGT]Sorry, it appears that the problem is that the iPod doesn't like having mp3 and m4a versions of the same song on it.  Once I deleted the mp3's I could play the m4a's.[/QUOTE]
Same problem here although I don't have any mp3 versions of the same song on the iPod.

Any ideas?

greetings,
Bazon

---

### Post by Bazon on 2006-04-16
Solved.

I edited the Tag and Filename with (the windows program) [mp3tag](www.mp3tag.de) but luckily kept the originals. And as I copied the originals to the iPod, they got actually played. :)

---

### Post by sinaen on 2006-10-04
do gtkpod have a good support to m4a and m4b files? as i want to use my ipod as an audiobook-player at my work

I dont think gtkpod work half as well as amarok as it is easier to transfer. gtkpod is easy if you want all your music on your ipod. but i dont want it al on my ipod only the best :D or the things i want to listen to at the moment.

---

### Post by mike_tyrell on 2007-10-03
> **luffy said:**
> It's not like we need magic to get video support; simply install the libgpod-package found on the first page of this post, compile and install the libmp4v2-sources (mpeg4ip-1.4.1), then compile and install the GTKpod 0.99.2 sources, and voila! Video-support. My problem was getting all the depenencies to install the three separate libgpod-packages (libgpod-common, libgpod0, libgpod-dev), but the libgpod-package provided here did the trick.

Hi I am new to this and from what you said you make it sound so simple. Iv been going around the net for ages and still cant do the simple steps you just mentioned :)

---


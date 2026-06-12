---
title: "Making a video from images"
date: 2008-09-22
forum: Ubuntu Studio
---

### Post by GammaPoint on 2008-09-22
Hi, I'd like to make a small animation from a collection of images (as in .png files). What's a simple and intuitive program to do this in?

Thanks for the help!

---

### Post by FakeOutdoorsman on 2008-09-22
FFmpeg FAQ: [How do I encode single pictures into movies?]("http://ffmpeg.mplayerhq.hu/faq.html#TOC14")
> First, rename your pictures to follow a numerical sequence. For example, img1.jpg, img2.jpg, img3.jpg,... Then you may run:

  ffmpeg -f image2 -i img%d.jpg /tmp/a.mpg

Notice that `%d' is replaced by the image number.

`img%03d.jpg' means the sequence `img001.jpg', `img002.jpg', etc...

The same logic is used for any image format that ffmpeg reads. 
Perhaps not simple and intuitive, but it works for me.

---

### Post by GammaPoint on 2008-09-22
Thanks for the response. I did that and was able to generate a movie. However, the movie has a huge green bar on the left hand side and the color is distorted. Anyone have an idea of why this might be?  Here is the command I issued and the output if that gives any indication:

gammapoint@home:~/test$ ffmpeg  -r 0.5 -b 1800 -i %03d.jpg test.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, image2, from '%03d.jpg':
  Duration: 00:00:06.0, start: 0.000000, bitrate: N/A
  Stream #0.0: Video: mjpeg, yuvj444p, 644x650,  0.50 fps(r)
File 'test.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'test.mp4':
  Stream #0.0: Video: mpeg4, yuv420p, 644x650, q=2-31, 1 kb/s,  0.50 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=    3 q=2.0 Lsize=      36kB time=6.0 bitrate=  48.9kbits/s   
video:35kB audio:0kB global headers:0kB muxing overhead 1.932528%

---

### Post by cotcot on 2008-09-24
kdenlive (simple)
blender VSE (more powerful)

---

### Post by richardcoates on 2008-09-30
I found dvd-slideshow to be very effective. I used it to create a movie of
1800 jpeg camera photos and am quite pleased with the result.
The learning process was a little daunting however...I had to write a script to automate the process. If anyone is interested I could write a howto.

---

### Post by locum on 2008-10-09
Hi Richard, personally I would be extremely grateful for a dvd–Sideshow howto as I enjoy watching & sharing holiday pics this way,  I usually end up back on XP running Studio 10 or Roxio 8. I hope you get more interest in your offer which may inspire you to do it. 
Regards. Martin.

---

### Post by richardcoates on 2008-10-11
why: My daughters kindy wanted a disk of the years precious memories.
     This added up to about 2,000 jpeg camera pictures. I thought it would be nice if these could be viewed using a standard dvd player in a slideshow format. Hours of web searching produced little in the way of help for the first time Ubuntu user. Hopefully my experiences will help others.

My first install was on  my "7.10" box. The package in the repos is flawed and while there are workarounds I decided to start again fresh...

mysetup:
ubuntu 8.04
dvd-slideshow 0.8.1 
libsox-fmt-all
custom script to call programs as needed.

lets begin, i'll try to remember everything I did:

installation:
1/ standard Ubuntu 8.04 with latest updates
2/ use Synaptic to install dvd-slideshow 0.7.5 and dependencies, then uninstall dvd-slideshow 0.7.5. The dependencies will be left in place.
3/ Now download "dvd-slideshow 0.8.1 svn". from (paste code into firefox window)..
[http://svn.sourceforge.net/viewvc/dvd-slideshow.tar.gz?view=tar](http://svn.sourceforge.net/viewvc/dvd-slideshow.tar.gz?view=tar)
4/ create a /bin directory in your home directory
      mkdir  ~/bin   or use nautilus.
5/ Double click on dvd-slideshow.tar.gz (downloaded above) in nautilus or open from "downloads" in Firefox. Copy the executables:
 dir2slideshow, dvd-burn, dvd-menu, dvd-slideshow, dvd-slideshowrc, 
gallery1-to-slideshow, jigl2slideshow to 
  ~/bin instead of running the install script. 
6/ Because of this I had to add ~/bin to the "path" ..
run:  gedit .bashrc  in terminal (or open this HIDDEN file in nautilus)  .bashrc (note dot), and add this line to end of file....
     export PATH=$HOME/bin:$PATH
7/ Now open Synaptic and install libsox-fmt-all and dependencies. 
   now logout & back in or reboot.
8/ make sure the executables are in fact "executable".. 
run in terminal:   chmod 700 -R ~/bin      OR in Nautilus, navigate to the bin directory in your "home", right-click on each file, click Properties, click Permissions tab, tick box "Execute".
To test, run in terminal:   which dvd-slideshow 
should produce something like..  /home/richard/bin/dvd-slideshow

Now you should have a working setup of Dvd-slideshow 0.8.1.
To make it a little easier to use..

9/  I created a script which calls dvd-slideshow and its utilities as  needed and creates an iso image ready for burning when done. It is heavily commented. Make sure you have plenty of disk space! Set the options: dvd name, working directory, pics location on disk. "Swipe" the code and save into a "Gedit" text file as myslideshow.sh in ~/bin. Make executable as in "8/" above. 
edit: set for PAL (-p) tv output


#! /bin/sh
#  create slideshow  of jpeg images
echo "        !!!!!!!!!!!!! NO SPACES IN PICTURE NAMES !!!!!!!!!!!!!!         "
#  package "libsox-fmt-all" and deps needed for Ubuntu 8.04
# Set your options below..
dvd="Kindy 2008"
workdir=/home/richard/temp/
pics="/media/disk/backup/mynewpics/kindypics/not-done/"
#pics=/media/disk/backup/mynewpics/kindypics/not-done/2008-9-19-TeddyBearsPicnic/  #nb trailing slash

mkdir $workdir/ISOs  $workdir/temp $workdir/Videos/ >/dev/null
for piccies in `ls $pics`
  do
name=$piccies
#
#  from:   [http://dvd-slideshow.sourceforge.net/wiki/Dir2slideshow_0.8.0](http://dvd-slideshow.sourceforge.net/wiki/Dir2slideshow_0.8.0)
#  dir2slideshow - Creates an input (text)file for dvd-slideshow from pictures(jpg,png) in a directory.
#  dir2slideshow [-o <output directory>] [-t <Seconds per picture>] [-w (wipe)or -c <Crossfade seconds>] -n <Slideshow name> [-T] [-M] [-s subtitle_text] [-notitle] <Images directory>
#
cd $workdir
dir2slideshow -o $workdir/temp/ -t 5  -c 1  -n "$name"  -i "$pics$piccies"
sleep 2s
#    from         [http://dvd-slideshow.sourceforge.net/wiki/Dvd-slideshow_0.8.0](http://dvd-slideshow.sourceforge.net/wiki/Dvd-slideshow_0.8.0)
#  dvd-slideshow - Creates a slideshow movie in DVD video format from a list of pictures and effects.
#  dvd-slideshow [-n <slideshow name>] [-o <output directory>] [-b <background jpeg>] [-a <audiofile1> -a <audiofile2> -a <audiofileN>] [-p] [-L] [-H] [-mp2] [-r] [-smp] [-border <bordersize>] [-theme <themename>] [-f] <input text file>
#          -r <autocrop>
dvd-slideshow -n $name -o $workdir/temp/ -p -r -f $workdir/temp/$name.txt  # *each dir o/p as dirname.vob* #
done
#
sleep 2s
vobs="$(ls $workdir/temp/*.vob|awk '{FS="\*.vob"} { for (i=1; i<=NF; i++) print " -f " $i }'  |awk '{printf("%s ",$0)}' )"
# vobs displayed as:  -f dirname.vob -f dirothername.vob -f dirotherothername.vob ...
echo "  vob-files.... $vobs"
#
#  copy pics to dvd filesystem dir to include them in iso.
#  cp -a ${pics}${idx} dvd_fs
#
#  create manual iso (instead of using dvd-menu)
#  mkisofs -dvd-video -udf -o dvd.iso dvd_fs
#
echo "do you want to create a video filesystem & Iso image of ALL the vob files? ...."
echo "     type y to continue, press enter, any other key to exit."
key=a; read key
if [ "$key" != "y" ]; then exit; fi
#
cd $workdir/ISOs
#
#  from:  [http://dvd-slideshow.sourceforge.net/wiki/Dvd-menu_0.8.0](http://dvd-slideshow.sourceforge.net/wiki/Dvd-menu_0.8.0)
#  dvd-menu creates menu structure (if required), and calls dvdauthor to create the dvd video file structure
#       I/P file               O/P dir          Name          pal  don't-create-menu,  create iso-in-current-dir_can't_change!
dvd-menu  $vobs -o $workdir/Videos/ -n $dvd -p -nomenu  -iso
#        (-f in var)           $name.vob
#

10/ how-and-why:
   I set my script like this because of the sheer number of jpg files.
My pics are saved at weekly/fortnightly intervals in subdirectories named something like.. 2008-10-10  inside the pics directory, each one containing about 150 to 300 files. Then if the script falls over its easier to track down the cause. For example, one month all the pics had spaces in their filenames ( the pics came from a windows box) and it took ages to find out why it was crashing.. I now have code to check this if anyone asks? 
  This script will create extra working directories inside the "workdir" you set. These are: temp, videos, ISOs. A "directory-name.vob" file will be created in the temp dir above for each subdirectory in "pics".
  After the vobs are created the script will ask for a "y" to continue and create the iso and save it in ISOs. I did this so I can set a different working dir and create monthly vobs, and at the end of the year copy them all to "temp" and then create one iso of them all.
  I hope this gives someone a start.. Many thanks to Scott Dylewski for this fine product, more info at...
[http://dvd-slideshow.sourceforge.net/wiki/Dvd-slideshow_0.8.0](http://dvd-slideshow.sourceforge.net/wiki/Dvd-slideshow_0.8.0)
regards, Richard Coates.

---

### Post by richardcoates on 2008-10-16
Does it work ok for you?

---

### Post by Wobblybob on 2008-12-14
Thanks Richard,
I've been using linux ubuntu [now ubuntu 8.10] for a year now and when someone at work asked me to do them a slideshow with music I was lost for a while.
Your script pointed me in the the right direction once I sorted out some problems with ffmpeg and amended the script a little. I found your script gave me a directory not found error until I amended your line:
dir2slideshow -o $workdir/temp/ -t 5 -c 1 -n "$name" -i "$pics$piccies"
to
dir2slideshow -o $workdir/temp/  -t 10 -c 1 -n "$name" -i "$pics"

I also found my test run with 3 and 5 images resulted in a slideshow of 15 and 25 images until I moved the "done" option under the first dvd-slideshow call.

My script now looks like this, I've marked my amendments and additions;

#! /bin/sh
# create slideshow of jpeg images
echo " !!!!!!!!!!!!! NO SPACES IN PICTURE NAMES !!!!!!!!!!!!!! "
# package "libsox-fmt-all" and deps needed for Ubuntu 8.04
# Set your options below..
[COLOR="Red"]dvd_name="Yorkshire_Sculpture_Park"[/COLOR]
## dvd_name shows the title of your slideshow on the 1st slide, use underscores for spaces dvd-slideshow removes them ##
#
workdir=/home/martin/Photos/slideshow-temp/
## dir for dvd-slideshows workig files and results, use trailing slash ##
#
pics=/home/martin/Photos/slideshow-photos/
## path to photos, use trailing slash ##
#
[COLOR="Red"]music=/home/martin/Photos/slideshow-music/[/COLOR]
## path to slideshow music, use trailing slash
#
## make working directories ##
mkdir $workdir/ISOs $workdir/temp $workdir/Videos/ >/dev/null
#
## list and store names of images ##
for piccies in `ls $pics`
do
#
name=$piccies
#
# from: [http://dvd-slideshow.sourceforge.net...lideshow_0.8.0](http://dvd-slideshow.sourceforge.net...lideshow_0.8.0)
# dir2slideshow - Creates an input (text)file for dvd-slideshow from pictures(jpg,png) in a directory.
# dir2slideshow [-o <output directory>] [-t <Seconds per picture>] [-w (wipe)or -c <Crossfade seconds>] -n <Slideshow name> [-T] [-M] [-s subtitle_text] [-notitle] <Images directory>
[COLOR="Red"]done[/COLOR]
#
[COLOR="Red"]## add title to text file to on 1st slide ##
name=$dvd_name[/COLOR]
#
cd $workdir
dir2slideshow -o $workdir/temp/  -t 10 -c 1 -n "$name" -i "$pics"
## dir2slideshow -o $workdir/temp/ -t 5 -c 1 -n "$name" -i "$pics" ##
#
sleep 2s
#
# from [http://dvd-slideshow.sourceforge.net...lideshow_0.8.0](http://dvd-slideshow.sourceforge.net...lideshow_0.8.0)
# dvd-slideshow - Creates a slideshow movie in DVD video format from a list of pictures and effects.
# dvd-slideshow [-n <slideshow name>] [-o <output directory>] [-b <background jpeg>] [-a <audiofile1> -a <audiofile2> -a <audiofileN>] [-p] [-L] [-H] [-mp2] [-r] [-smp] [-border <bordersize>] [-theme <themename>] [-f] <input text file>
# -r <autocrop>
dvd-slideshow -n $name -o $workdir/temp/ [COLOR="Red"]-a $music/everyday.mp3[/COLOR] -p -r -f $workdir/temp/$name.txt # *each dir o/p as dirname.vob* #
#
#
sleep 2s
vobs="$(ls $workdir/temp/*.vob|awk '{FS="\*.vob"} { for (i=1; i<=NF; i++) print " -f " $i }' |awk '{printf("%s ",$0)}' )"
# vobs displayed as: -f dirname.vob -f dirothername.vob -f dirotherothername.vob ...
echo " vob-files.... $vobs"
#
# copy pics to dvd filesystem dir to include them in iso.
# cp -a ${pics}${idx} dvd_fs
#
# create manual iso (instead of using dvd-menu)
# mkisofs -dvd-video -udf -o dvd.iso dvd_fs
#
echo "do you want to create a video filesystem & Iso image of ALL the vob files? ...."
echo " type y to continue, press enter, any other key to exit."
key=a; read key
if [ "$key" != "y" ]; then exit; fi
#
cd $workdir/ISOs
#
# from: [http://dvd-slideshow.sourceforge.net...Dvd-menu_0.8.0](http://dvd-slideshow.sourceforge.net...Dvd-menu_0.8.0)
# dvd-menu creates menu structure (if required), and calls dvdauthor to create the dvd video file structure
# I/P file O/P dir Name pal don't-create-menu, create iso-in-current-dir_can't_change!
dvd-menu $vobs -o $workdir/Videos/ -n $dvd_name -p -nomenu -iso
# (-f in var) $name.vob

Thanks again

Martin

---

### Post by annietc on 2008-12-15
Wow this might be useful for me but it seems a bit daunting for a newbie.. with all the scripts... 
I also want to make the same thing and I installed SMILE but it requires a powerful computer to operate it...so I can't use it now. 
Will this work on very simple and old laptop, I mean mine has only 512M RAM....

---

### Post by annietc on 2008-12-15
If want to just make a simple video, with 24 pix, and a 4.5mins mp3 song, with each pic lasting 7.5 seconds, each black screen between pic lasting 3.5 seconds, between each one of them there is a "fade" effect, and the music starts from the 4th second of the whole video, finally I need a small video that I could post on youtube, how to type the script for this? Sorry I just switched to Linux.. and know nothing about those. Thanks!

---

### Post by cowanh00 on 2008-12-16
> **annietc said:**
> If want to just make a simple video, with 24 pix, and a 4.5mins mp3 song, with each pic lasting 7.5 seconds, each black screen between pic lasting 3.5 seconds, between each one of them there is a "fade" effect, and the music starts from the 4th second of the whole video, finally I need a small video that I could post on youtube, how to type the script for this? Sorry I just switched to Linux.. and know nothing about those. Thanks!

I personally like a program called [Kdenlive]("http://www.kdenlive.org/") for this sort of thing.

---


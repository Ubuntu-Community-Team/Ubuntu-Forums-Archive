---
title: "Script to find duplicate videos based on content regardless of format."
date: 2009-03-29
forum: Tutorials
---

### Post by xxsludgexx on 2009-03-29
Edit: mis-spelling in the title... Fail.

Let's say you have 3 videos, all of which are the same content, but one is a .mov, one is a .avi and one is a .wmv? A md5 check won't do much good, you could check the movie times and do some comparisons, but frame rates and such change when a video gets re-encoded. So here's my fancy method that works pretty well, but it's kind of slow if you want it to perform a good check.

This script helps try to track down those kinds of videos that are similar in content, but not in format.
It requires mplayer, imagemagick, sort, uniq, find, md5sum, grep and perl.

It basically does this: it grabs the first 1000 frames of the movies in question, re-sizes them to 10x10 and convents them to simple black and white images. Not gray scale, but either full black, or full white. This is called a threshold.

[This is the effect. I'm referring to.]("http://www.insidegraphics.com/digital_art/images/photoshop_layers_green.jpg")

What you are left with are a bunch of images that look like little checkerboards. My idea (I don't know how original this idea is but who cares) was this: 

[B]Those checker boards should match up often with another video that has the same content. And videos that are not the same content, shouldn't match up, at least not much.
[/B]

Pseudo-code:
I render out 1000 frames, starting from the 1st frame (you can start later in, but key frames become an issue and can cause time sync to be lost between potentially similar videos). I then delete the first 300 of those frames (I have blank screens and fades in's at the start so I skip a couple seconds in. Similar concept people use when making video thumbnails. Skip a little ways in.) I then convert them to those threshold'd images. I then calculate md5 hashes of these uncompressed bmp images. Two identical bmp files will have the same md5 hash as oppose to two jpegs of various compression levels. I then do some sorting and uniq'n and it tells me how many frames from one video, matched that in another video. I would love for someone to add on to this in some way. Let me know if anyone can make it better. =)

I release this code under the GPLv2. So send me some changes if you make any. =)
 

Example Output:
```

sludge@ttzztt:/$ ~/scripts/viddupes3.pl
Cleaning up directories...
Rendering 1000 frame(s), skipping the first 300. (700 end result)
/mnt/Seagate/akira.the.dog.wmv
/mnt/Seagate/akira.the.dog.mp4
/mnt/Seagate/meowser.the.cat.wmv
/mnt/Seagate/meowser.the.cat.avi
Calculating hash table...
Here come the delicious dupes:
/mnt/Seagate/akira.the.dog.wmv.count
        63.14% match with /mnt/Seagate/akira.the.dog.mp4

/mnt/Seagate/meowser.the.cat.wmv.count
        63.29% match with  /mnt/Seagate/meowser.the.cat.avi

```
akira.the.dog.mp4 is about a 200meg mp4 640x480
akira.the.dog.wmv is about 30 megs and is about half that rez.
similar type of thing with the other cat files.

This code could use a bit of cleanup, but I'm a nerd, and wanted to share it somewhere. CHECK MY CODE COMMENTS BEFORE YOU RUN THIS.

```

#!/usr/bin/perl
use File::Path;

my $ofh = select STDOUT; #Make stdout hot
$| = 1;
select STDOUT;

$getimages = 1000; #render out 1000 images
$deletefirst = 300; #delete the first 300
$totalimages = $getimages - $deletefirst; 
$minmatch = 2; #might use this later (not used now)

$searchdir = "/mnt/Seagate/"; #directory to scan
$basedir = "/tmp/hashchecker/"; #working directory, this directory will get clobbered, make it something uniq in /tmp/

print "Cleaning up directories...\n";
rmtree($basedir); #see, I told you.

print "Rendering $getimages frame(s), skipping the first $deletefirst. ($totalimages end result)\n";

@videofiles=`find "$searchdir" -type f -printf "%p\n" | grep -Ei "\.(mp4|flv|wmv|mov|avi|mpeg|mpg|m4v|mkv|divx|asf)"`;
foreach $i (@videofiles)
{
 chomp $i;
 print "$i";
 @filename = split(/\//,$i);
 $imgdir = $basedir . "/$filename[-1]";
 mkpath($imgdir);
 $data=`cd "$imgdir"; mplayer -really-quiet -vo png -frames $getimages -ao null "$i" 2>&1`;
 @data=`find "$imgdir" -type f -name "*.png" | sort`;
 for ($deletecount=0; $deletecount < $deletefirst; $deletecount++)
 {
   chomp $data[$deletecount];
   unlink $data[$deletecount];
 }
 $data=`mogrify -resize 10x10! -threshold 50% -format bmp "$imgdir/*"`;
 $data=`find "$imgdir" -type f -name "*.png" -delete`;
 print "\n";
}
print "Calculating hash table...\n";
@md5table=`find "$basedir" -type f -name "*.bmp" -exec md5sum "{}" \\; | sort | uniq -D -w32`;
foreach $x (@md5table)
{
 chomp $x;
 $x =~ m/^([0-9a-f]{32})/i;
 $md5=$1;
 $x =~ m/^[0-9a-f]{32}[ \t]*(.*)/i;
 $fullpath=$1;
 @filename = split(/\//,$x);
 open (MYFILE, ">>$basedir/$md5.md5") or die "couldnt open file\n";
 print MYFILE "$fullpath\n";
 close (MYFILE);
}

@hashfiles=`find "$basedir" -type f -name "*.md5"`;
foreach $i (@hashfiles)
{
 chomp $i;
 @uniqfiles=`sort "$i" | uniq`;
 $uniqsize=@uniqfiles;
 if ($uniqsize > 1)
 {
   $firstpass = 1;
   foreach $x (@uniqfiles)
   {
     chomp $x;
     @filename=split(/\//,$x);
     if ($firstpass == 1)
     {
       $outfile=$filename[-2];
       $firstpass=0;
     }
     else
     {
       if ($outfile ne $filename[-2])
       {
         open (COUNTFILE, ">>$basedir/$outfile.count") or die "$outfile -> couldnt open file\n";
         print COUNTFILE "$filename[-2]\n";
         close (COUNTFILE);
       }
     }
   }

 }
}
print "Here come the delicious dupes:\n";
@hashfiles=`find "$basedir" -type f -name "*.count"`;
foreach $i (@hashfiles)
{
 chomp $i;
 print "$i\n";
 @uniqfiles=`sort "$i" | uniq -c`;
 foreach $x (@uniqfiles)
 {
    chomp $x;
    $x =~ m/^[ \t]*([0-9]{1,50})/i;
    $percent = $1/$totalimages*100;
    $x =~ m/^[ \t]*[0-9]{1,50}(.*)/i;
    $filename=$1;
    printf "\t%.2f% match with %s\n",$percent,$filename;
 }
 print "\n";

}
exit;


```
Now that it works, I now have the task of coding it better and cleaner, and use less unix utils.
:guitar:

---

### Post by hackel on 2010-04-29
I've been looking for a program to do exactly this for a while now...  My problem is having several clips of the same content, cut in different places, different lengths, etc. and I want to group them all together to either remove duplicates or splice them together.  Have you made any improvements to this at all?  I look forward to trying it out, great idea!

---

### Post by ChrisQ on 2011-02-27
Hi,
This seems pretty useful. Have you updated this at all? One feature that would be really useful for those of use with multiple core machines would be an option to choose how many process to run in parallel.


Thanks,

Chris

---

### Post by hackeron on 2011-07-11
Rewrote that script into Ruby. Source code available here:

[https://github.com/hackeron/ruby_experiments/blob/master/dedup.rb](https://github.com/hackeron/ruby_experiments/blob/master/dedup.rb)

Needs some improvements but seems to work :)

Note, if you get something like: `require': no such file to load -- mimemagic OR child process, you may need to run:

```

gem install mimemagic
gem install childprocess

```

---

### Post by DieterDHoker on 2012-04-24
interesting approach, i will give it a try. Currently I'm trying to do the same for a library of movies by looking at the audio fingerprint of the last minutes instead, using:
[http://search.cpan.org/~pepe/Audio-Ofa-1.01/lib/Audio/Ofa.pm](http://search.cpan.org/~pepe/Audio-Ofa-1.01/lib/Audio/Ofa.pm)

---


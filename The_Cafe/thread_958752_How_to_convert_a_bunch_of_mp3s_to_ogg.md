---
title: "How to convert a bunch of mp3s to ogg?"
date: 2008-10-25
forum: The Cafe
---

### Post by days_of_ruin on 2008-10-25
Anyone know of a good program/shell script?
I just updated the firmware on my sansa fuze so now it can play ogg.

---

### Post by ad_267 on 2008-10-25
You can use soundconverter, a small gtk app.

---

### Post by days_of_ruin on 2008-10-25
> **ad_267 said:**
> You can use soundconverter, a small gtk app.

Can it do it by the folder?I have programs that do it a file at a time.
I want something that is automated.

---

### Post by Eisenwinter on 2008-10-25
Here's a small script I wrote in Perl, which uses ffmpeg.
```

#!/usr/bin/perl -w

use strict;
use File::Find;
use File::Basename;
#use Irssi;

#sub get_path_irssi {
 #my ($data, $server, $witem) = @_;
#}
my $dir = shift; #get directory.
return unless $dir;
my (@Files, $match);
my $MyUsername = `whoami`; #Get username, so we can move the files to the trash later, dynamically, should this script ever be released to the public.
find(\&search_, $dir);

sub search_ {
 my $File_ = $File::Find::name;
 if ($File_ =~ /\.mp3$/i) {             
  push(@Files, chr(34) . $File_ . chr(34));
 }
}

#for (my $i = 0; $i < scalar @Files; $i++) {

foreach $match (@Files) {
 #WELCOME TO PERL BITCH!
 my ($fname, $fpath, $sufx) = fileparse($match);
 #print "$fname\n$fpath\n";
 my $outpath = $fpath . $fname;
 $outpath =~ s/\.mp3/\.ogg/;
 #print "$outpath\n";
 `ffmpeg -i $match -acodec vorbis -ab 192k -ac 2 $outpath`;
 `mv $match /home/$MyUsername/.local/share/Trash/files/`;
  print "File converted and moved to Trash";
}

```

Usage: open up the terminal, and type "perl <dir you wish to convert all files in>".
It will then search for all the files in that directory, add them to an array, and convert them one by one, after each file has finished being converted, the source file will be moved to trash.

I made it move to trash instead of using "rm file" so in case there's some ffmpeg error, you don't lose the file. Hope you find this useful.

---

### Post by tikal26 on 2008-10-25
If you use KDE you can use Pearl Audio converter which can b euse as a stand alon inside konqueror, Dolphin or Amarok i like it very much and its easy as picking the files you need form konqueror/dolphin right cliick and click on the fromatt of you choice

---

### Post by maestrobwh1 on 2008-10-25
The kde equivalent soundkonverter will do it for you and yes, you can just add an entire folder.

---

### Post by AndyCooll on 2008-10-25
There's an app in the repos called mp32ogg. That will do the job for you. Though it's command line only, the manpages are easy to follow and it's quite easy to configure.

:cool:

---

### Post by Turgon on 2008-10-25
Remember you will losse some quality when you do lossy to lossy convertion, so its really not at good idea.

---

### Post by bruce89 on 2008-10-25
> **Turgon said:**
> Remember you will losse some quality when you do lossy to lossy convertion, so its really not at good idea.

Indeed, recompressing a lossily compressed file again is pointless. It only makes the original file even worse, and perhaps makes it bigger too.

---

### Post by stmiller on 2008-10-25
Yes don't do this. It's is like taking audio which has gone through one type of shredder and putting it through then another type of shredder.

---

### Post by LookTJ on 2008-10-25
[http://freshmeat.net/projects/audio-convert](http://freshmeat.net/projects/audio-convert)

this is what I used when I was using Arch.

[http://download.savannah.gnu.org/releases/audio-convert/audio-convert_0.3.1.1-0ubuntu1_all.deb](http://download.savannah.gnu.org/releases/audio-convert/audio-convert_0.3.1.1-0ubuntu1_all.deb)

here's one with a GUI.. [http://www.diffingo.com/oss/audio-convert-mod](http://www.diffingo.com/oss/audio-convert-mod)

---

### Post by treesurf on 2008-10-25
The soundconverter program, which is in the repos can do entire folders with no problems.  It is a very easy program to use.  

Of course, what has been said above about the loss in audio quality should be kept in mind.

---

### Post by Spike-X on 2008-10-26
Never mind how, the question is why?

Just because you can, doesn't mean you should.

---

### Post by hessiess on 2008-10-26
You should never convert between lossy formats. in the future try to source uncompressed audio and convert that to Vorbis.

---

### Post by nixscripter on 2008-10-26
Well, you can try this, which I've done just recently. It's similar to the perl script idea, but a little shorter:

```

cd my_music
find . -name '*mp3' -exec ffmpeg -ab 1024k -i {} {}.ogg \;

```

The number 1024k is to address the critical who rightly point out the problem with overlapping artifacts between lossy formats. It is an attempt to make the maximum bitrate so high that the VBR will actually be converted at whatever rate the data will support, i.e there isn't 1024 kbits of data to be read. There will still be artifacts, but fewer of them.

By the way, I believe in open formats, but I find MPEG-4 audio was much better quality for the same bitrate. Perhaps it's ffmpeg, I'm not sure.

---


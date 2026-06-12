---
title: "Howto: Setup more realistic voices in Festival."
date: 2008-01-24
forum: Tutorials
---

### Post by patrock on 2008-01-24
The [CMU Arctic]("http://festvox.org/cmu_arctic/") voices sound magnitudes better than the standard Festival voices.  They use prerecorded utterances from Project Gutenberg.

The voices can be downloaded from [here.]("http://www.speech.cs.cmu.edu/cmu_arctic/packed/") Each voice is around 120 MB.  For a description of each voice visit the [CMU Arctic]("http://festvox.org/cmu_arctic/") page.  To hear them visit the [voice demo page.]("http://festvox.org/voicedemos.html")

Here's an example of howto install one.

If it's not already installed you'll need to get festlex-cmu:
```
sudo apt-get install festlex-cmu
```

Then:
```

cd /usr/share/festival/voices/english/
sudo wget -c http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_clb_arctic-0.95-release.tar.bz2
sudo tar jxf cmu_us_clb_arctic-0.95-release.tar.bz2 
sudo ln -s cmu_us_clb_arctic cmu_us_clb_arctic_clunits
sudo cp /etc/festival.scm /etc/festival.scm.backup
sudo echo "(set! voice_default 'voice_cmu_us_clb_arctic_clunits)" >> /etc/festival.scm

```

Test it out:
```
echo "This is a test." | festival --tts
```

You can delete the voice's .tar.bz2 file once it's unpacked.
```
rm /usr/share/festival/voices/english/cmu_us_clb_arctic-0.95-release.tar.bz2 
```

If you install another one comment out the first voice_default line in /etc/festival.scm with 2 semi-colons.

```
;;(set! voice_default 'voice_cmu_us_clb_arctic_clunits) 
```

---

### Post by PinkFloyd102489 on 2008-01-24
SIOD ERROR: could not open file /usr/share/festival/dicts/cmu/cmulex.scm
closing a file left open: /usr/share/festival/voices/english/cmu_us_clb_arctic_clunits/festvox/cmu_us_clb_arctic_lexicon.scm
closing a file left open: /usr/share/festival/voices/english/cmu_us_clb_arctic_clunits/festvox/cmu_us_clb_arctic_clunits.scm
closing a file left open: /usr/share/festival/init.scm
festival: fatal error exiting.

---

### Post by PinkFloyd102489 on 2008-01-25
You also included a female voice in the install process. Might want to post both male and female, as Im now removing the female and installing male. :-P

---

### Post by patrock on 2008-01-25
The male voices sound good too.  The [HTS voices sound better]("http://http://hts.sp.nitech.ac.jp/") but I haven't gotten them working yet.  You can hear them on the [demo page.]("http://festvox.org/voicedemos.html")

---

### Post by dchurch24 on 2008-02-14
I cannot get Festival to work at all - it worked fine in Feisty, but in Gusty I get the following error:

SIOD ERROR: could not open file /usr/share/festival/voices/english/cmu_us_clb_arctic_clunits/festvox/cmu_us_clb_arctic_clunits.scm
closing a file left open: /usr/share/festival/init.scm
festival: fatal error exiting.


I have no idea where to go or what to do next! Please help!

---

### Post by peabody on 2008-02-14
First I would try and see if I could get it working with the packaged voices in fiesty.  Install the festvox-rablpc16k and put this in your festival.scm:

(set! default_voice 'voice_rab_diphone)

---

### Post by joerite on 2008-02-29
Thanks for this. Is there one similar to GLaDOS. I would make it if I knew how

---

### Post by unimatrix on 2008-03-15
If somebody is getting this error:
> 
lexicon english_poslex not defined

It means you need to:
```

sudo apt-get install festlex-poslex

```

Just had to write this down here, because I couldn't find any solutions elsewhere.

---

### Post by MonkeeSage on 2008-04-10
> **patrock said:**
> The male voices sound good too.  The [HTS voices sound better]("http://http://hts.sp.nitech.ac.jp/") but I haven't gotten them working yet.  You can hear them on the [demo page.]("http://festvox.org/voicedemos.html")

I got the HTS voices working by doing the following (not sure, but they may depend on the CMU Arctic voices being installed (***edit:** they don't*), which I already have — they are *way* smaller):

(*[color=green]NOTE:[/color] I've started a HOWTO with detailed instructions on how to install all of the available English voices for festival: MBROLA, CMU Arctic, and Nitech HTS. [thread="751169"]HOWTO[/thread].*)

Firstly, downloaded them to a tmp dir:

```

mkdir hts_tmp
cd hts_tmp/
wget http://hts.sp.nitech.ac.jp/archives/2.0.1/festvox_nitech_us_awb_arctic_hts-2.0.1.tar.bz2
wget http://hts.sp.nitech.ac.jp/archives/2.0.1/festvox_nitech_us_bdl_arctic_hts-2.0.1.tar.bz2
wget http://hts.sp.nitech.ac.jp/archives/2.0.1/festvox_nitech_us_clb_arctic_hts-2.0.1.tar.bz2
wget http://hts.sp.nitech.ac.jp/archives/2.0.1/festvox_nitech_us_rms_arctic_hts-2.0.1.tar.bz2
wget http://hts.sp.nitech.ac.jp/archives/2.0.1/festvox_nitech_us_slt_arctic_hts-2.0.1.tar.bz2
wget http://hts.sp.nitech.ac.jp/archives/2.0.1/festvox_nitech_us_jmk_arctic_hts-2.0.1.tar.bz2

```


Extracted them:

```

for t in `ls festvox_nitech_us_*` ; do tar xvf $t ; done

```


Made a dir for them to live in:

```

sudo mkdir /usr/share/festival/voices/us

```


Moved them there:

```

sudo mv lib/voices/us/nitech_us_* /usr/share/festival/voices/us/

```


Move the hts.scm file into festival's home dir (may not be necessary, but can't hurt):

```

sudo mv lib/hts.scm /usr/share/festival/hts.scm

```


Cleaned up:

```

cd ../
rm -rf hts_tmp/

```


That's it. :)


Ps. Like I said, I haven't tried them without having the CMU Arctic voices installed as described above, so that may also be a prerequisite. (***edit:** They work fine by themselves.*)

Pss. Festvox also has some [HTS]("http://www.festvox.org/packed/festival/latest/") voices on their site. I'm not sure, but they look like they may just be copies or older versions of the nitech ones. Not sure though.

---

### Post by wersdaluv on 2008-11-06
> **MonkeeSage said:**
> I got the HTS voices working by doing the following (not sure, but they may depend on the CMU Arctic voices being installed (***edit:** they don't*), which I already have — they are *way* smaller):

(*[color=green]NOTE:[/color] I've started a HOWTO with detailed instructions on how to install all of the available English voices for festival: MBROLA, CMU Arctic, and Nitech HTS. [thread="751169"]HOWTO[/thread].*)

Firstly, downloaded them to a tmp dir:

```

mkdir hts_tmp
cd hts_tmp/
wget http://hts.sp.nitech.ac.jp/archives/2.0.1/festvox_nitech_us_awb_arctic_hts-2.0.1.tar.bz2
wget http://hts.sp.nitech.ac.jp/archives/2.0.1/festvox_nitech_us_bdl_arctic_hts-2.0.1.tar.bz2
wget http://hts.sp.nitech.ac.jp/archives/2.0.1/festvox_nitech_us_clb_arctic_hts-2.0.1.tar.bz2
wget http://hts.sp.nitech.ac.jp/archives/2.0.1/festvox_nitech_us_rms_arctic_hts-2.0.1.tar.bz2
wget http://hts.sp.nitech.ac.jp/archives/2.0.1/festvox_nitech_us_slt_arctic_hts-2.0.1.tar.bz2
wget http://hts.sp.nitech.ac.jp/archives/2.0.1/festvox_nitech_us_jmk_arctic_hts-2.0.1.tar.bz2

```


Extracted them:

```

for t in `ls festvox_nitech_us_*` ; do tar xvf $t ; done

```


Made a dir for them to live in:

```

sudo mkdir /usr/share/festival/voices/us

```


Moved them there:

```

sudo mv lib/voices/us/nitech_us_* /usr/share/festival/voices/us/

```


Move the hts.scm file into festival's home dir (may not be necessary, but can't hurt):

```

sudo mv lib/hts.scm /usr/share/festival/hts.scm

```


Cleaned up:

```

cd ../
rm -rf hts_tmp/

```


That's it. :)


Ps. Like I said, I haven't tried them without having the CMU Arctic voices installed as described above, so that may also be a prerequisite. (***edit:** They work fine by themselves.*)

Pss. Festvox also has some [HTS]("http://www.festvox.org/packed/festival/latest/") voices on their site. I'm not sure, but they look like they may just be copies or older versions of the nitech ones. Not sure though.
Man, this is great! Can you suggest more voices? :)

---

### Post by wisam74us on 2010-03-15
Hi guys, I see the post is too old but hopefully I can still get some support.

I have installed Festival yesterday, there are two voices in the English folder which are working good, there are four in the us folder none of them is working for me.

It seems the the new version of Festival is a bit different, here is the command that I am trying to use:

text2wave -o a/1003150903140.wav -scale 5 -eval '(voice_cmu_us_slt_arctic_hts)' t/1003150903140 

Am I missing anything 

Thanks

---

### Post by solomonson on 2010-04-30
Is there a way to speed up the voices?

---

### Post by hansum_rahul on 2010-06-07
Great! Thank You!

---

### Post by Superkuh on 2010-08-31
> **solomonson said:**
> Is there a way to speed up the voices?

Not in the default/Ubuntu build of festival. You can output to wav and then use the sox audio tools to increase the tempo. I wrote very simple and clumsy perl script for a friend that takes an aribtrary number of text files and converts them into mp3 of the same name with a variable speed.

You might find it useful.

```
#!/usr/bin/perl
use Getopt::Std;

# INSTRUCTIONS FOR USE:
# 1. sudo apt-get install shntool lame festival sox
# 2. 
#		$ wget http://superkuh.ath.cx/ttsbatchtomp3.pl
#		$ chmod +x ttsbatchtomp3.pl
#		$ ls *.txt
#			yourfile.txt examplefile.txt hmm.txt
#		$ ./ttsbatchtomp3.pl -s 1.5 -f "yourfile.txt examplefile.txt"
#			...
#			...
#
#		$ ls *.mp3
#			yourfile.mp3 examplefile.mp3
#
# Example 2: ls | grep *.txt | /ttsbatchtomp3.pl
#
# -s 1.5  , would set the speed to 1.5 times normal.
# -s 0.5  , set the speed to half 



#for file in "*.txt"; do $(text2wave "$file" | lame -h - "${file%.txt}.mp3"); done

my $tempo = 1.5;
my $tempfile = '/tmp/tts-tmp.txt';
my @filenames;

getopts('hf:s:', \%opts);
if ($opts{h} or ($ARGV[0] =~ /help/i)) {
	print "Options:\n";
	print "-s 1.5 , speed is 1.5 times normal\n";
	print "-f \"file.txt anotherexample.txt\"\n";
	print "\nExamples:\n\n";
	print "$0 -s 1.5 -f \"someshit.txt file\\ with\\ spaces.txt othershit.txt moreshit.txt\"\n\n";
	print "Go to the directory with the files. Do some **** like,\n\$ ls | grep \"elp.txt\" | $0 , to match kelp.txt and yelp.txt\n";
	print "You should get a directory with mp3 with the same filenames as all the text files.\n\n";
	exit;	
}
if ($opts{s}){
	$tempo = $opts{s};
}
if ($opts{f}) {
		@filenames = split(/ /, $opts{f});
} else {
	while (<>) {
		chomp($_);
		print "\nname: $_\n";
		push(@filenames, $_);
	}
}

foreach my $filename (@filenames) {
	my $outname = $filename;
	$outname =~ s/\.txt//;
#	system("text2wave $filename | lame --tg Speech --preset mw-us - $outname");
#	system("text2wave $filename | sox -t wav - -p temp 1.5 | lame --tg Speech --preset mw-us - $outname");

	my $command_textwav = "text2wave $filename -o $outname.wav";
	my $command_tempo = "sox \"$outname.wav\" \"tempo_$outname.wav\" tempo $tempo";
	my $command_mp3 = "lame \"tempo_$outname.wav\" --tg Speech --preset mw-us $outname.mp3";

	system($command_textwav);
	sleep 1 while ( !(-e "$outname.wav") );
	system($command_tempo);
	sleep 1 while ( !(-e "tempo_$outname.wav") );
	system($command_mp3);
	sleep 1 while ( !(-e "$outname.mp3") );

	unlink "$outname.wav";
	unlink "tempo_" . "$outname.wav";
}

```

---

### Post by Sabinin on 2011-06-23
[B]SIOD ERROR: could not open file /usr/lib/festival/siod.scm
SIOD ERROR: could not open file /usr/lib/festival/siod.scm[/B]

I install festival, speech_tools, festvox (everything i need it) but i don't know what to do in this case. Someone have any idea about it?

thanks

---

### Post by geazzy on 2011-06-24
nice tutorial :)

---

### Post by gardengxc on 2012-01-06
I receive the following message,

```
bash: /etc/festival.scm: Permission denied
```

NVMD, I just did it manually with,

```
gksu gedit /etc/festival.scm
```

If there is a better way for other who have the same problem you may still want to answer.

---

### Post by go_beep_yourself on 2012-05-09
I think you will be happy with this one.

[http://linuxinnovations.blogspot.com/2012/05/jspeak-ultimate-in-linux-text-to-speach.html](http://linuxinnovations.blogspot.com/2012/05/jspeak-ultimate-in-linux-text-to-speach.html)

---

### Post by Sorbing on 2012-06-17
Russian Documentation [How to install festival and examples for Ubuntu 11.04]("http://note.sectorit.net/os:linux:ubuntu:ubuntu-speak-text-to-voice"). Give me please the optimal settings for festival. Is there Russian female voice? Thanks.

---


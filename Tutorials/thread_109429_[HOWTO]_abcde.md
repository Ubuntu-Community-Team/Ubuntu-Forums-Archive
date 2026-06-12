---
title: "[HOWTO] abcde"
date: 2005-12-28
forum: Tutorials
---

### Post by daschl on 2005-12-28
Hello and welcome to my first HOWTO at ubuntuforums.org

The reason why i wrote this HOWTO is, that i dont like all this stuff with many eyecandy. I know that there are loads of real nice CD Encoders based on GTK+ or stuff like that, but as you already know shell-based applications are faster and in my opinion they dont lose usability. So this tutorial is about encoding your music-cds with the nice gadget called abcde.

abcde stands for **a** **b**etter **c**d **e**ncoder and is your comfortable front-end, so you dont have to deal with LAME (for example) directly.

Ok let's start.

At first, we have to _install abcde_. You can use Synaptic for that, or just apt-get it directly (thats what i like to do, because its faster :))

```

sudo apt-get -y install abcde

```
_Note:_ the -y options only answers all questions with yes. if you dont want apt-get to do so, just remove the -y parameter.

If you read the apt-get output you can see the dependencies installed

```

cd-discid (0.9-1)
liboggflac3 (1.1.2-1ubuntu2)
vorbis-tools(1.0.1-1.4)

```

_Optional:_
If you want to encode your CD's as mp3-files you have to install LAME too.

```

sudo apt-get -y install lame

```


_Configuration_
So now we have all the important stuff on our system. We now have to find the config file and copy it to our home-directory

```

find / -name abcde.conf 2> /dev/null

```

Lets have a look at the find-output. There you can see, that the file is located in the /etc/ directory. so now lets copy it to our home directory...

```

cp /etc/abcde.conf ~/.abcde.conf

```

...and open it

```

gedit ~/.abcde.conf

```

Lets have a look at the important sections. every option is well-commented and should be easy to understand. if you have specific questions about a section dont hesitiate to ask!
By default, abcde uses the .ogg codec to encode your files. if you want to encode your files with the LAME-Encoder you have to uncomment this line

```

# Paths of programs to use
LAME=lame
#GOGO=gogo
#BLADEENC=bladeenc
#L3ENC=l3enc
#XINGMP3ENC=xingmp3enc
#MP3ENC=mp3enc
#VORBIZE=vorbize
#OGGENC=oggenc
#FLAC=flac
#SPEEXENC=speexenc
#MPPENC=mppenc

```

important is this parameter. you have to set it to your cd-drive

```

# CD device you want to read from
#CDROM=/dev/cdrom
CDROM=/dev/hdc

```

in my case i have to change it to /dev/hdc. DONT use /media/cdrom, because audio-cds never get mounted :)

if you want to encode your files to a fixed directory, and not to your current directory change this parameter for example

```

# If you'd like to make a default location that overrides the current
# directory for putting mp3's, uncomment this.
#OUTPUTDIR=`pwd`
OUTPUTDIR=~/music/

```

there are loads of other options, if you have a specific question just ask here.

_finish_
so now, if you want to encode a cd all you have to do is 

(1) put the music cd in your drive
(2) open a terminal
(3) type "abcde"

and just wait for the output. abcde automatically searches for the names and if you want to change this, you can do so. otherwise press return twice and wait until the files are encoded

i hope you liked this short tutorial and please post your questions underneath

kind regards,
daschl

---

### Post by vassie on 2006-02-08
Nice How To, thanks

I also thought i'd share my .abcde.conf

```
# no submitting of cddb info 
NOSUBMIT=y  

# rip to mp3 via lame
MP3ENCODERSYNTAX='lame'

# selection of cd reader
CDROMREADERSYNTAX=cdparanoia 

# zero ifront of tr.no. below 10
PADTRACKS=y

# lame encoder settings
LAMEOPTS="--alt-preset standard"

# Actions to do
ACTIONS=cddb,read,encode,tag,move,clean

# Output dir
OUTPUTDIR='/home/ben/Music'

# temp dir 
WAVOUTPUTDIR='/tmp'

# output type
OUTPUTTYPE=mp3

# naming 
OUTPUTFORMAT='${ARTISTFILE}/${ALBUMFILE}/${TRACKNUM} - ${TRACKFILE}'

# naming of multi artist albums (same)
VAOUTPUTFORMAT='${ARTISTFILE}/${ARTISTFILE} - ${ALBUMFILE}/${ARTISTFILE} - ${TRACKNUM} - ${TRACKFILE}'

# don't convert spaces to underscores
mungefilename ()
{
echo "$@" | sed s,:,\ -,g | tr / _ | tr -d \"\?\[:cntrl:\]
}
```

Ben

---

### Post by Parkotron on 2006-02-09
I've always been a huge abcde fan. It's biggest advantages are the shear number of options in .abcde.conf and that it's written in Bash (so it's a joke to tweak something to suit your personal needs.) I also like that it uses the cdparanoia executable, not just the library, so you get to see those ever so informative cdparanoia progress bars. I like to number the tracks on multidisc albums as 101, 102, ... , 201, 202... and abcde is that only ripper I've ever seen that supports this.

It's certainly not pretty, but nothing does a better job of getting .cda to .flac, .ogg or .mp3.

---

### Post by Josh M on 2006-03-18
Thank you for this How To. abcde works great. I was having problems getting Sound Juicer and Grip working so I had been going back to Windows to rip and encode with EAC. Now I am very happy to be ripping and encoding in Linux. :)

---

### Post by bionnaki on 2006-03-18
im getting this error:

> bill@ubuntu:~$ abcde
/home/bill/.abcde.conf: line 129: MP3:: command not found
abcde error: id3v2 is not in your path.


I have lame installed:

> bill@ubuntu:~$ lame
LAME version 3.96.1 ([http://lame.sourceforge.net/](http://lame.sourceforge.net/))

usage: lame [options] <infile> [outfile]

    <infile> and/or <outfile> can be "-", which means stdin/stdout.

Try:
     "lame --help"           for general usage information
 or:
     "lame --preset help"    for information on suggested predefined settings
 or:
     "lame --longhelp"
  or "lame -?"              for a complete options list


---

### Post by Josh M on 2006-03-18
I had the Id3v2 error. You need to: 
```

sudo apt-get install id3v2

```

If you post the contents of your .abcde.conf file I will compare it to mine and see if I can spot the cause of the MP3 command not found error.

---

### Post by GabrielWolff on 2006-04-01
Hey, I guess the above description is missing one big issue: don't you have to copy the .abcde.conf back to etc?

Plus, I'd like to rip albums that contain non-english characters. Daschl, you should know how. For example: an Album By Die Ertsä Allgämeine Värunsicherung. abcde just turns it into Die Erst? Allg?meine V?runsicherung.

How do I keep the Umlauts?

Thanx

G

---

### Post by jgdempsey on 2006-04-06
Ok, Time to throw this out to the world. I've scoured the web for ideas. I'm using Kubuntu 5.10 and abcde 2.2.6. When I try to run abcde as me, I get the following error: ____________________________________________________________ 

johnd@SlimServer:~$ abcde /home/johnd/.abcde.conf: line 185: /home/johnd/Music/: is a directory 
/home/johnd/.abcde.conf: line 189: /home/johnd/temp/: is a directory 
Grabbing entire CD - tracks: 01 02 03 04 05 06 07 08 09 10 11 12 
mkdir: cannot create directory `/abcde.aa0c970c': Permission denied 
abcde: Temp directory /abcde.aa0c970c could not be created. ____________________________________________________________ 

It works when I run it as root, since root has permission to create files/folders in /, so I know that everything seems to be working correctly. I've checked the permissions on abcde itself, and it looks fine. The Music directory is a symbolic link to /Music, which is the mount dir for a USB attached 300 gb drive. Its probably something goofy I'm missing. Here's my abcde.conf file with the comments removed for clarity: (hence the line 185 in the above message)
 ___________________________________________________________ CDDBURL="http://freedb.freedb.org/~cddb/cddb.cgi" 
HELLOINFO="`whoami`@`hostname`" 
CDDBSUBMIT=freedb-submit@freedb.org 
NOCDDBQUERY=n 
FLACENCODERSYNTAX=default 
CDROMREADERSYNTAX=cdparanoia 
KEEPWAVS=n 
PADTRACKS=y 
INTERACTIVE=n 
ENCNICE=10 
READNICE=10 
DISTMP3NICE=10 
VORBIZE=vorbize 
FLAC=flac 
ID3=id3 
ID3V2=id3v2 
CDPARANOIA=cdparanoia 
CDDBTOOL=cddb-tool 
EJECT=eject 
MD5SUM=md5sum 
DISTMP3=distmp3 
VORBISCOMMENT=vorbiscomment 
NORMALIZE=normalize-audio 
CDSPEED=eject 
HTTPGET=wget 
HTTPGETOPTS="-q -O -" 
FLACOPTS= 
CDROM=/dev/cdrom 
OUTPUTDIR=`$HOME/Music/` 
WAVOUTPUTDIR=`$HOME/temp/` 
OUTPUTTYPE=flac 
OUTPUTFORMAT='${ARTISTFILE}/${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}' VAOUTPUTFORMAT='${ARTISTFILE}/${ARTISTFILE}-${ALBUMFILE}/${ARTISTFILE}-${TRACKNUM}.${TRACKFILE}' 
mungefilename () 
{ 
         echo "$@" | sed s,:,\ -,g | tr \ /\* __+ | tr -d \'\"\?\[:cntrl:\] 
} 
EJECTCD=y 
__________________________________________________________________ 

Any suggestions are welcome. 
Thanks 
JD

---

### Post by elektronaut on 2006-04-10
I also have the problem with non-ASCII characters and abcde. That's sad, as this seems to be the only program which can rip and encode in several formats (for me vorbis and flac) at the same time.

---

### Post by pestilence4hr on 2006-04-10
[QUOTE=jgdempsey]
johnd@SlimServer:~$ abcde /home/johnd/.abcde.conf: line 185: /home/johnd/Music/: is a directory 
/home/johnd/.abcde.conf: line 189: /home/johnd/temp/: is a directory 
Grabbing entire CD - tracks: 01 02 03 04 05 06 07 08 09 10 11 12 
mkdir: cannot create directory `/abcde.aa0c970c': Permission denied 
abcde: Temp directory /abcde.aa0c970c could not be created. 
[/QUOTE]
...
> 
OUTPUTDIR=`$HOME/Music/` 
WAVOUTPUTDIR=`$HOME/temp/` 


You've got the wrong kind of quotes there.  You need the " type of quote.  The kind of quote you have there is trying to save the result of executing the command $HOME/Music/ into the variable $OUTPUTDIR...which is why you are getting the error "that's a directory"...you can't execute directories.

---

### Post by elektronaut on 2006-04-10
I tried to delete this message but didn't find the option...

---

### Post by jgdempsey on 2006-04-10
Thanks for taking the time to respond, that did that trick..  
I knew it had to be some kind of silly *** thing that I was missing.
Thanks again

---

### Post by daschl on 2006-04-30
[QUOTE=GabrielWolff]Hey, I guess the above description is missing one big issue: don't you have to copy the .abcde.conf back to etc?

Plus, I'd like to rip albums that contain non-english characters. Daschl, you should know how. For example: an Album By Die Ertsä Allgämeine Värunsicherung. abcde just turns it into Die Erst? Allg?meine V?runsicherung.

How do I keep the Umlauts?

Thanx

G[/QUOTE]
no, you don't have to copy it back (if you do that, all users will use the new file if they dont have their own .abce.conf in their home-dir)

iirc umlauts are saved correctly. maybe you can't display it in your terminal because you use the wrong charset!
btw: its the "Erste Allgemeine Verunsicherung", and there's no umlaut ;)

---

### Post by gnemo on 2006-09-27
Thanks for the how-to. I've been searching for a way to simultaneously rip my CD collection to FLAC and mp3 formats, one for archival and one for use with portables.

Now, is there a way to have the flac and mp3 output files go into different subdirectories? I don't want both sets of files ripped into the same directory. For instance, let's say I have a big second hard drive mounted at /music, and I want to have the flac files go into /music/flac , and the mp3s into /music/mp3.

Anyone know how to do this?

TIA,

-Gnemo

---

### Post by gnemo on 2006-09-29
Okay, I figured it out. The following snippets from abcde.conf tell how to do this:
> 
OUTPUTDIR="/music"
OUTPUTTYPE=flac,mp3
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'

This combination puts the FLAC files in /music/flac, and the mp3 files in /music/mp3.

The key is the ${OUTPUT}/ bit in OUTPUTFORMAT; ${OUTPUT} is "flac" for FLAC and "mp3" for MP3.

-Gnemo

---

### Post by kpkeerthi on 2006-09-29
Excellent... Can't wait to try this when I get home.

---

### Post by VCSkier on 2006-10-06
First of all, I wanted to share this with you guys, thinking it might be appealing to some of you.  Secondly, I'm looking for help with it.

How would I would go about applying a patch to abcde?  Namely, this one over at Hydrogenaudio.org...

[Patch: Add Test & Copy to abcde/cdparanoia, Got tired of checking manually]("http://www.hydrogenaudio.org/forums/index.php?showtopic=42895")

---

### Post by VCSkier on 2006-11-29
Ok, I've got this working pretty well (I gave up on the patch, because I'm interested in single-file rips).  Here's my situation though, I want to be able to rip to single file flac, that I can easily and accurately burn to a blank cd.  I think that with brasero (formerly bonfire) I can point it to a cue sheet that references a flac image, it will burn it to the cd properly, but what about if the cue sheet is embedded?  Are there any native linux applications that can easily and accurately burn a single file, cue embedded flack file to a cd? 

If not, I will need to set up abcde to output a single file flac with embedded cue (so I can use abcde to split and encode to mp3 at a later time), AND an external cue sheet, so I can burn copies easily with Brasero (or other capable burning application).  Thanks!

---

### Post by VCSkier on 2007-02-06
bump.  are there any abcde users out there that can help me?  what should i have in my abcde.conf to let me rip to a single-file flac image that i can later burn to a cd easily?  also, if possible, i'd like to rip to mp3 tracks also, can this be done simultaneously, or do i need to do it in through a separate process?

finally, I want to apply album based replay-gain to all of my files.  should i apply this in the "FLACOPTS" field, or through the "normalize" options?

---

### Post by phido on 2007-02-20
need some help
```
 VAOUTPUTFORMAT=’VA-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE**_} - $_**{TRACKFILE}’
```gives me an error and the Track gets written "as Artist -.mp3", without spaces it gets written correct.
So how do I get spaces in there?

---

### Post by skralljt on 2007-06-28
Hey, anybody know how to get abcde to pass files to vorbisgain?  It rips everything to ogg vorbis files beautifully, tagged and everything, but i cannot for the life of me figure out what to put in the conf file to get it to automatically pass disc info to vorbisgain.  I can't even get abcde to open vorbisgain!  It seems like the commandline would be abcde -a vorbisgain, or is it abcde -a <vorbisgain>?

---

### Post by victor123 on 2007-07-02
*edit*

Is it possible to add the year to the filename?

---

### Post by andrew.46 on 2007-08-21
Hi,
Saw your post about abcde:

> **skralljt said:**
> Hey, anybody know how to get abcde to pass files to vorbisgain?  It rips everything to ogg vorbis files beautifully, tagged and everything, but i cannot for the life of me figure out what to put in the conf file to get it to automatically pass disc info to vorbisgain.  I can't even get abcde to open vorbisgain!  It seems like the commandline would be abcde -a vorbisgain, or is it abcde -a <vorbisgain>?

Have you added the following lines to your ~/.abcde.conf file?:

```
VORBISGAIN=vorbisgain
ACTIONS=cddb,read,normalize,encode,tag,move,clean
```

I don't use 'normalizeing' myself but this looks like the way to do it. The first line is the path to Vorbisgain, perhaps /usr/bin/vorbisgain ??

               Andrew

---

### Post by Chemist on 2008-01-01
how do i change the bitrate when encoding to .ogg, i've been trying to figure it out for a while but can only encode at 112kb/s??

---

### Post by andrew.46 on 2008-01-15
Hi,

> **Chemist said:**
> how do i change the bitrate when encoding to .ogg, i've been trying to figure it out for a while but can only encode at 112kb/s??

You are after the -q setting. From the man page:

>        -q n, --quality=n
              Sets encoding quality to n, between -1 (very low) and  10  (very
              high).  This  is  the  default mode of operation, with a default
              quality level of 3. Fractional quality levels such  as  2.5  are
              permitted.  Using  this  option  allows the encoder to select an
              appropriate bitrate based on your desired quality level.

-q 6 usually encodes to about 180 - 190.

     Andrew

---

### Post by Chemist on 2008-02-24
thanks dude

---

### Post by playinpearls on 2008-05-21
ok, i installed everything as it said in the begining but when I start ripping the cd, it still saves it as a ogg file. I did change this in the cfg file:

# Paths of programs to use
[COLOR="Red"]LAME=lame[/COLOR]
#GOGO=gogo
#BLADEENC=bladeenc

but that is the only thing. Is there something else I have to change to get it to start encoding to mp3?

---

### Post by citybird on 2008-10-24
```
mungefilename ()
{
echo "$@" | sed s,:,\ -,g | tr \ /\* __+ | tr -d \'\"\?\[:cntrl:\]
} 
```

What the hell does this mean? can someone please translate this for me? I know it converts characters to underscores or spaces or whatever you tell it to but I don't speak this language and I need a primer.

My goal is to just leave spaces alone and not convert them to underscores.
Basicly just not have any underscores.

What is the difference between what is above and this here below:
```

# don't convert spaces to underscores
mungefilename ()
{
echo "$@" | sed s,:,\ -,g | tr / _ | tr -d \"\?\[:cntrl:\]
}

```

---

### Post by nick_h on 2008-10-25
> **citybird said:**
> ```
mungefilename ()
{
echo "$@" | sed s,:,\ -,g | tr \ /\* __+ | tr -d \'\"\?\[:cntrl:\]
} 
```

What the hell does this mean? can someone please translate this for me? I know it converts characters to underscores or spaces or whatever you tell it to but I don't speak this language and I need a primer.

My goal is to just leave spaces alone and not convert them to underscores.
Basicly just not have any underscores.

What is the difference between what is above and this here below:
```

# don't convert spaces to underscores
mungefilename ()
{
echo "$@" | sed s,:,\ -,g | tr / _ | tr -d \"\?\[:cntrl:\]
}

```

It alters the filenames in 3 steps:

Firstly, it used the *sed* command to replace all occurrences of ":" with " -".  For details read the manual page with:
```
man sed
```

Then it uses the *tr* command to convert " " to "_", "\" to "_" and "*" to "+".  There is also a manual page for *tr*:
```
man tr
```

Finally the *tr* command is used to delete quotation marks, question marks and control characters.

The second example doesn't replace the spaces or the asterisk.

If you are moving files onto a FAT filesystem then some characters are not allowed.

I think they are:      " . / \ : < > ? * |

---

### Post by Piraja on 2008-11-05
Dear all,

one thing I don't really understand is that when CDDB gives **multiple exact matches** — e.g. as follows —

[INDENT]Multiple exact matches:
[COLOR="SeaGreen"][...][/COLOR]

#3: ---- blues b1102f0c Nirvana / In Utero ----
1: Serve The Servants
2: Scentless Apprentice
3: Heart-Shaped Box
4: Rape Me
5: Frances Farmer Will Have Her Revenge On Seattle
6: Dumb
7: Very Ape
8: Milk It
9: Pennyroyal Tea
10: Radio Friendly Unit Shifter
11: Tourette's
12: All Apologies

#4: ---- newage b1102f0c Nirvana / in Utero ----
1: Nirvana / SERVE THE SERVANTS
2: SCENTLESS APPRENTICE
3: HEART-SHAPED BOX
4: RAPE ME
5: FRANCES FARMER WILLHAVE HER REVENGE ON SEATTLE
6: DUMP
7: VERY APE
8: MILK IT
9: PENNYROYAL TEA
10: RADIO FRIENDLY UNIT SHIFTER
11: TOURETTES
12: ALL APOLOGIES

(END)[/INDENT]

how do I continue from here, i.e. from the **(END)** line? I could not figure this out by a quick lookup at the help file and the man page.

*All apologies* for my ignorance, and thanks in advance,

cheers,

*Very Ape* (a.k.a. Piraja)

---

### Post by Piraja on 2008-11-05
*NEVERMIND* &#8212; it seems I figured it out already! Hitting "q" (for "quit") while "(END)" is highlighted brings up the prompt for choosing the desired entry, and then the process continues...

*All apologies* (track 12) for being so *dumb* (track 06 &#8212; and not *DUMP* you silly "newage" track 07)!

---

### Post by andrew.46 on 2008-11-05
Hi Piraja:

> **Piraja said:**
> 

one thing I don't really understand is that when CDDB gives **multiple exact matches**  [...]

how do I continue from here, i.e. from the **(END)** line? I could not figure this out by a quick lookup at the help file and the man page.
,

All that is required is to scroll through the list and decide which 'match' you prefer and then close the editor window. abcde will then ask you to select the match by number (ie 1, 2, 3 or 4).

 All the best,

   Andrew

---

### Post by andrew.46 on 2008-11-09
Hi:

> **playinpearls said:**
> ok, i installed everything as it said in the begining but when I start ripping the cd, it still saves it as a ogg file. I did change this in the cfg file:

# Paths of programs to use
[COLOR="Red"]LAME=lame[/COLOR]
#GOGO=gogo
#BLADEENC=bladeenc

but that is the only thing. Is there something else I have to change to get it to start encoding to mp3?

Ogg Vorbis is the default format used by abcde. The section you actually need to change is:

```
OUTPUTTYPE="mp3"
```

and I would suggest as well:

```
LAMEOPTS='--preset extreme'
```

  Andrew

---

### Post by Piraja on 2008-12-30
Dear all,

I'd like to submit CDDB information for an album whose details I had to edit manually, but "cddb-tool send <filename>" returns just

```
/usr/bin/cddb-tool: 242: mail: not found
```

I haven't really been able to dig up information about this feature of abcde ([cddb-tool]("http://lly.org/~rcw/abcde/page/cddb-tool.1.html") is, anyway, "a backend tool for abcde").

---

### Post by logos34 on 2008-12-30
> **Piraja said:**
> Dear all,

I'd like to submit CDDB information for an album whose details I had to edit manually, but "cddb-tool send <filename>" returns just

```
/usr/bin/cddb-tool: 242: mail: not found
```

I haven't really been able to dig up information about this feature of abcde ([cddb-tool]("http://lly.org/~rcw/abcde/page/cddb-tool.1.html") is, anyway, "a backend tool for abcde").

hmm...reading the man page options:
> 
send [file] address

Mails file file (or stdin of no file specified) to specified address, using correct format. Category should be one of blues, classical, country, data, fold, jazz, newage, reggae, rock, soundtrack, misc. 

Have you tried removing '#' here:

> # This controls the email address CDDB changes are submitted to.
CDDBSUBMIT=freedb-submit@freedb.org

Then maybe adding options here:

> CDDBTOOLOPTS="send [email]freedb-submit@freedb.org[/email]"

just a shot in the dark...

---

### Post by Piraja on 2008-12-30
Thanks logos34! 

No hit, sorry to say.

The script /usr/bin/cddb-tool contains 242 lines, of which the last is just "esac". I removed the hash in .abcde.conf, to no avail, and tried adding CDDBTOOLOPTS="send [email]freedb-submit@freedb.org[/email]" as you suggested; adding the email address to the "send" command does not help either:

```
piraja@ubuntu-64bit:~$ cddb-tool send /home/piraja/abcde.6d10eb08/cddbread.0 freedb-submit@freedb.org 
/usr/bin/cddb-tool: 242: mail: not found 
```

**PS**. I attached the /usr/bin/cddb-tool file (as .txt) for reference. I suppose it should not be edited manually, but I'm at my wit's end about .abcde.conf, since the suggested changes did not help.

---

### Post by logos34 on 2008-12-30
I didn't have very high hopes it would work!  

abcde can be frustrating. There are several things I never figured out how to do--e.g. how to get it to autorun vorbisgain (whereas I can get it to run 'replaygain' for mp3 by simply editng the lameopts line...)

oh well, hopefully someone out there has an answer for you

---

### Post by Piraja on 2009-01-02
I wonder if this extract from the ripping process helps to solve the problem — abcde reads the information from the cddread.0 file that I edited but I cannot send the information to FreeDB (cf. the couple of posts preceding this one). Something seems to be missing... ("No such file or directory"? Why's that, when it's an address?)

```
Edit selected CDDB data? [y/n] (n): y
Is the CD multi-artist? [y/n] (n): 
grep: freedb-submit@freedb.org: No such file or directory
grep: freedb-submit@freedb.org: No such file or directory
grep: freedb-submit@freedb.org: No such file or directory
/usr/bin/cddb-tool: 242: mail: not found
Grabbing track 1: EDWARD ELGAR _1857-1934_ - Introduction and Allegro, op 47...
cdparanoia III release 10.0 (June 10, 2008)
```

---

### Post by andrew.46 on 2009-01-02
Hi,

I have not been able to get abcde to even call cd-discid from within the script to send the updated information. The section of /usr/bin/abcde looks fairly straightforward:

```
			# submit the modified file, if they want
			[B][COLOR="Red"]if [ "$NOSUBMIT" != "y" ]; then
				echo -n "Do you want to submit this entry to $CDDBSUBMIT? [y/n] (n): "[/COLOR][/B]
				read YESNO
				while [ "$YESNO" != "y" ] && [ "$YESNO" != "n" ] && [ "$YESNO" != "Y" ] && \
					[ "$YESNO" != "N" ] && [ "$YESNO" != "" ]
				do
					echo -n 'Invalid selection. Please answer "y" or "n": '
					read YESNO
				done
				if [ "$YESNO" = "y" ] || [ "$YESNO" = "Y" ]; then
					echo -n "Sending..."
					$CDDBTOOL send "$CDDBDATA" $CDDBSUBMIT
					echo "done."
				fi
			fi
		fi
	fi
```

But I cannot get it to work by using this option. Unfortunately at the moment the project seems a little quiet. Have you tried an email to Jesus Clement who answered a couple of my emails quite courteously in the past?

More than a little exasperating :confused:. Perhaps abcde expects a *local* copy of the freedb, or even simply the option CDDBLOCALDIR="$HOME/.cddb"? The documentation is particularly unhelpful with all this.

Andrew

---

### Post by andrew.46 on 2009-01-02
Hi,

Never one to let an issue like this rest I have submitted a bug-report:

[http://code.google.com/p/abcde/issues/detail?id=1](http://code.google.com/p/abcde/issues/detail?id=1)

This site has been a little quiet but I gather it is the home of abcde at the moment and looks like the best place to get some resolution of the issue. Interested in getting involved in the process? Confirmation of the bug may help matters along, if the new developers are active.

All the best,

 Andrew

---

### Post by Piraja on 2009-03-01
Hi,

ABCDE has somehow stopped working properly on my old desktop machine, running Crunchbang presently. The process stops after ripping the CD tracks with *cdparanoia*, without the encoding phase. That's not a big problem, actually, and fixing it can wait &#8212; I can always convert the *wave* files with *oggenc*, *flac* or *lame*. However, I would like to know if and how I can retrieve the CDDB information from the *cddbread.1* file so that I would not have to add the tags manually (with Easytag, for instance). I decided to make both *flac* and small *ogg* copies of the original *wav*'s of an album, and I may be using both *ogg* and *flac* on different devices (e.g. leaving the *flacs* on the big HDD and copying the tiny *oggs* onto my daughter's Sansa player); now I'm not sure how I could take an advantage of the tag information available in the CDDB file(s) already present in the *~/abcde.870a2f0a* directory.

Thanks in advance!

**P.S.** Oh, by the way, the *errors* file in the mentioned directory states the following:
```
encodetrack-ogg-01: returned code 1: nice -n 10 oggenc 8 -o /home/piraja/abcde.870a2f0a/track01.ogg /home/piraja/abcde.870a2f0a/track01.wav
```

---

### Post by Piraja on 2009-03-02
OK, I dug up some information on the mysterious "nice"ness (see [linux.com]("http://www.linux.com/feature/58638") on this) and will try what happens if I set encoding "nice"ness to zero... It's an old desktop, anyway, and encoding to compressed formats is extremely CPU hungry. So, let's see if I allow ABCDE to be less nice, i.e. more rude (do you native speakers say "ruder"?)... Below you see what I find in the default *.abcde.conf* before uncommenting and changing the "ENCNICE" value:

```
# Specify 'nice'ness of the encoder, the CD reader and the distmp3 proc.
# This is a relative 'nice'ness (that is, if the parent process is at a
# nice level of 12, and the ENCNICE is set to 3, then the encoder will
# run with an absolute nice value of 15. Note also, that setting these
# to be empty will result in some default niceness increase (4 in tcsh
# and 10 using the bsdutils' nice).
#ENCNICE=10
#READNICE=10
#DISTMP3NICE=10
```
**Report, 35 mins later**: "ENCNICE=0" had no effect on the problem. The file */home/piraja/abcde.2d0f7816/errors* reads as follows:
```
encodetrack-ogg-01: returned code 1: nice -n 0 oggenc 8 -o /home/piraja/abcde.2d0f7816/track01.ogg /home/piraja/abcde.2d0f7816/track01.wav
```

---

### Post by Piraja on 2009-03-02
I continue for another bit these ramblings &#8212; maybe I should create a blog for these instead of burdening Ubuntu Forums with these remarks? Hmm...

Anyway, this is what I used for encoding some WAV's that were left as orphans by the broken ABCDE ("broken" means here perhaps just that I have configured it erroneously):

```
piraja@chittychittybangbang:~$ flac --tag-from-file=1=/home/piraja/abcde.2d0f7816/cddbchoices /home/piraja/abcde.2d0f7816/*.wav
```

This produced metatags to the flac files. Yet, metatags are not shown by e.g. VLC in its General tab, as you see comparing the screenshots below.

[[IMG]http://www.aijaa.com/img/t/00373/3713568.t.jpg[/IMG]](http://www.aijaa.com/v.php?i=3713568.jpg)  [[IMG]http://www.aijaa.com/img/t/00644/3713579.t.jpg[/IMG]](http://www.aijaa.com/v.php?i=3713579.jpg)

In case I get this sorted out myself, I'll let you know...

---

### Post by Piraja on 2009-03-19
I thought it would be fair to report that I got the problem sorted out with ABCDE — there was some problem in my ~/.abcde.conf, but I'm afraid I cannot specify which was the actual misconfigured part, since I went through the whole file and changed quite a few details. Anyway, it works great once again.

---

### Post by SteveNorman on 2009-06-11
This thread made me soooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo
Happy!:KS:KS:KS:KS:KS:KS:KS:KS:

---

### Post by nickrout on 2009-06-26
> **Piraja said:**
> Dear all,

I'd like to submit CDDB information for an album whose details I had to edit manually, but "cddb-tool send <filename>" returns just

```
/usr/bin/cddb-tool: 242: mail: not found
```

I haven't really been able to dig up information about this feature of abcde ([cddb-tool]("http://lly.org/~rcw/abcde/page/cddb-tool.1.html") is, anyway, "a backend tool for abcde").

you do not have the command mail on your system.```
nick@bilbo:~$ mail
The program 'mail' can be found in the following packages:
 * heirloom-mailx
 * mailutils
Try: sudo apt-get install <selected package>
bash: mail: command not found

```

---

### Post by Piraja on 2009-06-26
> **nickrout said:**
> you do not have the command mail on your system
Thank you – the answer to my question was lying right under our noses, as it seems. Actually it has been a long time since I last used ABCDE. I have switched to Rubyripper's CLI version. I'm no longer using Ubuntu, either, but CrunchBang Linux instead – and "mail" is indeed one of the programs that come by default in #!.

---

### Post by emkamau on 2009-10-18
Does anybody know whether/how abcde can use multiple drives. I want to rip on a computer with two cdrom drives and have each drive ripping at the same time.

emk

---

### Post by andrew.46 on 2009-10-18
Hi emkamu,

> **emkamau said:**
> Does anybody know whether/how abcde can use multiple drives. I want to rip on a computer with two cdrom drives and have each drive ripping at the same time.

abcde can select different cdrom devices with the -d option:

```

-d [devicename | filename]
     CD-ROM block device that  contains  audio  tracks  to  be  read.
     Alternatively, a single-track flac file with embedded cuesheet.

```

I don't believe that the same instance of abcde can run from 2 devices though. Perhaps try opening abcde *twice* using the -d option to open the 2nd cdrom device?

Andrew

---

### Post by nickrout on 2009-10-18
> **andrew.46 said:**
> Hi emkamu,



abcde can select different cdrom devices with the -d option:

```

-d [devicename | filename]
     CD-ROM block device that  contains  audio  tracks  to  be  read.
     Alternatively, a single-track flac file with embedded cuesheet.

```

I don't believe that the same instance of abcde can run from 2 devices though. Perhaps try opening abcde *twice* using the -d option to open the 2nd cdrom device?

Andrew

You can run as many instances of abcde as you like. I only have one cd drive, but I can run ```
abcde -x 
```in one terminal. Once the cd pops out I know abcde has finished ripping, although it will still be encoding etc. In another terminal I can run it again and it will rip the next cd. I could do this as many times as I liked. Although the ripping and encoding will slow down, at least I can set it up to do a lot of ripping before I go to bed.

So I see no reason not to run

```
abcde -d /dev/cdrom0 
```in one terminal and ```
abcde -d /dev/cdrom1 
```in another.

---

### Post by slakkie on 2009-10-20
I know this is a pretty old guide, but the find / -name abcde.conf is not needed: 

dpkg -L abcde | grep conf 

will do the same without having to search on disk.

---

### Post by Captain_Falafel on 2010-05-09
I'm trying to get abcde to do a number of things such as name all my files based on their titles with the OUTPUTFORMAT option, however, it's not really working and just outputting track01.flac, etc.
MKCUE=mkcue isn't generating a cue sheet either

Is there something I'm missing with editing the configuration file?

This is essentially what I have in my configuration file (everything that I have uncommented)

```
# Track padding: force abcde to pad tracks using 0
PADTRACKS=y

# Make a cue sheet
MKCUE=mkcue


#ACTIONS=cddb,read,encode,tag,move,clean
ACTIONS=cddb,tag

# Default location
OUTPUTDIR=/blah/blah/abcde

# Output type
OUTPUTTYPE=flac,ogg

# Output Format
OUTPUTFORMAT='${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'

# Like OUTPUTFORMAT but for Various Artists discs.
VAOUTPUTFORMAT='Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'


mungefilename ()
{
	echo "$@" | sed s,:,\ -,g | tr \ / __ | tr -d \'\"\?\[:cntrl:\]
}
```

Thank you in advance! :)

---

### Post by mc4man on 2010-05-09
Here is a basic guide and sample configs by andrew.46 - maybe take a look
[http://andrews-corner.org/abcde.htm](http://andrews-corner.org/abcde.htm)

I used one of his as a starting point to do .aac with nero - for output have this (note what I highlighted in blue
> OUTPUTDIR="$HOME/music/"               
OUTPUTFORMAT='[COLOR="Blue"]${OUTPUT}/[/COLOR]${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'

I put .abcde.conf in home folder - leave the default one in /etc alone

In case any interest sometime - conf set up for neroAacEnc (does requires a patched abcde for nero and also to use cdda2wav instead of cdparanoia

```
# -----------------$HOME/.abcde.conf----------------- #
#   A sample configuration file to convert music cds to 
#      MP3, Ogg Vorbis, FLAC, Musepack & AAC 
#          using abcde version 2.4.2
#      Modified for neroAacEnc and atomicParsley from
#       [http://andrews-corner.org/abcde.html](http://andrews-corner.org/abcde.html)
#      Uses either cdparanoia or Jörg Schilling's cdda2wav
# -------------------------------------------------- #
#CDROM=/dev/cdrom

#OGGENCODERSYNTAX=oggenc                # Specify encoder for Ogg Vorbis
MP3ENCODERSYNTAX=lame                  # Specify encoder for MP3
FLACENCODERSYNTAX=flac                 # Specify encoder for FLAC
#MPPENCODERSYNTAX=mppenc                # Specify encoder for Musepack
AACENCODERSYNTAX=neroAacEnc                 # Specify encoder for AAC

#OGGENC=oggenc                          # Path to Ogg Vorbis encoder
LAME=lame                              # Path to MP3 encoder
FLAC=flac                              # Path to FLAC encoder
#MPPENC=mppenc                          # Path to Musepack encoder
AACENC=neroAacEnc                            # Path to AAC encoder
ATOMICPARSLEY='AtomicParsley'

#OGGENCOPTS='-q 6'                      # Options for Ogg Vorbis
LAMEOPTS='-V 0'            # Options for MP3 
FLACOPTS='--verify --best'             # Options for FLAC
#MPPENCOPTS='--extreme'                 # Options for Musepack
AACENCOPTS='-q 0.65'              # Options for AAC
 
OUTPUTTYPE="m4a"      # Encode to all 5 formats! only 1 here

CDROMREADERSYNTAX=cdparanoia
CDPARANOIA=cdparanoia 
#CDROMREADERSYNTAX=cdda2wav 
#CDDA2WAV=cdda2wav            
CDPARANOIAOPTS="--never-skip=40"
#CDDA2WAVOPTS="-paranoia -paraopts=proof"

# Give the location of the CD identification program:       
CDDISCID=cd-discid           
                               
OUTPUTDIR="$HOME/music/"               
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}
MAXPROCS=2                              # Run a few encoders simultaneously
PADTRACKS=y                             # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)
```

---

### Post by Captain_Falafel on 2010-05-09
> **mc4man said:**
> Here is a basic guide and sample configs by andrew.46 - maybe take a look
[http://andrews-corner.org/abcde.htm](http://andrews-corner.org/abcde.htm)

I used one of his as a starting point to do .aac with nero - for output have this (note what I highlighted in blue


I put .abcde.conf in home folder - leave the default one in /etc alone

In case any interest sometime - conf set up for neroAacEnc (does requires a patched abcde


Thank you for the link! it was really helpful! :)

---

### Post by andrew.46 on 2010-05-10
Hi,

@mc4man; Nice link indeed :). I see that the page has only recently added some details on how to automatically generate a playlist as well, not the most complex thing to do I will admit but it is nice to use some more features of this nice script...

@Captain_Falafel: You saw on that page in the flac section how 'cue' either needs to be added to your commandline or in the ~/.abcde.conf file under the 'ACTIONS' section?

Andrew

---

### Post by JRobertBuchanan on 2010-05-30
Hello,

Looks like abcde and its associated tools is just the thing to help me easily rip my CD library to multiple formats on harddisks. I have installed abcde and all the tools mentioned that it may use. I have even run abcde on a couple of CDs, but I must have something misconfigured since the results it get are incomplete. Only the first four tracks are encoded, but abcde seems to go to sleep after that and the command line prompt never returns. I can show you my .abcde.conf file and the error and status files generated by one of the runs of abcde. Can anyone see something configured incorrectly? Any suggestions will be appreciated.

My .abcde.conf file (slightly modified stock file, only encodes 3 formats):
```

# -----------------$HOME/.abcde.conf----------------- #
# 
#   A sample configuration file to convert music cds to 
#      MP3, Ogg Vorbis, FLAC, Musepack & AAC 
#          using abcde version 2.3.99.6
# 
#       http://andrews-corner.org/abcde.html
# -------------------------------------------------- #

OGGENCODERSYNTAX=oggenc                # Specify encoder for Ogg Vorbis
MP3ENCODERSYNTAX=lame                  # Specify encoder for MP3
FLACENCODERSYNTAX=flac                 # Specify encoder for FLAC
MPPENCODERSYNTAX=mppenc                # Specify encoder for Musepack
AACENCODERSYNTAX=faac                  # Specify encoder for AAC

OGGENC=oggenc                          # Path to Ogg Vorbis encoder
LAME=lame                              # Path to MP3 encoder
FLAC=flac                              # Path to FLAC encoder
MPPENC=mppenc                          # Path to Musepack encoder
AACENC=faac                            # Path to AAC encoder

OGGENCOPTS='-q 6'                      # Options for Ogg Vorbis
LAMEOPTS='--preset extreme'            # Options for MP3 
FLACOPTS='--verify --best'             # Options for FLAC
MPPENCOPTS='--extreme'                 # Options for Musepack
AACENCOPTS='-q 250 -w -s'              # Options for AAC
 
OUTPUTTYPE="mp3,flac,m4a"      # Encode to just 3 formats!

CDROMREADERSYNTAX=cdparanoia            
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
CDDISCID=cd-discid           
                               
OUTPUTDIR="$HOME/Music/"               
ACTIONS=cddb,playlist,read,encode,tag,move,clean
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'

mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}
MAXPROCS=4                              # Run a few encoders simultaneously
PADTRACKS=y                             # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)

```

The contents of one of the temporary directories created while abcde runs (note only the first 4 tracks are encoded):
```

bob@Basement:/home/xbmc/abcde.e7112e11$ ls
cddbchoices  status        track02.wav   track04.wav  track10.wav  track16.wav
cddbquery    track01.flac  track03.flac  track05.wav  track11.wav  track17.wav
cddbread.1   track01.mp3   track03.mp3   track06.wav  track12.wav
cddbstat     track01.wav   track03.wav   track07.wav  track13.wav
discid       track02.flac  track04.flac  track08.wav  track14.wav
errors       track02.mp3   track04.mp3   track09.wav  track15.wav

```

The contents of the file "errors":
```

encodetrack-m4a-01: returned code 1: nice -n 10 faac -q 250 -w -s --artist Prince --album The Very Best of Prince --title I Wanna Be Your Lover --track 01 --genre Rock --year 2001 --comment  -o /home/xbmc/abcde.e7112e11/track01.m4a /home/xbmc/abcde.e7112e11/track01.wav
encodetrack-m4a-02: returned code 1: nice -n 10 faac -q 250 -w -s --artist Prince --album The Very Best of Prince --title 1999 --track 02 --genre Rock --year 2001 --comment  -o /home/xbmc/abcde.e7112e11/track02.m4a /home/xbmc/abcde.e7112e11/track02.wav
encodetrack-m4a-03: returned code 1: nice -n 10 faac -q 250 -w -s --artist Prince --album The Very Best of Prince --title Little Red Corvette --track 03 --genre Rock --year 2001 --comment  -o /home/xbmc/abcde.e7112e11/track03.m4a /home/xbmc/abcde.e7112e11/track03.wav
encodetrack-m4a-04: returned code 1: nice -n 10 faac -q 250 -w -s --artist Prince --album The Very Best of Prince --title When Doves Cry --track 04 --genre Rock --year 2001 --comment  -o /home/xbmc/abcde.e7112e11/track04.m4a /home/xbmc/abcde.e7112e11/track04.wav

```

The contents of the file "status":
```

abcde-version=2.4
cdparanoia-audio-tracks=17
cddbmethod=cddb
cddb-statcomplete
cddb-querycomplete
cddb-read-1-complete
cddb-choice=1
cddb-readcomplete
variousartists=
variousartiststyle=forward
cddb-edit
playlistcomplete
playlistcomplete
playlistcomplete
readtrack-01
encodetracklocation-%local1%=01
readtrack-02
encodetracklocation-%local2%=02
encodetrack-mp3-01
encodetrack-flac-01
readtrack-03
encodetracklocation-%local3%=03
encodetrack-mp3-02
readtrack-03
encodetracklocation-%local3%=03
encodetrack-mp3-02
encodetrack-flac-02
readtrack-04
encodetracklocation-%local4%=04
encodetrack-mp3-03
readtrack-05
encodetrack-mp3-04
encodetrack-flac-03
encodetrack-flac-04
readtrack-06
readtrack-07
readtrack-08
readtrack-09
readtrack-10
readtrack-11
readtrack-12
readtrack-13
readtrack-14
readtrack-15
readtrack-16
readtrack-17

```

---

### Post by andrew.46 on 2010-05-31
Hi JRobertBuchanan,

I wonder if your copy of faac has been compiled against mp4v2, which is where the *-w -s* options come from. Have a look at:

```

andrew@skamandros~$ **[COLOR="Red"]faac -h[/COLOR]**
Freeware Advanced Audio Coder
FAAC 1.28

Usage: faac [options] infiles ...
Options:
  -q <quality>	Set quantizer quality.
  -b <bitrate>	Set average bitrate to x kbps. (ABR, lower quality mode)
  -c <freq>	Set the bandwidth in Hz. (default=automatic)
  -o X		Set output file to X (only for one input file)
  -r		Use RAW AAC output file.
  -P		Raw PCM input mode (default 44100Hz 16bit stereo).
  -R		Raw PCM input rate.
  -B		Raw PCM input sample size (8, 16 (default), 24 or 32bits).
  -C		Raw PCM input channels.
  -X		Raw PCM swap input bytes
  -I <C,LF>	Input channel config, default is 3,4 (Center third, LF fourth)

MP4 specific options:
[B][COLOR="Red"]  -w		Wrap AAC data in MP4 container. (default for *.mp4 and *.m4a)
  -s		Optimize MP4 container layout after encoding[/COLOR][/B]
  --artist X	Set artist to X
  --writer X	Set writer to X
  --title X	Set title to X
  --genre X	Set genre to X
  --album X	Set album to X
  --compilation	Set compilation
  --track X	Set track to X (number/total)
  --disc X	Set disc to X (number/total)
  --year X	Set year to X
  --cover-art X	Read cover art from file X
  --comment X	Set comment to X

Documentation:
  --license	Show the FAAC license.
  --help	Show this abbreviated help.
  --long-help	Show complete help.

  More tips can be found in the audiocoding.com Knowledge Base at
  <http://www.audiocoding.com/wiki/>

```

and see if these options exist for you. If not, and I suspect this is the problem, you could try and recompile faac against libmp4v2 or simply alter the aac options in ~/.abcde.conf to:

```

AACENCOPTS='-q 250'              # Options for AAC

```

That 'andrews-corner' abcde webpage certainly is popular :).

All the best,

Andrew

---

### Post by JRobertBuchanan on 2010-05-31
Andrew,

Thanks for your razor sharp insight. I have faac version 1.26.1 which has the -w option, but not the -s option. I removed the -s portion of the AACENOPTS, and it looks like things are working now. Your page certainly is popular. abcde (once configured properly) is very easy to use. I have twenty years worth of CDs to rip, archive, and make available for streaming to my squeezebox, iphone, xbmc, etc and I just like being able to pop a CD in the tray, type "abcde" and forget about it. Now if I could just teach the cat to change the CDs for me, it would be nearly automated.

Thanks again,
Bob

---

### Post by JRobertBuchanan on 2010-05-31
Just one more problem to solve for today:

Thanks to Andrew's help I've made a great deal of progress today. The last error I seem to be unable to overcome on my own is the tagging of some flac files. Here are the errors:

```

[ERROR] abcde: The following commands failed to run:
tagtrack-flac-01: returned code 1: nice -n 10 metaflac --no-utf8-convert --import-tags-from=- /home/xbmc/abcde.a60ce50c/track01.flac
tagtrack-flac-04: returned code 1: nice -n 10 metaflac --no-utf8-convert --import-tags-from=- /home/xbmc/abcde.a60ce50c/track04.flac
tagtrack-flac-07: returned code 1: nice -n 10 metaflac --no-utf8-convert --import-tags-from=- /home/xbmc/abcde.a60ce50c/track07.flac
tagtrack-flac-11: returned code 1: nice -n 10 metaflac --no-utf8-convert --import-tags-from=- /home/xbmc/abcde.a60ce50c/track11.flac

```

I get the same errors with and also without the "--no-utf8-convert" option. One of these track titles contains an umlaut, but the other three are all just english letters (and spaces).

Any help or suggestions will be appreciated.

Thanks,
Bob

---

### Post by andrew.46 on 2010-06-01
Hi JRobertBuchanan,

This one I am not sure about, but I would certainly check the obvious i.e. that both metaflac and flac are installed. If they are in place try running abcde in 'debug' mode:

```
abcde -D 2>$HOME/Desktop/abcde_log
```

Hopefully this will reveal the problem... Perhaps have a quick look at this thread as well:

metaflac, utf-8 (and abcde)
[http://ubuntuforums.org/showthread.php?t=534603](http://ubuntuforums.org/showthread.php?t=534603)

All the best,

Andrew

---

### Post by JRobertBuchanan on 2010-06-01
Andrew,

Thanks I figured it out after watching the reading and encoding process carefully.

It just wouldn't be Tuesday if I didn't have yet another question. I am using the following formats in my .abcde.conf file.

```

OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}/${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various/${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}/${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various/${ALBUMFILE}/${ALBUMFILE}.m3u'

```

The OUTPUTFORMAT and VAOUTPUTFORMAT seem to be honored by abcde, but it seems like the PLAYLISTFORMAT and VAPLAYLISTFORMAT are sticking to the defaults in the bash script. Since, I'm new to understanding abcde and it function, could there be a bug in the script? For example after ripping the CD "Comfort Eagle" by the artist CAKE, I get the following in my music folder.

```

bob@Basement:~$ ls -R /home/xbmc/Music/mp3/CAKE*
/home/xbmc/Music/mp3/CAKE:
Comfort Eagle

/home/xbmc/Music/mp3/CAKE/Comfort Eagle:
01.Opera Singer.mp3                   07.Comfort Eagle.mp3
02.Meanwhile, Rick James....mp3       08.Long Line Of Cars.mp3
03.Shadow Stabbing.mp3                09.Love You Madly.mp3
04.Short Skirt_Long Jacket.mp3        10.Pretty Pink Ribbon.mp3
05.Commissioning A Symphony In C.mp3  11.World Of Two.mp3
06.Arco Arena (Instrumental).mp3

/home/xbmc/Music/mp3/CAKE-Comfort Eagle:
Comfort Eagle.m3u

```

Do the constructed playlists really matter? Could I move them into the proper folders myself?

Thanks,
Bob

---

### Post by ikacer on 2010-06-22
A quick correction to [post 23]("http://ubuntuforums.org/showpost.php?p=3226612&postcount=23") in this thread, for those wondering how to get vorbisgain to work with abcde:

VorbisGain puts a replay gain tag in the ogg file, so you want to use the replaygain action instead of the normalize action in you abcde.conf.

The following are the minimum settings in abcde.conf which will enable album gain using vorbisgain.

```

OGGENCODERSYNTAX=oggenc
OGGENC=oggenc
VORBISGAIN=vorbisgain
VORBISGAINOPTS='-a'
ACTIONS=cddb,playlist,read,encode,replaygain,tag,move,clean
BATCHNORM=y
OUTPUTTYPE=ogg

```

note, the actions array must contain replaygain after encode.

---

### Post by area46 on 2010-08-15
Many thanks for this great guide on abcde!
It helped me to save many hours to search for the right settings. With this guide I learned how to encode in flac and mp3 and to save automatically into different folders. This is very close to perfect!

There is just one thing that I would need to make it perfect.
Is there a way to automatically download cover art?
What tool do you use to add the cover art to the ripped cds?

---

### Post by drknot on 2011-03-26
I cannot get abcde to save to a specified directory 

I have tried 
OUTPUTDIR = ~/Music/
or
OUTPUTDIR = "$HOME/Music/"
and variations with and without trailing/, subdirectory targets and still get something along the lines of :

/home/drknot/.abcde.conf: line 232: /home/drknot/Music/: is a directory


Frustrated!!
Once I can get this to work I'll try having separate directories for ogg v MP3

---

### Post by nickrout on 2011-03-26
try without a space either side of the = sign

---

### Post by drknot on 2011-03-27
I now feel officially daft!

Thank you - the leading space after the OUTPUTDIR= was the problem.

---

### Post by andrew.46 on 2012-12-06
This long thread will not be open for much longer so I will necropost a little to let the abcde faithful know that there have been 2 nice changes in abcde just recently:

[LIST=1]
[*]Musepack SV8 is now supported, support for SV7 has been discarded.
[*]Encoding with neroAacEnc is now possible without patching, Tagging with AtomicParsley for the moment.
[/LIST]

Details here:

[http://code.google.com/p/abcde/source/list](http://code.google.com/p/abcde/source/list)

Still exciting times now and in the future for abcde :)

---

### Post by offgridguy on 2012-12-06
Interesting thread.

---

### Post by andrew.46 on 2012-12-16
And now encoding with opusenc is in place so abcde can rip cds to the new Opus Interactive Audio Codec.

Opus Interactive Audio Codec
[http://www.opus-codec.org/](http://www.opus-codec.org/)

---

### Post by 73bazinga on 2013-01-30
I read earlier in the thread about selecting cd drive to read from. i am trying to read from and external usb drive. 

I can see the disc but cannot get abcde to read it instead of my main drive. using -d. I assume i have the wrong path to the drive but being new cannot figure out how to find the path. i bookmarked the drive and got cdda://sr1/ but cannot figure out how to format the path to get abcde to read it i just get the error cannot find cd drive.

any suggestions?

---

### Post by andrew.46 on 2013-01-30
If you have an ~/.abcde.conf file try placing:

```

CDROM=/dev/sr1

```

and this might get things going...

---

### Post by nickrout on 2013-01-30
> **73bazinga said:**
> I read earlier in the thread about selecting cd drive to read from. i am trying to read from and external usb drive. 

I can see the disc but cannot get abcde to read it instead of my main drive. using -d. I assume i have the wrong path to the drive but being new cannot figure out how to find the path. i bookmarked the drive and got cdda://sr1/ but cannot figure out how to format the path to get abcde to read it i just get the error cannot find cd drive.

any suggestions?

it will be something like /dev/sr1

when you plug in the drive the output of the dmesg command will give you some clues.

---

### Post by 73bazinga on 2013-02-01
Thank you nicrout and andrew.46 i will try this when i get home.
 
> it will be something like /dev/sr1

when you plug in the drive the output of the dmesg command will give you some clues. 
 
what is dmsg comand. and how do i use it effectively?

---

### Post by nickrout on 2013-02-01
type dmesg into a terminal and see the output of the the kernel ring buffer, ie what the kernel ouputs when (for example) and external device is plugged  or unplugged.

---

### Post by 73bazinga on 2013-02-01
Thank you nickrout. i will try that in a few hours. hopefully i can get it to work.

---

### Post by 73bazinga on 2013-02-02
Worked for sure. turns out it was /dev/sr1 although i could have sworn i tried that yesterday.

thanks for the help guys. was able to run both drives at the same time from different terminals

---

### Post by andrew.46 on 2013-02-02
Good to hear the issue has been resolved :)

---

### Post by BFG on 2013-02-15
I'm just getting into abcde as I found that my old fave - ripperx is unstable after 12.04.

Lots of good info in this thread.  I'm trying to get abcde to write into the ID3 comment tag for mp3s, giving the lame parameters used in the encoding, which works to a point.  

Edit: Got it working.

In my ~/.abcde.conf I have the following set:

```

# Add a comment into the ID3 comment tag
COMMENT='Created using lame ${MP3ENCODEROPTS}' 

```

In my case the mp3 tag results in "Created using lame -V0 --vbr-new -q0 --lowpass 19.7 -b96"

---

### Post by 73bazinga on 2013-02-16
> **BFG said:**
> I'm just getting into abcde as I found that my old fave - ripperx is unstable after 12.04.

Lots of good info in this thread.  I'm trying to get abcde to write into the ID3 comment tag for mp3s, giving the lame parameters used in the encoding, which works to a point.  

Edit: Got it working.

In my ~/.abcde.conf I have the following set:

```

# Add a comment into the ID3 comment tag
COMMENT='Created using lame ${MP3ENCODEROPTS}' 

```In my case the mp3 tag results in "Created using lame -V0 --vbr-new -q0 --lowpass 19.7 -b96"

I am not 100% sure what all you are hoping to accomplish but you can edit the CDDB info before you start the rip.  

A good allternative if you don't mind a small bit of post tagging, EasyTAG is a great program for mass editing of ID3 tags. particularly if you are wanting to insert the same thing in a field for multiple files.

---

### Post by andrew.46 on 2013-04-19
Those who follow the development version of abcde might be interested to know that there is now support for the newest version of eyeD3 (the new default mp3 tagger):

[http://code.google.com/p/abcde/source/detail?r=379](http://code.google.com/p/abcde/source/detail?r=379)

---

### Post by Anaximander Thales on 2013-06-04
I am trying to get some post encoding commands to run -- specifically I am running two commands.  The first is running avconv to convert the FLAC files to ALAC.  The second then changes ownership from root to my user.  The files belong to root as I have a udev rule to automatically run abcde on the insertion of a cd.

However, neither of these are working.  I attempted to put in echo commands; I don't get any output from post_encode().  Not sure what I'm doing wrong.

I've looked through the original/full abcde.conf file, and I can see nothing about enable post_encode() other than uncomment and replace the ':' with my commands.  Here's what I have in post_encode (in my /etc/abcde.conf)

```


# post_encode
# By default it does nothing.
# You can set some things to get abcde function in better ways:
# * Move the resulting directory over the network
# * Compare results with a previously made run, for tests
# KEEP IN MIND that executables included in post_encode must be in 
# your $PATH or you have to define them with full /path/to/binary
#
# Convert from FLAC to ALAC in .m4a format for ipod, then set owner 
# privledge's for user.
post_encode ()
{
  cd "$OUTPUTDIR/$ARTISTFILE/$ALBUMFILE"
  for FILE in *.flac;
    /bin/echo "Converting $FILE to ALAC ..."
    do /usr/bin/avconv -i "$FILE" -c:a alac "${FILE%.flac}.m4a";
  done
  
  cd "$OUTPUTDIR"
  
  echo "Setting priveledges to $ARTISTFILE ..."
  /bin/chown -R at:at $ARTISTFILE
  
}

```

---

### Post by Anaximander Thales on 2013-06-07
Okay -- after much tinkering I figured out what needed to be done to make my post_encode portion work.

I first had to edit the /usr/bin/abcde file and add these parts after the call to post_encode:
```
[COLOR=red]line 4451 /usr/bin/abcde version 2.5.4[/COLOR]

post_encode $(mungefilename $TRACKARTIST) $(mungefilename $DALBUM) $OUTPUTDIR

```

Then, my abcde.conf file changed thusly:
```
[COLOR=red]abcde.conf file[/COLOR]

post_encode()
{
  BASEDIR="$3"
  ARTIST="$1"
  ALBUM="$2"

  cd "$BASEDIR/$ARTIST/$ALBUM"
  pwd

  for FILE in *.flac; do
    echo "Converting $FLAC to ALAC ..."
    avconv -i "$FILE" -c:a alac "${FILE%.flac}.m4a";
  done

  rm *.flac

  cd "$BASEDIR"
  pwd

  echo "Setting privledges to $ARTIST ..."
  chown -R at:at "$ARTIAT"

}

```

---

### Post by ljpp on 2013-07-08
Is ABCDE ripping secure and can it handle drive's read offset? I am under the impression that RubyRipper is the way to go on Ubuntu/Linux, or Exact Audio Copy but that needs Wine.
Article on RubyRipper: [http://www.bitburners.com/blogs/2](http://www.bitburners.com/blogs/2)

---


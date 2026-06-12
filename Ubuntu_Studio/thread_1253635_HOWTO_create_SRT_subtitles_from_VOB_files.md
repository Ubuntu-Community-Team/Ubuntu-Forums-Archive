---
title: "HOWTO create SRT subtitles from VOB files"
date: 2009-08-30
forum: Ubuntu Studio
---

### Post by bernardfrancois on 2009-08-30
**FIRST METHOD:**

Use the **ksubtitleripper** package from synaptic.

**SECOND METHOD:**

If ksubtitleripper doesn't work for you, or you dont want to use it you can follow these steps:
[LIST=1]
[*]Install the subtitleripper package from synaptic.
[*]Change your working directory to the directory containing the VOB files. These files should not be encrypted.
[*]Copy and paste the script below into a terminal window.
[/LIST]

```

# NOTE: this script assumes there are no more than 9 subtitle tracks
# creates subtitle files for the 9 first languages
for lang in {0..9} ; do
    (
        # extract the given language and creates a subtitle file
        tccat -i *.VOB | tcextract -x ps1 -t vob -a 0x2$lang > subs-$lang ;
        
        # converts the subtitle file to an .srt file (if the file isn't empty)
        if [[ -s subs-$lang ]] ; then
        
            (
                # convert the subtitle frames to seperate images
                echo "LANGUAGE $lang: WILL NOW CREATE SUBTITLE FRAME IMAGES" ;
                mkdir pgm-$lang ;
                subtitle2pgm -o pgm-$lang/pgm-$lang- < subs-$lang ;
                
                # use gocr to convert the subtitle frames to text
                echo "LANGUAGE $lang: WILL START OCR ON SUBTITLE FRAME IMAGES" ;
                pgm2txt pgm-$lang/pgm-$lang- ;
                
                #convert the text to a .srt file
                echo "LANGUAGE $lang: WILL NOW CONVERT THE TEXT TO AN SRT FILE" ;
                srttool -s -w < pgm-$lang/pgm-$lang-.srtx > subs-$lang.srt ;
            ) ;
              
        else
            # removes the empty subtitle file (a languages that wasn't available)
            rm subs-$lang ;
        fi
    ) ;
done

```

Notes:
[LIST=1]
[*]ksubtitleripper didn't work for me. I reported a bug regarding the issues I had with it:
[https://bugs.launchpad.net/ubuntu/+source/ksubtitleripper/+bug/421470](https://bugs.launchpad.net/ubuntu/+source/ksubtitleripper/+bug/421470)
[*]Depending on the actual subtitles you want to copy, you may have to be the copyright holder of the subtitles.
[*]Use this script at your own risk.
[*]Feel free to ask any questions about the script, or to send me a personal message in case it would be broken.
[/LIST]
Note that

---

### Post by legatek on 2009-09-10
LANGUAGE 0: WILL NOW CREATE SUBTITLE FRAME IMAGES
LANGUAGE 0: WILL START OCR ON SUBTITLE FRAME IMAGES
Using /usr/share/subtitleripper/gocrfilter_none.sed to filter gocr output
creating directory ./db/
creating empty file ./db//db.lst
File pgm-0/pgm-0-*.pgm not found
File pgm-0/pgm-0-*.pgm.gz not found
LANGUAGE 0: WILL NOW CONVERT THE TEXT TO AN SRT FILE
/home/monkey/subtitle-extract.sh: line 23: ../../subs-0.srt: Permission denied

---

### Post by legatek on 2009-09-10
I tried on another movie, and this was the console output:

LANGUAGE 0: WILL NOW CREATE SUBTITLE FRAME IMAGES
LANGUAGE 0: WILL START OCR ON SUBTITLE FRAME IMAGES
Using /usr/share/subtitleripper/gocrfilter_none.sed to filter gocr output
creating directory ./db/
creating empty file ./db//db.lst
File pgm-0/pgm-0-*.pgm not found
File pgm-0/pgm-0-*.pgm.gz not found
LANGUAGE 0: WILL NOW CONVERT THE TEXT TO AN SRT FILE
LANGUAGE 1: WILL NOW CREATE SUBTITLE FRAME IMAGES
LANGUAGE 1: WILL START OCR ON SUBTITLE FRAME IMAGES
Using /usr/share/subtitleripper/gocrfilter_none.sed to filter gocr output
File pgm-1/pgm-1-*.pgm not found
File pgm-1/pgm-1-*.pgm.gz not found
LANGUAGE 1: WILL NOW CONVERT THE TEXT TO AN SRT FILE

-----

db, pgm-0 and pgm-1 directories were created, and the pgm directories had files named pgm-0-.srtx and pgm-1-.srtx, respectively, both with size 0.

---

### Post by bernardfrancois on 2009-10-14
Was this a VOB file from a commercial movie? Typically, those are encrypted. Probably my script doesn't work on encrypted VOB files.

If anyone tried with a non-encrypted VOB file, please let me know if it worked.

---

### Post by phenest on 2010-09-28
I've been having trouble decrypting a copy protected DVD (Alice in Wonderland & Avatar). Then I found this script...

I've been ripping from DVD's (even copy protected) using...
```
mplayer dvdnav://$title -dumpstream -dumpfile $name.VOB
```
...and discovered this script works on that file. Nice.

One question: when it asks to enter a character it doesn't recognize, how does one enter italic or bold? Apparently I can enter it as UTF8, but I don't know how.

---

### Post by phenest on 2010-10-03
Ok, so you can't enter *italic* or **bold** characters because gocr doesn't support it.

---

### Post by maghoxfr on 2010-10-03
Isn't it possible using Avidemux?

---

### Post by andrew.46 on 2010-10-05
Hi,

I see that the writer of this guide has not been active on these forums for a while which is a great pity. I have not used this script but I have certainly used the tools mentioned in it and I can add one small snippet to the pgm2txt syntax. If you have an image viewer defined in the script /usr/bin/pgm2txt alter the line to:

```
pgm2txt **[COLOR="Red"]-v[/COLOR]** pgm-$lang/pgm-$lang- ;
```

and an image viewer should then show the exact image that gocr will query when the OCR fails to guess the text. Makes life a lot easier :).

Andrew

---

### Post by phenest on 2010-10-05
> **phenest said:**
> Ok, so you can't enter *italic* or **bold** characters because gocr doesn't support it.

It may be possible as gocr allows a string to be entered for each character, rather than just one character. This means you could theoretically enter "<i>P</i>" for an italic P. But it seems to double up these strings in the finished text. Not sure why, maybe a bug? I'm having a look at gocr's code to see why. If this theory worked, it would only require a script to remove surplus formatting tags as each character would be formatted individually. Incidentally, the gocr package in Debian Squeeze is nearly 3 years out of date, and I'm guessing Ubuntu's will be too. There is a much more up to date source code available from their site.

> **maghoxfr said:**
> Isn't it possible using Avidemux?

Only for hard coded subs I believe.

Thanks for the tip Andrew.

---

### Post by maghoxfr on 2010-10-05
> **phenest said:**
> Only for hard coded subs I believe.

Thanks for the tip Andrew.

You got me, I wasn't aware of that. 
See you around

---

### Post by gecka on 2010-12-08
pgm2txt is a total fail it cannot convert simple numbers like attached

---


---
title: "Video Converter that seeks out file formats and converts them"
date: 2012-04-13
forum: Server Platforms
---

### Post by ads2996 on 2012-04-13
Hi

This is my first post, I'm trying to create a home server to stream to the PCs in myhouse and to my PS3

I was looking for a way to have a video converter installed that scans specefic folders looking for file formats such as .mkv and converting them and placing them in a specefic folder to be streamed.

Thanks in advance.

---

### Post by papibe on 2012-04-14
Hi ads2996. Welcome to the forums!

A few ideas:
[LIST]
[*]To find and move files take a look at the command find (with option -excec).
[*]For converting files there are several command line options:
[LIST]
[*]mkvtoolnix with tools for mkv.
[*]gpac with tools for mp4s
[*]ffmpeg is the best command line media converter IMHO.
[/LIST]
[*]For streaming take a look at mediatomb and Ps3MediaServer.
[*]You'll need a bash script to automate the whole process.
[*]You could use crontab to set the script to run at specific times.
[/LIST]
I hope that helps, and tell us if you need more help with that.
Regards.

---

### Post by CharlesA on 2012-04-14
+1 to ffmpeg and ps3mediaserver.

I am not sure there is a single program that does what you want, but papibe has given you a nice breakdown of some of the ones out there. :)

---

### Post by Jonathan L on 2012-04-14
> **ads2996 said:**
> Hi

This is my first post, I'm trying to create a home server to stream to the PCs in myhouse and to my PS3

I was looking for a way to have a video converter installed that scans specefic folders looking for file formats such as .mkv and converting them and placing them in a specefic folder to be streamed.

Thanks in advance.

Hi Ads

What a great project.  For the occasional video conversions I do, I use ffmpeg with good results.

For the issue of automatically converting videos, which typically takes many minutes or longer to do, I'd suggest using crontab to launch a script which converts the first video.  If you're new to autoating things, crontab is a great way to do things, as you don't have to worry about long-running processes perhaps going wrong.  You write a single script to bite one chunk off the problem, and let crontab run it again and again.  In this particular case you only have to ensure you don't get lots of concurrent conversions, as they are likely to take a long time.

Here's such a script I was playing with, for converting gif images to png using Image Magick's "convert" program.   You'll need to adapt the part which goes 'gif' to deal with 'mkv' by choosing the appropriate flags for ffmpeg (or whatever you choose).

The idea is you have an input directory, perhaps /var/lib/upload
And an output directory, perhaps /var/www/video

It takes the first one in the input directory, converts it to the output directory, and moves the file there too.  Keeps a lock/status file "flag" so you only have one on the boil at a time.

```
#!/bin/sh

# autoconv
# autoconvert files from here to there
# jonathanl/2012-04014

# converts at most one file per run, intended for long conversions eg video
# ignores files younger than a certain age
# intended to be run from crontab
#       * * * * * /path/autoconv.sh /tmp/autoconv /var/lib/upload /var/www/video

if [ $# -lt 3 ]; then
        echo "Usage: $0 flagfile inputdir outputdir"
        exit 1
fi

MINAGE=180

flag="$1"
src="$2"
dst="$3"

# if already running, just quit
#
if [ -f $flag ]; then
        echo "$0: busy (`cat $flag`)"
        exit 0
fi

# find first file in input queue
#
file=''

for f in $src/* ; do

        # deal with empty input directory etc
        #
        if [ ! -f "$f" ]; then
                continue;
        fi

        # find out age
        #       ignore recent files
        #       might still be uploading
        #
        t=`stat --printf='%Y' "$f"`
        now="`date '+%s'`"
        age=$(($now - $t))

        if [ $age -lt $MINAGE ]; then
                echo "$f: ignoring recent ($age)"
                continue;
        fi

        # this is our file
        #
        file="$f"
        break
done

# just going to convert first one we found
#
if [ -e "$file" ]; then
        b=`basename "$file"`
        echo "$file found"

        # decide how to convert
        #
        case "$b" in
        *.[COLOR=Red]gif[/COLOR])
                echo "$file: converting"
                # do flag file
                echo "converting $file, started `date`" > $flag

                # the acutal convert
                [COLOR=Red]convert[/COLOR] "$file" "$dst/$b.png"

                # remove from input queue
                mv "$file" "$dst"

                # unlock
                rm $flag
                ;;
        *)
                echo "$file: ignoring"
                ;;
        esac

fi

# end
```Perhaps that will help you along the road.

Kind regards,
Jonathan.

---


---
title: "good looking bash commands"
date: 2013-04-13
forum: Ubuntu, Linux and OS Chat
---

### Post by scy on 2013-04-13
Hey everyone!

I wanted to start a thread about really clean and good looking bash commands. I'll start off.

I make os testbeds a lot out of older computers with floppy drives. To test if there is a floppy in the drive:

```
if sudo dd if=/dev/null of=/dev/fd0 >/dev/null 2>&1; then
    echo "Floppy is in drive 0."
else
    echo "No floppy in drive 0."
fi
```

It just tries to write null to the floppy and if there is an error then there is no floppy in the drive.

I thought this was pretty sweet when I came up with it :D

---

### Post by prodigy_ on 2013-04-13
First, having any output on success is wrong (it's not Windows, mate). Second, you used five lines and a **dd** invocation for something that could be achieved with **bash -c "exec 3< /dev/fd0" 2>&1 | grep 'No medium found'**. Clean indeed. ;)

---

### Post by scy on 2013-04-13
Thanks for raining on my parade :)

Can you explain that code?

---

### Post by scy on 2013-04-13
Seriously, though, improvement's what this thread is for.

 "In pursuit of the elusive clean command..." ;)

---

### Post by prodigy_ on 2013-04-13
Well, **bash -c "exec 3< /dev/fd0"** tries to open /dev/fd0 for reading to file descriptor 3 (0 is stdin, 1 is stdout and 2 is stderr). And 2>&1 redirects stderr to stdout to that we could grep on the error message. If a floppy is present in the drive the error message should be "Permission denied".

In a script that is running with root privileges you can simplify the whole thing to just **exec 3< /dev/fd0** and then check the $? (exit status) variable. 0 would mean there's a floppy in the drive and 1 would mean there isn't.

---

### Post by Primefalcon on 2013-04-13
> **scy said:**
> 
 "In pursuit of the elusive clean command..." ;)
```
sudo apt-get autoclean
```

---

### Post by andrew.46 on 2013-04-16
What about a simple script that converts almost all audio files to aac using NeroAacEnc? It does not do a lot of checking but I use it on my system for a quick and dirty conversion, as a bonus it also copies a couple of the  tags across :)

```

#!/bin/sh
# ----------------------------------------------- #
# Convert most audio files to aac using FFmpeg,   # 
# neroAacEnc and neroAacTag.                      #
# ----------------------------------------------- #      

# Select an input and output filename:

echo -n "Chose an input filename: "
read -e "INPUT"

echo -n "Chose an output filename: "
read -e "OUTPUT"

# Create some metatag variables from the input file:

TITLE=$(ffprobe "$INPUT" 2>&1 | grep -i 'TITLE' | sed 's/.\{24\}//')
ARTIST=$(ffprobe "$INPUT" 2>&1 | grep -i 'ARTIST' | sed 's/.\{24\}//')
ALBUM=$(ffprobe "$INPUT" 2>&1 | grep -i 'ALBUM' | sed 's/.\{24\}//')

# Convert the file to aac:

ffmpeg -i "$INPUT" -f wav - | \
          neroAacEnc -ignorelength -q 0.5 -if - -of "$OUTPUT"

# Add in the tags:

neroAacTag "$OUTPUT" \
           -meta:title="$TITLE" \
           -meta:artist="$ARTIST" \
           -meta:album="$ALBUM"

# Enjoy the music!!

```

Feel free to make this more useful....

---

### Post by evilsoup on 2013-04-16
You might want to look at ffprobe's -show_format, -show_streams and -select_stream options, which all output a single key=value pair per line (easier to regex)and output to stdout. For example,

```

TITLE=$(ffprobe "$INPUT" 2>&1 | grep -i 'TITLE' | sed 's/.\{24\}//')

```

could become:

```

TITLE=$(ffprobe -show_format "$INPUT" | grep -i 'TAG:title' | sed 's/.*=//')
##  or even...
TITLE=$(ffprobe -show_format "$INPUT" | sed -n '/TAG:title/s/.*=//p')

```

---


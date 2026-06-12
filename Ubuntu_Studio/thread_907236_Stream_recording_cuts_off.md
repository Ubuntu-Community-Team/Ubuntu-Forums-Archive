---
title: "Stream recording cuts off"
date: 2008-09-01
forum: Ubuntu Studio
---

### Post by jordon on 2008-09-01
I'm trying to use mplayer to record an audio stream for an hour. Cron manages to get the shell script running, but the recording stops after 15 or 20 minutes. I'm using a script from a [Linux Journal article]("http://www.linuxjournal.com/article/8171"), namely:

```
#!/bin/bash
DATE=`date +%F`  # Save the date as YYYY-MM-DD
YEAR=`date +%Y` # Save just the year as YYYY
FILE="/home/jordon/Desktop/Open Source Radio Hour - $DATE.mp3" # Where to save it
STREAM=http://kruufm.com/live.pls
DURATION=1h # length of the show

# For the id3v2 Tags
AUTHOR="James Moore"
ALBUM="KRUU-LP 100.1 Stream Rip"
TITLE="Open Source Radio Hour - $DATE"

# Use mplayer to capture the stream
# at $STREAM to the file $FILE
mplayer -really-quiet -cache 256 \
    -dumpfile "$FILE" -dumpaudio -playlist $STREAM &
# the & turns the capture into a background job

sleep $DURATION  # wait for the show to be over

kill $! # end the stream capture

# Tag the resulting captured .mp3
id3v2 -a "$AUTHOR" -A "$ALBUM" \
    -t "$TITLE" -y $YEAR -T 1/1 -g 255 \
    --TCON "Radio" "$FILE"
```

The metadata does get added after an hour has elapsed.

The only thing I can think of is to change mplayer's -cache option to a higher number, but I'm not sure. Ideas, anyone?

---

